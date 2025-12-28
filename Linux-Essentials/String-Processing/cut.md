# **`cut`**  
The `cut` command extracts specific sections of each line in a file. It is commonly used for extracting columns from structured text data such as CSV files, logs, or system output.  


## **Syntax**  
```bash
cut [OPTIONS] [file]
```

## **Examples**  

- Extract the **first 10 characters** from each line:  
  ```bash
  cut -c 1-10 filename.txt
  ```

- Extract **only the 5th character** from each line:  
  ```bash
  cut -c 5 filename.txt
  ```

- Extract **characters from multiple positions** (e.g., 1st, 3rd, and 5th):  
  ```bash
  cut -c 1,3,5 filename.txt
  ```

- Extract the **first column** from a CSV file (comma as a delimiter):  
  ```bash
  cut -d ',' -f 1 data.csv
  ```

- Extract **multiple columns** (e.g., 1st and 3rd) from a CSV file:  
  ```bash
  cut -d ',' -f 1,3 data.csv
  ```

- Extract the **first and second fields** from `/etc/passwd` (colon-separated file):  
  ```bash
  cut -d ':' -f 1,2 /etc/passwd
  ```

- Extract the **username field** from `/etc/passwd` (first field before `:`):  
  ```bash
  cut -d ':' -f 1 /etc/passwd
  ```

- Extract the **third field** from a space-separated file:  
  ```bash
  cut -d ' ' -f 3 filename.txt
  ```

- Cut from a command output (Extract usernames from `who` command output):  
  ```bash
  who | cut -d ' ' -f 1
  ```

- Extract fields using **tab as a delimiter**:  
  ```bash
  cut -d $'\t' -f 2 data.tsv
  ```

- Cut data from a pipeline (Extract only process names from `ps` output):  
  ```bash
  ps aux | cut -d ' ' -f 11
  ```