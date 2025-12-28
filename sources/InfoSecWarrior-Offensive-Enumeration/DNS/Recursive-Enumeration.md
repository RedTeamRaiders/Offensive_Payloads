# 🔄 **Recursive Enumeration for Subdomains** 🕵️‍♂️

Recursive subdomain enumeration helps identify common base domains from a list of subdomains. This technique aids in recognizing domain patterns and expanding enumeration efforts. 🌐

---

## 🛠️ **Commands for Recursive Enumeration**

### **Extracting and Sorting Root Domains:**

This command extracts the root domain (e.g., example.com, sub.example.com) from a list of subdomains, sorts them, and identifies frequently occurring ones.

```bash
cat tesla.com-subdomain.txt | rev | cut -d '.' -f 3,2,1 | rev | sort | uniq -c | sort -nr | grep -v ' 1 ' | head -n 10 | sed -e 's/^[[:space:]]*//' | cut -d ' ' -f 2

```

---

### **Explanation of the Command:**

- `cat tesla.com-subdomain.txt` 📄 → Reads the file containing the list of subdomains.
- `rev` 🔄 → Reverses each line to process domain components more effectively.
- `cut -d '.' -f 3,2,1` ✂️ → Extracts the last three components (e.g., example.com from api.sub.example.com).
- `rev` 🔄 → Reverses it back to its original form.
- `sort` 🔠 → Sorts the domains alphabetically.
- `uniq -c` 🔢 → Counts occurrences of each domain.
- `sort -nr` 🔽 → Sorts the domains in descending order of frequency.
- `grep -v ' 1 '` 🚫 → Removes entries that occur only once (to filter out noise).
- `head -n 10` 📊 → Displays the top 10 most frequent domains.
- `sed -e 's/^[[:space:]]*//'` ✨ → Trims leading spaces.
- `cut -d ' ' -f 2` ✂️ → Extracts only the domain names.

---

### **Extracting Domains with an Additional Subdomain Level**

For more granular enumeration (including fourth-level subdomains, e.g., dev.api.example.com):

```bash
cat tesla.com-subdomain.txt | rev | cut -d '.' -f 4,3,2,1 | rev | sort | uniq -c | sort -nr | grep -v ' 1 ' | head -n 10 | sed -e 's/^[[:space:]]*//' | cut -d ' ' -f 2

```

---

### **Differences in This Command:**

- `cut -d '.' -f 4,3,2,1` 🔄 → Extracts the last four components, ensuring deeper subdomain enumeration.
- This helps identify frequently occurring third and fourth-level subdomains.

---

## 📝 **Example Output**

### **If you run the first command:**
```bash
cat tesla.com-subdomain.txt | rev | cut -d '.' -f 3,2,1 | rev | sort | uniq -c | sort -nr | grep -v ' 1 ' | head -n 10 | sed -e 's/^[[:space:]]*//' | cut -d ' ' -f 2

```

You might get results like:
- `tesla.com`
- `energy.tesla.com`
- `solar.tesla.com`
- `api.tesla.com`

---

### **If you run the second command:**
```bash
cat tesla.com-subdomain.txt | rev | cut -d '.' -f 4,3,2,1 | rev | sort | uniq -c | sort -nr | grep -v ' 1 ' | head -n 10 | sed -e 's/^[[:space:]]*//' | cut -d ' ' -f 2
```

The output may include:
- `dev.api.tesla.com`
- `staging.solar.tesla.com`
- `test.energy.tesla.com`
- `iotenv01.api.tesla.com`

---

## ✅ **Conclusion**

This recursive enumeration method helps:

- 🚀 Identify frequently used root domains.
- 🔍 Discover patterns in multi-level subdomains.
- 🛠️ Provide a solid starting point for further reconnaissance.

