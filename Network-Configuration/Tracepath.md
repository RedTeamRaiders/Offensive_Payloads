# **Tracepath Command**  

The `tracepath` command is used to trace the network path to a destination, similar to `traceroute`. It is a simpler alternative, requiring no root privileges and working with UDP by default.  



## **Installation**  

### **Debian/Ubuntu**  
```bash
sudo apt install iputils-tracepath -y
```

### **RHEL/CentOS/Fedora**  
`tracepath` is included in the `iputils` package and is usually pre-installed. If missing, install it using:  
```bash
sudo yum install iputils -y  # RHEL/CentOS
sudo dnf install iputils -y  # Fedora
```



## **Syntax**  
```bash
tracepath [options] destination
```



## **Examples**  

- **Basic Tracepath to a Host**  
  ```bash
  tracepath google.com
  ```

- **Specify Maximum Hops (Default: 30)**  
  ```bash
  tracepath -m 15 google.com
  ```

- **Tracepath Using a Specific Interface**  
  ```bash
  tracepath -i enp0s3 google.com
  ```

- **Show Only Numeric IP Addresses (No Hostnames)**  
  ```bash
  tracepath -n google.com
  ```