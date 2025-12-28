The `gzip` command is used for **compressing** files, while `gunzip` is used for **decompressing** `.gz` files. `gzip` uses the **Lempel-Ziv (LZ77) compression algorithm**, making it fast and efficient for reducing file sizes.  


## **`gzip`**  

### **Syntax**  
```
gzip [OPTIONS] file
```

### **Examples**  

- Compress a file:  
  ```
  gzip file.txt
  ```

- Compress multiple files:  
  ```
  gzip file1.txt file2.txt file3.txt
  ```

- Compress a file while keeping the original:  
  ```
  gzip -k file.txt
  ```

- Compress with maximum compression:  
  ```
  gzip -9 largefile.log
  ```

- Compress with the fastest speed (lower compression):  
  ```
  gzip -1 quickfile.txt
  ```

- Test a compressed file for corruption:  
  ```
  gzip -t file.txt.gz
  ```

- Force overwrite an existing `.gz` file:  
  ```
  gzip -f file.txt
  ```


## **`gunzip`**  

### **Syntax**  
```
gunzip [OPTIONS] file.gz
```

### **Examples**  

- Decompress a `.gz` file:  
  ```
  gunzip file.txt.gz
  ```

- Keep the original compressed file while decompressing:  
  ```
  gunzip -k file.txt.gz
  ```

- Decompress multiple `.gz` files:  
  ```
  gunzip file1.txt.gz file2.txt.gz
  ```

- Test the integrity of a `.gz` file:  
  ```
  gunzip -t file.txt.gz
  ```

- Decompress with verbose output:  
  ```
  gunzip -v file.txt.gz
  ```



For more details, check the manual pages:  
```
gzip --help
gunzip --help
```
```
man gzip
man gunzip
```