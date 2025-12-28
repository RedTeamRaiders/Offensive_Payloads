# **`passwd`**  
The `passwd` command is used to change or manage user passwords in Linux.

### **Syntax**  
```bash
passwd [options] [username]
```

---

### **Examples**  

- **Change the current user's password:**  
  ```bash
  passwd
  ```
  _(Prompts for the current and new password)_

- **Change another user's password (root or sudo required):**  
  ```bash
  passwd username
  ```

- **Force a user to change their password on the next login:**  
  ```bash
  passwd -e username
  ```

- **Lock a user’s password (disable login):**  
  ```bash
  passwd -l username
  ```

- **Unlock a locked user account:**  
  ```bash
  passwd -u username
  ```

- **Check password status of a user:**  
  ```bash
  passwd -S username
  ```

- **Set password expiry to 30 days:**  
  ```bash
  passwd -x 30 username
  ```

- **Disable password expiry:**  
  ```bash
  passwd -x -1 username
  ```

---

### **Important Notes**  
- Regular users can only change **their own** passwords.  
- `root` or `sudo` privileges are required to change **another user's** password.  
- To enforce strong passwords, Linux systems may use the **`pam_pwquality`** module.  
- Users can view password expiry details with:  
  ```bash
  chage -l username
  ```