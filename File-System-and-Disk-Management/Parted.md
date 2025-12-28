
## **🛠️ `parted` Utility**  

`parted` is a modern command-line tool used for creating and managing partitions, especially for larger disks (over 2TB) using GPT.

### **Syntax**  
```bash
parted /dev/sdX [command]
```

### **Examples**  

- **Check Partition Table of a Disk**  
  ```bash
  parted /dev/sda print
  ```

- **Create a GPT Partition Table**  
  ```bash
  parted /dev/sda mklabel gpt
  ```

- **Create a New Partition (100GB, Primary, ext4)**  
  ```bash
  parted /dev/sda mkpart primary ext4 0% 100GB
  ```

- **Resize a Partition**  
  ```bash
  parted /dev/sda resizepart 1 150GB
  ```

- **Delete a Partition**  
  ```bash
  parted /dev/sda rm 1
  ```

💡 **`parted` is preferred for disks larger than 2TB because it supports GPT, unlike `fdisk` which supports MBR.**