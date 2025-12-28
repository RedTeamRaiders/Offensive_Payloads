# **`ip` Command**  
The `ip` command is used to manage network interfaces, routes, and IP addresses in Linux.


## **Syntax**  
```bash
ip [options] [object] [command]
```

## **Examples**  

- **Show all network interfaces and their IP addresses**  
  ```bash
  ip a
  ```

- **Show IPv4 and IPv6 addresses of all interfaces**  
  ```bash
  ip addr show
  ```

- **Show details of a specific network interface (`enp0s3`)**  
  ```bash
  ip addr show enp0s3
  ```

- **Enable a network interface (`enp0s3`)**  
  ```bash
  ip link set enp0s3 up
  ```

- **Disable a network interface (`enp0s3`)**  
  ```bash
  ip link set enp0s3 down
  ```

- **Assign an IP address to an interface (`enp0s3`)**  
  ```bash
  ip addr add 192.168.1.110/24 dev enp0s3
  ```

- **Remove an IP address from an interface (`enp0s3`)**  
  ```bash
  ip addr del 192.168.1.110/24 dev enp0s3
  ```

- **Show the routing table**  
  ```bash
  ip route show
  ```

- **Add a default gateway (`192.168.1.1`)**  
  ```bash
  ip route add default via 192.168.1.1
  ```

- **Delete a default gateway**  
  ```bash
  ip route del default via 192.168.1.1
  ```

- **Show ARP table (neighbor cache)**  
  ```bash
  ip neigh show
  ```

- **Flush all IP addresses from an interface (`enp0s3`)**  
  ```bash
  ip addr flush dev enp0s3
  ```

- **Show network interface statistics**  
  ```bash
  ip -s link
  ```

- **Change the MAC address of an interface**  
  ```bash
  ip link set dev enp0s3 address 00:11:22:33:44:55
  ```