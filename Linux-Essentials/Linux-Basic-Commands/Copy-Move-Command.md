## `cp`

The `cp` command is used to copy files and directories in Linux.

### Syntax

```
cp [OPTION]... SOURCE DESTINATION
```

### Examples

- Copy a file from one location to another:
   ```
   cp file.txt /home/user/Documents/
   ```

- Copy a directory and its contents recursively:
   ```
   cp -r my_folder /home/user/backup/
   ```

- Copy a file and preserve attributes (timestamps, ownership, etc.):
   ```
   cp -p file.txt /home/user/backup/
   ```

- Copy multiple files to a directory:
   ```
   cp file1.txt file2.txt /home/user/backup/
   ```

- Copy a file with verbose output:
   ```
   cp -v file.txt /home/user/Documents/
   ```

-  Copy a file but prompt before overwriting:
   ```
   cp -i file.txt /home/user/Documents/
   ```

- Copy only newer files (to avoid overwriting newer versions):
   ```
   cp -u file.txt /home/user/backup/
   ```

-  Copy a symbolic link instead of its target:
   ```
   cp -P symlink /home/user/backup/
   ```

-  Copy a file to multiple destinations:
   ```
   cp file.txt /home/user/Documents/ /home/user/backup/
   ```

## `mv`

The `mv` command is used to move or rename files and directories in Linux.

## Syntax

```
mv [OPTION]... SOURCE DESTINATION
```

## Examples

-  Move a file to another directory:
   ```
   mv file.txt /home/user/Documents/
   ```

-  Rename a file:
   ```
   mv oldname.txt newname.txt
   ```

-  Move a directory:
   ```
   mv my_folder /home/user/backup/
   ```

-  Move multiple files to a directory:
   ```
   mv file1.txt file2.txt /home/user/Documents/
   ```

-  Rename a directory:
   ```
   mv old_folder new_folder
   ```

-  Move a file but prompt before overwriting:
   ```
   mv -i file.txt /home/user/Documents/
   ```

-  Move a file and provide verbose output:
   ```
   mv -v file.txt /home/user/Documents/
   ```

-  Force move a file without prompting:
   ```
   mv -f file.txt /home/user/Documents/
   ```

-  Backup an existing destination file before moving:
   ```
   mv --backup file.txt /home/user/Documents/
   ```

-  Move a file but prevent overwriting if the file exists:
   ```
   mv -n file.txt /home/user/Documents/
   ```