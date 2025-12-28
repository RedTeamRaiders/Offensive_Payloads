# **`usermod`**  
The `usermod` command modifies user account settings, such as groups, shell, home directory, and other attributes. The `usermod` command is useful for updating user settings without deleting and recreating the account.

### **Syntax**  
```bash
usermod [options] username
```

---

### **Examples**  

- **Change the user's login name:**  
  ```bash
  usermod -l newusername oldusername
  ```

- **Change the user's home directory:**  
  ```bash
  usermod -d /new/home/directory username
  ```

- **Move the user's existing home directory to a new location:**  
  ```bash
  usermod -d /new/home/directory -m username
  ```

- **Change the user's shell:**  
  ```bash
  usermod -s /bin/zsh username
  ```

- **Change the user's primary group:**  
  ```bash
  usermod -g newgroup username
  ```

- **Add the user to a supplementary group:**  
  ```bash
  usermod -aG groupname username
  ```

- **Add the user to multiple groups:**  
  ```bash
  usermod -aG sudo,docker username
  ```

- **Lock a user account (disable login):**  
  ```bash
  usermod -L username
  ```

- **Unlock a locked user account:**  
  ```bash
  usermod -U username
  ```

- **Set an expiration date for a user account (YYYY-MM-DD format):**  
  ```bash
  usermod -e 2025-12-31 username
  ```

- **Change the user ID (UID) of a user:**  
  ```bash
  usermod -u 2001 username
  ```

- **Change the user's comment (Full Name or other details):**  
  ```bash
  usermod -c "John Doe - Developer" username
  ```