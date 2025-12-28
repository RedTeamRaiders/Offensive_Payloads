# **`which`**  
The `which` command is used to locate the executable file associated with a given command.

### **Syntax**  
```bash
which [command]
```

### **Examples**  

- **Find the path of an executable command:**  
  ```bash
  which ls
  ```

- **Find the path of multiple commands:**  
  ```bash
  which cp mv rm
  ```

- **Find all occurrences of an executable in `PATH`:**  
  ```bash
  which -a python
  ```

- **Check if a command exists in `PATH`:**  
  ```bash
  which nano || echo "nano is not installed"
  ```

- **Find the location of `bash`:**  
  ```bash
  which bash
  ```
