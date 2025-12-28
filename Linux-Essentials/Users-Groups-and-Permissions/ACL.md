
# **Access Control List (ACL)**  

Access Control List (ACL) provides a more flexible way to define file and directory permissions beyond the traditional **owner-group-other** model in Linux. ACLs allow administrators to assign specific access rights (**read, write, execute**) to individual users or groups, ensuring finer control over permissions.  


## **Why Use ACL?**  

- Assign specific permissions to multiple users or groups for the same file or directory.  
- Extend beyond standard **rwx** permissions for more complex access control scenarios.  
- Allow finer-grained control over permissions when the default **owner-group-other** model is insufficient.  


## `getfacl` - **Checking ACL Permissions**
The `getfacl` command is used to **view ACL settings** on files and directories.

### **Syntax**
```bash
getfacl [filename or directory]
```

### **Examples**
1. **Check ACL of a file**
   ```bash
   getfacl myfile
   ```
   **Output:**
   ```
   # file: myfile
   # owner: user1
   # group: users
   user::rw-
   user:user2:r--
   group::r--
   mask::r--
   other::---
   ```
   Explanation:
   - **user::rw-** → Owner (`user1`) has read & write access.
   - **user:user2:r--** → User `user2` has read-only access.
   - **group::r--** → The default group has read-only access.
   - **other::---** → No permissions for others.

2. **Check ACL of a directory**
   ```bash
   getfacl mydir
   ```

3. **Check ACL of multiple files**
   ```bash
   getfacl file1 file2 file3
   ```

## `setfacl` - **Setting ACL Permissions**
The `setfacl` command **modifies ACL settings** on files and directories.

### **Syntax**
```bash
setfacl [options] [permissions] [file/directory]
```

### **Common Options**
| **Option** | **Description** |
|------------|----------------|
| `-m` | Modify or add ACL entry |
| `-x` | Remove ACL entry |
| `-b` | Remove all ACLs |
| `-d` | Set default ACL for directories |
| `-k` | Remove default ACL |

---

### **Examples of `setfacl` Usage**
1. **Grant read (`r`) and write (`w`) permissions to user `user2`**
   ```bash
   setfacl -m u:user2:rw myfile
   ```
   - `-m` → Modify ACL
   - `u:user2:rw` → Grant `rw` permissions to `user2`

2. **Grant read (`r`) permission to a group (`group1`)**
   ```bash
   setfacl -m g:group1:r myfile
   ```

3. **Grant full (`rwx`) access to `user3` on a directory**
   ```bash
   setfacl -m u:user3:rwx mydir
   ```

4. **Remove ACL permissions for `user2`**
   ```bash
   setfacl -x u:user2 myfile
   ```

5. **Remove ACL permissions for `group1`**
   ```bash
   setfacl -x g:group1 myfile
   ```

6. **Set default ACL for a directory (`mydir`)**
   ```bash
   setfacl -d -m u:user2:rwx mydir
   ```

7. **Remove all ACL settings from a file**
   ```bash
   setfacl -b myfile
   ```