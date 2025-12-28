# Wildcards in Linux

Wildcards are special characters used to represent one or more characters in file and directory names. They are commonly used in commands like `ls`, `cp`, `mv`, and `rm` to perform operations on multiple files at once. Mastering wildcards can greatly enhance your efficiency when working with the Linux command line.

---

## Summary of Wildcard Characters

- `*` : Matches zero or more characters.
- `?` : Matches exactly one character.
- `[]` : Matches any one character within the brackets.
- `{}` : Used to generate multiple strings or patterns (brace expansion).
- `-` : Specifies a range within square brackets.
- `!` : Used to negate a pattern within square brackets.
- `**` : Matches files and directories recursively (with `globstar` enabled).
- `~` : Represents the home directory.

---

## Wildcard Characters Explained

### 1. `*` (Asterisk)

- **Matches any number of characters (including zero characters).**
- Used to match files or directories with any name or extension.

**Examples:**

- `*.txt` &rarr; Matches all files with a `.txt` extension (e.g., `file1.txt`, `document.txt`).
- `file*` &rarr; Matches all files starting with `file` (e.g., `file1`, `file_abc`, `file123.txt`).

---

### 2. `?` (Question Mark)

- **Matches exactly one character.**
- Useful when you want to match files or directories where one character is variable.

**Examples:**

- `file?.txt` &rarr; Matches `file1.txt`, `fileA.txt`, but not `file.txt` (expects one character between `file` and `.txt`).
- `?abc` &rarr; Matches `1abc`, `aabc`, but not `abc`.

---

### 3. `[]` (Square Brackets)

- **Matches any one of the characters inside the brackets.**
- Can specify a range of characters.

**Examples:**

- `file[123].txt` &rarr; Matches `file1.txt`, `file2.txt`, `file3.txt`, but not `file4.txt`.
- `file[a-d].txt` &rarr; Matches `filea.txt`, `fileb.txt`, `filec.txt`, `filed.txt`.

**Negation inside square brackets:**

- `file[!a-d].txt` &rarr; Matches files like `filee.txt`, `filez.txt`, but not `filea.txt`, `fileb.txt`, etc.

---

### 4. `{}` (Curly Braces)

- **Used for brace expansion to generate multiple strings or patterns.**
- Creates combinations of strings, simplifying commands.

**Examples:**

- `file{1,2,3}.txt` &rarr; Matches `file1.txt`, `file2.txt`, `file3.txt`.
- `a{a,b,c}d` &rarr; Matches `aad`, `abd`, `acd`.

**Note:** Brace expansion is performed before wildcard matching.

---

### 5. `-` (Hyphen)

- **Specifies a range within square brackets `[]`.**

**Examples:**

- `file[a-z].txt` &rarr; Matches `filea.txt` to `filez.txt` (all lowercase letters).
- `file[0-9].txt` &rarr; Matches `file0.txt` to `file9.txt` (digits).

---

### 6. `!` (Exclamation Mark)

- **Negates a pattern within square brackets `[]`.**
- Matches any character *not* in the brackets.

**Examples:**

- `file[!a-c].txt` &rarr; Matches files not ending with `a`, `b`, or `c` (e.g., `filed.txt`).
- `file[!1-5].txt` &rarr; Matches `file6.txt`, `file7.txt`, but not `file1.txt` to `file5.txt`.

---

### 7. `**` (Double Asterisk)

- **Matches directories and files recursively.**
- Requires enabling the `globstar` shell option (Bash 4.0+).

**Examples:**

- `**/*.txt` &rarr; Matches all `.txt` files in the current and all subdirectories.
- `**/file` &rarr; Matches all files or directories named `file` at any directory level.

**To enable `globstar`:**

```
shopt -s globstar
```

---

### 8. `~` (Tilde)

- **Represents the home directory of the current user.**

**Examples:**

- `cd ~` &rarr; Navigates to the home directory.
- `ls ~/Documents` &rarr; Lists files in the `Documents` directory in your home folder.

---

## Practical Examples

