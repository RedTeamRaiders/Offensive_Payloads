# Find-Sensitive-File

## Overview

Find-Sensitive-File is a Bash script designed to search for potentially sensitive files on a system. It scans directories recursively to identify configuration files, credential files, SSH keys, database credentials, and other critical files that could contain sensitive information.

## Features

- Searches for commonly known sensitive files such as:
  - Configuration files (`config.php`, `wp-config.php`, `settings.php`)
  - Credential files (`.env`, `credentials.json`, `.aws/credentials`)
  - SSH-related files (`id_rsa`, `authorized_keys`, `ssh_config`)
  - Web server configuration (`nginx.conf`, `apache2.conf`, `httpd.conf`)
  - Database configuration (`.my.cnf`, `database.php`, `dbconnect.php`)
  - Log and history files (`.bash_history`, `.zsh_history`)
  - VPN and key files (`.key`, `.pem`, `.p12`, `.ovpn`)
- Uses the `find` command to locate these files efficiently.
- Can be executed from any directory.

## Usage

### Running the Script

1. **Clone the repository:**
   ```bash
   git clone https://github.com/InfoSecWarrior/Offensive-Pentesting-Scripts/Find-Sensitive-Files/find_sensitive_files.sh
   cd Find-Sensitive-File
   ```
2. **Give execution permissions to the script:**
   ```bash
   bash find_sensitive_files.sh
   ```
3. **Run the script:**
   ```bash
   ./find_sensitive_files.sh
   ```

ScreenShot :
![2025-02-06_12-37](https://github.com/user-attachments/assets/d413509e-f7fb-4e5b-9619-aff7c6240ad9)

### Customizing the Search

- Modify the `files` array in the script to add or remove filenames as needed.
- Change the `base_dir` variable to restrict the search to a specific directory instead of the entire system.

## Disclaimer

This script is intended for security auditing and educational purposes only. Running it on unauthorized systems without permission may violate legal and ethical guidelines.

## Contribution

Feel free to contribute by submitting issues or pull requests to improve the script.

