# DNS-Zone-Transfer-(AXFR)

---

A **DNS Zone Transfer** is a mechanism designed to replicate DNS databases (zone files) between DNS servers, typically from a **primary (master)** server to one or more **secondary (slave)** servers.

In recon and penetration testing, DNS Zone Transfer is attempted to **retrieve all DNS records** for a domain. If misconfigured, it allows attackers to enumerate all subdomains, mail servers, IPs, and more in a single query

In offensive security, if a DNS server is **misconfigured,** it may allow unauthenticated zone transfers, which can expose:

---

### What Can Be Discovered?

If successful, a zone transfer can reveal:

- All subdomains (A, AAAA records)
- Mail servers (MX records)
- Name servers (NS records)
- TXT records (e.g., SPF DKIM)
- Internal domains (dev, staging, etc)
- Private infrastructure details
- IP addresses of infrastructures

---

### Types of Lookups

### Forward Lookup

```bash
dig example.com
```

Resolves domain names to IP addresses.

### Reverse Lookup

```bash
dig -x 192.0.2.1
```

Resolves IP addresses back to hostnames.

---

### AXFR vs IXFR

| **Type** | **Description** |
| --- | --- |
| AXFR | Full zone transfer |
| IXFR | Incremental zone transfer (only changed records) |

---

## Step 1: Find Name Servers (Authoritative DNS)

```bash
nslookup -type=ns armour.local 192.168.1.41
```

```bash
dig armour.local ns @192.168.1.41
```

```bash
dig zonetransfer.me ns
```

**Check SOA record (Start of Authority):**

```bash
dig zonetransfer.me SOA
```

**Discover DNS services in local network:**

```bash
nmap -v -sT -sU -p T:53,U:53 192.168.1.1/24
```

**Check resolver DNS:**

```bash
cat /etc/resolv.conf
```

---

## Step 2: Find DNS for Host/IP

```bash
nslookup server.armour.local 192.168.1.41
```

```bash
dig server.armour.local @192.168.1.41
```

Public name servers:

```bash
dig nsztm1.digi.ninja
```

```bash
dig nsztm2.digi.ninja
```

---

## Step 3: Attempt DNS Zone Transfer

**Using `host`** 

```bash
host -t axfr zonetransfer.me 81.4.108.41
```

```bash
host -t axfr ai.local 192.168.1.71
```

- Forward Zone
    
    ```bash
    host -t axfr armour.local 192.168.1.41
    ```
    
- Reverse Zone
    
    ```bash
    host -t axfr 1.168.192.in-addr.arpa 192.168.1.41
    ```
    

---

### Using nslookup

```bash
nslookup -type=axfr ai.local 192.168.1.71
```

```bash
nslookup -type=axfr zonetransfer.me 81.4.108.41
```

---

### Using `dig`

```bash
dig zonetransfer.me -t axfr @81.4.108.41
```

```bash
dig zonetransfer.me axfr @81.4.108.41
```

```bash
dig -t axtr zonetransfer.me @81.4.108.41
```

```bash
dig armour.local axfr @192.168.1.41
```

```bash
dig -t axfr armour.local @192.168.1.41
```

```bash
dig -t axfr zonetransfer.me @nsztm1.digi.ninja
```

```bash
dig zonetransfer.me axfr @nsztm1.digi.ninja
```

---

### How Zone Transfer Works

Zone transfers use the **AXFR protocol** (Authoritative Transfer) on port **53/tcp** between DNS servers.

If the target DNS server doesn’t properly restrict AXFR requests, an attacker can do something like:

```bash
host -l example.com ns1.example.com
```

And receive the full zone data.

---

### How to Discover Name Servers for Zone Transfer

Before attempting a zone transfer, identify the domain's name servers:

```bash
dig NS example.com
```

Example output:

```bash
ns1.example.com.
ns2.example.com.
```

Checking which nameserver is primary (master) and which is secondary (slave) as because only master can transfer the zone

```bash
dig soa example.com
```

Then try:

```bash
dig AXFR exemple.com @ns1.example.com
```

### Example Output (if vulnerable)

```bash
; <<>> DiG 9.16.1-Ubuntu <<>> @ns1.zonetransfer.me example.com AXFR
; (1 server found)
;; global options: +cmd
example.com.        3600    IN      A       192.0.2.1
example.com.        3600    IN      MX      10 mail.example.com.
example.com.        3600    IN      NS      ns1.example.com.
example.com.        3600    IN      NS      ns2.example.com.
mail.example.com.   3600    IN      A       192.0.2.2
www.example.com.    3600    IN      CNAME   example.com.

```

---

### Using `nmap`

```bash
nmap -v -sT -sU -p 53 --script=dns-zone-transfer.nse \
--script-args dns-zone-transfer.domain=zonetransfer.me nsztm1.digi.ninja
```

---

### DNS Zone Transfer Script

Automate zone transfer checks with a short script:

```bash
for ns in $(dig ns example.com +short); do
		dig axfr example.com @$ns
done
```

---

### Defensive Notes

- Most modern DNS servers restrict AXFR to trusted IPs only.
- Still useful to test during:
    - Internal assessments
    - Red team engagements
    - Misconfigured staging/test environments
- Reverse zone transfers ( [in-addr.arpa](https://in-addr.arpa/) ) can leak internal PTR records.

---

**Summary**

- AXFR is a powerful recon technique if exploitable.
- Automate checks early in the recon phase.
- Most live domains block AXFR, but **internal DNS often doesn't**.

---
