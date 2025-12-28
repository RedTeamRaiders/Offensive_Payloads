# 🔍 github-subdomains

**GitHub Subdomains** 🔗 

[🔗 github.com/gwen001/github-subdomains](https://github.com/gwen001/github-subdomains)

`github-subdomains` is a tool developed by **gwen001** that searches GitHub repositories for subdomains related to a given target domain. This is useful for:

• 🔎 Discovering exposed subdomains in public GitHub repositories  
• 🧪 Finding assets that developers might have accidentally leaked  
• 📊 Gathering more intelligence for security assessments

---

## ⚙️ Installation

To install `github-subdomains`, use:

```bash
go install github.com/gwen001/github-subdomains@latest
```

👉 Make sure **Go** is installed and properly configured before running this command.

---

## 🚀 Usage

### 📘 Displaying Help Information

To view available options and flags:

```bash
github-subdomains -h
```

### 🌐 Finding Subdomains for a Target Domain

To search for subdomains associated with `example.com`, using a list of GitHub tokens:

```bash
github-subdomains -d example.com -t tokens.txt -o output.txt
```

### 🧾 Explanation of Flags:
• `-d example.com` → Specifies the target domain  
• `-t tokens.txt` → Uses API tokens for authenticated GitHub searches (improves results and avoids rate limiting)  
• `-o output.txt` → Saves the extracted subdomains to a file

### ⚡ Finding Subdomains for Tesla

For a real-world example using Tesla:

```bash
github-subdomains -d tesla.com -t github-tokens.txt -o tesla.com-github-subdomains-output.txt
```

This will extract any subdomains related to `tesla.com` found in public GitHub repositories.

---

## 📄 Example Output

If you run:

```bash
github-subdomains -d tesla.com -t github-tokens.txt -o tesla.com-github-subdomains-output.txt
```

The output might contain subdomains like:

```
api.tesla.com
dev.tesla.com
staging.tesla.com
internal.tesla.com
```

These subdomains might have been found in public GitHub repositories due to accidental exposure. 😬

---

## 🔐 Importance of Using GitHub Tokens

GitHub has strict rate limits for unauthenticated searches. To **maximize results**, use personal access tokens stored in a file like `tokens.txt`.

You can generate GitHub tokens from:
👉 [GitHub Token Settings](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

### ✅ Recommended Scopes for the Token:
• `repo`  
• `read:public_key`  
• `read:org`

---

## 🏁 Conclusion

`github-subdomains` is an effective tool for uncovering subdomains leaked in GitHub repositories. 💥

When combined with other enumeration tools, it provides a **comprehensive reconnaissance strategy**. 🧰

Stay safe and happy recon! 💻🔐

