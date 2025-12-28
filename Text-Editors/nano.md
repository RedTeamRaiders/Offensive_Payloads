# **`nano` Text Editor**  

The `nano` command is a simple and user-friendly text editor for editing files directly in the terminal. It is easy to use and comes pre-installed on many Linux distributions.  


## **`nano`**  

### **Syntax**  
```
nano [OPTIONS] filename
```

### **Examples**  

- Opens `file.txt` or creates a new file if it doesn’t exist.
  ```
  nano file.txt
  ```


- `-l` shows line numbers in the editor.
  ```
  nano -l file.txt
  ```
  

- `-v` prevents accidental modifications.
  ```
  nano -v file.txt
  ```

- Open a file and position the cursor at a specific line and column:  
  ```
  nano +10,5 file.txt
  ```

- Open a file without wrapping long lines:  
  ```
  nano -w file.txt
  ```

## **Basic `nano` Keyboard Shortcuts**  

- **Save (Write to file):** `CTRL + O` (Press **Enter** to confirm)  
- **Exit nano:** `CTRL + X`  
- **Cut a line:** `CTRL + K`  
- **Paste a line:** `CTRL + U`  
- **Copy a line:** `CTRL + K` (cut) and `CTRL + U` (paste multiple times)  
- **Find text in file:** `CTRL + W` (Type text and press **Enter**)  
- **Find and replace text:** `CTRL + \` (Enter search text, then replacement text)  
- **Move to the beginning of the file:** `CTRL + Y`  
- **Move to the end of the file:** `CTRL + V`  
- **Undo last action:** `ALT + U`  
- **Redo last undone action:** `ALT + E`  

---

For more details, check the manual pages:  
```
nano --help
man nano
```