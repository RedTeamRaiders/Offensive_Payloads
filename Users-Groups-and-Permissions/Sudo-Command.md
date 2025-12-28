## Introduction to `sudo`

The `sudo` command allows a user to run specific commands with root privileges **without switching users**. Unlike `su`, it requires the user’s own password instead of the root password.  


## Installing `sudo`

### Check if `sudo` is Installed

```
rpm -qa | grep sudo
```


### Install `sudo` (if not installed)

For **RPM-based distributions** (e.g., RHEL, CentOS):

```
yum install sudo
```

For **DEB-based distributions** (e.g., Debian, Ubuntu):

```
apt-get install sudo
```

## **Syntax**  
```bash
sudo [options] command
```


## **Switches and Options**  

- `-l` → List the commands the user can execute with `sudo`.  
- `-u` → Run a command as a specific user.  
- `-i` → Open an interactive root shell.  
- `-s` → Start a shell with root privileges.  
- `-k` → Reset the timestamp (requires re-authentication).  
- `-v` → Extend the sudo session without running a command.  
- `-b` → Run a command in the background.  


## **Examples**  

- Run a command as a specific user (`john`):  
  ```bash
  sudo -u john whoami
  ```

- Open an interactive root shell:  
  ```bash
  sudo -i
  ```

- Open a shell as a specific user (`john`):  
  ```bash
  sudo -u john -s
  ```

- Run a background process with sudo:  
  ```bash
  sudo -b command
  ```

- List allowed sudo commands for the current user:  
  ```bash
  sudo -l
  ```

- Reset the sudo session (requires password next time):  
  ```bash
  sudo -k
  ```

- Extend the sudo session without executing a command:  
  ```bash
  sudo -v
  ```


## **Granting `sudo` Privileges to a User**  

To allow a user (`john`) to use `sudo`:  

1. Add the user to the `sudo` group:  
   ```bash
   usermod -aG sudo john
   ```
2. Verify the user's sudo access:  
   ```bash
   sudo -l
   ```


## **Managing `sudo` Privileges with the `/etc/sudoers` File**  

The `/etc/sudoers` file is a critical configuration file that defines which users and groups can execute commands with elevated privileges using `sudo`.

## **Editing the `sudoers` File Safely**  
Instead of editing `/etc/sudoers` directly, use `visudo` to prevent syntax errors.

- Open the file with `visudo`:  
  ```bash
  sudo visudo
  ```
- If using a specific editor (e.g., nano or vim):  
  ```bash
  EDITOR=nano sudo visudo
  ```

## **Understanding the `sudoers` File Format**  

Each entry in `/etc/sudoers` follows this structure:  

```plaintext
<user or group> <hostname> = (<run_as_user>) <command>
```

- **User/Group**: The user or `%group` being granted permissions.  
- **Hostname**: Specifies which hosts this rule applies to (use `ALL` for all hosts).  
- **Run as User**: Defines which user the command runs as (use `ALL` for any user).  
- **Command**: Specifies the allowed commands (use `ALL` for all commands).  


## **Examples of sudo Permissions**  

- **Grant Full sudo Privileges to a User**  
  ```bash
  john ALL=(ALL) ALL
  ```
  - `john` → User  
  - `ALL` → Any host  
  - `(ALL)` → Can run commands as any user  
  - `ALL` → Can run all commands  

- **Restrict sudo to Specific Commands**  
  ```bash
  john ALL=(ALL) /bin/systemctl restart apache2, /bin/apt update
  ```

- **Grant Passwordless sudo Access**  
  ```bash
  john ALL=(ALL) NOPASSWD: ALL
  ```
- **Grant sudo Access to a Group (`admins`)**  
  ```bash
  %admins ALL=(ALL) ALL
  ```

## **Special Tags in sudoers File**  

| Tag         | Description |
|-------------|-------------|
| `NOPASSWD`  | No password required for specified commands |
| `PASSWD`    | Require password (default) |
| `NOEXEC`    | Prevent running subcommands |
| `EXEC`      | Allow execution of subcommands |
| `SETENV`    | Allow setting environment variables |
| `NOSETENV`  | Prevent setting environment variables |

### **Example: Passwordless Package Updates for User `dave`**  
```bash
dave ALL=(ALL) NOPASSWD: /usr/bin/apt-get update
```
- `dave` can update packages without a password.


## **Using Aliases in `sudoers`**  

Aliases simplify permission management by grouping multiple values.  

### **Host Aliases**  
- Define multiple machines:  
  ```bash
  Host_Alias FILESERVERS = fs1, fs2, fs3
  ```

### **User Aliases**  
- Group multiple users:  
  ```bash
  User_Alias ADMINS = alice, bob, charlie
  ```

### **Command Aliases**  
- Group multiple commands:  
  ```bash
  Cmnd_Alias MAINTENANCE = /bin/systemctl restart apache2, /bin/systemctl restart mysql
  ```

### **Example Using Aliases**  
  ```bash
  ADMINS FILESERVERS = (ALL) NOPASSWD: MAINTENANCE
  ```

## **Restricting `sudo` Permissions**  

- **Deny a User from Running Commands with sudo**  
  ```bash
  john ALL=(ALL) !/bin/rm -rf, !/bin/shutdown
  ```

- **Prevent Users from Running Any Command as root**  
  ```bash
  john ALL=(ALL,!root) ALL
  ```