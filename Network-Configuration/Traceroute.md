# **Traceroute Command**  

The `traceroute` command is used to track the path that packets take from your system to a destination host. It helps in diagnosing network issues by showing each hop along the way and measuring transit delays.  


## **Installation**  

### **Debian/Ubuntu**  
```bash
sudo apt install traceroute -y
```

### **RHEL/CentOS**  
```bash
sudo yum install traceroute -y
```


## **Syntax**  
```bash
traceroute [options] destination
```



## **Examples**  

- **Basic Traceroute to a Host**  
  ```bash
  traceroute google.com
  ```

- **Specify Number of Probes per Hop** (default is 3)  
  ```bash
  traceroute -q 5 google.com
  ```

- **Limit the Maximum Number of Hops**  
  ```bash
  traceroute -m 15 google.com
  ```

- **Use ICMP Instead of UDP** (Similar to Windows `tracert`)  
  ```bash
  traceroute -I google.com
  ```

- **Use TCP SYN Instead of UDP** (Useful for bypassing firewalls)  
  ```bash
  traceroute -T google.com
  ```

- **Specify a Source IP Address**  
  ```bash
  traceroute -s 192.168.1.100 google.com
  ```

- **Specify a Gateway (Default Gateway is Used if Not Set)**  
  ```bash
  traceroute -g 192.168.1.1 google.com
  ```

- **Set a Custom Packet Size**  
  ```bash
  traceroute -p 80 -q 5 -m 20 google.com
  ```