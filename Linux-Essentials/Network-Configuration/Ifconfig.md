# **`ifconfig`**  
The `ifconfig` command is used for configuring and displaying network interface information in Linux.

## **Syntax**  
```bash
ifconfig [interface] [options]
```


## **Examples**  

- **Show active network interfaces**  
  ```bash
  ifconfig
  ```

- **Show all network interfaces (including inactive ones)**  
  ```bash
  ifconfig -a
  ```

- **Show details of a specific network interface (`enp0s3`)**  
  ```bash
  ifconfig enp0s3
  ```

- **Enable a network interface (`enp0s3`)**  
  ```bash
  ifconfig enp0s3 up
  ```

- **Disable a network interface (`enp0s3`)**  
  ```bash
  ifconfig enp0s3 down
  ```

- **Assign an IP address to an interface (`enp0s3`)**  
  ```bash
  ifconfig enp0s3 192.168.1.110
  ```

- **Assign an IP address with a subnet mask**  
  ```bash
  ifconfig enp0s3 192.168.1.100 netmask 255.255.255.0
  ```

- **Assign an IP address using CIDR notation**  
  ```bash
  ifconfig enp0s3 192.168.1.100/24
  ```

- **Restart a network interface (`enp0s3`)**  
  ```bash
  ifconfig enp0s3 down && ifconfig enp0s3 up
  ```

- **Change the MAC address of an interface**  
  ```bash
  ifconfig enp0s3 hw ether 00:11:22:33:44:55
  ```

- **Set the MTU (Maximum Transmission Unit) value**  
  ```bash
  ifconfig enp0s3 mtu 1500
  ```

- **Enable promiscuous mode (capture all network packets)**  
  ```bash
  ifconfig enp0s3 promisc
  ```

- **Disable promiscuous mode**  
  ```bash
  ifconfig enp0s3 -promisc
  ```

- **Create an alias interface (`enp0s3:1`) with a new IP**  
  ```bash
  ifconfig enp0s3:1 192.168.1.101/24
  ```

- **Remove an alias interface (`enp0s3:1`)**  
  ```bash
  ifconfig enp0s3:1 down
  ```