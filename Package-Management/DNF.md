# `dnf`  
The `dnf` (Dandified YUM) command is the default package manager for RHEL-based distributions, including Fedora, CentOS 8+, and Rocky Linux. It replaces `yum` with improved dependency resolution and performance.


## **Syntax**  
```bash
dnf [options] [command] [package_name]
```


## **Examples**  

### **General DNF Commands**  

- **Show DNF version**  
  ```bash
  dnf --version
  ```

- **Show enabled repositories**  
  ```bash
  dnf repolist
  ```

- **Show both enabled and disabled repositories**  
  ```bash
  dnf repolist all
  ```

---

### **Listing Packages**  

- **Show available packages**  
  ```bash
  dnf list available
  ```

- **Show all installed and available packages**  
  ```bash
  dnf list all
  ```

- **Show installed packages**  
  ```bash
  dnf list installed
  ```

- **Show recently installed packages**  
  ```bash
  dnf list recent
  ```

---

### **Checking DNF and Updates**  

- **Check if DNF is working properly**  
  ```bash
  dnf check
  ```

- **Check for available updates**  
  ```bash
  dnf check-update
  ```

- **Update all installed packages**  
  ```bash
  dnf update
  ```

- **Update a specific package**  
  ```bash
  dnf update package_name
  ```

---

### **Installing and Removing Packages**  

- **Search for a package**  
  ```bash
  dnf search package_name
  ```

- **Install `nmap` package**  
  ```bash
  dnf install nmap
  ```

- **Remove `nmap` package**  
  ```bash
  dnf remove nmap
  ```

- **Install `nmap` and related packages**  
  ```bash
  dnf install nmap*
  ```

- **Remove `nmap` and related packages** *(Not recommended!)*  
  ```bash
  dnf remove nmap*
  ```

- **Find which repository provides `nmap`**  
  ```bash
  dnf provides nmap
  ```

- **Upgrade `nmap` package**  
  ```bash
  dnf upgrade nmap
  ```

- **Downgrade `nmap` to the previous version**  
  ```bash
  dnf downgrade nmap
  ```

- **Reinstall `nmap` package**  
  ```bash
  dnf reinstall nmap
  ```

---

### **Cleaning and Caching**  

- **Clear DNF cache and metadata**  
  ```bash
  dnf clean all
  ```

- **Rebuild repository cache**  
  ```bash
  dnf makecache
  ```

---

### **History and Synchronization**  

- **Check DNF transaction history**  
  ```bash
  dnf history
  ```

- **Synchronize installed packages with the latest available versions**  
  ```bash
  dnf distro-sync
  ```

---

### **Managing Language and Groups**  

- **Show available language packages**  
  ```bash
  dnf langavailable
  ```

- **Show group package details**  
  ```bash
  dnf group
  ```

- **List available groups**  
  ```bash
  dnf group list
  ```

- **Show details of "Development Tools" group**  
  ```bash
  dnf group info "Development Tools"
  ```

- **Install "Development Tools" group**  
  ```bash
  dnf group install "Development Tools"
  ```

- **Remove "Development Tools" group**  
  ```bash
  dnf group remove "Development Tools"
  ```

- **Mark "Security Tools" group for automatic installation with updates**  
  ```bash
  dnf group mark install "Security Tools"
  ```

- **Unmark "Security Tools" group to prevent automatic updates**  
  ```bash
  dnf group mark remove "Security Tools"
  ```
