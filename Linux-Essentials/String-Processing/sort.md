# **`sort`**  

The `sort` command arranges lines of text files in **ascending** or **descending** order. It is useful for organizing data, sorting numbers, and handling large text files.  


## **Syntax**  
```
sort [OPTIONS] file
```

## **Examples**  

- Sort a file in **ascending** order (default):  
  ```bash
  sort file.txt
  ```

- Sort a file in **descending** order:  
  ```bash
  sort -r file.txt
  ```

- Sort numbers instead of treating them as text:  
  ```bash
  sort -n numbers.txt
  ```
  *(Useful when sorting numerical values like 1, 10, 2, 20.)*  

- Sort numbers in **descending** order:  
  ```bash
  sort -nr numbers.txt
  ```

- Remove duplicate lines while sorting:  
  ```bash
  sort -u file.txt
  ```

- Sort based on the **second column** (numerically if needed): 
  ```bash
  sort -k2,2 file.txt
  ```

- Sort a file while ignoring case:  
  ```bash
  sort -f file.txt
  ```

- Sort a CSV file based on the **third column**:  
  ```bash
  sort -t, -k3 file.csv
  ```
  *(Here, `-t,` specifies a comma as the delimiter.)*

- Sort with a human-readable size (e.g., KB, MB, GB):  
  ```bash
  sort -h sizes.txt
  ```

- Sort a file and **save the output** to a new file:  
  ```bash
  sort file.txt > sorted_file.txt
  ```