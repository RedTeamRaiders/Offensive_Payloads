# Redirection Operators

- `>` : Redirect stdout to a file (overwrites file).
- `>>` : Append stdout to a file.
- `2>` : Redirect stderr to a file (overwrites file).
- `2>>` : Append stderr to a file.
- `<` : Redirect stdin from a file.
- `|` : Pipe stdout of one command to stdin of another command.
- `2>&1` : Combine stderr and stdout.
- `<<` : Here document for input redirection.


# Redirection in Linux

Redirection in Linux allows you to control the input and output of commands. It enables you to redirect the standard output (stdout), standard error (stderr), and standard input (stdin) to and from files or other commands.

### Types of Redirection

1. **Standard Output (stdout):**
   - The default output stream, usually displayed on the terminal.
   - **Redirecting stdout to a file:**

     ```
     command > file.txt
     ```

     This will redirect the output of `command` to `file.txt`, overwriting the file if it exists.

   - **Appending to a file:**

     ```
     command >> file.txt
     ```

     This appends the output of `command` to `file.txt`.

2. **Standard Error (stderr):**
   - Used to display error messages.
   - **Redirecting stderr to a file:**

     ```
     command 2> error.txt
     ```

     This will redirect any error messages from `command` to `error.txt`.

   - **Appending stderr to a file:**

     ```
     command 2>> error.txt
     ```

     This appends any error messages from `command` to `error.txt`.

3. **Standard Input (stdin):**
   - Used to provide input to a command.
   - **Redirecting input from a file:**

     ```
     command < input.txt
     ```

     This feeds `input.txt` as input to `command`.


## Combined Redirection

1. **Redirecting Both stdout and stderr:**
   - You can redirect both standard output and standard error to the same file:

     ```
     command > output.txt 2>&1
     ```

     This redirects both the output and errors of `command` to `output.txt`.

   - **Alternatively, appending both stdout and stderr:**

     ```
     command >> output.txt 2>&1
     ```

2. **Redirecting stdout and stderr to Different Files:**
   - You can redirect stdout and stderr to different files:

     ```
     command > output.txt 2> error.txt
     ```

## Pipe (`|`) in Redirection

- A pipe is used to pass the output of one command as input to another:

  ```
  command1 | command2
  ```

- **Example:**

  Sending the output of `ls` to `grep`:

  ```
  ls | grep "file"
  ```


## Here Document (`<<`)

- A here document is used to provide input to a command from the script or command line itself, rather than from a file.

  ```
  cat <<EOF
  This is the input text.
  EOF
  ```


## Examples of Redirection

- **Redirecting output to a file:**

  ```
  echo "Hello, World!" > hello.txt
  ```

- **Appending output to a file:**

  ```
  echo "Appending to file." >> hello.txt
  ```

- **Redirecting error messages to a file:**

  ```
  ls non_existent_file 2> error.txt
  ```

- **Using a pipe to filter output:**

  ```
  ps aux | grep apache
  ```

- **Redirecting both output and error to different files:**

  ```
  command > output.txt 2> error.txt
  ```
