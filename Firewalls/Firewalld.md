# `firewalld`

`firewalld` is a dynamic firewall management tool used in Linux distributions such as RHEL, CentOS, Fedora, and Rocky Linux. It provides a way to manage firewall rules without restarting services.  



## **Installation**  

### **Debian/Ubuntu**  
```bash
sudo apt install firewalld -y
```

### **RHEL/CentOS/Fedora**  
```bash
sudo yum install firewalld -y  # RHEL/CentOS
sudo dnf install firewalld -y  # Fedora
```

### **Enable and Start Firewalld**  
```bash
sudo systemctl enable firewalld --now
```



## **Syntax**  
```bash
firewall-cmd [options]
```



## **Examples**  

### **Reload & Reset Firewall**  

- **Reload Firewall Rules**  
  ```bash
  firewall-cmd --reload
  ```

- **Completely Reload Firewall**  
  ```bash
  firewall-cmd --complete-reload
  ```

- **Reset to Default Zone**  
  ```bash
  firewall-cmd --reset-default-zone
  ```



### **View Active Firewall Settings**  

- **Check Firewalld Status**  
  ```bash
  firewall-cmd --state
  ```

- **Get Active Zones**  
  ```bash
  firewall-cmd --get-active-zones
  ```

- **Get Default Zone**  
  ```bash
  firewall-cmd --get-default-zone
  ```

- **List All Available Zones**  
  ```bash
  firewall-cmd --get-zones
  ```

- **List All Configured Zones**  
  ```bash
  firewall-cmd --list-all-zones
  ```

- **List All Active Firewall Services**  
  ```bash
  firewall-cmd --get-services
  ```

- **List Interfaces Assigned to Zones**  
  ```bash
  firewall-cmd --list-interfaces
  ```

- **List Rich Rules (Advanced Rules)**  
  ```bash
  firewall-cmd --list-rich-rules
  ```



### **Managing Firewall Zones & Interfaces**  

- **Change Default Zone Permanently**  
  ```bash
  firewall-cmd --set-default-zone=work --permanent
  ```

- **Assign an Interface to a Zone**  
  ```bash
  firewall-cmd --zone=home --change-interface=eth0 --permanent
  ```

- **Remove an Interface from a Zone**  
  ```bash
  firewall-cmd --zone=home --remove-interface=eth0 --permanent
  ```



### **Managing Ports & Services**  

- **Add a Port to a Zone**  
  ```bash
  firewall-cmd --zone=public --add-port=8080/tcp --permanent
  ```

- **Remove a Port from a Zone**  
  ```bash
  firewall-cmd --zone=public --remove-port=8080/tcp --permanent
  ```

- **Add a Service to a Zone**  
  ```bash
  firewall-cmd --zone=public --add-service=http --permanent
  ```

- **Remove a Service from a Zone**  
  ```bash
  firewall-cmd --zone=public --remove-service=http --permanent
  ```

- **List All Rules in a Zone**  
  ```bash
  firewall-cmd --zone=public --list-all
  ```

- **List Open Ports in a Zone**  
  ```bash
  firewall-cmd --zone=public --list-ports
  ```

- **List Enabled Services in a Zone**  
  ```bash
  firewall-cmd --zone=public --list-services
  ```



### **Forwarding & Masquerading**  

- **Enable Port Forwarding (8080 → 80)**  
  ```bash
  firewall-cmd --zone=public --add-forward-port=port=8080:proto=tcp:toport=80 --permanent
  ```

- **Enable Masquerading (NAT for Internet Sharing)**  
  ```bash
  firewall-cmd --zone=public --add-masquerade --permanent
  ```

- **Disable Masquerading**  
  ```bash
  firewall-cmd --zone=public --remove-masquerade --permanent
  ```



### **Managing Rich Rules (Advanced Rules)**  

- **Allow Specific IP Address**  
  ```bash
  firewall-cmd --zone=public --add-rich-rule='rule family="ipv4" source address="192.168.1.100" accept' --permanent
  ```

- **Block Specific IP Address**  
  ```bash
  firewall-cmd --zone=public --add-rich-rule='rule family="ipv4" source address="192.168.1.100" reject' --permanent
  ```

- **Remove a Rich Rule**  
  ```bash
  firewall-cmd --zone=public --remove-rich-rule='rule family="ipv4" source address="192.168.1.100" reject' --permanent
  ```



### **Other Useful Commands**  

- **Convert Runtime Rules to Permanent Rules**  
  ```bash
  firewall-cmd --runtime-to-permanent
  ```

- **Set Firewall to Log Denied Packets**  
  ```bash
  firewall-cmd --set-log-denied=all
  ```