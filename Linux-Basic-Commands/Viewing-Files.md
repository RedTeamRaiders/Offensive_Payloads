Linux provides several commands to view the contents of a file without opening a text editor. The `less` and `more` commands are commonly used for this purpose.


# **`less`**

The `less` command allows you to view the contents of a file one screen at a time. 

### **Syntax**
```
less [OPTIONS] filename
```

### **Examples**

1. View a file using `less`:
   ```bash
   less file.txt
   ```
   This opens `file.txt` in the `less` viewer.

2. Scroll down one page at a time:
   - Press `Space` or `PgDn`

3. Scroll up one page at a time:
   - Press `b` or `PgUp`

4. Search for a word:
   ```bash
   /word
   ```
   - Press `n` to jump to the next match.
   - Press `N` to jump to the previous match.

5. View a file with line numbers:
   ```bash
   less -N file.txt
   ```
   This will display line numbers alongside the text.

6. Exit `less`:
   - Press `q`.

7. Display file contents and monitor updates in real-time:
   ```bash
   less +F logfile.log
   ```
   - Similar to `tail -f`, but allows scrolling back with `Ctrl + C`.

# **`more`**

The `more` command is another pager that allows viewing file contents one page at a time. Unlike `less`, it does not allow backward navigation.

### **Syntax**
```
more [OPTIONS] filename
```

### **Examples**

1. View a file using `more`:
   ```bash
   more file.txt
   ```

2. Scroll down one page at a time:
   - Press `Space`

3. Scroll line by line:
   - Press `Enter`

4. Search for a word:
   ```bash
   /word
   ```
   - Press `n` to jump to the next match.

5. View file contents with percentage display:
   ```bash
   more -d file.txt
   ```
   - Displays a percentage indicator at the bottom.

6. Exit `more`:
   - Press `q`.
