# **`userdel`**  
The `userdel` command is used to delete a user account from a Linux system.  

### **Syntax**  
```bash
userdel [options] username
```

---

### **Examples**  

- **Delete a user account (without removing home directory):**  
  ```bash
  userdel username
  ```

- **Delete a user account and remove their home directory:**  
  ```bash
  userdel -r username
  ```

- **Force delete a user account (even if the user is logged in):**  
  ```bash
  userdel -f username
  ```
---

### **Important Notes**  
- If the user is logged in, you may need to **kill their session** before deleting:  
  ```bash
  pkill -u username
  ```
- The `-r` option **removes the home directory and mail spool** (`/home/username`).  
- If deleting a user with an active process, use:  
  ```bash
  userdel -f username
  ```
- To verify if the user was deleted:  
  ```bash
  cat /etc/passwd | grep username
  ```
