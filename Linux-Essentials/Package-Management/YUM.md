# `yum`  
It helps install, update, remove, and manage software packages with their dependencies.


## **Syntax**  
```bash
yum [options] [command] [package_name]
```


## **Examples**  

### **General YUM Commands**  

- **Show YUM version**  
  ```bash
  yum version
  ```

- **Show enabled repositories**  
  ```bash
  yum repolist
  ```

- **Show both enabled and disabled repositories**  
  ```bash
  yum repolist all
  ```

---

### **Listing Packages**  

- **Show available packages**  
  ```bash
  yum list available
  ```

- **Show all installed and available packages**  
  ```bash
  yum list all
  ```

- **Show installed packages**  
  ```bash
  yum list installed
  ```

- **Show recently installed packages**  
  ```bash
  yum list recent
  ```

---

### **Checking YUM and Updates**  

- **Check if YUM is working properly**  
  ```bash
  yum check
  ```

- **Check for available updates**  
  ```bash
  yum check-update
  ```

- **Update all installed packages**  
  ```bash
  yum update
  ```

- **Update a specific package**  
  ```bash
  yum update package_name
  ```

---

### **Installing and Removing Packages**  

- **Search for a package**  
  ```bash
  yum search package_name
  ```

- **Install `nmap` package**  
  ```bash
  yum install nmap
  ```

- **Remove `nmap` package**  
  ```bash
  yum remove nmap
  ```

- **Install `nmap` and related packages**  
  ```bash
  yum install nmap*
  ```

- **Remove `nmap` and related packages** *(Not recommended!)*  
  ```bash
  yum remove nmap*
  ```

- **Find which repository provides `nmap`**  
  ```bash
  yum provides nmap
  ```

- **Upgrade `nmap` package**  
  ```bash
  yum upgrade nmap
  ```

- **Downgrade `nmap` to the previous version**  
  ```bash
  yum downgrade nmap
  ```

- **Reinstall `nmap` package**  
  ```bash
  yum reinstall nmap
  ```

---

### **Cleaning and Caching**  

- **Clear YUM cache and metadata**  
  ```bash
  yum clean all
  ```

- **Rebuild repository cache**  
  ```bash
  yum makecache
  ```

---

### **History and Synchronization**  

- **Check YUM transaction history**  
  ```bash
  yum history
  ```

- **Synchronize installed packages with the latest available versions**  
  ```bash
  yum distro-sync
  ```

---

### **Managing Language and Groups**  

- **Show available language packages**  
  ```bash
  yum langavailable
  ```

- **Show group package details**  
  ```bash
  yum groups
  ```

- **List available groups**  
  ```bash
  yum groups list
  ```

- **Show details of "Development Tools" group**  
  ```bash
  yum groups info "Development Tools"
  ```

- **Install "Development Tools" group**  
  ```bash
  yum groups install "Development Tools"
  ```

- **Remove "Development Tools" group**  
  ```bash
  yum groups remove "Development Tools"
  ```

- **Mark "Security Tools" group for automatic installation with updates**  
  ```bash
  yum groups mark install "Security Tools"
  ```

- **Unmark "Security Tools" group to prevent automatic updates**  
  ```bash
  yum groups mark remove "Security Tools"
  ```
