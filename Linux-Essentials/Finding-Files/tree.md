# **`tree`**  
The `tree` command displays the directory structure in a hierarchical format.

### **Syntax**  
```bash
tree [OPTIONS] [directory]
```

### **Examples**  

- **Display the directory structure:**  
  ```bash
  tree
  ```

- **Show hidden files as well:**  
  ```bash
  tree -a
  ```

- **Limit depth to 2 levels:**  
  ```bash
  tree -L 2
  ```

- **Display only directories:**  
  ```bash
  tree -d
  ```

- **Print the full path of each file:**  
  ```bash
  tree -f
  ```

- **Sort files alphabetically:**  
  ```bash
  tree --dirsfirst
  ```

- **Ignore specific directories:**  
  ```bash
  tree -I "node_modules"
  ```
- **List directory structure:**
    ```bash
    tree /home/user
    ```

- **Display only directories:**
    ```bash
    tree -d /home/user
    ```

- **Limit tree depth:**
    ```bash
    tree -L 2 /home/user
    ```