1. `*.txt` &rarr; Matches all `.txt` files.
2. `file*` &rarr; Files starting with `file`.
3. `*file` &rarr; Files ending with `file`.
4. `*` &rarr; All files in the current directory.
5. `*.*` &rarr; Files with an extension.
6. `file*log*` &rarr; Files starting with `file` containing `log`.
7. `file?` &rarr; Files like `file1`, `fileA`.
8. `file[123]` &rarr; Matches `file1`, `file2`, or `file3`.
9. `file[a-z]` &rarr; Files `filea` to `filez`.
10. `file[0-9]` &rarr; Files `file0` to `file9`.
11. `file[a-d].txt` &rarr; `filea.txt` to `filed.txt`.
12. `file[!a-d].txt` &rarr; Files not ending with `a` to `d`.
13. `file{1,2,3}.txt` &rarr; Specific numbered files.
14. `file{a,b,c}.txt` &rarr; Files `filea.txt`, `fileb.txt`, `filec.txt`.
15. `*file*.txt` &rarr; Files containing `file` ending with `.txt`.
16. `file[abc]*` &rarr; Files starting with `filea`, `fileb`, or `filec`.
17. `*file[123].txt` &rarr; Any files ending with `file1.txt`, `file2.txt`, or `file3.txt`.
18. `**/*.txt` &rarr; All `.txt` files recursively.
19. `~` &rarr; Home directory reference.
20. `file[-abc]` &rarr; Files named `file-`, `filea`, `fileb`, or `filec`.
21. `file\!` &rarr; Files starting with `file!`.

**Note:** Escape special characters with `\` to match them literally.

22. `*~` &rarr; Files ending with `~` (backup files).
23. `*.bak` &rarr; Files with `.bak` extension.
24. `file{1..5}.txt` &rarr; `file1.txt` to `file5.txt` (sequence expansion).
25. `*.log*` &rarr; Files containing `.log`.
26. `*log` &rarr; Files ending with `log`.
27. `*test*` &rarr; Files containing `test`.
28. `file*txt` &rarr; Files starting with `file` ending with `txt`.
29. `file?.txt` &rarr; Files like `file1.txt`, `fileA.txt`.
30. `[a-c]*.txt` &rarr; Files starting with `a`, `b`, or `c`, ending with `.txt`.
31. `[!a-c]*.txt` &rarr; Files not starting with `a`, `b`, or `c`, ending with `.txt`.
32. `*[!.txt]` &rarr; Files not ending with `.txt`.
33. `*[^a-c]*.txt` &rarr; Files not containing `a` to `c`, ending with `.txt`.
34. `*.*.*` &rarr; Files with two dots in the name.
35. `file*.txt` &rarr; Files starting with `file` ending with `.txt`.

---

## Additional Notes

- **Escaping Wildcards:** To match wildcard characters (`*`, `?`, etc.) literally, precede them with a backslash (`\`):

  ```
  ls file\*
  ```

- **Character Classes:** Use character classes for advanced matching:

  - `[[:digit:]]` &rarr; Any digit (same as `[0-9]`).
  - `[[:alpha:]]` &rarr; Any alphabetic character (same as `[a-zA-Z]`).
  - `[[:alnum:]]` &rarr; Any alphanumeric character.
  - `[[:space:]]` &rarr; Any whitespace character.
  - `[[:upper:]]` &rarr; Uppercase letters.
  - `[[:lower:]]` &rarr; Lowercase letters.

**Examples:**

- `file[[:digit:]].txt` &rarr; Matches `file0.txt` to `file9.txt`.
- `*[[:space:]]*` &rarr; Files with spaces in their names.

---

### Enabling Recursive Matching with `**`

To use the `**` wildcard for recursive searches:

1. **Enable `globstar`:**

   ```
   shopt -s globstar
   ```

2. **Use `**` in your commands:**

   ```
   ls **/*.txt
   ```

   This lists all `.txt` files in the current directory and all subdirectories.

---

### Caution with Wildcards

- **Using Wildcards with `rm`:**

  Be extremely careful when using wildcards with the `rm` command to avoid deleting unintended files.

  **Safe Practice:**

  - Preview files before deleting:

    ```
    ls *.txt
    ```

  - Use interactive mode:

    ```
    rm -i *.txt
    ```
