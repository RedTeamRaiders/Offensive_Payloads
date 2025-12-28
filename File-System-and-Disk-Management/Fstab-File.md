# `fstab`

**The `/etc/fstab` file defines how disk partitions, block devices, and remote filesystems should be mounted at system boot.**

## **Fstab Entry Structure**

The `/etc/fstab` file defines how storage devices and partitions are mounted. Each entry follows this format:

```
<device>  <mount_point>  <filesystem_type>  <options>  <dump>  <pass>
```

## **Entry Components**  

| **Field**             | **Description**                                            | **Examples**                           |
|-----------------------|----------------------------------------------------------|----------------------------------------|
| **`<device>`**       | Identifies the filesystem to mount                        | `/dev/sdXn`, `UUID=xxxx`, `LABEL=xxx`, `//server/share` |
| **`<mount_point>`**  | Directory where the device is mounted                     | `/`, `/home`, `/mnt/data`, `/media/external` |
| **`<filesystem_type>`** | Type of filesystem                                      | `ext4`, `xfs`, `btrfs`, `ntfs`, `vfat`, `nfs`, `cifs` |
| **`<options>`**      | Mounting options                                          | `defaults`, `ro`, `rw`, `noauto`, `user`, `noexec`, `noatime`, `sync`, `async` |
| **`<dump>`**         | Backup utility (`dump`)                                   | `0` (No backup), `1` (Backup) |
| **`<pass>`**         | Filesystem check order (`fsck` priority)                  | `0` (Skip check), `1` (Root filesystem), `2` (Other filesystems) |



### **`<device>` – Specifies the Filesystem to Mount**  
This field defines the storage device or partition. It can be specified in different ways:  

- **By Device Name:** `/dev/sdXn` (e.g., `/dev/sda1`)  
- **By UUID:** `UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`  
- **By Label:** `LABEL=mydisk`  
- **By Network Path:** `//server/share` (for remote mounts like NFS, CIFS)  

---

### **`<mount_point>` – Mount Location**  
This specifies where the device or partition will be attached in the filesystem hierarchy.  

**Common Mount Points:**
- `/` – Root filesystem  
- `/home` – Home directory  
- `/mnt/data` – Custom mount point for data storage  
- `/media/external` – USB or external drive  

---

### **`<filesystem_type>` – Type of Filesystem**  
Indicates the filesystem type used on the device.  

**Common Filesystem Types:**
| Type    | Description |
|---------|------------|
| `ext4`  | Standard Linux filesystem |
| `xfs`   | High-performance journaling filesystem |
| `btrfs` | Advanced Linux filesystem with snapshots |
| `ntfs`  | Windows filesystem (read/write support via `ntfs-3g`) |
| `vfat`  | FAT filesystem (used for USB drives, Windows compatibility) |
| `nfs`   | Network File System |
| `cifs`  | Windows network shares (SMB) |

---

### **`<options>` – Mounting Options**  
Determines how the filesystem is mounted and accessed.  

| **Option**  | **Description** |
|------------|----------------|
| `defaults` | Standard mount options (`rw, suid, dev, exec, auto, nouser, async`) |
| `ro`       | Mount as read-only |
| `rw`       | Mount as read-write |
| `noauto`   | Do not mount at boot |
| `user`     | Allow non-root users to mount |
| `noexec`   | Prevent execution of binaries |
| `noatime`  | Do not update file access time (improves performance) |
| `sync`     | Writes data immediately (safer but slower) |
| `async`    | Writes data asynchronously (faster but riskier) |

---

### **`<dump>` – Backup Utility**  
Controls whether the `dump` utility should back up this filesystem.  

- `0` – Do not back up  
- `1` – Enable backup  

---

### **`<pass>` – Filesystem Check Order (`fsck` Priority)**  
Defines the order in which `fsck` (filesystem check) runs during boot.  

- `0` – Skip filesystem check  
- `1` – First check (used for root `/` filesystem)  
- `2` – Checked after root filesystem  


