# 🔍 Findomain

**Findomain** is a simple and fast tool to find subdomains of websites. Great for ethical hacking and bug bounty!  
🔗 [GitHub Repository](https://github.com/Findomain/Findomain)

---

## ⚙️ Installation

### 📦 Using APT
```bash
apt install findomain
```

---

## 📥 Download Findomain
[Go to Releases](https://github.com/findomain/findomain/releases) or run:
```bash
curl -LO https://github.com/Findomain/Findomain/releases/download/8.2.1/findomain-linux.zip
```

---

## 📂 Unzip the File
```bash
unzip findomain-linux.zip
```

---

## ✅ Make it Executable
```bash
chmod +x findomain
```

---

## 📁 Move to System Path
```bash
cp -vr findomain /usr/local/bin/
```

---

## 🧹 Reduce Size (Optional)
```bash
strip -s /usr/local/bin/findomain
```

---

## 🧪 Check if Installed
```bash
findomain --help
```

---

## 🚀 Basic Usage
Find subdomains of `tesla.com` and save them:
```bash
findomain -t tesla.com -u output.txt
```

---

## 💡 Other Examples

- Show result on screen:
```bash
findomain -t tesla.com
```

- Use domain list from file:
```bash
findomain -f domains.txt -u results.txt
```

- Use with API key:
```bash
findomain -t tesla.com --api-key YOUR_API_KEY
```

---

## 📚 Official Documentation
For detailed usage and advanced options, check the 👉 [Findomain Official Docs](https://github.com/Findomain/Findomain/blob/master/docs/INSTALLATION.md)

---

## 🏁 Conclusion
⚡ Fast and easy subdomain finder for recon.  
🎯 Perfect tool for bug bounty hunters!

