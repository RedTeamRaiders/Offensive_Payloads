# **Quota Management in Linux**  

## **Introduction**  
Quota management in Linux helps restrict and monitor disk space usage for users and groups. This prevents any single user or process from consuming excessive resources, ensuring fair resource allocation.


## **Types of Quotas**  
There are two types of disk quotas:  

| **Quota Type** | **Description** |
|--------------|----------------|
| **Soft Quota** | Warning threshold limit; users can exceed temporarily. |
| **Hard Quota** | Absolute limit; users cannot exceed this limit. |



## **Installing Quota Package**  

- **For Debian-based Systems (Ubuntu, Debian)**  
  ```bash
  sudo apt install quota -y
  ```
- **For RHEL, CentOS, Rocky Linux**  
  ```bash
  sudo yum install quota -y
  ```
- **For Fedora**  
  ```bash
  sudo dnf install quota -y
  ```


## **Enabling Quotas on a Filesystem**  

### **Step 1: Modify `/etc/fstab` to Enable Quotas**  
Edit the `/etc/fstab` file and add `usrquota` and `grpquota` to the filesystem options:  
```bash
/dev/sdb1 /d1 ext4 defaults,usrquota,grpquota 0 0
```

### **Step 2: Remount the Filesystem**  
```bash
sudo mount -o remount /d1
```

### **Step 3: Create Quota Database Files**  
```bash
sudo quotacheck -cugv /d1
```
**Options Explanation:**  
- `c` → Create quota files  
- `u` → Check user quotas  
- `g` → Check group quotas  
- `v` → Verbose output  



## **Activating Quotas**  
Enable quotas on the specified directory or partition:  
```bash
sudo quotaon /d1
```


## **Managing Quotas**  

- **Set User or Group Quota**  
  Use `edquota` to edit quotas for a user or group:  
  ```bash
  sudo edquota -u username
  sudo edquota -g groupname
  ```

**Quota Parameters:**
| **Parameter** | **Description** |
|--------------|----------------|
| **Blocks**   | Disk space in KB |
| **Soft**     | Soft quota limit |
| **Hard**     | Hard quota limit |



- **Verify Quota Usage**  
  ```bash
  sudo quota -u username
  sudo quota -g groupname
  ```


- **Generate Quota Report**  
  ```bash
  sudo repquota -a
  ```
  This displays the quota usage of all users.


- **Manually Create Required Quota Files**  
If quota files are missing, manually create them:  
  ```bash
  sudo touch /d1/aquota.user /d1/aquota.group
  sudo chmod 600 /d1/aquota.*
  sudo quotacheck -cug /d1
  ```