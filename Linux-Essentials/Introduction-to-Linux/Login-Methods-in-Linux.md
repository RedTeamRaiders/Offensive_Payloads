## Linux Login Methods
In Linux, there are multiple methods to log in to the system, depending on the environment and authentication method used. 

## Common login methods:

### 1. **Console Login (TTY)**
   - When using a Linux system without a graphical user interface (GUI), you log in via a terminal (TTY).
   - After booting, the system presents a text-based login prompt where you enter your username and password.
   - Example:
     ```
     login: username
     Password: ******
     ```

### 2. **Graphical Login (GUI)**
   - If a display manager (e.g., GDM, LightDM, SDDM) is installed, you can log in using a graphical interface.
   - You select a user, enter a password, and access the desktop environment.

### 3. **SSH Login (Remote Login)**
   - Secure Shell (SSH) allows remote login to a Linux system.
   - The command to log in remotely from another system:
     ```
     ssh username@hostname_or_IP
     ```
   - It can use password-based authentication or SSH key-based authentication for security.

### 4. **Root Login (Superuser)**
   - The root user can log in directly using:
     ```
     su -
     ```
   - However, direct root login is often disabled for security reasons.
   - Instead, use `sudo` to execute commands as root:
     ```
     sudo command
     ```


### 5. **Login Using LDAP or Active Directory**
   - Large organizations may use LDAP (Lightweight Directory Access Protocol) or integrate with Active Directory for centralized authentication.

### 6. **Single-User Mode (Recovery Mode)**
   - Used for system maintenance and recovery.
   - Accessed by booting into recovery mode via GRUB.
   - Provides a root shell without requiring a password (in some configurations).

