## `touch`  
Creates a new empty file or updates the timestamp of an existing file without modifying its contents.  

**Syntax:**  
```
touch [filename]
```

**Examples:**  
- Create a new empty file  
  ```
  touch myfile.txt
  ```
- Create multiple files at once  
  ```
  touch file1.txt file2.txt file3.txt
  ```
- Update the timestamp of an existing file  
  ```
  touch existingfile.txt
  ```
- Set a specific timestamp (e.g., January 1, 2024, at 12:00 PM)  
  ```
  touch -t 202401011200 myfile.txt
  ```



## `mkdir`  
Creates one or multiple directories at the specified location.  

**Syntax:**  
```
mkdir [directory_name]
```

**Examples:**  
- Create a single directory  
  ```
  mkdir new_folder
  ```
- Create multiple directories at once  
  ```
  mkdir folder1 folder2 folder3
  ```
- Create nested directories in one command  
  ```
  mkdir -p parent/child/grandchild
  ```
- Set permissions while creating a directory  
  ```
  mkdir -m 755 my_secure_folder
  ```



## `rmdir`  
Deletes an empty directory; does not work if the directory contains files.  

**Syntax:**  
```
rmdir [directory_name]
```

**Examples:**  
- Remove an empty directory  
  ```
  rmdir old_folder
  ```
- Remove multiple empty directories at once  
  ```
  rmdir dir1 dir2 dir3
  ```
- Remove nested empty directories  
  ```
  rmdir -p parent/child/grandchild
  ```


## `rm`  
Removes files or directories permanently. Be careful, as deleted files cannot be easily recovered.  

**Syntax:**  
```
rm [options] [file/directory]
```

**Examples:**  
- Remove a single file  
  ```
  rm file.txt
  ```
- Remove multiple files at once  
  ```
  rm file1.txt file2.txt file3.txt
  ```
- Remove a directory and all its contents (use with caution)  
  ```
  rm -rf foldername
  ```
- Remove files with a confirmation prompt  
  ```
  rm -i file.txt
  ```
- Remove all `.txt` files in the current directory  
  ```
  rm *.txt
  ```
- Remove all files except one specific file  
  ```
  rm !(important.txt)
  ```
