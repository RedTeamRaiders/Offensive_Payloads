# `ufw`

UFW (Uncomplicated Firewall) is a simple yet powerful command-line tool for managing firewall rules on Linux, primarily used in Debian-based distributions like Ubuntu.



## **Installation & Service Management**  

- **Install UFW**  
  ```bash
  sudo apt install ufw -y
  ```
- **Enable UFW**  
  ```bash
  sudo ufw enable
  ```

- **Disable UFW**  
  ```bash
  sudo ufw disable
  ```

- **Reload UFW**  
  ```bash
  sudo ufw reload
  ```

- **Reset UFW to Default Settings**  
  ```bash
  sudo ufw reset
  ```

- **Check UFW Service Status**  
  ```bash
  sudo systemctl status ufw.service
  ```

- **Enable UFW on System Boot**  
  ```bash
  sudo systemctl enable ufw.service
  ```

- **Start UFW Service**  
  ```bash
  sudo systemctl start ufw.service
  ```

## **Checking Firewall Status**  

- **View UFW Status**  
  ```bash
  sudo ufw status
  ```

- **View Detailed Status**  
  ```bash
  sudo ufw status verbose
  ```

- **View Status with Rule Numbers**  
  ```bash
  sudo ufw status numbered
  ```



## **Allowing Connections**  

- **Allow SSH (Port 22, TCP)**  
  ```bash
  sudo ufw allow ssh
  ```
  ```
  sudo ufw allow 22/tcp
  ```

- **Allow Web Traffic (HTTP & HTTPS)**  
  ```bash
  sudo ufw allow http
  ```
  ```
  sudo ufw allow https
  ```
  ```
  sudo ufw allow 80
  ```

- **Allow Specific Ports**  
  ```bash
  sudo ufw allow 53/udp
  ```
  ```
  sudo ufw allow 8088/tcp
  ```

- **Allow Port Range (TCP & UDP)**  
  ```bash
  sudo ufw allow 1000:2000/tcp
  ```
  ```
  sudo ufw allow 5000:5100/udp
  ```

- **Allow Specific IP Address**  
  ```bash
  sudo ufw allow from 192.168.1.100
  ```

- **Allow IP Address to a Specific Port**  
  ```bash
  sudo ufw allow from 192.168.1.50 to any port 22 proto tcp
  ```

- **Allow Entire Subnet**  
  ```bash
  sudo ufw allow from 192.168.1.0/24
  ```

- **Allow Traffic to a Specific Destination**  
  ```bash
  sudo ufw allow to 192.168.1.200 port 22 proto tcp
  ```

- **Allow Traffic on a Specific Interface**  
  ```bash
  sudo ufw allow in on eth0 to any port 22 proto tcp
  ```



## **Blocking & Rejecting Traffic**  

- **Deny SSH (Port 22, TCP)**  
  ```bash
  sudo ufw deny 22/tcp
  ```

- **Deny Specific Ports**  
  ```bash
  sudo ufw deny 53/udp
  ```
  ``` 
  sudo ufw deny 6000:7000/tcp
  ```

- **Deny Specific IP Address**  
  ```bash
  sudo ufw deny from 192.168.1.50
  ```

- **Deny Specific IP to a Port**  
  ```bash
  sudo ufw deny from 192.168.1.52 to any port 22 proto tcp
  ```

- **Deny an Entire Subnet**  
  ```bash
  sudo ufw deny from 10.10.10.0/24
  ```

- **Deny Traffic to a Specific Destination**  
  ```bash
  sudo ufw deny to 192.168.1.44 port 22 proto tcp
  ```

- **Reject RDP (Port 3389, TCP)**  
  ```bash
  sudo ufw reject 3389/tcp
  ```

- **Reject Specific IP to a Port**  
  ```bash
  sudo ufw reject from 192.168.1.45 to any port 22 proto tcp
  ```

- **Reject Traffic to a Destination**  
  ```bash
  sudo ufw reject to 192.168.1.33 port 22 proto tcp
  ```



## **Rate Limiting (Prevent Brute Force Attacks)**  

- **Limit SSH Login Attempts**  
  ```bash
  sudo ufw limit ssh
  ```

- **Limit HTTPS (Port 443, TCP)**  
  ```bash
  sudo ufw limit 443/tcp
  ```

- **Limit Access for a Specific IP to a Port**  
  ```bash
  sudo ufw limit from 192.168.1.50 to any port 22 proto tcp
  ```



## **Routing & NAT Rules**  

- **Allow Forwarding Between Interfaces**  
  ```bash
  sudo ufw route allow in on eth1 out on eth0 to any port 80 proto tcp
  ```

- **Deny Forwarding Between Interfaces**  
  ```bash
  sudo ufw route deny in on eth1 out on eth0 to 192.168.2.100
  ```

- **Enable NAT for a Specific Subnet (eth0 interface)**  
  Edit `/etc/ufw/before.rules` and add:  
  ```bash
  echo "net/ipv4/ip_forward=1" >> /etc/ufw/sysctl.conf
  ```



## **Managing Rules**  

- **View Rules with Numbers**  
  ```bash
  sudo ufw status numbered
  ```

- **Delete a Rule by Number**  
  ```bash
  sudo ufw delete 3
  ```
  ```
  sudo ufw delete 12
  ```

- **Delete a Specific Rule**  
  ```bash
  sudo ufw delete allow 90:99/tcp
  ```
  ```
  sudo ufw delete allow from 192.168.1.28 to any port 22 proto tcp
  ```



## **Logging & Monitoring**  

- **Enable Logging**  
  ```bash
  sudo ufw logging on
  ```

- **Set Logging Level (Low, Medium, High, Full)**  
  ```bash
  sudo ufw logging high
  ```

- **Disable Logging**  
  ```bash
  sudo ufw logging off
  ```

- **View Firewall Logs in Real-Time**  
  ```bash
  tail -f /var/log/ufw.log
  ```



## **Application Profiles**  

- **List Available Application Profiles**  
  ```bash
  sudo ufw app list
  ```

- **View Details of a Specific Application Profile**  
  ```bash
  sudo ufw app info "Apache"
  ```

- **Allow a Service Using an Application Profile**  
  ```bash
  sudo ufw allow "Apache Full"
  ```



## **Other UFW Commands**  

- **Show Raw Rules**  
  ```bash
  sudo ufw show raw
  ```

- **Show Recently Added Rules**  
  ```bash
  sudo ufw show added
  ```

- **Check UFW Version**  
  ```bash
  sudo ufw version
  ```