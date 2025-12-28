# Linux Directory Structure 

The Linux directory structure is organized hierarchically and adheres to the **Filesystem Hierarchy Standard (FHS)**, ensuring a consistent way of locating files and directories across Linux distributions. 

#### Below is an overview table of each major directory, its purpose, and examples of its usage.

| Directory | Purpose |
| --- | --- |
| `/` | Root directory, the top-most level of the file system. Contains all other directories. |
| `/bin` | Essential system binaries for basic commands (e.g., `ls`, `cp`, `mv`). |
| `/sbin` | System binaries for administrative tasks, usually executed by the root user (e.g., `fsck`, `reboot`). |
| `/etc` | Configuration files for the system and applications (e.g., network, user settings). |
| `/dev` | Device files representing hardware devices (e.g., `tty`, `sda`, `null`). |
| `/proc` | Virtual files providing process and kernel information, such as `/proc/cpuinfo` and `/proc/meminfo`. |
| `/home` | Home directories for regular users where personal files and configurations are stored. |
| `/root` | Home directory for the root user (administrator). |
| `/lib` | Shared libraries required by system binaries and programs to run. |
| `/lib64` | 64-bit shared libraries for modern systems, similar to `/lib` but for 64-bit architecture. |
| `/media` | Mount points for removable media (e.g., CD/DVD drives, USB drives). |
| `/mnt` | Temporary mount points for manually mounted devices (e.g., mounting a network share). |
| `/opt` | Optional application software and packages not part of the core system. |
| `/srv` | Service data provided by the system, such as web server data or FTP server data. |
| `/tmp` | Temporary files used by applications. Cleared on reboot. |
| `/usr` | User programs, data, and shared files. This directory contains most user utilities and applications. |
| `/var` | Variable data files that change during system operation (e.g., logs in `/var/log`, spools, cache). |
| `/run` | Runtime data for processes since the last boot. Replaces `/var/run` and is available early during boot. |
| `/boot`| directory contains essential files required to boot the operating system. |
---

### Below is a detailed explanation of each directory.

## `/` (Root Directory)

- The root directory is the starting point of the Linux filesystem hierarchy. It is represented by a single forward slash (`/`). All other files and directories are contained within this directory.

- **Key Note**: Only the root user (administrator) has full access to this directory.

## `/bin` (User Binaries)

- The `/bin` directory contains essential user command binaries (executables) needed for system booting, repairing, maintenance, and basic operations.

- **Examples**: `ls` (list directory contents), `cat` (concatenate files), `cp` (copy files), `mv` (move/rename files), `mkdir` (create directories).

## `/sbin` (System Binaries)

- The `/sbin` directory holds binary executables used for system administration tasks. These commands are typically used by the root user for system maintenance.

- **Examples**: `fsck` (filesystem check), `reboot` (restart the system), `ifconfig` (network interface configuration).


## `/etc` (Configuration Files)

- The `/etc` directory contains system-wide configuration files and directories. It holds settings and configurations for the operating system and installed applications.


- **Examples**:
  - `/etc/passwd`: Contains user account information.
  - `/etc/shadow`: Stores hashed user passwords (accessible only by root).


## `/dev` (Device Files)

- The `/dev` directory is a special location that contains device files representing hardware components and peripherals. These are special files that act as interfaces to the hardware devices.

- **Examples**:
  - `/dev/null`: Discards all data written to it; acts as a black hole.
  - `/dev/sda`: Represents the first hard disk drive.
  - `/dev/tty`: Represents terminal devices.

## `/proc` (Process Information)

- The `/proc` directory is a virtual filesystem that provides a hierarchical view of the processes and kernel parameters. It contains files that represent system and process information.

- **Examples**:
  - `/proc/cpuinfo`: Displays information about the CPU.
  - `/proc/meminfo`: Provides memory usage information.
  - `/proc/[PID]/`: Contains information about a specific process with the given PID (Process ID).

## `/home` (User Home Directories)

