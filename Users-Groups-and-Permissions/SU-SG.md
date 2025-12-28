# **Sharing Superuser Privileges**  

In Linux, administrative tasks require superuser privileges. Instead of logging in as `root`, users can temporarily gain superuser access using `su` or `sudo`.  


## **`su` (Substitute User) – Switch to Another User**  

The `su` command allows switching to another user account, including `root`. By default, it switches to `root` unless another username is specified.  

### **Syntax**  
```bash
su [options] [username]
```

### **Common Options**  
- `-` → Start a login shell with the target user’s environment.  
- `-c "command"` → Execute a single command as the target user.  
- `-s /bin/sh` → Specify a shell for the session.  
- `-m` or `-p` → Preserve the current user’s environment.  

### **Examples**  
- Switch to the root user (requires root password):  
  ```bash
  su -
  ```
- Switch to another user (e.g., `john`):  
  ```bash
  su john
  ```
- Run a single command as root:  
  ```bash
  su -c "apt update" root
  ```
- Use a different shell while switching users:  
  ```bash
  su -s /bin/sh john
  ```
- Preserve the current environment while switching:  
  ```bash
  su -m john
  ```

⚠️ **Security Concern**: `su` requires the root password, which can be a security risk if shared with multiple users.


## **`sg`** – Switch Group  

The `sg` (Substitute Group) command allows executing a command as a different group.  

### **Syntax**  
```bash
sg groupname -c "command"
```

### **Examples**  
- Run a command as the `developers` group:  
  ```bash
  sg developers -c "whoami"
  ```
- Switch to the `finance` group and start a new shell:  
  ```bash
  sg finance
  ```
- Execute a script as the `marketing` group:  
  ```bash
  sg marketing -c "./script.sh"
  ```
- Run a command with multiple groups:  
  ```bash
  sg developers -c "sg testers -c 'id'"
  ```