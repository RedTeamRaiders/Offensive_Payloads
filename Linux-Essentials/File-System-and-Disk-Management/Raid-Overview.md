## **RAID (Redundant Array of Independent Disks) - Overview**  

RAID is a **data storage virtualization technology** that combines multiple physical disks into a single logical unit to improve **performance, redundancy, or both**. It is widely used in **servers, high-performance computing, and data centers** to enhance data reliability and system performance.  


### **Uses of RAID**  
RAID is implemented for several key reasons:  

1. **Fault Tolerance (Redundancy)**  
   - Ensures data is still accessible even if a disk fails.  
   - Used in **mission-critical applications** like banking and cloud storage.  

2. **Performance Improvement**  
   - Increases **read and write speeds** by distributing data across multiple drives.  
   - Useful for databases, video editing, and high-speed computing.  

3. **Data Protection**  
   - Some RAID configurations offer automatic data recovery.  
   - Protects against **disk failures and data corruption**.  

4. **Scalability**  
   - Can expand storage capacity by adding more disks without affecting existing data.  

5. **Load Balancing**  
   - Spreads data access across multiple disks, reducing bottlenecks in high-demand environments.  



## **RAID Levels**  

Different RAID configurations, known as **RAID levels**, provide varying degrees of **redundancy, speed, and storage efficiency**.  

| **RAID Level** | **Description** | **Pros** | **Cons** |
|--------------|-----------------|-----------|----------|
| **RAID 0 (Striping)** | Data is split across multiple disks for speed. **No redundancy.** | High performance | No fault tolerance |
| **RAID 1 (Mirroring)** | Data is duplicated on two disks. If one fails, the other takes over. | High redundancy | Uses double the storage |
| **RAID 5 (Striping with Parity)** | Data is spread across disks with **parity for recovery**. Requires **3+ disks**. | Balanced speed, storage, and redundancy | Slower writes due to parity calculation |
| **RAID 6 (Striping with Double Parity)** | Similar to RAID 5 but with **extra parity** for higher fault tolerance. Needs **4+ disks**. | Can survive **2 disk failures** | Slower than RAID 5 |
| **RAID 10 (RAID 1+0)** | Combines RAID 1 & RAID 0: **Mirroring + Striping**. Needs **minimum 4 disks**. | High performance & fault tolerance | Expensive (uses 50% of total storage) |



### **RAID Selection Guide**
- **Need high performance?** → **RAID 0** (if redundancy isn't important)  
- **Want redundancy and simple recovery?** → **RAID 1**  
- **Balanced performance & fault tolerance?** → **RAID 5**  
- **Extra protection against disk failures?** → **RAID 6**  
- **Best of speed and redundancy?** → **RAID 10**  
