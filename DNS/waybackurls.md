## 🔙 waybackurls - Extract Historical URLs for Reconnaissance

### 🔗 Official Repository
**GitHub:** [tomnomnom/waybackurls](https://github.com/tomnomnom/waybackurls)

`waybackurls` is a tool developed by **tomnomnom** that extracts URLs from the **Wayback Machine (Internet Archive)** for a given domain. This is useful for reconnaissance, subdomain enumeration, and discovering old endpoints.

---

### ⚙️ Installation
To install `waybackurls`, ensure your Go environment is set up properly, then run:

```bash
go install github.com/tomnomnom/waybackurls@latest
```

✅ Make sure `$GOPATH/bin` is added to your system's `$PATH` if it's not already.

---

### 🚀 Usage

#### 📥 Fetching URLs from Wayback Machine
To retrieve historical URLs for a domain (e.g., `tesla.com`):

```bash
waybackurls tesla.com
```

To save the output:

```bash
waybackurls tesla.com > tesla.com-waybackurls.txt
```
This will return a list of archived URLs for tesla.com.

---

### 🧹 Extracting Only Subdomains
Since `waybackurls` outputs full URLs, use `unfurl` to extract only domain names:

```bash
waybackurls tesla.com | unfurl -u domains
```

#### 💾 Saving the Output to a File
```bash
waybackurls tesla.com | unfurl -u domains > waybackurls-output.txt
```

---

### 📄 Example Output
If you run the command:

```bash
waybackurls tesla.com | unfurl -u domains
```

You might get results like:
- www.tesla.com  
- shop.tesla.com  
- blog.tesla.com  
- assets.tesla.com

---

### 🌟 Advantages
- 🔍 Helps uncover historical endpoints that may be forgotten or unindexed.
- 📜 Provides a larger attack surface for security assessments.
- 🧩 Useful in bug bounty programs for finding hidden or deprecated functionality.
- 🛠️ Easy to combine with other tools (e.g., `unfurl`, `dnsgen`, `httpx`) in automation pipelines.
- ⏱️ Fast and simple to use with minimal setup.

---

### ✅ Conclusion
`waybackurls` is a powerful tool for gathering historical web data. When combined with `unfurl`, it helps extract useful information like subdomains, which can be further analyzed for security assessments. 🔐🔍

