# TCPDump COMMANDS

TCPDump is a command-line packet analyzer that captures and inspects network traffic in real time. It is widely used for troubleshooting, security analysis, protocol debugging, and network monitoring. While it provides packet capture functionality similar to Wireshark, it is a separate tool designed for command-line environments.

---

## Installation

### On RHEL/CentOS
Install using yum:

```
yum install tcpdump
```

### On Debian/Ubuntu
Install using apt:

```
apt install tcpdump
```

### Verify Installation
To check the installed version:

```
tcpdump --version
```

---

## Basic Usage

### Display Help Information
To view available options and usage instructions:

```
tcpdump -h
```

### List Available Interfaces
Display all network interfaces (including virtual, Docker, etc.) that can be used for packet capture:

```
tcpdump -D
```
```
tcpdump --list-interfaces
```

Example output:
```
1.enp0s3 [Up, Running, Connected]
2.any (Pseudo-device that captures on all interfaces) [Up, Running]
3.lo [Up, Running, Loopback]
4.bluetooth-monitor (Bluetooth Linux Monitor) [Wireless]
5.usbmon2 (Raw USB traffic, bus number 2)
6.usbmon1 (Raw USB traffic, bus number 1)
7.usbmon0 (Raw USB traffic, all USB buses) [none]
8.nflog (Linux netfilter log (NFLOG) interface) [none]
9.nfqueue (Linux netfilter queue (NFQUEUE) interface) [none]
```

### Capture on Default Interface
To start a packet capture on the default interface (using enp0s3 everywhere):

```
tcpdump -i enp0s3
```

---

## Analyzing TCPDump Output

A typical TCPDump output might look like this:

```
20:43:56.123456 IP 192.168.1.10.34256 > 8.8.8.8.53: UDP, length 64
```

Key components:
- **Timestamp:** `20:43:56.123456` – when the packet was captured.
- **Protocol:** `IP` indicates the protocol used (IP, TCP, UDP, etc.).
- **Source:** `192.168.1.10.34256` – source IP address and port.
- **Direction:** `>` indicates the flow of the packet.
- **Destination:** `8.8.8.8.53` – destination IP address and port.
- **Packet Details:** e.g., `UDP, length 64` shows protocol specifics and packet size.

---

## Capturing Packets

### Capture on a Specific Interface
To capture packets on interface enp0s3:

```
tcpdump -i enp0s3
```

### Capture Only TCP or UDP Packets
- **TCP Packets:**

  ```
  tcpdump -i enp0s3 tcp
  ```

- **UDP Packets:**

  ```
  tcpdump -i enp0s3 udp
  ```

### Avoid DNS Resolution
To display only numerical IP addresses (avoid hostname resolution):

- **For TCP packets:**

  ```
  tcpdump -n -i enp0s3 tcp
  ```

- **For UDP packets:**

  ```
  tcpdump -n -i enp0s3 udp
  ```

### Limit Packet Capture Count
Capture only a specific number of packets (e.g., 10 packets):

```
tcpdump -c 10 -i enp0s3
```

---

## Filters

TCPDump offers a versatile filtering system that allows you to capture only the traffic of interest. Filters can be based on protocol, host, port, network range, packet size, or even complex combinations using logical operators.

### Filter by Protocol
- **ARP Traffic:**

  ```
  tcpdump -i enp0s3 arp
  ```

- **IP Traffic (IPv4):**

  ```
  tcpdump -i enp0s3 ip
  ```

- **IPv6 Packets:**

  ```
  tcpdump -i enp0s3 ip6
  ```

- **ICMPv6 Traffic:**

  ```
  tcpdump -i enp0s3 icmp6
  ```

- **IPsec ESP Traffic:**

  ```
  tcpdump -i enp0s3 esp
  ```

- **GRE Tunnels:**

  ```
  tcpdump -i enp0s3 gre
  ```

- **IGMP (Multicast) Traffic:**

  ```
  tcpdump -i enp0s3 igmp
  ```

- **VLAN-Tagged Packets:**

  ```
  tcpdump -i enp0s3 vlan
  ```

### Filter by Host
- **From or To a Specific Host:**

  ```
  tcpdump -i enp0s3 host 192.168.1.1
  ```

- **Based on Source Host:**

  ```
  tcpdump -i enp0s3 src host 192.168.1.1
  ```

- **Based on Destination Host:**

  ```
  tcpdump -i enp0s3 dst host 192.168.1.2
  ```

### Filter by Source or Destination Network Range

- **Capture traffic for a specific subnet (e.g., 192.168.1.0/24):**
  
  ```
  tcpdump -i enp0s3 net 192.168.1.0/24
  ```
- **Source Network Range:**

  ```
  tcpdump -i enp0s3 src net 192.168.1.0/24
  ```

- **Destination Network Range:**

  ```
  tcpdump -i enp0s3 dst net 192.168.1.0/24
  ```

### Filter by Port
- **Single Port Filter (e.g., HTTP on port 80):**

  ```
  tcpdump -i enp0s3 port 80
  ```

- **Source Port:**

  ```
  tcpdump -i enp0s3 src port 443
  ```

- **Destination Port:**

  ```
  tcpdump -i enp0s3 dst port 53
  ```
  
### Combining Filters
Use logical operators (`and`, `or`, `not`) to combine multiple filters.

- **HTTP Traffic on Port 80 or 443:**

  ```
  tcpdump -i enp0s3 port 80 or port 443
  ```

- **Capture DNS Queries (Port 53) but Exclude a Specific Host:**

  ```
  tcpdump -i enp0s3 port 53 and not host 192.168.1.100
  ```

- **Capture Traffic from a Specific Source and Going to a Specific Port:**

  ```
  tcpdump -i enp0s3 src host 192.168.1.10 and dst port 80
  ```

### Traffic Direction Filters
- **Only Incoming Traffic:**

  ```
  tcpdump -i enp0s3 inbound
  ```

- **Only Outgoing Traffic:**

  ```
  tcpdump -i enp0s3 outbound
  ```

### Filter by Packet Size
- **Packets Larger Than 1000 Bytes:**

  ```
  tcpdump -i enp0s3 greater 1000
  ```

- **Packets Smaller Than 500 Bytes:**

  ```
  tcpdump -i enp0s3 less 500
  ```

---

## Saving and Reading Captures

### Save Captured Packets to a File
To capture packets on enp0s3 and save them for later analysis:

```
tcpdump -w capture.pcap -i enp0s3
```

*Example:* Save UDP packets on port 53 to a file:

```
tcpdump -n -i enp0s3 udp port 53 -w dnsdump.pcap
```

### Read a Saved Capture File
To analyze or review a previously captured file:

```
tcpdump -r capture.pcap
```

---

## Additional Options

### Verbose Output
Capture packets with extra detail:

```
tcpdump -vv -i enp0s3
```

### Capture and Display Packet Contents
- **Hexadecimal Output Only:**

  ```
  tcpdump -x -i enp0s3
  ```

- **Hex and ASCII Output:**

  ```
  tcpdump -X -i enp0s3
  ```

- **ASCII Output Only (ideal for HTTP traffic):**

  ```
  tcpdump -A -i enp0s3
  ```

---

## Common Use Cases

- Troubleshooting network issues.
- Capturing and analyzing HTTP, DNS, and SSH traffic.
- Detecting malicious network traffic and security threats.
- Monitoring network performance.
- Debugging client-server communications.

---
