## 🛠️ OneForAll - Subdomain Enumeration Tool

🔗 **Repository:** [OneForAll GitHub](https://github.com/shmilylty/OneForAll)  
**Description:** OneForAll is a powerful and fast subdomain enumeration tool designed for security professionals.

---

### 📥 Cloning the Repository
To install OneForAll, first, clone the repository from GitHub:
```bash
git clone https://github.com/shmilylty/OneForAll.git
```

---

### 📁 Navigating to the OneForAll Directory
Change into the cloned directory:
```bash
cd OneForAll
```

---

### 📦 Installing Dependencies
Install all required Python dependencies using pip:
```bash
pip install -r requirements.txt
```

---

### ✅ Verifying Installation
Check if OneForAll is installed correctly by displaying the help menu:
```bash
python oneforall.py --help
```

---

### 🚀 Running OneForAll for Subdomain Enumeration
To enumerate subdomains for a target domain (e.g., tesla.com), run:
```bash
python3 oneforall.py --target tesla.com run
```
This command will scan for subdomains and save the results in the default `results` directory.

---

### 📄 Extracting Subdomains from Results
After the scan, you can extract subdomains from the results using:
```bash
cat /opt/OneForAll/results/tesla.com.csv | cut -d "," -f6 | grep -Ev "^subdomain*"
```
- `cut -d "," -f6`: Extracts the 6th column from the CSV file.
- `grep -Ev "^subdomain*"`: Filters out the header row.

---

### 📁 Customizing the Output Path
To save the results in a custom directory (e.g., `/tmp`), use:
```bash
python3 oneforall.py --target tesla.com run --path /tmp
```

---

### 🔧 Additional Usage Examples

1. 📝 Enumerate multiple domains from a file (`domains.txt`):
```bash
python3 oneforall.py --target-file domains.txt run
```

2. 📣 Use verbose mode for more detailed output:
```bash
python3 oneforall.py --target tesla.com run --verbose
```

3. 📦 Save output in JSON format:
```bash
python3 oneforall.py --target tesla.com run --format json
```

📚 For more options and configurations, refer to the official documentation:  
👉 https://github.com/shmilylty/OneForAll

---

✅ Conclusion

OneForAll is a handy tool for fast and efficient subdomain enumeration  It’s perfect for bug bounty and security tasks.
