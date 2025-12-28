# Extracting Files from RPM Packages and ISO Images on Linux


## Extracting Files from an RPM Package

**`rpm2cpio`** is a command-line utility that converts an RPM package into a CPIO (Copy In, Copy Out) archive. This allows you to extract the contents of an RPM package without installing it using the traditional RPM package manager.

To extract the contents of an RPM package, use the following command:

```
rpm2cpio nginx-1.26.2-2.el9.ngx.x86_64.rpm | cpio -idmv
```

**Explanation:**

- **`rpm2cpio nginx-1.26.2-2.el9.ngx.x86_64.rpm`** converts the specified RPM package into a CPIO archive.
- The pipe symbol `|` passes the output of `rpm2cpio` directly to the `cpio` command.
- **`cpio -idmv`** extracts files from the CPIO archive with the following options:
  - **`-i`**: Extract files from the archive.
  - **`-d`**: Create leading directories where needed.
  - **`-m`**: Retain previous file modification times when creating files.
  - **`-v`**: Verbosely list files processed.

After running this command, all the files contained in the RPM package will be extracted into the current working directory, preserving the directory structure.

You can verify the list of files in the RPM package using:

```
rpm -qlp nginx-1.26.2-2.el9.ngx.x86_64.rpm
```


This command displays all the files that the RPM package would install, allowing you to compare them with the extracted files.




## Extracting Files from an ISO File

ISO files are disk images that contain the file system used on optical discs like CDs or DVDs. They often use the ISO 9660 file system format.

First, identify the file type using the `file` command:

```
file ubuntu.iso
```

**Sample Output:**

```
ubuntu.iso: ISO 9660 CD-ROM filesystem data (DOS/MBR boot sector) 'Ubuntu 24.04.1 LTS amd64' (bootable)
```

This confirms that the file is an ISO 9660 file system.

### Mounting the ISO File

To access the contents of the ISO file without burning it to a disc, you can mount it to a directory.

Create a mount point directory (if it doesn't already exist):

```
mkdir /mnt/iso
```

Mount the ISO file:

```
mount -t iso9660 ubuntu.iso /mnt/iso
```
  -   **`-t iso9660`**: Specifies the type of the file system (ISO 9660 in this case).

Navigate to the mounted directory to access the contents:

```
cd /mnt/iso
```

List the contents:

```
ls -l
```

You will now see all the files and directories contained within the ISO image.

### Unmounting the ISO File

After you're finished accessing the ISO contents, unmount the ISO to free up the mount point:

```
umount /mnt/iso
```

