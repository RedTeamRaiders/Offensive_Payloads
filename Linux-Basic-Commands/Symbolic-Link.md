# **Symbolic Links in Linux**

A **symbolic link** (also called a **symlink** or **soft link**) is a special type of file that points to another file or directory. It acts as a shortcut, allowing you to access the target file or directory from another location.

### **Types of Links in Linux**  
1. **Hard Link** – Creates a duplicate entry pointing to the same data on disk.  
2. **Soft Link (Symbolic Link)** – A reference to another file or directory.


## **Creating Symbolic Links**  

### **Basic Syntax**
```bash
ln -s TARGET LINK_NAME
```
- `TARGET` – The original file or directory.  
- `LINK_NAME` – The name of the symbolic link.

### **Examples**
1. Create a symbolic link to a file:
   ```bash
   ln -s /path/to/original.txt link.txt
   ```

2. Create a symbolic link to a directory:
   ```bash
   ln -s /home/user/Documents my_docs
   ```

3. Overwrite an existing symbolic link:
   ```bash
   ln -sf /new/path/to/file link.txt
   ```

4. Create a symbolic link with absolute path:
   ```bash
   ln -s /var/www/html website_link
   ```

5. Create a symbolic link with a relative path:
   ```bash
   ln -s ../folder/file.txt link.txt
   ```


## **Managing Symbolic Links**  

### **View Symbolic Links**
- **List symbolic links in a directory:**
  ```bash
  ls -l
  ```
  Symlinks are indicated by `l` at the beginning, e.g.:
  ```
  lrwxrwxrwx 1 user user 10 Mar 10 12:00 link.txt -> original.txt
  ```

- **Find all symbolic links in a directory:**
  ```bash
  find /path/to/directory -type l
  ```

- **Check where a symlink points to:**
  ```bash
  readlink -f link.txt
  ```


## **Removing Symbolic Links**  
To remove a symbolic link, use:
```bash
rm link.txt
```
or
```bash
unlink link.txt
```
**Note:** Deleting a symlink does **not** delete the target file.