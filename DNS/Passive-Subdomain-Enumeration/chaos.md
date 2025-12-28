# ☁️ ProjectDiscovery Chaos - Asset Discovery Guide

[Chaos](https://chaos.projectdiscovery.io/#/) is a publicly available reconnaissance platform for bug bounty and red teaming. It provides DNS records of known assets for popular organizations, frequently used in recon automation.

---

## Authentication AND SETUP

You’ll need to be logged in to access the Chaos API.

- **Account:** `Account USer`
- **API Key:** `YOUR_API_KEY`  
  *(Note: Don't share your API key in public repos)*

---

##  Installation

Install the Chaos CLI client using `go`:

```bash
go install -v github.com/projectdiscovery/chaos-client/cmd/chaos@latest
```

Move the binary to a system-wide path:

```bash
cd
cp -v go/bin/chaos /usr/local/bin/
chmod +x /usr/local/bin/chaos
```

Set your API key environment variable (persist it across shell sessions):

Edit your `.bashrc` or `.zshrc`:

```bash
vim ~/.bashrc
# OR
vim ~/.zshrc
```

Add the following line at the end of the file:

```bash
export PDCP_API_KEY=09e4ef57-0409-46b7-bb4b-41ba4901c568
```

Apply changes:

```bash
source ~/.bashrc
# OR
source ~/.zshrc
```

Or simply restart your terminal.

---

##  Commands

### Basic Subdomain Enumeration

```bash
chaos -d tesla.com -silent
```

### 💾 Save Output to a File

```bash
chaos -d tesla.com -silent -o /home/raj/Downloads/tesla-chaos.txt
```

### merge Chaos Data with Other Recon Files

Use `unfurl` (from `tomnomnom`) to extract and merge domains:

```bash
cat tesla-domains.txt tesla-chaos.txt | unfurl -u domains > tesla-domains-list.txt
```

- This merges all previously collected subdomains and deduplicates them.
- The final file `tesla-domains-list.txt` contains a clean list of unique domains.

---

## Tips

- Combine with tools like `dnsx`, `httpx`, and `nuclei` for deep recon.
- Automate API-based fetches for continuous recon pipelines.
- Rotate API keys if making the repo public.

---


