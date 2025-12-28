# `netstat`

The `netstat` (network statistics) command is used to display network connections, routing tables, interface statistics, and more. It is useful for monitoring active connections and troubleshooting network-related issues.  



## **Installation**  

### **Debian/Ubuntu**  
```bash
sudo apt install net-tools -y
```

### **RHEL/CentOS/Fedora**  
```bash
sudo yum install net-tools -y  # RHEL/CentOS
sudo dnf install net-tools -y  # Fedora
```



## **Syntax**  
```bash
netstat [options]
```



## **Examples**  

- **Show All Active Network Connections**  
  ```bash
  netstat
  ```

- **Display Active Connections with Numeric Addresses**  
  ```bash
  netstat -n
  ```

- **Show All Open Network Connections (TCP & UDP, Listening & Established)**  
  ```bash
  netstat -a
  ```

- **Display Only TCP Connections**  
  ```bash
  netstat -t
  ```

- **Display Only UDP Connections**  
  ```bash
  netstat -u
  ```

- **Show Listening Ports (Services Waiting for Connections)**  
  ```bash
  netstat -l
  ```

- **Display the Process ID (PID) and Program Name Associated with Connections**  
  ```bash
  netstat -p
  ```

- **Monitor Active Network Connections Continuously**  
  ```bash
  netstat -c
  ```

- **Show Kernel Routing Table**  
  ```bash
  netstat -r
  ```

- **Display Network Interface Statistics**  
  ```bash
  netstat -i
  ```

- **Show Summary Statistics for Each Protocol (TCP, UDP, ICMP, etc.)**  
  ```bash
  netstat -s
  ```

- **Show All Active Network Connections with Numeric Addresses**  
  ```bash
  netstat -an
  ```

- **Show Only TCP and UDP Connections**  
  ```bash
  netstat -ut
  ```

- **Display Detailed Interface Statistics**  
  ```bash
  netstat -ie
  ```

- **Show Listening TCP and UDP Ports**  
  ```bash
  netstat -ltun
  ```

- **List All Open Ports Along with Process Names**  
  ```bash
  netstat -nltup
  ```

- **Show Active TCP Connections with Process Names**  
  ```bash
  netstat -natup
  ```
