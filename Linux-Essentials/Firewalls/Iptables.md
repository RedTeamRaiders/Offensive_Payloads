# **iptables Command Guide**  

`iptables` is a powerful firewall tool in Linux used to configure packet filtering rules. It is part of the Netfilter framework and operates on different tables (filter, nat, mangle, raw, and security).  



## **Installation**  

### **Debian/Ubuntu**  
```bash
sudo apt install iptables -y
```

### **RHEL/CentOS/Fedora**  
```bash
sudo yum install iptables-services -y  # RHEL/CentOS  
sudo dnf install iptables -y  # Fedora  
```

### **Enable iptables Service**  
```bash
sudo systemctl enable iptables --now
```



## **Syntax**  
```bash
iptables [options] chain rule
```

- `-A` → Append a rule  
- `-D` → Delete a rule  
- `-F` → Flush rules  
- `-L` → List rules  
- `-P` → Set default policy  
- `-t` → Specify a table (filter, nat, mangle)  



## **Managing iptables Rules**  

### 🔄 **Flush & List Rules**  

- **Flush All Rules**  
  ```bash
  iptables -F
  ```

- **Flush Only INPUT Chain**  
  ```bash
  iptables -F INPUT
  ```

- **List All Rules Verbosely**  
  ```bash
  iptables -L -v -n
  ```

- **List Rules in the `filter` Table**  
  ```bash
  iptables -t filter -L
  ```



### 🎯 **Saving & Restoring Rules**  

- **Save Current Rules**  
  ```bash
  iptables-save > /etc/iptables.rules
  ```

- **Restore Saved Rules**  
  ```bash
  iptables-restore < /etc/iptables.rules
  ```



### 🚪 **Setting Default Policies**  

- **Drop All Incoming Traffic by Default**  
  ```bash
  iptables -P INPUT DROP
  ```

- **Allow All Incoming Traffic by Default**  
  ```bash
  iptables -P INPUT ACCEPT
  ```



### 🔥 **Allowing & Blocking Traffic**  

- **Allow SSH (Port 22)**  
  ```bash
  iptables -A INPUT -p tcp --dport 22 -j ACCEPT
  ```

- **Allow HTTP & HTTPS (Ports 80, 443)**  
  ```bash
  iptables -A INPUT -p tcp -m multiport --dports 80,443 -j ACCEPT
  ```

- **Block All Incoming Traffic**  
  ```bash
  iptables -A INPUT -j DROP
  ```

- **Allow Traffic from a Specific IP (192.168.1.100)**  
  ```bash
  iptables -A INPUT -s 192.168.1.100 -j ACCEPT
  ```

- **Block Traffic from a Specific IP (192.168.1.100)**  
  ```bash
  iptables -A INPUT -s 192.168.1.100 -j DROP
  ```

- **Remove a Specific Rule (Example: Remove SSH Allow Rule)**  
  ```bash
  iptables -D INPUT -p tcp --dport 22 -j ACCEPT
  ```



### ⚡ **Rate Limiting & Connection Tracking**  

- **Limit SSH Connections to 10 per Minute**  
  ```bash
  iptables -A INPUT -p tcp --dport 22 -m limit --limit 10/min -j ACCEPT
  ```

- **Drop Invalid Packets**  
  ```bash
  iptables -A INPUT -m conntrack --ctstate INVALID -j DROP
  ```



### 🌍 **Network Address Translation (NAT)**  

- **Enable Masquerading (For Internet Sharing)**  
  ```bash
  iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
  ```

- **Forward Incoming Port 80 Traffic to 192.168.1.100:8080**  
  ```bash
  iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination 192.168.1.100:8080
  ```



### 📜 **Logging & Monitoring Traffic**  

- **Log Dropped Packets**  
  ```bash
  iptables -A INPUT -j LOG --log-prefix "DROPPED: " --log-level 4
  ```

- **Add a Comment to a Rule**  
  ```bash
  iptables -A INPUT -j ACCEPT -m comment --comment "Count accepted packets"
  ```



### 🔄 **Saving & Enabling iptables on Boot**  

- **Save Current Rules Permanently**  
  ```bash
  iptables-save > /etc/iptables.rules
  ```

- **Enable iptables on Boot (Systemd)**  
  ```bash
  systemctl enable iptables
  ```
