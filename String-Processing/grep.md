# **`grep`**  
The `grep` command searches for a pattern in a file and prints matching lines. It is useful for filtering text, searching logs, and extracting specific data from files.  


## **Syntax**  
```bash
grep [options] pattern [file]
```


## **Examples**  

- Find occurrences of **'searchword'** in a file:  
  ```bash
  grep searchword filename
  ```

- Find **'root'** in the `/etc/passwd` file:  
  ```bash
  grep "root" /etc/passwd
  ```

- Find **'root'** in multiple files:  
  ```bash
  grep root /etc/passwd /etc/shadow
  ```

- Perform **case-insensitive** search:  
  ```bash
  grep -i root messages
  ```

- Find multiple words (**'session', 'root', or 'mounting'**):  
  ```bash
  grep -E "session|root|mounting" /var/log/messages
  ```

- Find lines containing **both** 'session' and 'root':  
  ```bash
  grep "session" /var/log/messages | grep root
  ```

- Find lines with **'session'** but **not** 'root':  
  ```bash
  grep "session" /var/log/messages | grep -v root
  ```

- Find lines where **'root' appears at the start**:  
  ```bash
  grep "^root" /var/log/messages
  ```

- Find lines where **'root' appears at the end**:  
  ```bash
  grep "root$" /var/log/messages
  ```

- Find logs for **'root' on 2nd September'**:  
  ```bash
  grep "^2sep" /var/log/messages | grep root
  ```

- Find **'roo'** followed by any **single character**:  
  ```bash
  grep 'roo.' filename
  ```

- Find **'roo'** followed by **two characters**:  
  ```bash
  grep 'roo..' filename
  ```

- Find **empty lines** in a file:  
  ```bash
  grep '^$' filename
  ```

- Exclude lines **starting with `#`** (useful for config files):  
  ```bash
  grep -v '^#' ssd_config
  ```

- Find all **alphanumeric characters**:  
  ```bash
  grep "[[:alnum:]]" filename
  ```

- Search for **domains** from `domain.txt` in `url.txt`:  
  ```bash
  grep -f domain.txt url.txt
  ```
