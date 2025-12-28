# **FTP (File Transfer Protocol) Commands**  

FTP (File Transfer Protocol) is used to transfer files between a client and a server over a network. It supports interactive file management and authentication.  


## **Installation**  

### **Debian/Ubuntu**  
```bash
sudo apt install ftp -y
```

### **RHEL/CentOS/Fedora**  
```bash
sudo yum install ftp -y  # RHEL/CentOS
sudo dnf install ftp -y  # Fedora
```

## **Syntax**  
```bash
ftp [options] [hostname/IP]
```



## **Examples**  

### **Connecting to an FTP Server**  
```bash
ftp ftp.example.com
```

### **Login to an FTP Server**  
```bash
ftp
```
```bash
open ftp.example.com
```
*You will be prompted for a username and password.*


## **Basic FTP Commands**  

- **List files in the current directory**  
  ```bash
  ls
  ```

- **Change directory on the remote server**  
  ```bash
  cd /path/to/directory
  ```

- **Change directory on the local machine**  
  ```bash
  lcd /local/path
  ```

- **Upload a file to the server**  
  ```bash
  put file.txt
  ```

- **Download a file from the server**  
  ```bash
  get file.txt
  ```

- **Download multiple files**  
  ```bash
  mget *.txt
  ```

- **Upload multiple files**  
  ```bash
  mput *.txt
  ```

- **Check the current working directory on the server**  
  ```bash
  pwd
  ```

- **Enable binary mode for non-text files (e.g., images, archives, etc.)**  
  ```bash
  binary
  ```

- **Enable ASCII mode for text files**  
  ```bash
  ascii
  ```

- **Delete a file on the server**  
  ```bash
  delete file.txt
  ```

- **Remove a directory on the server**  
  ```bash
  rmdir directory_name
  ```

- **Create a directory on the server**  
  ```bash
  mkdir new_directory
  ```

- **Close the FTP session**  
  ```bash
  bye
  ```

- **Quit the FTP session**  
  ```bash
  quit
  ```
