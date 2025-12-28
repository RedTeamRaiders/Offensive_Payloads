The `nmtui` and `nmcli` commands are used for managing network connections in Linux.  

- **`nmtui` (Network Manager Text User Interface):** A graphical, text-based utility.  
- **`nmcli` (Network Manager Command Line Interface):** A command-line tool for advanced network management.  


## **Installation**  
On **RHEL/CentOS/Fedora**:  
```bash
yum install NetworkManager-tui -y
```
or  
```bash
dnf install NetworkManager-tui -y
```

On **Debian/Ubuntu**:  
```bash
apt install network-manager -y
```


## **`nmtui`**  

- **Start `nmtui` (Graphical Interface)**  
  ```bash
  nmtui
  ```

- **Edit a connection**  
  ```bash
  nmtui edit enp0s3
  ```

- **Activate a connection**  
  ```bash
  nmtui connect enp0s3
  ```

- **Deactivate a connection**  
  ```bash
  nmtui disconnect enp0s3
  ```

- **Set hostname**  
  ```bash
  nmtui hostname new-hostname
  ```


## **`nmcli`**  

- **Show all network connections**  
  ```bash
  nmcli connection show
  ```

- **Show active network interfaces**  
  ```bash
  nmcli device status
  ```

- **Show IP addresses and details**  
  ```bash
  nmcli device show
  ```

- **Enable a network interface (`enp0s3`)**  
  ```bash
  nmcli connection up enp0s3
  ```

- **Disable a network interface (`enp0s3`)**  
  ```bash
  nmcli connection down enp0s3
  ```

- **Add a new connection with static IP**  
  ```bash
  nmcli connection add type ethernet ifname enp0s3 con-name my-static-ip ipv4.addresses 192.168.1.100/24 gw4 192.168.1.1 ipv4.dns 8.8.8.8 ipv4.method manual
  ```

- **Modify an existing connection (`enp0s3`)**  
  ```bash
  nmcli connection modify enp0s3 ipv4.addresses 192.168.1.110/24 ipv4.gateway 192.168.1.1 ipv4.dns 8.8.8.8 ipv4.method manual
  ```

- **Delete a network connection**  
  ```bash
  nmcli connection delete enp0s3
  ```

- **Show network device information (`enp0s3`)**  
  ```bash
  nmcli device show enp0s3
  ```

- **Restart the NetworkManager service**  
  ```bash
  systemctl restart NetworkManager
  ```