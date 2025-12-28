The `tar` (Tape Archive) command is used for **archiving** multiple files and directories into a single file. It is commonly used with compression tools like `gzip` and `bzip2` to create `.tar.gz` or `.tar.bz2` files.  


## **`tar`**  

### **Syntax**  
```
tar [OPTIONS] archive_name.tar file1 file2 ...
```

### **Examples**  

- Create an uncompressed archive:  
  ```
  tar -cf archive.tar file1.txt file2.txt
  ```

- Create an archive from a directory:  
  ```
  tar -cf archive.tar my_folder/
  ```

- Create a compressed archive with `gzip` (`.tar.gz`):  
  ```
  tar -czf archive.tar.gz my_folder/
  ```

- Create a compressed archive with `bzip2` (`.tar.bz2`):  
  ```
  tar -cjf archive.tar.bz2 my_folder/
  ```

- Create a compressed archive with `xz` (`.tar.xz`):  
  ```
  tar -cJf archive.tar.xz my_folder/
  ```

- List contents of a tar archive:  
  ```
  tar -tf archive.tar
  ```

- Extract an archive:  
  ```
  tar -xf archive.tar
  ```

- Extract to a specific directory:  
  ```
  tar -xf archive.tar -C /path/to/destination/
  ```

- Extract a `.tar.gz` archive:  
  ```
  tar -xzf archive.tar.gz
  ```

- Extract a `.tar.bz2` archive:  
  ```
  tar -xjf archive.tar.bz2
  ```

- Extract a `.tar.xz` archive:  
  ```
  tar -xJf archive.tar.xz
  ```

- Append files to an existing archive:  
  ```
  tar -rf archive.tar newfile.txt
  ```

- Delete a file from an archive:  
  ```
  tar --delete -f archive.tar file1.txt
  ```

- Show progress while archiving:  
  ```
  tar -cvf archive.tar my_folder/
  ```


For more details, check the manual pages:  
```
tar --help
man tar
```