# **LibreOffice and Apache OpenOffice Installation & Uninstallation**

## **LibreOffice**

**LibreOffice** is a powerful and free open-source office suite developed by The Document Foundation. It offers a comprehensive set of applications that cater to various productivity needs, making it a popular alternative to proprietary office suites like Microsoft Office. Below is an overview of the primary applications provided by LibreOffice:

## LibreOffice Applications

| **Application**            | **Description**                                                                                         |
|----------------------------|---------------------------------------------------------------------------------------------------------|
| **Writer**                 | Create and format text-heavy documents with ease.                                                       |
| **Calc**                   | Manage and analyze numerical data efficiently.                                                          |
| **Impress**                | Develop engaging and professional presentations.                                                         |
| **Draw**                   | Design intricate graphics and schematics.                                                                |
| **Base**                   | Build and maintain structured databases.                                                                 |
| **Math**                   | Insert and edit mathematical formulas seamlessly.                                                        |
| **Extensions and Templates** | Customize and accelerate your workflow with additional features and ready-made designs.                 |

**Note:** Installing LibreOffice via RPM as described results in a system-wide installation, making LibreOffice available to all users on the machine.

## **Installing LibreOffice via RPM**

### **Step 1: Download the RPM Package**

Ensure you download the correct 64-bit RPM package for your system.

```
wget https://download.documentfoundation.org/libreoffice/stable/25.2.0/rpm/x86_64/LibreOffice_25.2.0_Linux_x86-64_rpm.tar.gz
```

### **Step 2: Transfer the Package Using SCP (If Downloaded on Another Machine)**

Use the **Secure Copy Protocol (SCP)** to transfer the downloaded package to your target machine.

```
scp <username-of-source>@<ip-of-source>:"<source-path-to-file>" <username-of-destination>@<ip-of-destination>:"<destination-path>"
```

**Examples:**

```
scp "C:/Users/user1/LibreOffice_25.2.0_Linux_x86-64_rpm.tar.gz" root@192.168.1.121:"/root/Downloads/"
```
```
scp user1@192.168.1.120:"C:/Users/user1/LibreOffice_25.2.0_Linux_x86-64_rpm.tar.gz" root@192.168.1.121:"/root/Downloads/"
```
```
scp user1@192.168.1.120:"C:/Users/user1/LibreOffice_25.2.0_Linux_x86-64_rpm.tar.gz" "/root/Downloads/"
```

**Note:** There is no need to specify the IP address and username if running the SCP command from the local machine.

### **Step 3: Uncompress the Downloaded Package**

The downloaded file is in **gzip** format. Use the `gunzip` command to uncompress it.

```
gunzip LibreOffice_25.2.0_Linux_x86-64_rpm.tar.gz
```

### **Step 4: Extract the Tar Archive**

The uncompressed file is a tar archive. Use the `tar` command to extract it.

```
tar -xvf LibreOffice_25.2.0_Linux_x86-64_rpm.tar
```

### **Step 5: Install All RPM Packages**

Navigate to the extracted RPM directory and install all packages.

```
cd LibreOffice_25.2.0.3_Linux_x86-64_rpm/RPMS/
```
```
rpm -ivh *.rpm
```
- This package includes all necessary dependencies, so installing all RPM files will resolve dependencies automatically.
- Administrative (root) privileges are required to install RPM packages system-wide.

### **Step 6: Verify Installation**

- **Login via GUI Mode:**
  - Open your desktop environment's application menu.
  - LibreOffice applications should be listed under the "Applications" section.
  - Launch any LibreOffice application (e.g., Writer) to confirm successful installation.

## **Uninstalling LibreOffice**

### **Step 1: List Installed LibreOffice Packages**

Run the following command to display all installed LibreOffice packages in a space-separated format.

```
ls | awk -F ".rpm" '{print $1}' | tr "\n" " "
```

### **Step 2: Remove All LibreOffice Packages**

Copy the output from the previous command and paste it into the following command to uninstall all packages.

```
 rpm -evh <output-of-previous-command>
```

**Example:**

```
 rpm -evh LibreOfficeAB LibreOfficeCore LibreOfficeCL LibreOfficeWR LibreOfficeDR LibreOfficeAR LibreOfficeML
```

---

## **Apache OpenOffice Overview**

**Apache OpenOffice** is a free and open-source office productivity suite developed by the Apache Software Foundation. It serves as a popular alternative to proprietary office suites like Microsoft Office and LibreOffice. Below is an overview of the primary applications provided by Apache OpenOffice:

## LibreOffice Suite Applications

| **Application**               | **Description**                                                      |
|-------------------------------|----------------------------------------------------------------------|
| **Writer**                    | Create and format text-heavy documents with ease, such as letters, reports, and essays. |
| **Calc**                      | Manage and analyze numerical data efficiently for tasks like data analysis, budgeting, and financial calculations. |
| **Impress**                   | Develop engaging and professional presentations for meetings, lectures, and conferences. |
| **Draw**                      | Design intricate graphics and schematics for diagrams, flowcharts, and illustrations. |
| **Base**                      | Build and maintain structured databases for storing and organizing data. |
| **Math**                      | Insert and edit mathematical formulas seamlessly, enhancing document precision. |
| **Extensions and Templates**  | Enhance functionality and provide pre-designed document formats, customizing and accelerating your workflow with additional features and ready-made designs for resumes, brochures, and more. |

## **Installing Apache OpenOffice via RPM**

### **Step 1: Download the RPM Package**

Ensure you download the correct 64-bit RPM package for your system.

*Download Links:*

