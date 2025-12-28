# **RPM Commands**  

The `rpm` (Red Hat Package Manager) command is used to install, query, verify, and manage `.rpm` packages on RHEL-based distributions like CentOS, Fedora, and Rocky Linux.  


### **Checking OS Details**  

To check your operating system details, use the following commands:  

```bash
cat /etc/os-release
```

```bash
cat /etc/system-release
```

```bash
cat /etc/redhat-release
```

```bash
uname -a
```

### **RPM Database**  

The RPM database is stored in `/var/lib/rpm`. You can list its contents using:  

```bash
ls /var/lib/rpm
```

### **Example Output:**  
```
/var/lib/rpmdb.sqlite  
/var/lib/rpmdb.sqlite-shm  
```

## Command **Syntax**  
```bash
rpm [options] [package_name/.rpm file]
```

## **Examples**  

### **General RPM Commands**  

- **Check `rpm` version**  
  ```bash
  rpm --version
  ```

- **Get help for `rpm` commands**  
  ```bash
  rpm --help
  ```

---

### **Querying Packages**  

- **Check if a package is installed**  
  ```bash
  rpm -q package_name
  ```

- **List all installed packages**  
  ```bash
  rpm -qa
  ```

- **Count installed packages**  
  ```bash
  rpm -qa | wc -l
  ```

- **List installed packages sorted by installation date**  
  ```bash
  rpm -qa --last
  ```

- **Find a package by name**  
  ```bash
  rpm -qa | grep package_name
  ```

- **Show detailed package information**  
  ```bash
  rpm -qi package_name
  ```

- **List all files installed by a package**  
  ```bash
  rpm -ql package_name
  ```

- **List configuration files of a package**  
  ```bash
  rpm -qc package_name
  ```

- **List documentation files of a package**  
  ```bash
  rpm -qd package_name
  ```

- **List dependencies required by a package**  
  ```bash
  rpm -qR package_name
  ```

- **Find the package that installed a file**  
  ```bash
  rpm -qf /path/to/file
  ```

---

### **Working with `.rpm` Files**  

- **Check details of a `.rpm` file before installing**  
  ```bash
  rpm -qip package_file.rpm
  ```

- **List configuration files in an `.rpm` file**  
  ```bash
  rpm -qcp package_file.rpm
  ```

- **List all files included in an `.rpm` file**  
  ```bash
  rpm -qlp package_file.rpm
  ```

- **List documentation files included in an `.rpm` file**  
  ```bash
  rpm -qdp package_file.rpm
  ```

- **List dependencies required by an `.rpm` file**  
  ```bash
  rpm -qRp package_file.rpm
  ```

- **Check the license of an `.rpm` package**  
  ```bash
  rpm -qip package_file.rpm | grep License
  ```

---

### **Verifying Installed Packages**  

- **Verify if installed package files have changed**  
  ```bash
  rpm -V package_name
  ```

- **Verify a package in verbose mode**  
  ```bash
  rpm -Vv package_name
  ```

---

### **Installing, Upgrading, and Removing Packages**  

- **Install an `.rpm` package**  
  ```bash
  rpm -i package_file.rpm
  ```

- **Install an `.rpm` package ignoring dependencies**  
  ```bash
  rpm -i --nodeps package_file.rpm
  ```

- **Install an `.rpm` package with verbose output and progress**  
  ```bash
  rpm -ivh package_file.rpm
  ```

- **Upgrade an `.rpm` package**  
  ```bash
  rpm -U package_file.rpm
  ```

- **Remove an installed package**  
  ```bash
  rpm -e package_name
  ```

- **Remove an installed package with verbose output**  
  ```bash
  rpm -evh package_name
  ```

- **Remove a package without checking dependencies**  
  ```bash
  rpm -e --nodeps package_name
  ```
