## **ClamAV - Open-Source Antivirus for Linux**  

**ClamAV** is an open-source antivirus software designed for detecting malware, viruses, and other threats on Linux systems. It is commonly used for scanning files, email gateways, and web servers to enhance security. ClamAV includes a command-line scanner (`clamscan`), a daemon for faster scanning (`clamd`), and an automatic virus definition updater (`freshclam`).  



## **Installation**  

### **Ubuntu/Debian**  
Update system packages and install ClamAV:  
```bash
sudo apt update && sudo apt upgrade -y  
sudo apt install clamav clamav-daemon -y  
```

### **CentOS/RHEL**  
Enable the EPEL repository and install ClamAV:  
```bash
sudo yum install epel-release -y  
sudo yum install clamav clamav-update -y  
```



## **Updating Virus Definitions**  

Before scanning, update the virus database:  
```bash
sudo freshclam  
```

For automatic updates, restart the update service:  
```bash
sudo systemctl enable --now clamav-freshclam  
```



## **Scanning Files and Directories**  

### **Basic Scans**  
- Scan a specific file:  
  ```bash
  clamscan /path/to/file  
  ```
- Scan a directory recursively:  
  ```bash
  clamscan -r /path/to/directory  
  ```

### **Advanced Scan Options**  
- Show detailed output:  
  ```bash
  clamscan -v /path/to/directory  
  ```
- Move infected files to quarantine:  
  ```bash
  clamscan --move=/path/to/quarantine /path/to/directory  
  ```
- Remove infected files automatically:  
  ```bash
  clamscan --remove /path/to/directory  
  ```
- Log scan results to a file:  
  ```bash
  clamscan -l /var/log/clamav_scan.log /path/to/directory  
  ```



## **Using ClamAV Daemon (`clamd`) for Faster Scans**  

Enable and start the ClamAV daemon:  
```bash
sudo systemctl enable --now clamav-daemon  
```

Scan files using `clamdscan` (faster than `clamscan`):  
```bash
clamdscan /path/to/directory  
```



## **Scheduling Regular Scans**  

Schedule a daily scan at 2 AM using **cron**:  
```bash
crontab -e  
```
Add the following line:  
```bash
0 2 * * * clamscan -r /home/user/documents --log=/var/log/clamav_scan.log  
```



## **Checking ClamAV Logs**  

To view scan results and errors:  
```bash
cat /var/log/clamav/clamd.log  
```



## **Testing ClamAV with the EICAR Test File**  

Download the **EICAR** test file (a harmless virus test file):  
```bash
wget https://www.eicar.org/download/eicar.com -O ~/eicar.com  
```

Scan the test file to verify ClamAV is working:  
```bash
clamscan ~/eicar.com  
```

ClamAV should detect and flag the test file as a virus.



## **Uninstalling ClamAV**  

### **Ubuntu/Debian**  
```bash
sudo apt remove --purge clamav clamav-daemon -y  
sudo apt autoremove -y  
```

### **CentOS/RHEL**  
```bash
sudo yum remove clamav clamav-update -y  
```
