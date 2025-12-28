# **`tr`**  
The `tr` (translate) command is used to replace, delete, or compress characters from standard input and write the result to standard output.


## **Syntax**  
```bash
tr [OPTIONS] SET1 [SET2]
```


## **Examples**  

### **Basic Character Translation**  

- **Convert lowercase letters to uppercase:**  
  ```bash
  echo "hello world" | tr 'a-z' 'A-Z'
  ```

- **Convert uppercase letters to lowercase:**  
  ```bash
  echo "HELLO WORLD" | tr 'A-Z' 'a-z'
  ```

- **Replace spaces with underscores:**  
  ```bash
  echo "hello world" | tr ' ' '_'
  ```

---

### **Deleting Characters**  

- **Remove digits from input:**  
  ```bash
  echo "abc123xyz" | tr -d '0-9'
  ```

- **Remove vowels from input:**  
  ```bash
  echo "Hello World" | tr -d 'aeiouAEIOU'
  ```

- **Remove all non-alphanumeric characters:**  
  ```bash
  echo "User@123\!" | tr -d '[:punct:]'
  ```

---

### **Squeezing Repeated Characters**  

- **Replace multiple spaces with a single space:**  
  ```bash
  echo "Hello     World" | tr -s ' '
  ```

- **Compress multiple blank lines into one:**  
  ```bash
  cat file.txt | tr -s '\n'
  ```

---

### **Working with Character Ranges and Classes**  

- **Convert digits to `X`:**  
  ```bash
  echo "My phone is 9876543210" | tr '0-9' 'X'
  ```

- **Convert lowercase letters to uppercase using character classes:**  
  ```bash
  echo "hello world" | tr '[:lower:]' '[:upper:]'
  ```

- **Remove all non-printable characters:**  
  ```bash
  cat file.txt | tr -cd '[:print:]'
  ```

---

### **Replacing and Cleaning Text**  

- **Replace colons (`:`) with spaces:**  
  ```bash
  echo "user:password:1234" | tr ':' ' '
  ```

- **Remove trailing newlines:**  
  ```bash
  echo -e "Hello\n\n\nWorld" | tr -s '\n'
  ```

- **Replace tabs with spaces:**  
  ```bash
  cat file.txt | tr '\t' ' '
  ```