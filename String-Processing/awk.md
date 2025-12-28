# **`awk`**  
The `awk` command is a powerful text-processing tool that is used for pattern scanning, data extraction, and text transformation. It works with structured data like CSV, log files, and system outputs.  


## **Syntax**  
```bash
awk 'pattern {action}' filename
```

## **Examples**  

- **Print all lines of a file:**  
  ```bash
  awk '{print $0}' filename
  ```

- **Print the first field (column) using `:` as a delimiter:**  
  ```bash
  awk -F: '{print $1}' filename
  ```

- **Print the first, second, and third fields from a file:**  
  ```bash
  awk -F: '{print $1, $2, $3}' filename
  ```

- **Extract the second field from `ifconfig` output:**  
  ```bash
  ifconfig | awk '{print $2}'
  ```

- **Find and print only `inet` addresses from network configurations:**  
  ```bash
  ifconfig | awk '/inet /{print $2}'
  ```

- **Use `BEGIN` and `END` blocks for formatting output:**  
  ```bash
  ifconfig | awk 'BEGIN{print "== IP Address =="} /inet /{print $2} END{print "====="}'
  ```

- **Process input text and print messages before and after execution:**  
  ```bash
  echo "one two three four" | awk 'BEGIN {print "=== Start ==="} {print $0} END {print "-- Stop --"}'
  ```

- **Print specific fields with separators:**  
  ```bash
  echo "one two three four" | awk 'BEGIN {print "=== start ==="} {print $1, " - ", $2} END {print "-- stop --"}'
  ```

- **Print fields with custom delimiters:**  
  ```bash
  echo "one two three four" | awk 'BEGIN {print "=== start ==="} {print $1, " / ", $2} END {print "-- stop --"}'
  ```

- **Modify text dynamically (change the first field to uppercase):**  
  ```bash
  echo "armour infosec" | awk '{$1=toupper($1); print}'
  ```

- **Filter and print lines from `/etc/passwd` where username is `root`:**  
  ```bash
  awk -F: '$1=="root" {print $0}' /etc/passwd
  ```

- **Exclude lines where the username is `root`:**  
  ```bash
  awk -F: '$1!="root" {print $0}' /etc/passwd
  ```

- **Print lines where the third field (UID) is zero:**  
  ```bash
  awk -F: '$3==0 {print $0}' /etc/passwd
  ```

- **Print lines where the third field (UID) is greater than or equal to 1000:**  
  ```bash
  awk -F: '$3>=1000 {print $0}' /etc/passwd
  ```

- **Find Ethernet addresses from `ifconfig` output:**  
  ```bash
  ifconfig | awk '$1=="ether" {print $2}'
  ```

- **Print the number of fields in each line:**  
  ```bash
  echo "one two three four" | awk '{print NF}'
  ```

- **Print the last field of a line:**  
  ```bash
  echo "one two three four" | awk '{print $NF}'
  ```

- **Print the second-to-last field of a line:**  
  ```bash
  echo "one two three four" | awk '{print $(NF-1)}'
  ```

- **Print both the last and second-to-last fields:**  
  ```bash
  echo "one two three four" | awk '{print $NF, $(NF-1)}'
  ```

- **Process `/etc/passwd` and extract specific fields:**  
  ```bash
  awk '{print NF}' /etc/passwd
  ```
  ```
  awk '{print $NF}' /etc/passwd
  ```
  ```
  awk '{print $NF, $(NF-1)}' /etc/passwd
  ```
