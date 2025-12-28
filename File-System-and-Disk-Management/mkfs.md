# MKFS COMMANDS

The `mkfs` command is used to format partitions with a specified filesystem. Use the commands below in one go as a quick reference for different filesystem types.

---

## Basic Syntax

```
mkfs -t <fstype> <device>
```
- **<fstype>**: Filesystem type (e.g., ext4, xfs, vfat, ntfs).  
- **<device>**: Target partition or disk (e.g., /dev/sda1).

---

## Filesystem Formatting Commands

- **ext4 Filesystem:**  
  ```
  mkfs.ext4 /dev/sdXn
  ```
  
- **ext3 Filesystem:**  
  ```
  mkfs.ext3 /dev/sdXn
  ```

- **ext2 Filesystem:**  
  ```
  mkfs.ext2 /dev/sdXn
  ```

- **XFS Filesystem:**  
  ```
  mkfs.xfs /dev/sdXn
  ```

- **Btrfs Filesystem:**  
  ```
  mkfs.btrfs /dev/sdXn
  ```

- **VFAT (FAT32) Filesystem:**  
  ```
  mkfs.vfat /dev/sdXn
  ```

- **NTFS Filesystem (requires ntfs-3g):**  
  ```
  mkfs.ntfs /dev/sdXn
  ```

---

## Additional Options

- **Specify a Filesystem Label (ext4):**  
  ```
  mkfs.ext4 -L MyLabel /dev/sdXn
  ```

- **Force Filesystem Creation (ext4):**  
  ```
  mkfs.ext4 -F /dev/sdXn
  ```

- **Set Block Size (XFS example):**  
  ```
  mkfs.xfs -b size=4096 /dev/sdXn
  ```

---

Replace `/dev/sdXn` with the appropriate partition identifier (e.g., `/dev/sda1`). Use these commands together as a concise reference for formatting disks with various filesystem types.
