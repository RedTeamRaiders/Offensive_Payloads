# **Network Configuration**  

Network configuration in Linux involves setting up and managing network interfaces, IP addresses, DNS settings, and routing tables. Different distributions use various tools, such as `ip`, `ifconfig`, `nmcli`, and `nmtui`, to configure networking.  

- [`hostname`](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Network-Configuration/Hostname.md)  
- [`ifconfig`](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Network-Configuration/Ifconfig.md)
- [`ip`](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Network-Configuration/IP.md)
- [`nmtui` and `nmcli`](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Network-Configuration/Nmtui-and-Nmcli.md)
- [Viewing Public IP](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Network-Configuration/Public-IP.md)



## **Important Network Terms**  

- **`enp0s3`** → Ethernet interface (PCI-based naming)  
- **`wlan0`** → First Wi‑Fi interface  
- **`lo`** → Loopback (self‑communication)  



# **Manually Configuring Network Settings**  

## **Viewing and Configuring DNS**  

- **View Current DNS Configuration**  
  ```bash
  cat /etc/resolv.conf
  ```
  *Note:* If managed by NetworkManager, changes may be overridden.

- **Temporarily Change DNS**  
  ```bash
  echo "nameserver 8.8.8.8" > /etc/resolv.conf
  ```

- **Permanent DNS Configuration**  

  - **Debian/Ubuntu (`/etc/network/interfaces`)**  
    ```bash
    dns-nameservers 8.8.8.8 8.8.4.4
    ```

  - **RHEL/CentOS (`/etc/NetworkManager/system-connections/XXXXX.nmconnection`)**  
    ```bash
    dns=8.8.8.8;8.8.4.4;
    ```



## **Viewing and Modifying Hostname**  

- **Check Current Hostname**  
  ```bash
  cat /etc/hostname
  ```



- **List All Network Interfaces and Their Statistics**  
  ```bash
  cat /proc/net/dev
  ```



## **Configuring IP Address Using NetworkManager**  

Network configuration is managed through connection files in NetworkManager.

1. **Navigate to the NetworkManager Directory**  
   ```bash
   cd /etc/NetworkManager/system-connections/
   ```

2. **Edit the Connection File (`enp0s3` as an example)**  
   ```bash
   vim enp0s3.nmconnection
   ```



## **Static IP Configuration Examples**  

### **Debian/Ubuntu (`/etc/network/interfaces`)**  
```bash
auto enp0s3
iface enp0s3 inet static
    address 192.168.1.34
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 8.8.8.8 8.8.4.4
```

### **RHEL/CentOS (`/etc/NetworkManager/system-connections/`)**  
```ini
[connection]
id=enp0s3
uuid=a32babc0-fbae-3089-b858-40d62bd6d445
type=ethernet
autoconnect-priority=-999
interface-name=enp0s3
timestamp=1739793171

[ethernet]

[ipv4]
address1=192.168.1.34/24
dns=8.8.8.8;8.8.4.4;
gateway=192.168.1.1
method=manual

[ipv6]
addr-gen-mode=eui64
method=disabled

[proxy]
```



## **Dynamic IP Configuration Example**  
```ini
[connection]
id=enp0s3
uuid=a32babc0-fbae-3089-b858-40d62bd6d445
type=ethernet
autoconnect-priority=-999
interface-name=enp0s3
timestamp=1739793171

[ethernet]

[ipv4]
method=auto

[ipv6]
addr-gen-mode=eui64
method=disabled

[proxy]
```



## **Assigning Multiple IPs to a Single Interface**  
```ini
[connection]
id=enp0s3
uuid=a32babc0-fbae-3089-b858-40d62bd6d445
type=ethernet
autoconnect-priority=-999
interface-name=enp0s3
timestamp=1739793171

[ethernet]

[ipv4]
address1=192.168.1.34/24
address2=192.168.1.35/24
address3=192.168.1.36/24
address4=192.168.1.37/24
dns=8.8.8.8;8.8.4.4;
gateway=192.168.1.1
method=manual

[ipv6]
addr-gen-mode=eui64
method=disabled

[proxy]
```