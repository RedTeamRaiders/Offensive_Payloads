# **`sed`**  
The `sed` (Stream Editor) command is a powerful text-processing tool used for modifying files, searching, filtering, replacing text, and more. It works line by line and is useful for automating text manipulation tasks.  


## **Syntax**  
```bash
sed [options] 'command' filename
```

## **Examples**  

### **Basic Commands**  

- **Append text after a matching line:**  
  ```bash
  sed '/pattern/a text' filename.txt
  ```

- **Insert text before a matching line:**  
  ```bash
  sed '/pattern/i text' filename.txt
  ```

- **Delete lines that match a pattern:**  
  ```bash
  sed '/pattern/d' filename.txt
  ```

- **Print lines that match a pattern:**  
  ```bash
  sed -n '/pattern/p' filename.txt
  ```

- **Quit `sed` processing after finding a pattern:**  
  ```bash
  sed '/pattern/q' filename.txt
  ```

---

### **Substitution Operations**  

- **Replace the first occurrence of a word in a line:**  
  ```bash
  sed 's/oldword/newword/' filename.txt
  ```

- **Replace all occurrences of a word in each line:**  
  ```bash
  sed 's/oldword/newword/g' filename.txt
  ```

- **Replace only the second occurrence in a line:**  
  ```bash
  sed 's/oldword/newword/2' filename.txt
  ```

- **Replace using extended regex (substitute all numbers with `***`):**  
  ```bash
  sed -r 's/[0-9]+/***/g' filename.txt
  ```

---

### **Line-Based Operations**  

- **Print only the first and second lines:**  
  ```bash
  sed -n '1,2p' /etc/passwd
  ```

- **Print only empty lines:**  
  ```bash
  sed -n '/^$/p' filename.txt
  ```

- **Print all non-empty lines:**  
  ```bash
  sed -n '/^$/!p' filename.txt
  ```

- **Print the last line of a file:**  
  ```bash
  sed -n '$p' filename.txt
  ```

- **Delete all lines from the 5th to the last:**  
  ```bash
  sed '5,$d' filename.txt
  ```

---

### **Advanced Usage**  

- **Replace all `/` occurrences with `-` in a file:**  
  ```bash
  sed 's#/#-#g' filename.txt
  ```

- **Convert uppercase letters to lowercase in a pattern:**  
  ```bash
  sed 's/\([A-Z]\)/(\1)/g' filename.txt
  ```

- **Print lines containing `root` and the next 3 lines:**  
  ```bash
  sed -n '/root/,+3p' /etc/passwd
  ```

- **Delete all lines that contain digits:**  
  ```bash
  sed '/[[:digit:]]/d' filename.txt
  ```

- **Replace a specific pattern with custom text:**  
  ```bash
  sed '/arnold/c ARNOLD User' filename.txt
  ```

- **Quit `sed` processing once a specific word is found:**  
  ```bash
  sed '/arnold/q' filename.txt
  ```

---

### **Execute Shell Commands in `sed`**  

- **Run a command (e.g., `date`) inside `sed`:**  
  ```bash
  sed '1e date' filename.txt
  ```

- **Replace all numbers with asterisks:**  
  ```bash
  echo "User ID 1000" | sed 's/[0-9]\+/*****/'
  ```

---

### **Multiple `sed` Commands**  

- **Print lines containing both `arnold` and `root`:**  
  ```bash
  sed -ne '/arnold/p' -ne '/root/p' filename.txt
  ```

- **Append and insert text around a pattern:**  
  ```bash
  sed -e '/arnold/a "+++++++++++++++++++++"' -e '/arnold/i "---------------------"' filename.txt
  ```

- **Modify files in place (without creating a backup):**  
  ```bash
  sed -i -e '/arnold/a "+++++++++++++++++++++"' -e '/arnold/i "---------------------"' filename.txt
  ```
