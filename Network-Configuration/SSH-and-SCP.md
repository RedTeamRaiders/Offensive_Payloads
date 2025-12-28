# **`ssh`**  

The `ssh` command is used to securely connect to remote systems over an encrypted channel.

### **Syntax**  
```bash
ssh [options] user@remote_host
```

### **Examples**  

- **Basic SSH Connection**  
  ```bash
  ssh user@192.168.1.100
  ```

- **Connects using port `2222` instead of the default `22`.**
  ```bash
  ssh -p 2222 user@192.168.1.100
  ```

- **Uses a specific SSH key for authentication.**
  ```bash
  ssh -i ~/.ssh/id_rsa user@192.168.1.100
  ```
  
- **Executes `uptime` on the remote machine and returns the output.**  
  ```bash
  ssh user@192.168.1.100 "uptime"
  ```

- **Shows detailed debugging information.**  
  ```bash
  ssh -v user@192.168.1.100
  ```

- **Disable Host Key Checking (Not Recommended for Security Reasons)**  
  ```bash
  ssh -o StrictHostKeyChecking=no user@192.168.1.100
  ```


# **`scp`**  

The `scp` command securely transfers files between local and remote systems.

### **Syntax**  
```bash
scp [options] source destination
```

### **Examples**  

- **Copy a File from Local to Remote System**  
  ```bash
  scp file.txt user@192.168.1.100:/home/user/
  ```

- **Copy a File from Remote to Local System**  
  ```bash
  scp user@192.168.1.100:/home/user/file.txt .
  ```

- **Copy an Entire Directory to a Remote System**  
  ```bash
  scp -r /local/directory user@192.168.1.100:/remote/directory
  ```

- **Copy a File Using a Custom SSH Port**  
  ```bash
  scp -P 2222 file.txt user@192.168.1.100:/home/user/
  ```

- **Limit Bandwidth Usage During Transfer**  
  ```bash
  scp -l 500 file.txt user@192.168.1.100:/home/user/
  ```

- **Use an SSH Key for Secure File Transfer**
  ```bash
  scp -i ~/.ssh/id_rsa file.txt user@192.168.1.100:/home/user/
  ```