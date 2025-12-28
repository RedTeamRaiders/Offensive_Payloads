# `rsync`

The `rsync` command is a fast and versatile tool for synchronizing files and directories between local and remote locations. It minimizes data transfer by copying only the differences between source and destination.  


## **Syntax**  
```bash
rsync [options] [source] [destination]
```


## **Examples**  

- **Copy a File Locally**  
  ```bash
  rsync -av file.txt /destination/path/
  ```

- **Copy a Directory Locally**  
  ```bash
  rsync -av /source/directory/ /destination/directory/
  ```

- **Synchronize a Directory with Progress**  
  ```bash
  rsync -av --progress /source/ /destination/
  ```

- **Copy Files to a Remote Server via SSH**  
  ```bash
  rsync -av -e ssh /local/path/ user@remote:/remote/path/
  ```

- **Copy Files from a Remote Server to Local Machine**  
  ```bash
  rsync -av -e ssh user@remote:/remote/path/ /local/path/
  ```

- **Delete Extra Files from the Destination** *(Mirror Sync)*  
  ```bash
  rsync -av --delete /source/ /destination/
  ```

- **Dry Run (Test Without Making Changes)**  
  ```bash
  rsync -avn /source/ /destination/
  ```

- **Compress Data During Transfer** *(Faster for Large Files)*  
  ```bash
  rsync -avz /source/ /destination/
  ```

- **Limit Bandwidth Usage to 500 KB/s**  
  ```bash
  rsync -avz --bwlimit=500 /source/ /destination/
  ```