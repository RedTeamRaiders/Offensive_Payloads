# **`whereis`**  
The `whereis` command locates the binary, source, and manual page files of a given command.  

### **Syntax**  
```bash
whereis [command]
```

### **Examples**  

- **Find the binary, source, and manual locations of a command:**  
  ```bash
  whereis ls
  ```

- **Find only the binary location of a command:**  
  ```bash
  whereis -b nano
  ```

- **Find only the manual pages of a command:**  
  ```bash
  whereis -m bash
  ```

- **Find only the source files of a command:**  
  ```bash
  whereis -s gcc
  ```

- **Limit search paths to specific directories:**  
  ```bash
  whereis -B /usr/bin -f python
  ```

- **Find the location of multiple commands:**  
  ```bash
  whereis vim nano gcc
  ```
