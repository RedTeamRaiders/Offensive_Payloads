# `hostname`  
The `hostname` command is used to display or set the system's hostname in Linux.

## **Syntax**  
```bash
hostname [options] [new_hostname]
```


## **Examples**  

### **Displaying Hostname**  

- **Show the current hostname**  
  ```bash
  hostname
  ```

- **Show the system's fully qualified domain name (FQDN)**  
  ```bash
  hostname -f
  ```

- **Show all network addresses associated with the hostname**  
  ```bash
  hostname -A
  ```

- **Show the short hostname**  
  ```bash
  hostname -s
  ```

- **Show the IP address of the hostname**  
  ```bash
  hostname -I
  ```

---

### **Changing the Hostname**  

- **Temporarily change the hostname** *(Resets after reboot)*  
  ```bash
  hostname new_hostname
  ```

- **Permanently change the hostname on modern Linux systems**  
  ```bash
  hostnamectl set-hostname new_hostname
  ```

- **Verify the new hostname**  
  ```bash
  hostnamectl
  ```

---

### **Managing Hostname with `hostnamectl`**  

- **Display detailed hostname information**  
  ```bash
  hostnamectl status
  ```

- **Set a new static hostname**  
  ```bash
  hostnamectl set-hostname new_hostname
  ```

- **Set a pretty hostname (for display purposes only)**  
  ```bash
  hostnamectl set-hostname "My Server" --pretty
  ```

- **Set a transient hostname (valid until reboot)**  
  ```bash
  hostnamectl set-hostname temp-hostname --transient
  ```

---

### **Editing the Hostname Manually**  

- **Edit the `/etc/hostname` file for permanent changes**  
  ```bash
  nano /etc/hostname
  ```

- **Edit the `/etc/hosts` file to map the hostname to an IP**  
  ```bash
  nano /etc/hosts
  ```

  Add or modify the following line:  
  ```
  127.0.0.1   new_hostname
  ```

- **Apply the changes without rebooting**  
  ```bash
  systemctl restart systemd-hostnamed
  ```

---

### **Verifying Network Information Related to Hostname**  

- **Check system's domain name**  
  ```bash
  domainname
  ```

- **Check network information related to the hostname**  
  ```bash
  uname -n
  ```

- **Check the DNS domain of the system**  
  ```bash
  dnsdomainname
  ```

