The `bzip2` command compresses files using the **Burrows-Wheeler** algorithm, providing better compression than `gzip`. The `bunzip2` command is used to decompress `.bz2` files.  


## **`bzip2`**  

### **Syntax**  
```
bzip2 [OPTIONS] file
```

### **Examples**  

- Compress a file:  
  ```
  bzip2 file.txt
  ```

- Compress multiple files:  
  ```
  bzip2 file1.txt file2.txt file3.txt
  ```

- Compress a file while keeping the original:  
  ```
  bzip2 -k file.txt
  ```

- Compress with maximum compression:  
  ```
  bzip2 -9 largefile.log
  ```

- Compress with the fastest speed (lower compression):  
  ```
  bzip2 -1 quickfile.txt
  ```

- Test a compressed file for corruption:  
  ```
  bzip2 -t file.txt.bz2
  ```

- Force overwrite an existing `.bz2` file:  
  ```
  bzip2 -f file.txt
  ```



## **`bunzip2`**  

### **Syntax**  
```
bunzip2 [OPTIONS] file.bz2
```

### **Examples**  

- Decompress a `.bz2` file:  
  ```
  bunzip2 file.txt.bz2
  ```

- Keep the original compressed file while decompressing:  
  ```
  bunzip2 -k file.txt.bz2
  ```

- Decompress multiple files at once:  
  ```
  bunzip2 file1.txt.bz2 file2.txt.bz2
  ```

- Test the integrity of a `.bz2` file:  
  ```
  bunzip2 -t file.txt.bz2
  ```

- Decompress with verbose output:  
  ```
  bunzip2 -v file.txt.bz2
  ```

For more details, check the manual pages:  
```
bzip2 --help
bunzip2 --help
```
```
man bzip2
man bunzip2
```