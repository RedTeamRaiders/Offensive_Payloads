# Installing Debian on VirtualBox

Welcome to this detailed guide on installing Debian on VirtualBox. This guide will walk you through downloading the Debian ISO, creating and configuring a new virtual machine, partitioning the disk, and completing the installation—all with theory and screenshots to help you every step of the way.

---

## 1. Download Required Files

- **Download Debian ISO**  
  Visit the official [Debian Download](https://www.debian.org/download) page and download the ISO file.
  
  ![Download Debian ISO](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb1.png)

---

## 2. Create a New Virtual Machine (VM)

1. Open VirtualBox and click **New**.
2. Enter the following details:
   - **Name**: Debian
   - **Type**: Linux
   - **Version**: Debian (64-bit)
3. Select Debian ISO
4. Click **Next**.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb2.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb3.png)

---

## 3. Configure Virtual Machine Settings

### A. Allocate RAM
- **Recommended**: At least **2048 MB (2 GB)**.
- For better performance (especially with a desktop environment), you can assign **4096 MB (4 GB)** if your host hardware permits.

### B. Create a Virtual Hard Disk
1. Select **"Create a virtual hard disk now"** and click **Create**.
2. Choose **"VDI (VirtualBox Disk Image)"** and click **Next**.
3. Set **Storage on physical hard disk** to **"Dynamically allocated"**.
4. Set the disk size – **Recommended**: 40 GB or more.
5. Click **Create**.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb4.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb5.png)

---

## 4. Start Debian Installation

1. Click **Start** to boot the VM.
2. When presented with the boot menu, choose either **"Graphical Install"** (recommended for ease of use) or **"Install"** (text-based installer).

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb6.png)

---

## 5. Select Language, Location, and Keyboard

- **Language**: Choose your preferred language.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb7.png)

- **Location**: Select your country.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb8.png)

- **Keyboard**: Choose your keyboard layout (default is usually US; select another if required).

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb9.png)

These selections help configure locale settings such as date formats and language options.

---

## 6. Configure Network

- Set a **hostname** for your system—for example, `debian`.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb10.png)

- Enter a **domain name** if needed, or you can leave it empty.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb11.png)

---

## 7. Set Root Password

- You will be asked to create a strong password for the root account (which has full privileges).

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb12.png)

---

## 8. Create User and Set Passwords

- **Create a New User**:  
  - Fill in the full name, username, and password for the non-root account.  

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb13.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb14.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb15.png)

- Using a non-root account for daily tasks increases system security.

---

## 9. Partition the Disk – (Manual Partitioning Method)

When you reach the partitioning step, you have options:

1. **Guided Options**:  
   - Use entire disk
   - Use entire disk with LVM
   - Use entire disk with encrypted LVM

### Theory & Key Points – Partitioning Options
- **Guided partitioning** simplifies the setup by automating partition creation.
- **Manual partitioning** offers flexibility for custom layouts (for example, splitting /home, /var, etc.).
- **LVM (Logical Volume Manager)** provides flexible storage management.
- **Encryption** options add an extra security layer for your data.

2. **Manual Partitioning**: Gives full control over partition setup. This guide demonstrates the manual method for a 40 GB disk.

### Recommended Partition Scheme:

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb16.png)

- Select hard disk 

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb17.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb18.png)

#### A. Boot Partition
- **Mount Point**: `/boot`
- **Size**: 2 GB (stores bootloader files and kernel images)
- **Type**: Primary
- **Filesystem**: ext4

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb19.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb20.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb21.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb22.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb23.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb24.png)

#### B. Swap Partition
- **Size**: 2 GB (or around the size of your physical RAM; typically do not exceed 4 GB in a VM)
- **Type**: Logical
- **Use as**: Swap area

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb25.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb26.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb27.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb28.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb29.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb30.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb31.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb32.png)

#### C. Root Partition
- **Mount Point**: `/`
- **Size**: Remaining space on the disk
- **Type**: Primary
- **Filesystem**: ext4

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb33.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb34.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb35.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb36.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb37.png)

#### D. Finish Partitioning

- Note: This will write changes to the disk, ensure everything is correct.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb38.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb39.png)

---

## 10. Install the Base System

- The installer will now copy the base system files onto the disk.
- This process may take several minutes; please be patient.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb40.png)

---

## 11. Configure Package Manager Source

- By default, Debian uses online repositories to install packages.
- Click **No** if you do not want to install packages from local installation media.
- For new users, it is recommended to **Click No**.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb41.png)

---

## 12. Configure Mirrors for Package Installation

- Select your country or continent.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb42.png)

- Select the Debian archive mirror.
- It is recommended to go with `deb.debian.org`.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb43.png)

---

## 13. Configure Proxy Server

- For beginners, skip this step and leave it blank.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb44.png)

---

## 14. Configure Package Usage Survey Participation

- This option allows Debian to anonymously collect data on the most used packages, aiding developers in optimizing package selections.
- It is recommended to select **No** to maintain privacy, but you can opt-in if you wish to contribute usage statistics.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb45.png)

---

## 15. Select Software

- **Desktop Environment**: Choose from available options such as GNOME (default), KDE, XFCE, LXDE, Cinnamon, etc.
- **Standard System Utilities**: Recommended for essential system management tools.
- **SSH Server**: Optionally select this if you plan to access your Debian VM remotely.

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb46.png)

Choose your software selections and continue with the installation process.

---

## 16. Install GRUB Bootloader

- When prompted, choose **Yes** to install the GRUB bootloader.
- GRUB will allow you to boot into Debian (and any other operating systems if applicable).

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb47.png)

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb48.png)

---

## 17. Finish Installation & Reboot

- After all installation steps are complete, the installer will prompt you to reboot.
- Remove the ISO from your virtual machine’s storage settings if necessary.

- Boot Normally

![image](https://github.com/InfoSecWarrior/Linux-Essentials/blob/main/Images/deb49.png)

---

# Congratulations!

You have now successfully installed Debian on VirtualBox. This guide covered everything from downloading the ISO file, creating and configuring the VM, partitioning the disk manually, selecting software, and installing the GRUB bootloader.
