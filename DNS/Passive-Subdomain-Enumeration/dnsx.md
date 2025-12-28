# 📦 DNSx Installation & Usage Guide

**DNSx** is a fast and multi-purpose DNS toolkit developed by [ProjectDiscovery](https://github.com/projectdiscovery).  
It is used to perform DNS queries at scale, extract DNS records (A, AAAA, CNAME, PTR, etc.), and is an essential tool in automated reconnaissance workflows during VAPT and bug bounty hunting.

---

## 🔧 Installation

Install `dnsx` using Go:

```bash
go install -v github.com/projectdiscovery/dnsx/cmd/dnsx@latest
```

Move the binary to a system-wide path:

```bash
cp -v dnsx /usr/local/bin/
chmod +x dnsx
```

---

## 🚀 Usage

### 🧪 Recon Workflow Integration

1. **Enumerate subdomains** using tools like `subfinder`, `amass`, etc.
2. **Merge and deduplicate** the outputs:
   ```bash
   cat *.txt | sort -u > all-domains.txt
   ```
3. **Filter in-scope/out-of-scope** domains as required.
4. **Run `dnsx`** to gather DNS records.

---

### 🔁 Reverse DNS Lookups (PTR Records)

Get the domain name associated with an IP address or a subnet:

```bash
echo "8.8.8.8" | dnsx -silent -resp-only -ptr
echo "192.168.43.1/24" | dnsx -silent -resp-only -ptr
```

---

### 🧠 Bulk DNS Querying (Higher Resource Usage)

```bash
cat tesla-domains.txt | dnsx -resp
```

Useful when dealing with large domain lists. May consume more CPU and memory.

---

### 🔍 Get A Records (IPv4 addresses)

```bash
dnsx -l tesla-domains.txt -silent -a -resp
```

---

### 🎯 Get Specific DNS Records

Query multiple DNS record types in a single command:

```bash
dnsx -l tesla-domains.txt -silent -a -aaaa -cname -ptr -resp
```

- `-a`     → A records  
- `-aaaa`  → AAAA (IPv6) records  
- `-cname` → Canonical Name records  
- `-ptr`   → Reverse DNS

---

### 🔎 Filter DNS Responses by RCODE

Useful for detecting errors, misconfigurations, or blocked queries:

```bash
dnsx -l tesla-domains.txt -silent -cname -rcode noerror,servfail,refused
```

- `noerror`: Successful DNS response  
- `servfail`: Server failure  
- `refused`: Query refused (e.g., due to DNS filtering)

---

### 💾 Save DNS Records to Text File

```bash
dnsx -l tesla-domains.txt -silent -a -aaaa -cname -ptr -resp -o tesla-domains-records.txt
```

---

### 📂 Save Output in JSON Format

```bash
dnsx -l tesla-domains.txt -silent -a -aaaa -cname -ptr -resp -json -o tesla-domains-records.json
```

---

## 💡 Tips

- Combine `dnsx` with tools like `httpx`, `nuclei`, and `naabu` for full recon automation.
- Use `-t` flag to control concurrency and performance.
- Always test large scans responsibly to avoid generating excessive traffic.

---

**DNSX:** This tool is multiutility tool and it is the advanced version of the dns client tools like dig and nslookup which just resolve single query at a time but with this you can resolve as many
