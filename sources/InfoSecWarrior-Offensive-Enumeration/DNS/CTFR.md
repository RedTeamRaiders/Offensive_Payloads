# 📜 CTFR

🎯 **CTFR** — A Python-Based Certificate Transparency Log Subdomain Extractor

🌐 GitHub Repository:  
👉 [🔗 github.com/UnaPibaGeek/ctfr](https://github.com/UnaPibaGeek/ctfr)

`CTFR` is a Python tool used to extract subdomains from **Certificate Transparency logs**. This helps discover both **active** and **historical** subdomains associated with a target domain.

---

## ⚙️ Installation

### 📥 Cloning the Repository
Navigate to a preferred directory and clone the CTFR repo:

```bash
cd /opt
git clone https://github.com/UnaPibaGeek/ctfr.git
cd ctfr
```

### 📦 Installing Dependencies
Install the required Python packages:

```bash
pip install -r requirements.txt
```

---

## 🚀 Usage

### 📘 Displaying Help Information
To view available options and flags:

```bash
python3 ctfr.py --help
```

### 🌐 Extracting Subdomains for a Target Domain
To extract subdomains for `tesla.com`:

```bash
python3 ctfr.py -d tesla.com
```

### 💾 Saving the Output to a File
To save the results in a file:

```bash
python3 ctfr.py -d tesla.com -o tesla.com-ctfr.txt
```

This will store the results in `tesla.com-ctfr.txt` for future analysis.

---

## 🛠️ Setting Up a Global Shortcut for CTFR

### 📁 Copy the Script to `/usr/local/bin`
```bash
cp -v /opt/ctfr/ctfr.py /usr/local/bin/ctfr
```

### 🔓 Make the Script Executable
```bash
chmod +x /usr/local/bin/ctfr
```

Now you can run CTFR from anywhere:
```bash
ctfr -h
```

---

## 📄 Example Output

If you run:
```bash
python3 ctfr.py -d tesla.com
```
You might get results like:
```
www.tesla.com
api.tesla.com
internal.tesla.com
staging.tesla.com
mail.tesla.com
```

---

## 🏁 Conclusion

`CTFR` is a **powerful tool** for discovering subdomains through Certificate Transparency logs. 🕵️‍♂️

It's especially useful for reconnaissance, as it can find domains that **may not be visible through other means**. 💡


