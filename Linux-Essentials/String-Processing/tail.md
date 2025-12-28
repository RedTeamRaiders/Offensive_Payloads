# **`tail`**  

The `tail` command is used to display the last few lines of a file. By default, it shows the last **10 lines**, but this can be adjusted using options. It is commonly used for monitoring log files in real-time.  


## **Syntax**  
```
tail [OPTIONS] file
```

## **Examples**  

- Display the last **10 lines** of a file (default):  
  ```bash
  tail file.txt
  ```

- Show the last **5 lines** of a file:  
  ```bash
  tail -n 5 file.txt
  ```

- Display the last **20 bytes** of a file:  
  ```bash
  tail -c 20 file.txt
  ```

- Show the last **10 lines** from multiple files:  
  ```bash
  tail file1.txt file2.txt
  ```

- Continuously monitor a file (useful for logs):  
  ```bash
  tail -f logfile.txt
  ```

- Monitor a file and show **5 latest lines**:  
  ```bash
  tail -n 5 -f logfile.txt
  ```

- Display the last 7 lines of a file efficiently:  
  ```bash
  tail -n 7 file.txt
  ```

