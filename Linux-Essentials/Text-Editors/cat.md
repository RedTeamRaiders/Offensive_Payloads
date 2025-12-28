## **`cat`**

The `cat` (short for concatenate) command is one of the most commonly used Linux commands. It is used to view, create, concatenate, and manipulate text files.

It can:

- Display the contents of a file.
- Merge multiple files into a single file.
- Create new files.
- Append content to an existing file.

### **Syntax:**  
```bash
cat [OPTION] [FILE...]
```
Where:  
- `[OPTION]` refers to flags that modify the behavior of `cat`.  
- `[FILE...]` specifies one or more files to read and process.  


### **Examples:**

- View the content of a file:
   ```bash
   cat file.txt
   ```

- Display a file with scrolling:
   ```bash
   cat file.txt | less
   ```
   or simply:
   ```bash
   less file.txt
   ```

- Create a new file and add content:
   ```bash
   cat > file1.txt
   ```
   (Press **Ctrl + D** to save and exit.)

- Append content to an existing file:
   ```bash
   cat >> file1.txt
   ```
- Combine multiple files into one:
   ```bash
   cat file1.txt file2.txt > merged.txt
   ```

- Display line numbers while viewing a file:
   ```bash
   cat -n filename
   ```
- Remove extra blank lines in a text file:
    ```bash
    cat -s file.txt
    ```