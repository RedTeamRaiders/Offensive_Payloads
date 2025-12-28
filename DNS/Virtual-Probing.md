#  Virtual Probing 

🔍 **HostHunter** — A Python-based tool for Virtual Host (VHOST) discovery and probing.

🌐 Explore the official GitHub repository:  
👉 [🔗 HostHunter GitHub Repository](https://github.com/SpiderLabs/HostHunter)

🔑 `HostHunter` is a powerful tool designed to:

• 🔎 Identify virtual hosts linked to an IP address.  
• 🌍 Discover hosted domains on shared hosting environments.  
• 🎯 Conduct reconnaissance on target infrastructure for security assessments.

---

## ⚙️ Installation

### 📥 Cloning the Repository  
Navigate to your desired directory and clone the **HostHunter** repository:

```bash
cd /opt  
git clone https://github.com/SpiderLabs/HostHunter.git  
cd HostHunter
```

### 📦 Installing Dependencies  
Install the required Python packages:

```bash
pip3 install -r requirements.txt
```

---

## 🚀 Usage

### 🖥️ Running HostHunter  
To start **HostHunter** without any parameters and see the available options:

```bash
python3 hosthunter.py
```

### 🌐 Probing a Specific IP for Virtual Hosts  
To find virtual hosts associated with an IP address (e.g., `8.8.8.8`):

```bash
python3 hosthunter.py -t 8.8.8.8
```

#### 🧩 Explanation of Flags:  
• `-t` → Specifies the target IP address.

---

## 📄 Example Output

If you run:

```bash
python3 hosthunter.py -t 8.8.8.8
```

You might get results like:

```
vhost1.example.com  
vhost2.example.com  
mail.example.com  
staging.example.com
```

These results indicate domains hosted on the specified IP address.

---

##  Conclusion

**HostHunter** is an essential tool for identifying virtual hosts associated with an IP address. It’s invaluable for reconnaissance, uncovering additional domains hosted on a target, and boosting your security research.

---

