# **`ss` Command (Socket Statistics)**  

The `ss` command is a powerful replacement for `netstat`, used to display detailed network socket information, including open ports, established connections, and listening services. It is faster and more efficient than `netstat` in modern Linux distributions. 

## **Installation**  

### **Debian/Ubuntu**  
```bash
sudo apt install iproute2 -y
```

### **RHEL/CentOS/Fedora**  
```bash
sudo yum install iproute -y  # RHEL/CentOS
sudo dnf install iproute -y  # Fedora
```



## **Syntax**  
```bash
ss [options]
```



## **Examples**  

- **Show All Network Connections**  
  ```bash
  ss -a
  ```

- **Display Only TCP Connections**  
  ```bash
  ss -t
  ```

- **Display Only UDP Connections**  
  ```bash
  ss -u
  ```

- **List Only Listening Ports**  
  ```bash
  ss -l
  ```

- **Show All Listening TCP Ports**  
  ```bash
  ss -lt
  ```

- **Show All Listening UDP Ports**  
  ```bash
  ss -lu
  ```

- **Display Process Name and PID with Open Sockets**  
  ```bash
  ss -p
  ```

- **Show Connections with Process Information (PID & Name)**  
  ```bash
  ss -tulpn
  ```

- **List Established TCP Connections**  
  ```bash
  ss -t state established
  ```

- **Display Connections in Listening State**  
  ```bash
  ss -t state listening
  ```

- **Show Summary of Network Connections**  
  ```bash
  ss -s
  ```

- **List IPv4 and IPv6 Sockets**  
  ```bash
  ss -4   # IPv4
  ss -6   # IPv6
  ```

- **Filter Connections for a Specific Port (e.g., Port 22 - SSH)**  
  ```bash
  ss -tulpn | grep :22
  ```

- **Show Sockets Using a Specific Network Interface**  
  ```bash
  ss -i
  ```

- **Display Only IPv4 TCP Connections**  
  ```bash
  ss -t4
  ```

- **Display Only IPv6 TCP Connections**  
  ```bash
  ss -t6
  ```