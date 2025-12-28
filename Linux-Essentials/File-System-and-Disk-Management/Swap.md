# **SWAP (Partitions and Files) in Linux**  

## **What is SWAP?**  

**SWAP** is a dedicated space on a disk that Linux uses as virtual memory when the system's **RAM (Random Access Memory)** is full. If the system runs out of RAM, it moves inactive processes to the SWAP space to prevent crashes and keep the system running smoothly.



## **Why Use SWAP?**  

- Prevents system crashes due to low memory  
- Helps multitasking on systems with limited RAM  
- Supports hibernation (suspend-to-disk feature)  
- Improves performance for memory-intensive applications  

**Note:** SWAP is slower than RAM because it relies on disk storage, so excessive swapping (thrashing) can degrade performance.



## **Types of SWAP in Linux**  

Linux allows SWAP space to be configured in two ways:  

**SWAP Partition** – A dedicated disk partition for swap usage.  
**SWAP File** – A special file on the filesystem that acts as swap space.  



## **Creating a SWAP Partition**  

### **Step 1: Check Existing SWAP**  
```bash
swapon --show
```
If no output appears, there is no active swap.

### **Step 2: Check Available Partitions**  
```bash
lsblk
```

### **Step 3: Create a SWAP Partition**  
1. Open `fdisk` to create a new partition:  
   ```bash
   sudo fdisk /dev/sdb
   ```
2. Inside `fdisk`:  
   - Press `n` → create new partition  
   - Choose partition type (default: primary)  
   - Select partition number  
   - Set the size (e.g., `+4G` for 4GB swap)  
   - Press `t` → Change type → Enter `82` (Linux Swap)  
   - Press `w` to save changes  

### **Step 4: Format the SWAP Partition**  
```bash
sudo mkswap /dev/sdb1
```

### **Step 5: Enable SWAP**  
```bash
sudo swapon /dev/sdb1
```

### **Step 6: Make SWAP Permanent**  
Add this line to `/etc/fstab`:  
```bash
/dev/sdb1 none swap sw 0 0
```



## **Creating a SWAP File**  

- **Create a Swap File (e.g., 2GB size)**  
   ```bash
   sudo fallocate -l 2G /swapfile
   ```
   (If `fallocate` is not available, use: `sudo dd if=/dev/zero of=/swapfile bs=1M count=2048`)

- **Set Correct Permissions**  
   ```bash
   sudo chmod 600 /swapfile
   ```

- **Format the File as SWAP**  
   ```bash
   sudo mkswap /swapfile
   ```

- **Enable the SWAP File**  
   ```bash
   sudo swapon /swapfile
   ```

- **Make the SWAP File Permanent**  
   Add the following line to `/etc/fstab`:  
   ```bash
   /swapfile none swap sw 0 0
   ```



## **Managing SWAP**  

- **Check Swap Usage**  
   ```bash
   free -m
   ```

- **Disable SWAP Temporarily**  
   ```bash
   sudo swapoff -a
   ```

- **Enable SWAP Again**  
   ```bash
   sudo swapon -a
   ```

### **Remove a SWAP File Permanently**  
1. Disable SWAP:  
   ```bash
   sudo swapoff /swapfile
   ```
2. Remove the file:  
   ```bash
   sudo rm /swapfile
   ```
3. Edit `/etc/fstab` and remove the swap entry.

## **How Much SWAP Do You Need?**  

| RAM Size | Recommended SWAP (No Hibernate) | Recommended SWAP (With Hibernate) |
|----------|--------------------------------|----------------------------------|
| 2GB or less | 2GB | 2× RAM |
| 4GB | 2GB | 1.5× RAM |
| 8GB | 2GB | 1× RAM |
| 16GB+ | 2GB (or none) | 1× RAM |

**Note:** If you use SSD storage, consider using a smaller swap size to reduce write operations.
