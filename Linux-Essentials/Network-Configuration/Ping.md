# **`ping`**  

The `ping` command is used to test network connectivity between two hosts by sending ICMP Echo Request packets and measuring response times. It helps diagnose network issues such as latency, packet loss, and host availability.  



## **Syntax**  
```bash
ping [options] destination
```


## **Examples**  

- **Ping a Host (Default Behavior)**  
  ```bash
  ping google.com
  ```

- **Ping a Host with a Specific Number of Packets**  
  ```bash
  ping -c 5 google.com
  ```

- **Ping a Host Until It Becomes Reachable**  
  ```bash
  ping -w 10 google.com
  ```

- **Ping with a Specific Packet Size**  
  ```bash
  ping -s 1000 google.com
  ```

- **Flood Ping (Send Packets as Fast as Possible – Requires Root)**  
  ```bash
  sudo ping -f google.com
  ```

- **Set Time Interval Between Pings**  
  ```bash
  ping -i 2 google.com
  ```

- **Limit Ping TTL (Time to Live) Value**  
  ```bash
  ping -t 10 google.com
  ```

- **Show Only Ping Statistics (Silent Mode)**  
  ```bash
  ping -q -c 5 google.com
  ```

- **Ping an IP Address Instead of a Domain Name**  
  ```bash
  ping 8.8.8.8
  ```

- **Ping a Local Network Device**  
  ```bash
  ping 192.168.1.1
  ```