# CentOS 9 Installation (GUI)

[Download CentOS 9 Stream ISO](https://mirror.stream.centos.org/9-stream/BaseOS/x86_64/iso/CentOS-Stream-9-20250210.0-x86_64-dvd1.iso)

---

### VirtualBox Setup

- Open VirtualBox and click **New**.
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent1.png)
 
  
- Set the name to **CentOS 9**, type to **Linux**, and version to **Red Hat (64-bit)**.
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent2.png)

  
- Allocate **4096 MB** RAM (According to requirement).  
  2 core CPU
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent3.png)
 
  
- Create a virtual disk:  
  - Select **VDI (Virtual Disk Image)**  
  - Choose **Dynamically allocated**  
  - Set **file location and size to 40 GB** (According to requirement)
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent4.png)
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent5.png)


  
- Start the virtual machine,  
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent6.png)

- select the CentOS 9 ISO
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent7.png)

- and click **mount and reboot**
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent8.png)




---

## Installation

- Choose **Install CentOS 9**.
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent9.png)

 
- Select **English > English (India) > Continue**.
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent10.png)


- Configure settings:  
  - **Date & Time**: Asia/Kolkata > Done  
  - **Keyboard Layout**: English (India, with rupee) > Add English (US) > Done  
  - **Language Support**: English (India) > Done
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent11.png)

  

- **Installation Source**: Verify ISO > Done  
  - Auto-Detect Media  
    Automatically detects bootable installation media (DVD, USB, ISO)  
  - Network Sources  
    Closest Mirror: Selects the fastest CentOS mirror  
    NFS: Installs from a shared network directory  
    HTTP/HTTPS: Fetches packages from online repositories via secure links  
    FTP: Downloads from an FTP server  
  - Custom Repositories  
    Allows specifying offline or private repositories for custom setups  
  - Manual Options  
    Change source, verify media, or fallback to network if no valid media is found  
  
  [for now select auto detect media]
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent12.png)

  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent13.png)
 
  
- **Software Selection**: Select **Server with GUI**  
  - Base Environment Options:  
    These define the primary purpose of the system.  
    -  Server with GUI: Installs a server environment with a graphical user interface (GNOME)  
    -  Server: Provides a CLI-based server setup with essential services  
    -  Minimal Install: A lightweight installation with the bare minimum required to run CentOS  
    -  Workstation: For desktop use with a GUI and development tools  
    -  Custom Operating System: A fully customized setup to meet specific requirements  
    -  Virtualization Host: Configured to host and manage virtual machines  

  [for now select Server With GUI]

  - Additional Software for Selected Environment:  
    -  Each base environment includes optional add-ons to enhance functionality  
    -  Examples:  
      -  Development Tools: Compiler and libraries  
      -  Web Server: Apache, Nginx  
      -  File Server: Samba, NFS utilities  
      -  System Administration Tools: Diagnostic and monitoring tools  
  
  [for now don't select anything]
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent14.png)
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent15.png)


 

- Installation Destination
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent16.png)

  
  - **Custom partitioning** > Done  
  - Create partitions:  
    - `/boot` - **1024 MiB**, **ext4**, Standard  
    - `swap` - **4096 MiB**, Standard  
    - `/` - **XFS file system**, Standard  
  - Click **Done > Accept Changes**

  Selecting the Installation Device  
  When you reach the Installation Destination screen:  
  - Local Standard Disks:  
    -  Displays the available storage devices (e.g., HDD, SSD)  
    -  Select the disk where CentOS will be installed by clicking the checkbox next to it  
  - Specialized Storage Devices (optional):  
    -  Used for network-attached storage (NAS) or advanced configurations like iSCSI

  Storage Configuration Options  
  After selecting a device, choose a storage configuration mode:  
  a) Automatic Partitioning  
    - The installer automatically creates default partitions:  
      -  /boot (for bootloader files)  
      -  swap (used for virtual memory)  
      -  / (root directory for the OS)  
    - Suitable for beginners or general-purpose installations
  
  b) Custom Partitioning  
    - Provides full control over partitioning, allowing manual definition of partitions and their sizes  
    - Steps:  
      1. Partition Scheme:  
         § Standard Partition: Traditional partitioning (no LVM)  
         § LVM (Logical Volume Manager): Allows resizing, snapshots  
         § LVM Thin Provisioning: Dynamically allocates storage  
      2. Create Partitions:  
         § Recommended scheme:  
           -  /boot → 1 GB (Standard Partition)  
           -  swap → 4 GB (Standard Partition)  
           -  / → Remaining space (Standard Partition)  
           -  File System: ext4 or XFS  
      3. Encrypt My Data:  
         § Option to encrypt partitions for security  
      4. Additional Space:  
         § Reclaim space from existing partitions if needed
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent17.png)
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent18.png)
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent19.png)
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent20.png)


 
  Partition Details  
  /boot Partition  
  - Purpose: Stores bootloader files  

  swap Partition  
  - Purpose: Virtual memory when physical RAM is fully used  

  / (root) Partition  
  - Purpose: Main directory containing the OS and user files  

- **KDUMP**: No changes  
  Purpose: Configure KDUMP for kernel crash dumping  
  Features:  
  Enable/disable KDUMP  
  Specify memory allocation for crash dumps  
  [for now Keep it Enabled]

- **Network & Hostname**:  
  - Enable **enp0s3**  
  - Configure IPv4 manually, disable IPv6, save settings  
  - Set hostname to **Demo**
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent21.png)

  
- **Security Policy**: No changes  
  Purpose: Apply predefined security policies to the system  
  Features:  
  Choose profiles like CIS or DISA STIG  
  Integrate system-wide security hardening  
  [for now Keep it disabled]

- 9. Set **root password** and create a user:  
  - Full name: `<demouser>`  
  - Username: `<demouser>`  
  - Tick **Make this user administrator**
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent22.png)
  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent23.png)



  

  Lock the Root Account [for now Keep it disabled]  
  - Purpose:  
    -  Prevents the root account from being used directly for login  
    -  The root account remains available but can only be accessed through sudo

  Allow Root SSH Login with Password [for now Keep it enabled]  
  - Purpose:  
    -  Enables the root user to log in remotely via SSH using a password

  - User Creation  
    Create a non-root user for daily use
    

  ![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/cent24.png)
