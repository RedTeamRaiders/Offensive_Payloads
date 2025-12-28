---

# Amass - Subdomain Enumeration & DNS Intelligence

[Amass](https://github.com/owasp-amass/amass) is one of the most trusted tools for discovering subdomains, mapping attack surfaces, and performing DNS resolution. It's a must-have for bug bounty hunters, pentesters, and recon automation.

---

## Installation and Setup

Install with Go:

```bash
go install -v github.com/owasp-amass/amass/v4/...@latest
```

Then move it to your path so you can run it from anywhere:

```bash
cp -v go/bin/amass /usr/local/bin/
chmod +x /usr/local/bin/amass
```

Verify it works:

```bash
amass -version
```

---

## ⚙️ Basic Configuration (Optional)

You can connect Amass to APIs (like VirusTotal, Shodan, etc.) for better results. Just add your API keys to the config file:

```bash
mkdir -p ~/.config/amass
vim ~/.config/amass/config.ini
```

Example:

```ini
[virustotal]
apikey = YOUR_VIRUSTOTAL_API_KEY

[shodan]
apikey = YOUR_SHODAN_API_KEY
```

---

## Different Modes in Amass

Amass isn't just one tool — it has multiple modes depending on your goal. Here's a breakdown of how each one works and when to use it:

---

### 1. Passive Mode

**Goal:** Quiet recon, no traffic sent to the target.

```bash
amass enum -passive -d tesla.com -o tesla-passive.txt
```

- Pulls data from public sources and APIs.
- Perfect for stealthy recon or when you want a quick overview.
- Doesn’t actively probe anything.

---

### 2. Active Mode

**Goal:** Thorough recon by querying and resolving domains.

```bash
amass enum -active -d tesla.com -o tesla-active.txt
```

- Sends DNS queries and probes targets directly.
- Can reveal more subdomains, but it's noisier.
- Useful when passive mode misses stuff.

---

### 3. Brute Force Mode

**Goal:** Discover hidden subdomains using wordlists.

```bash
amass enum -brute -d tesla.com -o tesla-brute.txt
```

- Tries common prefixes like `dev.`, `mail.`, `api.`, etc.
- Can be paired with active mode for deeper coverage.
- Can take time depending on wordlist size.

You can combine brute force with active mode:

```bash
amass enum -brute -active -d tesla.com -o tesla-full.txt
```

---

### 🔎 4. Resolve Mode

**Goal:** Check which domains actually resolve (i.e., point to an IP).

```bash
amass resolve -df all-subdomains.txt -o resolved.txt
```

- Filters out dead or parked domains.
- Only saves the ones that return valid DNS records.
- Great before doing HTTP probing or port scanning.

---

## Using Your Own DNS Resolvers

Want more speed or reliability? Use your own list of resolvers instead of the default ones.

### Create a file called `resolvers.txt`:

```
1.1.1.1         # Cloudflare
8.8.8.8         # Google
9.9.9.9         # Quad9
208.67.222.222  # OpenDNS
```

Then run:

```bash
amass resolve -df all-subdomains.txt -rf resolvers.txt -o resolved.txt
```

- `-rf` tells Amass to use your custom DNS servers.
- Speeds things up and avoids limits from public resolvers.



---

## Merging Amass with Other Tools

Combine Amass output with results from Chaos, Subfinder, etc.:

```bash
cat tesla-amass.txt tesla-chaos.txt | sort -u > all-subdomains.txt
```

Then resolve them:

```bash
amass resolve -df all-subdomains.txt -rf resolvers.txt -o final-resolved.txt
```

---

## Pro Tips

- Use passive mode first to avoid being loud.
- If you need deep coverage, add active + brute.
- Always resolve your domains before scanning — it saves time and reduces false positives.
- Save everything to files for easy use in automation pipelines.

---


