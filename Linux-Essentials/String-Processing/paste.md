# **`paste`**  
The `paste` command merges lines from multiple files or joins columns from structured data. It is useful for combining data side by side.  

## **Syntax**  
```bash
paste [OPTIONS] file1 file2 ...
```


## **Examples**  

- Merge two files line by line:  
  ```bash
  paste file1.txt file2.txt
  ```
  **Example Input:**  
  *file1.txt:*  
  ```
  Alice
  Bob
  Charlie
  ```
  *file2.txt:*  
  ```
  25
  30
  22
  ```
  **Output:**  
  ```
  Alice   25
  Bob     30
  Charlie 22
  ```

- Merge columns from a single file:  
  ```bash
  paste -d ',' names.txt ages.txt
  ```
  *(Uses `,` as a delimiter instead of the default tab.)*

- Merge multiple columns with a custom delimiter:  
  ```bash
  paste -d '|' file1.txt file2.txt
  ```
  *(Joins columns with `|` instead of tabs.)*

- Merge lines in a single file (convert multiple lines into a single line):  
  ```bash
  paste -s file.txt
  ```
  **Example Input:**  
  ```
  A
  B
  C
  ```
  **Output:**  
  ```
  A B C
  ```

- Merge lines with a specific delimiter:  
  ```bash
  paste -s -d ',' file.txt
  ```
  **Output:**  
  ```
  A,B,C
  ```

- Merge all lines into a single tab-separated row:  
  ```bash
  paste -s -d '\t' file.txt
  ```

- Combine multiple space-separated columns into a single tab-separated file:  
  ```bash
  paste file1.txt file2.txt file3.txt > merged.txt
  ```