- [SourceForge Mirror 1](https://downloads.sourceforge.net/project/openofficeorg.mirror/4.1.15/binaries/en-GB/Apache_OpenOffice_4.1.15_Linux_x86-64_install-rpm_en-GB.tar.gz?ts=gAAAAABnqPOiwY_XNzUs-gaeI4MyUQT-jsKXGsmPT-FJhNrJsc4RfymF51kv8N8KmFwCMJ9S6bBwmwWoh_mkZvDBMRxmYlWKMQ%3D%3D&r=https%3A%2F%2Fsourceforge.net%2Fprojects%2Fopenofficeorg.mirror%2Ffiles%2F4.1.15%2Fbinaries%2Fen-GB%2FApache_OpenOffice_4.1.15_Linux_x86-64_install-rpm_en-GB.tar.gz%2Fdownload)
- [SourceForge Mirror 2](https://cyfuture.dl.sourceforge.net/project/openofficeorg.mirror/4.1.15/binaries/en-GB/Apache_OpenOffice_4.1.15_Linux_x86-64_install-rpm_en-GB.tar.gz?viasf=1)

### **Step 2: Transfer the Package Using SCP (If Downloaded on Another Machine)**

Use the **Secure Copy Protocol (SCP)** to transfer the downloaded package to your target machine.

```
scp <username-of-source>@<ip-of-source>:"<source-path-to-file>" <username-of-destination>@<ip-of-destination>:"<destination-path>"
```

**Examples:**

```
scp "C://Users/user1/Apache_OpenOffice_4.1.15_Linux_x86-64_install-rpm_en-GB.tar.gz" root@192.168.1.121:"/root/Downloads/"
```
```
scp user1@192.168.1.120:"C:/Users/user1/Apache_OpenOffice_4.1.15_Linux_x86-64_install-rpm_en-GB.tar.gz" root@192.168.1.121:"/root/Downloads/"
```
```
scp user1@192.168.1.120:"C:/Users/user1/Apache_OpenOffice_4.1.15_Linux_x86-64_install-rpm_en-GB.tar.gz" "/root/Downloads/"
```

**Note:** There is no need to specify the IP address and username if running the SCP command from the local machine.

### **Step 3: Uncompress the Downloaded Package**

The downloaded file is in **gzip** format. Use the `gunzip` command to uncompress it.

```
gunzip Apache_OpenOffice_4.1.15_Linux_x86-64_install-rpm_en-GB.tar.gz
```

### **Step 4: Extract the Tar Archive**

The uncompressed file is a tar archive. Use the `tar` command to extract it.

```
tar -xvf Apache_OpenOffice_4.1.15_Linux_x86-64_install-rpm_en-GB.tar
```

### **Step 5: Install All RPM Packages**

Navigate to the extracted RPM directory and install all packages.

```
cd /root/Downloads/en-GB/RPMS/
```
```
 rpm -ivh *.rpm
```

- This package includes all necessary dependencies, so installing all RPM files will resolve dependencies automatically.
- Administrative (root) privileges are required to install RPM packages system-wide.

### **Step 6: Install Desktop Integration for Apache OpenOffice**

To integrate Apache OpenOffice into your Linux desktop environment by adding menu entries and shortcuts, install the appropriate desktop integration package.

```
cd /root/Downloads/en-GB/RPMS/desktop-integration/
```
```
rpm -ivh openoffice4.1.15-freedesktop-menus-4.1.15-9813.noarch.rpm
```

**Description:**

- **`openoffice4.1.15-freedesktop-menus-4.1.15-9813.noarch.rpm`**
  - **Function:** Integrates Apache OpenOffice into freedesktop.org-compliant Linux desktop environments by adding menu entries and shortcuts.

### **Step 7: Verify Installation**

- **Login via GUI Mode:**
  - Open your desktop environment's application menu.
  - Apache OpenOffice applications should be listed under the "Applications" section.
  - Launch any Apache OpenOffice application (e.g., Writer) to confirm successful installation.

## **Uninstalling Apache OpenOffice**

### **Step 1: Remove Core Apache OpenOffice Packages**

Navigate to the RPM directory and list all installed Apache OpenOffice packages except for desktop integration.

```
cd /root/Downloads/en-GB/RPMS/
```
```
ls | grep -v 'desktop-integration' | awk -F ".rpm" '{print $1}' | tr "\n" " "
```

**Example Output:**

```
openoffice4.1.15-core-4.1.15-9813
openoffice4.1.15-desktop-integration-4.1.15-9813
```

**Remove Core Packages:**

Copy the output from the previous command and paste it into the following command to uninstall all core packages.

```
 rpm -evh <output-of-previous-command>
```

**Example:**

```
 rpm -evh openoffice4.1.15-core-4.1.15-9813 openoffice4.1.15-desktop-integration-4.1.15-9813
```

### **Step 2: Remove Desktop Integration Packages**

Navigate to the desktop integration RPM directory and remove the desktop integration packages.

```
cd /root/Downloads/en-GB/RPMS/desktop-integration/
```
```
ls | grep -v 'desktop-integration' | awk -F ".rpm" '{print $1}' | tr "\n" " "
```

**Example Output:**

```
openoffice4.1.15-freedesktop-menus-4.1.15-9813
```

**Remove Desktop Integration Packages:**

Copy the output from the previous command and paste it into the following command to uninstall the desktop integration packages.

```
 rpm -evh <output-of-previous-command>
```

**Example:**

```
 rpm -evh openoffice4.1.15-freedesktop-menus-4.1.15-9813
```

**Outcome:**

- All Apache OpenOffice packages, including desktop integration components, will be removed from the system.

