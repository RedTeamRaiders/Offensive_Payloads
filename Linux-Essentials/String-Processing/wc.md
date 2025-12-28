# **`wc`**  

The `wc` (word count) command is used to count the number of **lines, words, characters, or bytes** in a file. It is useful for analyzing text files and checking file sizes.  

## **Syntax**  
```
wc [OPTIONS] file
```


## **Examples**  

- Count **lines, words, and characters** in a file (default output):  
  ```bash
  wc file.txt
  ```
  **Output format:**  
  ```
  20  150  1024 file.txt
  ```
  - `20` → Number of lines  
  - `150` → Number of words  
  - `1024` → Number of bytes  

- Count only **lines** in a file:  
  ```bash
  wc -l file.txt
  ```

- Count only **words** in a file:  
  ```bash
  wc -w file.txt
  ```

- Count only **characters** (including spaces) in a file:  
  ```bash
  wc -m file.txt
  ```

- Count only **bytes** in a file:  
  ```bash
  wc -c file.txt
  ```

- Count lines in multiple files:  
  ```bash
  wc -l file1.txt file2.txt
  ```

- Count words from the output of another command:  
  ```bash
  echo "Hello World" | wc -w
  ```