## **Example `/etc/fstab` Entries**

### **Basic Linux Partitions**
```
UUID=1234-5678   /               ext4    defaults        1 1
UUID=8765-4321   /home           ext4    defaults        1 2
/dev/sdb1        /mnt/data       xfs     defaults        0 2
```

### **Windows and Network Mounts**
```
/dev/sdc1        /media/usb      ntfs    defaults,noexec 0 0
//192.168.1.10/share /mnt/share  cifs    user,username=user,password=pass  0 0
```

## Permanent Mounting Methods

### 1. Mounting by Device Name
```
/dev/sda1  /  ext4  defaults  0  1
```
- **Pros:** Simple, direct
- **Cons:** Device names can change, less reliable

### 2. Mounting by UUID
```
UUID=550e8400-e29b-41d4-a716-446655440000  /  ext4  defaults  0  1
```
- **Pros:** Persistent, unique identifier
- **Recommended Method**
- **Find UUID:**
  ```
  blkid
  ```

### 3. Mounting by Label
```
LABEL=root  /  ext4  defaults  0  1
```
- **Pros:** Human-readable
- **Set Label:**
  ```
  e2label /dev/sda1 root
  ```

## Filesystem Mounting Types

### 1. Local Filesystem Mounts
```
# Ext4 Filesystem
/dev/sda1  /  ext4  defaults  0  1

# XFS Filesystem
/dev/sda2  /data  xfs  defaults  0  2
```

### 2. Network Filesystem Mounts
```
# NFS Mount
192.168.1.100:/share  /mnt/network  nfs  defaults,soft,intr  0  0

# CIFS/Samba Mount
//server/share  /mnt/windows  cifs  username=user,password=pass  0  0
```

### 3. Special Filesystems
```
# Temporary RAM Filesystem
tmpfs  /tmp  tmpfs  defaults,size=2G  0  0

# Proc Filesystem
proc  /proc  proc  defaults  0  0

# Sys Filesystem
sysfs  /sys  sysfs  defaults  0  0
```

### 4. Bind Mounts
```
# Duplicate directory to another location
/home/user/data  /mnt/backup  none  bind  0  0
```

### 5. Auto Mounts
```
/media/cdrom  /mnt/cdrom  auto  noauto,user,exec  0  0
```

## Advanced Mounting Options

### Security Options
```
# Secure Mount
/dev/sda2  /home  ext4  nodev,nosuid,noexec  0  2
```
- `nodev`: Disable device files
- `nosuid`: Ignore setuid/setgid
- `noexec`: Prevent binary execution

### Performance Options
```
# Performance Tuning
/dev/sda3  /data  ext4  noatime,data=writeback  0  2
```
- `noatime`: Disable access time updates
- `data=writeback`: Improved write performance

## Special Mounting Scenarios

### Removable Media
```
/dev/sr0  /media/cdrom  iso9660  noauto,user,exec  0  0
```

### External Drives
```
/dev/sdb1  /media/usb  vfat  user,noauto,exec  0  0
```

### Remote Mounts with Authentication
```
# NFS with Kerberos
192.168.1.100:/share  /mnt/secure  nfs  sec=krb5  0  0

# CIFS with Credentials File
//server/share  /mnt/windows  cifs  credentials=/etc/samba/credentials  0  0
```

## Persistent Mounting Commands
### Mount All Entries
```
mount -a
```
  - If no error is shown, fstab is correct.
  - If an error appears, fix /etc/fstab before rebooting.

### Verify Configuration
```
findmnt --verify
```

## Best Practices

1. Always use UUID for persistent mounts
2. Backup `/etc/fstab` before editing
3. Test configurations before system-wide apply
4. Use appropriate security and performance options
5. Regularly check filesystem health


## Troubleshooting

- Use recovery mode for boot issues
- Temporarily comment problematic entries
- Check system logs
- Verify filesystem configurations