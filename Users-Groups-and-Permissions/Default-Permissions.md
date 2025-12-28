## **Default Permissions in Linux**

When a **file** or **directory** is created in Linux, it **inherits default permissions** based on system settings and the `umask` value.

### **1. System Default Permissions**
By default, the system assigns:
- **Files:** `666` (`rw-rw-rw-`) → Read & write for all users  
- **Directories:** `777` (`rwxrwxrwx`) → Full access for all users  

However, these permissions are modified by `umask`.

### **2. What is `umask`?**
`umask` (User Mask) is a setting that **removes permissions** from the system’s default permissions when a new file or directory is created.

#### **Formula:**
```
Effective Permissions = Default Permissions - umask
```

For example, if the `umask` is `0022`:
- **Files:** `666 - 022 = 644` (`rw-r--r--`)
- **Directories:** `777 - 022 = 755` (`rwxr-xr-x`)

### **3. Checking the Current `umask` Value**
To check the current `umask` setting, run:
```bash
umask
```
**Output (for a regular user):**
```
0002
```
**Output (for the root user):**
```
0022
```

### **4. Creating a File & Directory to See Default Permissions**
```bash
mkdir mydir
touch myfile
ls -l
```

#### **Output (For a regular user with `umask 0002`):**
```
drwxrwxr-x  2 user user  40 Mar 13 11:38 mydir
-rw-rw-r--  1 user user   0 Mar 13 11:38 myfile
```
**Explanation:**
- **Files:** `666 - 0002 = 664` (`rw-rw-r--`)
- **Directories:** `777 - 0002 = 775` (`rwxrwxr-x`)

#### **Output (For root user with `umask 0022`):**
```
drwxr-xr-x  2 root root  40 Mar 13 11:38 mydir
-rw-r--r--  1 root root   0 Mar 13 11:38 myfile
```
**Explanation:**
- **Files:** `666 - 0022 = 644` (`rw-r--r--`)
- **Directories:** `777 - 0022 = 755` (`rwxr-xr-x`)


## **Common `umask` Values & Their Effects**

| **umask** | **File Permissions** | **Directory Permissions** | **Effect** |
|-----------|----------------------|--------------------------|------------|
| `000`     | `666` (`rw-rw-rw-`)   | `777` (`rwxrwxrwx`)      | Full access for all users |
| `002`     | `664` (`rw-rw-r--`)   | `775` (`rwxrwxr-x`)      | Default for regular users |
| `022`     | `644` (`rw-r--r--`)   | `755` (`rwxr-xr-x`)      | Default for root users |
| `027`     | `640` (`rw-r-----`)   | `750` (`rwxr-x---`)      | More restrictive |
| `077`     | `600` (`rw-------`)   | `700` (`rwx------`)      | Private access |


## **Changing Default Permissions Using `umask`**

### **1. Temporarily Change `umask` (For Current Session)**
```bash
umask 027
```
```
mkdir testdir
touch testfile
ls -l
```
**New Output:**
```
drwxr-x---  2 user user  40 Mar 13 11:38 testdir
-rw-r-----  1 user user   0 Mar 13 11:38 testfile
```
**Changes Applied:**
- **Files:** `666 - 027 = 640` (`rw-r-----`)
- **Directories:** `777 - 027 = 750` (`rwxr-x---`)

This change lasts only for the current session.

---

### **2. Permanently Change `umask`**
To **make the change permanent**, update the shell configuration files.

#### **For a Specific User**
Edit the user's `~/.bashrc` or `~/.profile`:
```bash
nano ~/.bashrc
```
Add this line:
```bash
umask 027
```
Save and apply:
```bash
source ~/.bashrc
```

#### **For All Users (System-Wide)**
Edit `/etc/profile` or `/etc/bash.bashrc`:
```bash
nano /etc/profile
```
Add this line:
```bash
umask 027
```
Save and apply:
```bash
source /etc/profile
```