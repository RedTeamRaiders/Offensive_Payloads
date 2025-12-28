# **`head`**  

The `head` command is used to display the first few lines of a file. By default, it shows the first **10 lines** unless specified otherwise. It is useful for previewing large files without opening them completely.  


## **Syntax**  
```
head [OPTIONS] file
```

## **Examples**  

- Display the first **10 lines** of a file (default):  
  ```bash
  head file.txt
  ```

- Show the first **5 lines** of a file:  
  ```bash
  head -n 5 file.txt
  ```

- Display the first **20 bytes** of a file:  
  ```bash
  head -c 20 file.txt
  ```

- Show the first **10 lines** from multiple files:  
  ```bash
  head file1.txt file2.txt
  ```

- Display the first **15 lines** of a log file with file name:  
  ```bash
  head -n 15 logfile.txt
  ```

- Display the first 7 lines of a file efficiently: 
  ```bash
  head -n 7 file.txt
  ```

