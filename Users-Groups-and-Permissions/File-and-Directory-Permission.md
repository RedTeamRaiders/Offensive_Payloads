# File & Directory Permissions

File and directory permissions determine who can read, write, or execute a file or folder. Permissions are set for three types of users: the owner, the group, and others.

### Types of Permissions
   - **Read (r)**: Allows the file to be opened and read.
   - **Write (w)**: Allows modifying or deleting the file.
   - **Execute (x)**: Allows executing the file as a program.
     
### Categories of Users
   - **User (u)**: The owner of the file.
   - **Group (g)**: A set of users who share the same group.
   - **Others (o)**: All other users on the system.
     
### **File Permission Format**
Use `ls -l` to view file permissions:  

```bash
ls -l file.txt
```

Example output:  
```bash
-rwxr-xr-- 1 user group 1024 Mar 10 12:00 file.txt
```

This string consists of 10 characters, with the following breakdown:
   - The first character represents the file type:
     - `-` for a regular file
     - `d` for a directory
     - `l` for a symbolic link
     - `b` Block device (e.g., hard drives, USB drives)
     - `c` Character device (e.g., keyboards, mice)
  
  - The remaining 9 characters represent the permissions for **user (owner)**, **group**, and **others** in the following order:
     - **User (Owner)**: The first three characters
     - **Group**: The next three characters
     - **Others**: The last three characters

  For example, `rwxr-xr--` means:
    - **User**: `rwx` (read, write, and execute permissions)
    - **Group**: `r-x` (read and execute permissions)
    - **Others**: `r--` (read permission)


  ### Numeric Representation of Permissions

  Permissions can also be represented by numeric values:
  | Permission | Numeric Value |
  |------------|---------------|
  | Read (r)   | 4             |
  | Write (w)  | 2             |
  | Execute (x)| 1             |

  Each permission type can be assigned a numeric value, and the sum of those values determines the permission setting.
  For example:
   - `rwx` = 4 + 2 + 1 = **7**
   - `r-x` = 4 + 0 + 1 = **5**
   - `r--` = 4 + 0 + 0 = **4**

  Thus, the permission `rwxr-xr--` corresponds to **755** in numeric form.
  
## `chmod` – Changing  Files and Directories Permissions
The `chmod` (change mode) command is used to modify file and directory permissions in Linux.  

## **Syntax**  
```bash
chmod [options] mode filename
```
### **Examples Using Symbolic Mode**  

- Add execute permission for the owner:  
  ```bash
  chmod u+x script.sh
  ```
- Remove write permission from the group:  
  ```bash
  chmod g-w file.txt
  ```
- Add read and execute permissions for others:  
  ```bash
  chmod o+rx document.txt
  ```
- Remove all permissions for others:  
  ```bash
  chmod o-rwx private.txt
  ```
- Grant full permissions to the owner, read to the group, and no permission to others:  
  ```bash
  chmod u=rwx,g=r,o= file.txt
  ```

### **Examples Using Numeric (Octal) Mode**  

- Grant full permissions to the owner, read & execute to the group, and read-only to others:  
  ```bash
  chmod 754 file.txt
  ```
- Set read, write, and execute for all users:  
  ```bash
  chmod 777 script.sh
  ```
- Remove execute permission for everyone:  
  ```bash
  chmod 666 file.txt
  ```
- Remove all permissions for others:  
  ```bash
  chmod 770 confidential.txt
  ```
- Change permissions for all files and subdirectories:  
  ```bash
  chmod -R 755 /var/www/html
  ```


# **`chown`** – Change  Files and Directories Owner and Group  

The `chown` command is used to change the ownership of files and directories in Linux. It allows modifying the owner (`user`) and group (`group`) associated with a file.  

## **Syntax**  
```bash
chown [OPTIONS] [OWNER][:GROUP] filename
```
- `OWNER` → The new owner of the file.  
- `GROUP` → The new group of the file (optional).  
- `filename` → The file or directory whose ownership is being changed.  


## **Examples**  

### **Change Ownership**  
- Change the owner of a file:  
  ```bash
  chown newuser file.txt
  ```
- Change the owner of multiple files:  
  ```bash
  chown newuser file1.txt file2.txt
  ```
- Change the owner of a directory and all its contents:  
  ```bash
  chown -R newuser /home/newuser/
  ```


### **Change Group Ownership**  
- Change the group of a file:  
  ```bash
  chown :newgroup file.txt
  ```
- Change both owner and group:  
  ```bash
  chown newuser:newgroup file.txt
  ```
- Change the group of multiple files:  
  ```bash
  chown :developers file1.txt file2.txt
  ```
- Change the group of all files inside a directory:  
  ```bash
  chown -R :developers /var/www/html/
  ```


### **Using UID and GID**  
Instead of specifying a username or group name, you can use their respective User ID (UID) and Group ID (GID).  
- Change owner using UID:  
  ```bash
  chown 1001 file.txt
  ```
- Change group using GID:  
  ```bash
  chown :2002 file.txt
  ```
- Change owner and group using UID & GID:  
  ```bash
  chown 1001:2002 my_directory/
  ```
