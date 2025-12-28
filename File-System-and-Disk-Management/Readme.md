## **What is a File System?**  
A **file system** is a method and data structure that an operating system (OS) uses to manage files on a storage device. It organizes data into files and directories, provides access control, and ensures data integrity. File systems also handle how data is stored, retrieved, and managed on a disk or other storage medium.  

**Functions of a File System:**  
- Organizes and stores data in a structured manner.  
- Manages file names, permissions, and metadata.  
- Controls access to data and maintains security.  
- Ensures data consistency and prevents corruption.  
- Supports various file operations like read, write, modify, and delete.  

Examples of file systems:  
- **FAT32, NTFS (Windows)**  
- **ext3, ext4 (Linux/Unix)**  
- **APFS, HFS+ (MacOS)**  



## **What is a Disk?**  
A **disk** is a storage medium used to store data permanently. It can be magnetic (like HDDs), solid-state (like SSDs), or optical (like CDs/DVDs).  

Disks are categorized based on their interface, speed, and capacity. They function as non-volatile storage, meaning data remains stored even after power is turned off.  



## **Types of Disks**  

### **1. ATA (Advanced Technology Attachment)**  
ATA is an older disk interface standard that connects storage devices like hard drives and CD-ROMs to a computer’s motherboard.  

- **Maximum Size**: 40 GB (Older technology)  
- Uses **PATA (Parallel ATA)** and **SATA (Serial ATA)** interfaces.  



### **2. PATA (Parallel Advanced Technology Attachment)**  
PATA, also known as **IDE (Integrated Drive Electronics)**, is an older interface for connecting hard drives and optical drives.  

- **Maximum Size**: 512 GB  
- Uses a **40 or 80-wire ribbon cable** for data transfer.  
- Supports two devices per cable (**Primary** and **Secondary** channels).  
- Devices are configured as **Master** and **Slave** using jumpers.  

**Device Naming in Linux (PATA Disks):**  
- **Primary Master:** `/dev/hda`  
- **Primary Slave:** `/dev/hdb`  
- **Secondary Master:** `/dev/hdc`  
- **Secondary Slave:** `/dev/hdd`  



### **3. SATA (Serial Advanced Technology Attachment)**  
SATA is the successor to PATA, offering faster data transfer speeds and improved reliability.  

- **Maximum Size**: 8 TB  
- **Speed:** 7200 RPM (Very fast)  
- Uses a **thin serial cable**, reducing clutter and improving airflow in PCs.  
- Each SATA device has its own dedicated cable.  

**Device Naming in Linux (SATA Disks):**  
- **First SATA Drive:** `/dev/sda`  
- **Second SATA Drive:** `/dev/sdb`  
- **Third SATA Drive:** `/dev/sdc`  
- **Fourth SATA Drive:** `/dev/sdd`  



### **4. SCSI (Small Computer System Interface)**  
SCSI is a high-speed interface standard used for connecting hard drives, tape drives, and optical drives in enterprise environments.  

- Faster than PATA and SATA.  
- Supports multiple devices on a single bus (up to 16 devices).  
- Used in **servers, workstations, and high-performance systems**.  



### **5. SSD (Solid State Drive)**  
SSDs use **flash memory** instead of spinning disks, providing much faster performance than HDDs.  

- **No moving parts**, making them more durable.  
- **Faster boot times and file transfers.**  
- **More expensive than HDDs**, but prices are decreasing.  



## **Types of Partitioning**  
Partitions divide a disk into sections to manage data more efficiently.  

1. **Primary Partition**  
   - A primary partition is a bootable partition that contains the OS.  
   - A disk can have up to **four primary partitions**.  

2. **Extended Partition**  
   - If more than four partitions are needed, one primary partition can be designated as **extended**.  
   - **Cannot store data directly**, but acts as a container for logical partitions.  

3. **Logical Partitions**  
   - Created inside the **extended partition**.  
   - Used for additional storage or separate OS installations.  

**Example of Partitioning in Linux (`/dev/sda`):**  
```
/dev/sda  -> Entire Disk  
├── /dev/sda1  -> Primary Partition  
├── /dev/sda2  -> Primary Partition  
└── /dev/sda3  -> Extended Partition  
    ├── /dev/sda4  -> Logical Partition  
    ├── /dev/sda5  -> Logical Partition  
```