- The `/home` directory contains the personal directories of all regular (non-root) users on the system. Each user has a subdirectory within `/home` to store personal files and configurations.

- **Examples**:
  - `/home/alice`: Home directory for the user `alice`.
  - `/home/bob`: Home directory for the user `bob`.

## `/root` (Root User Home Directory)

- The `/root` directory is the home directory for the root user, the superuser or administrator of the system.

- **Purpose**: Stores personal files and settings for the root user, separate from other users' data.

## `/lib` and `/lib64` (Libraries)

- The `/lib` and `/lib64` directories contain shared libraries needed by the binaries in `/bin` and `/sbin`. These libraries are similar to DLL files in Windows.

- **Purpose**: Provides essential shared libraries required by system programs to function properly.

- **Examples**:
  - `/lib/libc.so.6`: The GNU C Library.
  - `/lib64/`: Contains 64-bit libraries on systems that support both 32-bit and 64-bit applications.


## `/media` and `/mnt` (Mount Points)


- `/media`: Default mount point for removable media devices automatically mounted by the system, such as CDs, DVDs, and USB drives.
- `/mnt`: A directory where system administrators can mount temporary file systems manually.

## `/opt` (Optional Software)

- The `/opt` directory is used for installing additional or optional software packages that are not part of the default installation.

- **Purpose**: Stores third-party applications, typically in self-contained directories.

- **Examples**:
  - `/opt/google/chrome`: Installation directory for Google Chrome.
  - `/opt/myapp`: Custom application installed by the user.

- **Relevance for Pentesters**: Software here may not be managed by the system's package manager and could contain vulnerabilities due to outdated versions.

## `/srv` (Service Data)

- The `/srv` directory holds data for services provided by the system, such as web servers, FTP servers, and repositories.

- **Purpose**: Stores site-specific data served by the system.

- **Examples**:
  - `/srv/www`: Data for a web server.
  - `/srv/ftp`: Files for an FTP server.

## `/tmp` (Temporary Files)

- The `/tmp` directory is a world-writable space used for storing temporary files created by applications and the system.

- **Purpose**: Allows programs to store transient data that doesn't need to persist across reboots.


## `/usr` (User System Resources)

- The `/usr` directory (Unix System Resources) contains user programs, libraries, documentation, and other shared resources.

- **Purpose**: Stores applications and files that are not essential for booting or repairing the system but are used during normal operations.

- **Subdirectories**:
  - `/usr/bin`: General user command binaries (e.g., `gcc`, `python`).
  - `/usr/sbin`: Non-essential system administration binaries.
  - `/usr/local`: Locally installed software and custom applications.
  - `/usr/share`: Shared resources like documentation and icons.

## `/var` (Variable Data)

- The `/var` directory contains variable files that are expected to grow over time, such as logs, mail spools, and caches.

- **Purpose**: Stores data that changes frequently during system operation.

- **Examples**:
  - `/var/log`: System and application log files (e.g., `auth.log`, `syslog`).
  - `/var/www`: Default web server document root.
  - `/var/mail`: Incoming email storage.

## `/run` (Runtime Variable Data)

- The `/run` directory is a temporary filesystem that stores runtime data for processes since the last boot. It replaces older directories like `/var/run`.

- **Purpose**: Holds transient files like process IDs (PIDs), sockets, and other system information needed during operation.

- **Examples**:
  - `/run/nginx.pid`: Stores the process ID of the Nginx service.
  - `/run/systemd/journal/socket`: Socket file for systemd journaling.


## `/boot` (Boot Loader)

- The `/boot` directory contains essential files required to boot the operating system. These files are loaded during the system's startup process.


- **Examples**:
  - `/boot/grub/grub.cfg`: Configuration file for the GRUB bootloader, which determines how the system boots.
  - `/boot/vmlinuz`: The Linux kernel image file, which contains the core operating system code.
  - `/boot/initrd.img`: The initial RAM disk image, used during boot to mount the real root filesystem.