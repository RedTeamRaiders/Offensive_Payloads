# `wget`  

The `wget` command is a free utility for non-interactive downloading of files from the internet. It supports HTTP, HTTPS, and FTP protocols and is useful for automated downloads and scripting.  


## **Syntax**  
```bash
wget [options] [URL]
```

## **Examples**  

- **Download a File**  
  ```bash
  wget https://example.com/file.zip
  ```

- **Download a File and Save with a Different Name**  
  ```bash
  wget -O myfile.zip https://example.com/file.zip
  ```

- **Resume an Interrupted Download**  
  ```bash
  wget -c https://example.com/file.zip
  ```

- **Download a File in the Background**  
  ```bash
  wget -b https://example.com/file.zip
  ```

- **Limit Download Speed to 500 KB/s**  
  ```bash
  wget --limit-rate=500k https://example.com/file.zip
  ```

- **Download Multiple Files from a List**  
  ```bash
  wget -i urls.txt
  ```
  *(Ensure `urls.txt` contains one URL per line.)*

- **Download an Entire Website (Mirroring)**  
  ```bash
  wget --mirror -p --convert-links -P ./local https://example.com/
  ```

- **Download a File with Authentication (Username & Password)**  
  ```bash
  wget --user=username --password=password https://example.com/file.zip
  ```

- **Set a Custom User-Agent (Bypass Blocks)**  
  ```bash
  wget --user-agent="Mozilla/5.0" https://example.com/file.zip
  ```

- **Skip SSL Certificate Checks**  
  ```bash
  wget --no-check-certificate https://example.com/file.zip
  ```