# `dpkg`  
The `dpkg` command is a low-level package manager for Debian-based distributions like Ubuntu and Debian. It is used for installing, removing, and managing `.deb` packages.  


## Command Reference Overview

  In the Debian ecosystem, several commands/tools exist for package management:
  
  - **dpkg**: Install, remove, and manage .deb packages at a low level.  
  - **dpkg-deb**: Work with `.deb` files (list or extract) without installing them.  
  - **dpkg-query**: Query package databases for information.  
  - **dpkg-reconfigure**: Reconfigure installed packages.  
  - **dpkg-divert**: Prevent files from being overwritten by a package.  
  - **dpkg-statoverride**: Override file ownership/permissions set by packages.  
  - **apt / apt-get**: Higher-level package management tools that provide dependency resolution.  
  - **apt-cache**: Query package metadata (e.g., searching or listing versions).  
  - **aptitude**: A full-featured package management interface (text-based UI).
  
## **Syntax**  
```bash
dpkg [options] [package_name/.deb file]
```


## **Examples**  

### **Installing and Removing Packages**  

- **Install a `.deb` package**  
  ```bash
  dpkg -i package_file.deb
  ```

- **Remove a package (keep configuration files)**  
  ```bash
  dpkg -r package_name
  ```

- **Completely remove a package (including configuration files)**  
  ```bash
  dpkg -P package_name
  ```

---

### **Querying Installed Packages**  

- **List all installed packages**  
  ```bash
  dpkg -l
  ```

- **Check if a specific package is installed**  
  ```bash
  dpkg -l | grep package_name
  ```

- **Get detailed information about a package**  
  ```bash
  dpkg -s package_name
  ```

- **List all files installed by a package**  
  ```bash
  dpkg -L package_name
  ```

- **Find which package installed a specific file**  
  ```bash
  dpkg -S /path/to/file
  ```

---

### **Working with `.deb` Files**  

- **Extract a `.deb` package without installing**  
  ```bash
  dpkg-deb -x package_file.deb output_directory/
  ```

- **Show package details from a `.deb` file**  
  ```bash
  dpkg-deb -I package_file.deb
  ```

- **List files inside a `.deb` package**  
  ```bash
  dpkg-deb -c package_file.deb
  ```

---

### **Managing Package Configurations**  

- **Reconfigure an installed package**  
  ```bash
  dpkg-reconfigure package_name
  ```

- **Prevent a package from being overwritten (divert files)**  
  ```bash
  dpkg-divert --add /path/to/file
  ```

- **Override file permissions/ownership**  
  ```bash
  dpkg-statoverride --add user group permissions /path/to/file
  ```