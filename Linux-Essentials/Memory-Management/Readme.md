# Memory Management and System Performance

Memory management in Linux is crucial for optimizing system performance. It involves monitoring RAM usage, clearing cache, managing swap space, and tuning kernel parameters to ensure smooth operation.



## `free`

The free command is used to display information about system memory usage, including total, used, free, shared, buffer/cache, and swap memory.

   - Display memory usage in human-readable format (KB, MB, GB).
     ```bash
     free -h
     ```

   - Display memory usage in gigabytes.
     ```bash
     free -g
     ```

   - Display memory usage in megabytes.
     ```bash
     free -m
     ```

   - Display memory usage in kilobytes.
     ```bash
     free -k
     ```


## `vmstat`
The vmstat (Virtual Memory Statistics) command provides a real-time view of system performance, including CPU usage, memory, swap, disk I/O, and system processes.


   - Display basic system performance stats (memory, CPU, processes, etc.).
     ```bash
     vmstat
     ```

   - Show active memory and swap usage.
     ```bash
     vmstat -a
     ```

   - Display disk statistics.
     ```bash
     vmstat -d
     ```

   - Display summary of memory, swap, and disk statistics.
     ```bash
     vmstat -s
     ```

   - Display performance stats every 4 seconds for 5 iterations.
     ```bash
     vmstat 4 5
     ```

   - Display memory statistics every 4 seconds for 5 iterations.
     ```bash
     vmstat -s m 4 5
     ```

## `iostat`

The `iostat` command is used to **monitor CPU usage and disk I/O statistics**, helping to analyze system performance and identify bottlenecks.  

   - Display input/output statistics for devices and partitions.
     ```bash
     iostat
     ```

   - Display I/O statistics every 4 seconds for 5 iterations.
     ```bash
     iostat 4 5
     ```
  - **Monitor Disk and CPU Performance Continuously**  
    ```bash
    iostat 2
    ```
- **Show Detailed Disk Utilization (`-x` option)**  
    ```bash
    iostat -x
    ```
- **Display Output in Megabytes**  
    ```bash
    iostat -m
    ```
- **Monitor Specific Disk Only**  
    ```bash
    iostat -p sda
    ```
- **Show CPU Usage Only**  
    ```bash
    iostat -c
    ```


## `lsof`  

The `lsof` (**List Open Files**) command is used to display information about **open files and the processes using them**. Since **everything in Linux is a file** (including network connections, devices, and directories), `lsof` is a powerful tool for monitoring system activity.

- **Lists all open files on the system.**  
  ```bash
  lsof
  ```
- **List Open Files by a Specific User**  
  ```bash
  lsof -u username
  ```
- **Find the Process Using a Specific File**  
  ```bash
  lsof /path/to/file
  ```
- **Show Open Files for a Specific Process**  
  ```bash
  lsof -p 1234
  ```
- **Find Which Process is Using a Port**  
  ```bash
  lsof -i :80
  ```
- **List Open Files by Network Connections**  
  ```bash
  lsof -i
  ```
- **Show Open Files of a Specific Type**  
  ```bash
  lsof -i tcp
  ```
  ```
  lsof -i udp
  ```
- **Find Open Files on a Specific Disk or Mount Point**  
  ```bash
  lsof /mnt/usb
  ```

## `Kill`

The `kill` command in Linux is used to terminate processes by sending signals. It allows you to stop processes based on their Process ID (PID).  


## **Syntax**  
```bash
kill [signal] PID
```



## **Examples**  

- **List Running Processes (Find PID)**  
  ```bash
  ps aux
  ```

- **Kill a Process by PID (Default Signal: TERM - 15)**  
  ```bash
  kill 1234
  ```

- **Force Kill a Process (SIGKILL - 9)**  
  ```bash
  kill -9 1234
  ```

- **Kill All Instances of a Program**  
  ```bash
  killall firefox
  ```

- **Kill a Process by Name Using `pkill`**  
  ```bash
  pkill -9 firefox
  ```

- **Kill All Processes by a Specific User**  
  ```bash
  pkill -u username
  ```
- **View All Available Kill Signals**  
  ```bash
  kill -l
  ```