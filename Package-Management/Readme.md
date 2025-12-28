# **Package Management in Linux**  

Package management in Linux refers to the process of installing, updating, configuring, and removing software packages. Each Linux distribution uses a **package manager** to handle software installation while resolving dependencies automatically.  

There are two major package management systems in Linux:

1. **RPM-based Systems** (RHEL, CentOS, Fedora, openSUSE)  
2. **DPKG-based Systems** (Debian, Ubuntu, Kali Linux)  


## **RPM (Red Hat Package Manager)**  
**RPM (Red Hat Package Manager)** is used in **Red Hat-based distributions** like **RHEL, CentOS, Fedora, and openSUSE**. It allows users to install, update, and remove software packaged in `.rpm` files.

### **Features of RPM**  
- **RPM packages use the `.rpm` extension**  
- **Does not resolve dependencies automatically** (unlike `YUM` or `DNF`)  
- **Can verify installed files for corruption or modification**  

### **Types of RPM Files**  
| Type | Description |
|------|------------|
| **Binary RPM (.rpm)** | Precompiled application or libraries, ready for installation. |
| **Source RPM (.src.rpm)** | Contains source code and build instructions, used to compile and install software manually. |

### **Advanced Package Managers for RPM Systems**  
RPM is a **low-level package manager** and does not handle dependencies. Instead, **YUM and DNF** are used to simplify package management:

- **YUM (Yellowdog Updater, Modified)**  
  - Resolves dependencies automatically.  
  - Installs packages from configured repositories.  
  - Used in **older RHEL-based distributions**.  

- **DNF (Dandified YUM)**  
  - A modern replacement for YUM, offering **faster performance** and **better dependency handling**.  
  - Used in **Fedora** and **RHEL 8+**.  


## **DPKG (Debian Package Manager)**  
**DPKG (Debian Package Manager)** is used in **Debian-based distributions** such as **Debian, Ubuntu, and Kali Linux**. It manages `.deb` packages.  

### **Features of DPKG**  
- **Handles `.deb` packages**  
- **Does not resolve dependencies automatically** (use `APT` for dependency handling)  

### **APT vs. DPKG**  
- `dpkg` installs `.deb` packages but **does not** handle dependencies.  
- `apt` (Advanced Package Tool) **automatically** resolves dependencies and installs missing packages.  

## **Different Architectures**  
Linux software is compiled for specific CPU architectures. The correct package must be used based on the system architecture.  

| **Architecture** | **Description** |
|-----------------|----------------|
| `x86` / `i386` / `i686` | 32-bit Intel/AMD processors |
| `x86_64` / `amd64` | 64-bit Intel/AMD processors |
| `armhf` / `arm64` | ARM-based CPUs (Raspberry Pi, mobile devices) |
| `ppc64` / `ppc64le` | IBM PowerPC processors |
| `s390x` | IBM System Z (mainframe) |
| `aarch64` | ARM 64-bit processors |

### **Check System Architecture**
```bash
uname -m
```
#### **Example Outputs:**
- `x86_64` → 64-bit Intel/AMD system  
- `i686` → 32-bit Intel/AMD system  
- `aarch64` → ARM 64-bit system  

### **Installing Packages for Specific Architectures**  
- **RPM Systems:**  
  ```bash
  rpm -ivh package.x86_64.rpm
  ```
- **DPKG Systems:**  
  ```bash
  dpkg --add-architecture i386
  ```