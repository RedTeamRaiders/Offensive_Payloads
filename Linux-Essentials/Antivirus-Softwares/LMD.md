## **Linux Malware Detect (LMD) – Maldetect**  

**Linux Malware Detect (LMD)**, also known as **Maldetect**, is an open-source malware scanner designed for Linux servers. It is commonly used in combination with **ClamAV** for improved detection and cleaning of infected files. LMD is especially useful for detecting malware in shared hosting environments.  



## **Installing LMD**  

```bash
wget http://www.rfxn.com/downloads/maldetect-current.tar.gz  
```
```
tar -xvf maldetect-current.tar.gz  
```
```
cd maldetect-*  
```
```
sudo ./install.sh  
```


After installation, LMD will be located at:  
```bash
/usr/local/maldetect/  
```



## **Updating LMD and Virus Signatures**  

- **Update Maldetect**:  
  ```bash
  sudo maldet -u  
  ```
- **Update Malware Signatures**:  
  ```bash
  sudo maldet -d  
  ```



## **Basic Malware Scanning**  

- **Scan a directory**:  
  ```bash
  sudo maldet -a /path/to/directory  
  ```
- **Scan a specific file**:  
  ```bash
  sudo maldet -a /path/to/file  
  ```



## **Real-Time Monitoring with LMD**  

To enable real-time monitoring with **inotify**, edit the configuration file:  
```bash
sudo nano /usr/local/maldetect/conf.maldet  
```
Find the line:  
```ini
inotify_monitor="0"
```
Change it to:  
```ini
inotify_monitor="1"
```
Then restart Maldetect:  
```bash
sudo maldet --monitor /home/user/public_html  
```



## **Combining LMD with ClamAV**  

To improve malware detection, LMD can use **ClamAV** as a secondary scanner. Enable it by editing:  
```bash
sudo nano /usr/local/maldetect/conf.maldet  
```
Change:  
```ini
scan_clamscan="0"
```
To:  
```ini
scan_clamscan="1"
```
Save and restart LMD.



## **Advanced Scanning Options**  

- **Scan with verbose output**:  
  ```bash
  sudo maldet -a /var/www/html -v  
  ```
- **Scan and move infected files to quarantine**:  
  ```bash
  sudo maldet -a /home/user --move  
  ```
- **Scan and automatically clean infected files**:  
  ```bash
  sudo maldet -a /home/user --clean  
  ```
- **Scan and exclude specific file types**:  
  ```bash
  sudo maldet -a /var/www/html --exclude "*.log"  
  ```



## **Viewing Scan Reports**  

- **List all scan reports**:  
  ```bash
  sudo maldet --report list  
  ```
- **View a specific scan report**:  
  ```bash
  sudo maldet --report SCAN-ID  
  ```
  *(Replace SCAN-ID with the actual report ID)*  



## **Quarantine and Restore Infected Files**  

- **View quarantined files**:  
  ```bash
  sudo maldet --quarantine list  
  ```
- **Restore a quarantined file**:  
  ```bash
  sudo maldet --restore /usr/local/maldetect/quarantine/malicious-file  
  ```
- **Delete a quarantined file**:  
  ```bash
  sudo maldet --delete /usr/local/maldetect/quarantine/malicious-file  
  ```



## **Automating LMD Scans with Cron**  

To schedule a daily scan at **3 AM**, add a cron job:  
```bash
sudo crontab -e  
```
Add the following line:  
```bash
0 3 * * * /usr/local/maldetect/maldet -a /var/www/html --log  
```



## **Checking Logs**  

- **LMD scan logs**:  
  ```bash
  cat /usr/local/maldetect/logs/maldet.log  
  ```
- **Real-time monitoring logs**:  
  ```bash
  tail -f /usr/local/maldetect/logs/event_log  
  ```



## **Uninstalling LMD**  

To remove **Maldetect** from your system:  
```bash
sudo rm -rf /usr/local/maldetect  
```
```
sudo rm -f /usr/bin/maldet  
```