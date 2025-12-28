# **Adding Users in Linux**  

Linux provides two main commands for adding users: `useradd` and `adduser`.  

- **`useradd`**: A low-level command for creating new user accounts.  
- **`adduser`**: A user-friendly wrapper for `useradd` (available in Debian-based systems).  


## **`useradd`**  
The `useradd` command is used to create a new user account in Linux.  

### **Syntax**  
```bash
useradd [options] username
```

### **Examples**  

- **Create a new user:**  
  ```bash
  useradd newuser
  ```

- **Create a user with a specific home directory:**  
  ```bash
  useradd -d /home/customhome newuser
  ```

- **Create a user with a specific shell:**  
  ```bash
  useradd -s /bin/zsh newuser
  ```

- **Create a user with a specific user ID (UID):**  
  ```bash
  useradd -u 1050 newuser
  ```

- **Create a user and assign it to a group:**  
  ```bash
  useradd -g developers newuser
  ```

- **Create a user with an expiration date (YYYY-MM-DD format):**  
  ```bash
  useradd -e 2025-12-31 newuser
  ```

- **Create a system user (for services):**  
  ```bash
  useradd -r sysuser
  ```

- **Set a password for the user:**  
  ```bash
  passwd newuser
  ```


## **`adduser`**  
The `adduser` command is a user-friendly alternative to `useradd`, available in Debian-based distributions. It provides an interactive way to add users.  

### **Syntax**  
```bash
adduser username
```

### **Examples**  

- **Create a new user interactively:**  
  ```bash
  adduser newuser
  ```
  *(This prompts for user information, including password, full name, and home directory.)*  

- **Create a user and specify the home directory:**  
  ```bash
  adduser --home /custom/home newuser
  ```

- **Create a user and specify the shell:**  
  ```bash
  adduser --shell /bin/zsh newuser
  ```

- **Create a user and assign it to a specific group:**  
  ```bash
  adduser newuser developers
  ```

- **Add an existing user to a secondary group:**  
  ```bash
  adduser newuser sudo
  ```

- **Create a system user (for services):**  
  ```bash
  adduser --system sysuser
  ```


## **Differences Between `useradd` and `adduser`**

| **Feature**               | **`useradd`**                                  | **`adduser`**                                      |
|---------------------------|------------------------------------------------|----------------------------------------------------|
| **Type**                   | Low-level command (more control)               | High-level, interactive tool (user-friendly)       |
| **Home Directory**         | Not created by default unless `-m` option used | Automatically created with sensible permissions    |
| **Password**               | Not set by default                             | Password set interactively during user creation   |
| **Additional Info**        | No prompts for user info                       | Prompts for full name, phone number, etc. (optional)|
| **Groups**                 | Needs `-G` option to assign groups             | Prompts to add the user to groups                  |
| **Shell**                  | Needs `-s` option to specify shell             | Uses `/bin/bash` by default                        |
| **Default Use Case**       | Typically used in scripts, automation, or by sysadmins | Typically used for creating users interactively    |
