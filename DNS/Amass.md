# 🚀 Amass 

**🔗 GitHub Repository:** [OWASP Amass](https://github.com/OWASP/Amass)

**Amass** is a powerful tool designed for **network mapping** and **subdomain enumeration**. It helps security professionals gather information about a target, identify subdomains, track infrastructure changes over time, and map out an organization’s potential attack surface.

---

## 🧱 Subcommands Overview

- **`intel`** – Discover targets and gather intel information.  
- **`enum`** – Perform subdomain enumeration and network mapping.  
- **`viz`** – Visualize enumeration results.  
- **`track`** – Track changes across different enumerations.  
- **`db`** – Manage the Amass graph database.

---

## ⚙️ Installation

Install Amass on Debian-based systems:

```bash
apt install amass
```

---

## 📦 Basic Commands

Check if Amass is working:

```bash
amass
```

Display help and usage information:

```bash
amass --help
```

---

## 🛠️ Configuration Files

Amass supports configuration for better control and customization:

- 📁 [Example config.yaml](https://github.com/OWASP/Amass/blob/master/examples/config.yaml)  
- 📁 [Example datasources.yaml](https://github.com/OWASP/Amass/blob/master/examples/datasources.yaml)

---

## 🧠 Intel Subcommand

Use the `intel` subcommand to gather reconnaissance data on your target.

### 📋 Usage Help

```bash
amass intel -help
```

### 💡 Example Commands

List all available intel sources:

```bash
amass intel -list
```

With a specific config:

```bash
amass intel -list -config /opt/amass-config.ini
amass intel -list -config config.yaml
```

Collect intel on a domain:

```bash
amass intel -d tesla.com -whois
```

Gather intel on an organization:

```bash
amass intel -org tesla
```

Find data based on ASN:

```bash
amass intel -asn 394161
```

ASN lookup via Nmap:

```bash
nmap --script targets-asn --script-args targets-asn.asn=394161
```

Gather intel via CIDR blocks:

```bash
amass intel -ip -src -cidr 8.21.14.0/24
amass intel -ip -src -cidr 213.244.145.0/24
amass intel -ip -src -cidr 212.118.128.0/22,212.118.144.0/23,212.118.156.0/24,212.118.158.0/24,...
```

---

## 🔍 Enum Subcommand

The `enum` subcommand is for identifying subdomains and network mapping.

### 📋 Usage Help

```bash
amass enum --help
```

### 💡 Example Commands

List available enumeration sources:

```bash
amass enum -list
amass enum -list -config /opt/amass-config.ini
```

Perform **passive** subdomain enumeration:

```bash
amass enum -passive -d tesla.com
amass enum -passive -d tesla.com -v
amass enum -passive -d tesla.com -src -config /opt/amass-config.ini
```

Perform **active** enumeration with brute force:

```bash
amass enum -active -brute -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -d tesla.com -o tesla.com
```

Advanced active enumeration:

```bash
amass enum -active -d tesla.com -brute -w /usr/share/seclists/Discovery/DNS/dns-Jhaddix.txt -src -ip -dir amass4tesla -o amass_results.txt
```

With custom resolvers:

```bash
amass enum -active -d tesla.com -brute -w /usr/share/seclists/Discovery/DNS/dns-Jhaddix.txt -rf /opt/amass/lists/resolvers.txt -src -ip -dir amass4tesla/ -o amass_results.txt
```

---

## ✅ Conclusion
Amass is a handy tool for finding subdomains and mapping networks. Great for reconnaissance and security assessments.


---
