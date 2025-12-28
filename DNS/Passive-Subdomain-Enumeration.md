# Passive Subdomain Enumeration

Passive subdomain enumeration involves gathering subdomain information without directly querying the target’s infrastructure. This reduces the chance of detection.

## 🆔 WHOIS Lookup
Used to gather information about the registrant, name servers, and contact details.

### 🔥 Command:
```bash
whois armourinfosec.com
```

### 🌐 Web Tools:
- [who.is](https://who.is)
- [GoDaddy WHOIS](https://in.godaddy.com/whois)
- [Whoxy Reverse WHOIS](https://www.whoxy.com/reverse-whois/)

## 🆔 Reverse WHOIS
Find all domains registered with the same registrant or contact details.

### 🌐 Web Tools:
- [ViewDNS Reverse WHOIS](https://viewdns.info/reversewhois/)
- [ReverseWHOIS.io](https://www.reversewhois.io/)
- [Whoxy Reverse WHOIS](https://www.whoxy.com/reverse-whois/)

## 📊 Google Analytics Relationship
Use Google Analytics IDs to find related domains.

- [BuiltWith Relationships](https://builtwith.com/relationships/tesla.com)

## 🟧 Certificate Transparency (CT) Logs
Collect subdomains from SSL/TLS certificates.

### 🌐 Web Tools:
- [crt.sh](https://crt.sh/)
- [Censys](https://censys.io/)
- [Facebook CT](https://developers.facebook.com/tools/ct/)
- [Google CT Transparency](https://google.com/transparencyreport/https/ct/)
- [CertSpotter](https://sslmate.com/certspotter/)

### Example using crt.sh:
```bash
curl -s "https://crt.sh/?q=%.tesla.com&output=json" | jq -r '.[].name_value' | sed 's/^*.//g' | sort -u
```

### Example using jq and unfurl:
```bash
cat tesla.json | jq -r '.[].name_value' | unfurl -u domains > tesla.txt
```

## Extract Subdomains from SAN (Subject Alternative Names)
Extract SAN data from certificates.

### 🔧 Example using Nmap:
```bash
nmap --script targets-asn --script-args targets-asn.asn=394161
```

### 🐍 Python Script:
```bash
python san_subdomain_enum.py google.com
```

## 🔬 VirusTotal
Search for subdomain relationships in VirusTotal.

### 🌐 Web Tools:
- [VirusTotal](https://www.virustotal.com/gui/domain/www.tesla.com/relations/)

## 🔎 Google Dorks
Find subdomains using advanced search operators.

### Examples:
```bash
site:tesla.*
site:*.tesla.*
site:tesla.com -www -shop -xapps -autodiscover
```

## 🔍 Shodan and Censys
Find exposed services and subdomains.

### 🌐 Web Tools:
- [Censys](https://censys.io/)
- [Shodan](https://www.shodan.io/search?query=org%3A%22Tesla%22)
- [DNSDumpster](https://dnsdumpster.com/)

## 🌊 Rapid7 Sonar Datasets
Use Sonar datasets to find subdomains.

### 💻 Example:
```bash
wget https://opendata.rapid7.com/sonar.fdns_v2/2021-05-28-1622160364-fdns_a.json.gz
pv 2021-05-28-1622160364-fdns_a.json.gz | pigz -dc | grep -E "\.tesla\.com\"," | jq -r ".name"
```

## ⚡ Chaos Project Discovery
Discover subdomains using ProjectDiscovery Chaos datasets.

### Example Script:
```bash
#!/bin/bash  
Outputdir=/tmp/d1  
mkdir -p $Outputdir/zipFils  
mkdir -p $Outputdir/txtFils  
wget "https://chaos-data.projectdiscovery.io/index.json" -O $Outputdir/index.json  
grep 'URL' $Outputdir/index.json | sed -r 's/.*"URL": "//;s/".*//' > $Outputdir/alltargets-zip.txt  
wget -P $Outputdir/zipFils -i $Outputdir/alltargets-zip.txt  
unzip -d $Outputdir/txtFils $Outputdir/zipFils/*.zip  
cat $Outputdir/txtFils/*txt > $Outputdir/alltargets.txt  
rm -rf $Outputdir/zipFils $Outputdir/txtFils  
```

## 🛠 GitHub Subdomain Enumeration
Use GitHub to extract subdomains.

### 📜 Example using github-subdomains:
```bash
github-subdomains -d tesla.com -t <TOKEN>
```

## 🔧 Subdomain Enumeration Tools
1. **Sublist3r**  
2. **Amass**  
3. **Assetfinder**  
4. **Findomain**  
5. **AltDNS**  
6. **Gobuster**  

## ✅ Complete Automation Script
Example of a full automation script:

```bash
#!/bin/bash  
DOMAIN=$1  
amass enum -passive -d $DOMAIN > $DOMAIN-subdomains.txt  
subfinder -d $DOMAIN >> $DOMAIN-subdomains.txt  
assetfinder --subs-only $DOMAIN >> $DOMAIN-subdomains.txt  
sort -u $DOMAIN-subdomains.txt > $DOMAIN-final.txt  
cat $DOMAIN-final.txt  
```

---

