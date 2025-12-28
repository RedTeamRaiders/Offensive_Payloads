# `apt`  
APT (Advanced Package Tool) is a high-level package management system used in Debian-based Linux distributions like Ubuntu, Kali Linux, and Raspberry Pi OS. It simplifies package installation, removal, and updates while automatically handling dependencies.  


## **Syntax**  
```bash
apt [options] [package_name]
```


## **Examples**  

### **Updating and Upgrading Packages**  

- **Update the package list**  
  ```bash
  apt update
  ```

- **Check for upgradable packages**  
  ```bash
  apt list --upgradable
  ```

- **Upgrade all installed packages**  
  ```bash
  apt upgrade -y
  ```

- **Perform a full system upgrade (includes removing obsolete packages)**  
  ```bash
  apt full-upgrade -y
  ```

- **Upgrade the system while handling dependency changes**  
  ```bash
  apt dist-upgrade -y
  ```

---

### **Installing and Removing Packages**  

- **Install a package**  
  ```bash
  apt install package_name -y
  ```

- **Remove a package (keep configuration files)**  
  ```bash
  apt remove package_name -y
  ```

- **Remove a package along with its configuration files**  
  ```bash
  apt remove --purge package_name -y
  ```

- **Reinstall a package**  
  ```bash
  apt reinstall package_name
  ```

---

### **Cleaning and Managing Dependencies**  

- **Remove unused dependencies**  
  ```bash
  apt autoremove -y
  ```

- **Clean the APT cache**  
  ```bash
  apt autoclean
  ```

---

### **Searching and Viewing Package Information**  

- **Search for a package**  
  ```bash
  apt search package_name
  ```

- **Show detailed package information**  
  ```bash
  apt show package_name
  ```

- **List all installed packages**  
  ```bash
  apt list --installed
  ```

- **Check package dependencies**  
  ```bash
  apt depends package_name
  ```

- **Check reverse dependencies (which packages depend on this package)**  
  ```bash
  apt rdepends package_name
  ```

- **View package source information**  
  ```bash
  apt showsrc package_name
  ```

---

### **Managing Package Sources and Fixing Errors**  

- **Download a package without installing it**  
  ```bash
  apt download package_name
  ```

- **Fetch the source code of a package**  
  ```bash
  apt source package_name
  ```

- **Check package changelog**  
  ```bash
  apt changelog package_name
  ```

- **Fix broken dependencies**  
  ```bash
  apt --fix-broken install
  ```

- **Force reconfiguration of installed packages**  
  ```bash
  dpkg --configure -a
  ```

- **Unlock APT when another process is using it**  
  ```bash
  rm /var/lib/dpkg/lock
  ```
  ```
  rm /var/lib/dpkg/lock-frontend
  ```

---

### **6. Alternative APT Tools**  

#### **Using `apt-cache` for Searching and Checking Dependencies**  

- **Search for a package**  
  ```bash
  apt-cache search package_name
  ```

- **Show package details**  
  ```bash
  apt-cache show package_name
  ```

- **Check package dependencies**  
  ```bash
  apt-cache depends package_name
  ```

- **List reverse dependencies**  
  ```bash
  apt-cache rdepends package_name
  ```

- **View available package names**  
  ```bash
  apt-cache pkgnames
  ```

- **Check package policy (installed vs available versions)**  
  ```bash
  apt-cache policy package_name
  ```