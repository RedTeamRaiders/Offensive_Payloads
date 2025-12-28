# **nftables Command Guide**  

`nftables` is the modern replacement for `iptables`, introduced in Linux kernel 3.13. It provides better performance, a more unified syntax, and enhanced features for firewall and packet filtering.  



## **Installation**  

### **Debian/Ubuntu**  
```bash
sudo apt install nftables -y
```

### **RHEL/CentOS/Fedora**  
```bash
sudo yum install nftables -y  # RHEL/CentOS  
sudo dnf install nftables -y  # Fedora  
```

### **Enable nftables Service**  
```bash
sudo systemctl enable nftables --now
```



## **Basic Syntax & Commands**  

- **Start the `nftables` Interactive Shell**  
  ```bash
  nft
  ```

- **List All Active Rules**  
  ```bash
  nft list ruleset
  ```

- **Flush (Clear) All Rules**  
  ```bash
  nft flush ruleset
  ```

- **Save Rules to a File**  
  ```bash
  nft list ruleset > /etc/nftables.conf
  ```

- **Load Rules from a File**  
  ```bash
  nft -f /etc/nftables.conf
  ```

- **Check `nftables` Status**  
  ```bash
  systemctl status nftables
  ```



## **Creating a Simple Firewall Rule Set**  

1. **Create a New Ruleset**  
   ```bash
   nft add table inet my_filter
   nft add chain inet my_filter input { type filter hook input priority 0 \; }
   ```

2. **Set Default Policy (Drop All Incoming Traffic by Default)**  
   ```bash
   nft add rule inet my_filter input drop
   ```

3. **Allow Established Connections**  
   ```bash
   nft add rule inet my_filter input ct state established,related accept
   ```

4. **Allow SSH (Port 22)**  
   ```bash
   nft add rule inet my_filter input ip protocol tcp dport 22 accept
   ```

5. **Allow HTTP & HTTPS (Ports 80, 443)**  
   ```bash
   nft add rule inet my_filter input ip protocol tcp dport { 80, 443 } accept
   ```

6. **Allow ICMP (Ping)**  
   ```bash
   nft add rule inet my_filter input ip protocol icmp accept
   ```

7. **Save the Ruleset Permanently**  
   ```bash
   nft list ruleset > /etc/nftables.conf
   ```

8. **Enable Automatic Loading on Boot**  
   ```bash
   systemctl enable nftables
   ```



## **Managing NAT (Network Address Translation)**  

- **Enable Masquerading (For Internet Sharing)**  
  ```bash
  nft add table ip nat
  nft add chain ip nat postrouting { type nat hook postrouting priority 100 \; }
  nft add rule ip nat postrouting oifname "eth0" masquerade
  ```

- **Port Forwarding (Redirect Port 80 to Internal Server 192.168.1.100:8080)**  
  ```bash
  nft add rule ip nat prerouting iifname "eth0" tcp dport 80 dnat to 192.168.1.100:8080
  ```



## **Logging & Monitoring**  

- **Log Dropped Packets**  
  ```bash
  nft add rule inet my_filter input log prefix "Dropped: " level debug drop
  ```

- **View Packet Statistics for a Chain**  
  ```bash
  nft list chain inet my_filter input
  ```



## **Deleting Rules & Tables**  

- **Delete a Specific Rule (Example: SSH Allow Rule)**  
  ```bash
  nft delete rule inet my_filter input ip protocol tcp dport 22 accept
  ```

- **Delete a Chain**  
  ```bash
  nft delete chain inet my_filter input
  ```

- **Delete a Table**  
  ```bash
  nft delete table inet my_filter
  ```
