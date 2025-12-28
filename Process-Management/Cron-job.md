# Cron Jobs in Linux

---

## 1. Introduction to Cron

### What is Cron?  
Cron is a time-based job scheduler in Linux that automates tasks by executing scheduled commands or scripts at specific intervals. It runs as a background service (`crond`) and executes tasks defined in crontab files.

### What is a Cron Job?  
A cron job is a scheduled task that runs automatically at predefined times or intervals. These jobs are managed by the cron daemon, which continuously checks crontab files and executes scheduled commands.

### What is Crontab?  
A **crontab** (short for **cron table**) is a file that contains a list of cron jobs along with their schedules. Users define their cron jobs using `crontab -e`, and the system reads these files to execute scheduled commands.

---

## 2. Cron System Components

1. **Cron Daemon (`crond`)** – Background service that executes scheduled cron jobs.  
2. **Anacron (`anacron`)** – Ensures missed jobs run after system boot (for non-24/7 systems).  
3. **Cron Command (`crontab`)** – Used to create, list, edit, and remove user cron jobs.  
4. **Cron Files & Directories** – Stores and organizes scheduled tasks.  
5. **Run-Parts** – Executes scripts inside system cron directories automatically.

---

## 3. Installing and Verifying Cron

### Check If Cron Is Installed (CentOS 9)

```
rpm -qa | grep cron
```
```
rpm -qa | grep crontabs
```

### Install Cron (If Not Installed)

```
yum install crontabs
```

### Verify Installed Files

```
rpm -ql crontabs
```

### Check Package Information

```
rpm -qi crontabs
```

---

## 4. Cron Files and Directories

Cron jobs are managed in specific system directories:

```
ls -1 /etc/cron*
```

- **`/etc/crontab`** – System-wide cron job file for automated tasks.  
- **`/etc/cron.d/`** – Stores package-specific or categorized system cron jobs.  
- **`/etc/cron.hourly/`** – Runs scripts every hour (must be executable).  
- **`/etc/cron.daily/`** – Runs scripts once a day (default: 3 AM).  
- **`/etc/cron.weekly/`** – Runs scripts once a week (default: Sunday).  
- **`/etc/cron.monthly/`** – Runs scripts once a month (default: 1st day).  
- **`/etc/cron.allow`** – Controls which users are allowed to use cron.  
- **`/etc/cron.deny`** – Controls which users are denied access to cron.

---

## System-Wide Cron Directories

### `/etc/cron.hourly/` (Hourly Cron Jobs)
- A directory where scripts placed inside run **every hour** at 01 minute.
- Scripts must be executable (`chmod +x`).
- No need to specify time manually.

**Example: Log Synchronization Script**

```
#!/bin/bash
rsync -av /var/log/ /backup/logs/
```

Save as `/etc/cron.hourly/log_sync` and make it executable:

```
chmod +x /etc/cron.hourly/log_sync
```

---

**NOTE:**  
All scripts we create must be owned by root; otherwise, they will fail to run at the scheduled time.

---

### `/etc/cron.daily/` (Daily Cron Jobs)
- Runs scripts once per day (default: `3 AM`).
- Used for log rotation, system updates, and daily maintenance.

**Example: Cleaning Temporary Files**

```
#!/bin/bash
find /tmp -type f -mtime +7 -delete
```

Save as `/etc/cron.daily/clean_tmp` and make it executable:

```
chmod +x /etc/cron.daily/clean_tmp
```

---

### `/etc/cron.weekly/` (Weekly Cron Jobs)
- Runs scripts once per week (default: **Sunday**).
- Used for tasks like weekly backups or system maintenance.

**Example: Weekly System Backup**

```
#!/bin/bash
tar -czf /backup/system_backup_$(date +%F).tar.gz /home /etc /var
```

Save as `/etc/cron.weekly/system_backup` and make it executable:

```
chmod +x /etc/cron.weekly/system_backup
```

---

### `/etc/cron.monthly/` (Monthly Cron Jobs)
- Runs scripts once per month (default: **1st day of the month**).
- Used for monthly reports, system audits, or other periodic maintenance tasks.

**Example: Monthly User Activity Report**

```
#!/bin/bash
cat /var/log/secure | grep password > /backup/user_activity_$(date +%Y-%m).log
```

Save as `/etc/cron.monthly/user_report` and make it executable:

```
chmod +x /etc/cron.monthly/user_report
```

---

## How to Manually Run These Scripts

To manually execute the scripts in these directories, you can use:

```
run-parts /etc/cron.hourly
```
```
run-parts /etc/cron.daily
```
```
run-parts /etc/cron.weekly
```
```
run-parts /etc/cron.monthly
```

---

## Viewing and Editing `/etc/crontab` (System-Wide Crontab File)

- The system-wide cron job file.
- Defines environment variables (`SHELL`, `PATH`, `MAILTO`).
- Specifies scheduled tasks that apply to all users.
- Contains an additional **user field**, which defines which user will run the command.

To list the configuration files for crontabs:

```
rpm -qc crontabs
```

**Example `/etc/crontab` file:**

```
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root

# Job Format (Cron Scheduling Syntax)
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name command to be executed

  01 * * * * root run-parts /etc/cron.hourly

```

- **SHELL** – Specifies the shell to use (default is `/bin/bash`).
- **PATH** – Specifies the directories where cron searches for commands.
- **MAILTO** – Specifies the user to receive cron job output (empty string disables email).


---

## Job Format (Cron Scheduling Syntax)

```
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name command to be executed
```

### Common Symbols in Crontab

| Symbol | Meaning                                  |
|--------|------------------------------------------|
| `*`    | Any value                                |
| `,`    | List separator (e.g., 1,5,10)             |
| `-`    | Range of values (e.g., 1-5)                |
| `/`    | Step values (e.g., */5 means every 5 units)|

## Special Cron Time Strings

Some cron implementations support special strings to simplify scheduling:

```
@reboot   : Run once at startup.
@yearly   : Run once a year (equivalent to 0 0 1 1 *).
@annually : Same as @yearly.
@monthly  : Run once a month (equivalent to 0 0 1 * *).
@weekly   : Run once a week (equivalent to 0 0 * * 0).
@daily    : Run once a day (equivalent to 0 0 * * *).
@hourly   : Run once an hour (equivalent to 0 * * * *).
```

### For manual reference, see:  
  ```
  man crontab
  ```

### Online crontab scheduling reference:  
  
  [Crontab Guru](https://crontab.guru/)

---

## Example entries in /etc/crontab

- At 04:05 every day, the system runs a ClamAV scan on /opt/ recursively and removes any detected malware.  
  ```
  5 4 * * * root clamscan --remove -r /opt/
  ```

- At 00:05 every day during August, the system performs a yum update to update packages.  
  ```
  5 0 * 8 * root yum update
  ```

- At 14:15 on the 1st day of every month, the system clears out the /tmp/ directory by forcefully removing its contents.  
  ```
  15 14 1 * * root rm -rf /tmp/
  ```

- At 22:00 every Monday through Friday, the system copies all log files from /var/log/ to /tmp/ recursively with verbose output (using the "armour" user).  
  ```
  0 22 * * 1-5 armour cp -vr /var/log/* /tmp/
  ```

- At minute 23 past every 2nd hour from 00 through 20, the system kills all running SSH processes.  
  ```
  23 0-20/2 * * * root killall ssh
  ```

- At 04:05 every Sunday, the system creates a timestamped tar archive of the /home/armour directory and stores it in /tmp/.  
  ```
  5 4 * * sun armour tar -cvf /tmp/$(date "+\%d-\%m-\%Y-\%H-\%M").tar /home/armour
  ```

- At minute 0 past hour 0 and 12 on the 1st day of every 2nd month, the system creates a timestamped tar archive of the /home/armour directory and saves it in /tmp/.  
  ```
  0 0,12 1 */2 * armour tar -cvf /tmp/$(date +"\%F-\%H-\%M").tar /home/armour/
  ```

- At 04:00 on every day from the 8th to the 14th of each month, the system executes a custom backup script.  
  ```
  0 4 8-14 * * root /usr/local/bin/backup.sh
  ```

- At 00:00 on the 1st and 15th day of the month and every Wednesday, the system runs a cleanup script to remove or clean up temporary files or logs.  
  ```
  0 0 1,15 * 3 root /usr/local/bin/cleanup.sh
  ```

- At 00:00 every Sunday (using the @weekly macro), the system executes a weekly backup script.  
  ```
  @weekly root /usr/local/bin/weekly_backup.sh
  ```
---

## `/etc/cron.d/` (Package-Specific Cron Jobs)

- A directory where system packages can store their own scheduled cron jobs.
- Each file inside follows the same format as `/etc/crontab`.
- Used to keep system-wide scheduled tasks separate from user-defined tasks.

**Example file inside `/etc/cron.d/`:**

```
10 3 * * * root /usr/bin/backup_script.sh
```

This job runs `/usr/bin/backup_script.sh` daily at 3:10 AM as the root user.

---

## `/etc/cron.deny` (Denied Users for Cron)

- If this file exists, **users listed inside are blocked** from using cron.
- If `/etc/cron.allow` exists, this file is ignored.

To deny a user from using cron, add their name to this file:

```
echo "username" >> /etc/cron.deny
```

---

## Checking Cron Logs

To debug or check cron execution logs, use:

```
cat /var/log/cron
```

---

## Working with Date and Time in Cron Jobs

To fetch the current date and time:

```
date
```

### Formatting Date Output

```
date "+%F"
```
```
date "+%F-%H-%M"
```
```
date "+%d-%m-%Y-%H-%M"
```

### Creating Files with Timestamped Names

```
touch "$(date '+%d-%m-%Y-%H-%M')"
```
```
touch "$(date '+%d-%m-%Y-%H-%M-%S')"
```

### Archiving Files with Timestamps

```
tar -cvf /tmp/$(date "+%d-%m-%Y-%H-%M").tar /home/root/
```

If it gives problems on some Linux systems, escape the `%` symbols:

```
tar -cvf /tmp/$(date "+\%d-\%m-\%Y-\%H-\%M").tar /home/root/
```

---

## Example Cron Jobs

- **Run a script at 2:30 AM every day:**

  ```
  30 2 * * * /path/to/backup_script.sh
  ```

- **Clear the /tmp/ folder every Sunday at 3:00 AM:**

  ```
  0 3 * * 0 rm -rf /tmp/*
  ```

- **Check disk usage every 10 minutes and log it:**

  ```
  */10 * * * * df -h > /var/log/disk_usage.log
  ```

- **Run a PHP script on the 1st of every month at midnight:**

  ```
  0 0 1 * * php /path/to/script.php
  ```

---

## Managing User Cron Jobs

### User Crontab Format (for `crontab -e` command)

```
# ┌───────────── minute (0 - 59)
# │ ┌───────────── hour (0 - 23)
# │ │ ┌───────────── day of month (1 - 31)
# │ │ │ ┌───────────── month (1 - 12) OR jan,feb,mar,...
# │ │ │ │ ┌───────────── day of week (0 - 6; Sunday=0 or 7) OR sun,mon,...
# │ │ │ │ │
# * * * * * command-to-be-executed
```

- **List the current user's crontab:**

  ```
  crontab -l
  ```

- **Edit the crontab:**

  ```
  crontab -e
  ```
    #### Examples of `crontab -e` Entries  
  
    - Running a script every Monday at 6 AM  
      ```
      0 6 * * 1 /home/user/backup.sh
      ```
  
    - Clearing the system cache every day at 2 AM  
      ```
      0 2 * * * echo 3 > /proc/sys/vm/drop_caches
      ```
    
    - Sending an email notification every hour  
      ```
      0 * * * * echo "Hourly system check completed." | mail -s "System Check" user@example.com
      ```
      
    - Creating a timestamped backup of `/etc` every Sunday at 3:15 AM  
      ```
      15 3 * * 0 tar -czf /backup/etc_backup_$(date +\%F).tar.gz /etc/
      ```
      
    - Restarting Apache web server every day at midnight  
      ```
      0 0 * * * systemctl restart apache2
      ```

- **List another user's crontab:**

  ```
  crontab -l -u armour
  ```

- **Edit another user's crontab:**

  ```
  crontab -e -u armour
  ```

- **Remove all cron jobs for the current user:**

  ```
  crontab -r
  ```

- **Remove all cron jobs for another user:**

  ```
  crontab -r -u armour
  ```

---

## Monitoring Cron Service

- **Check the status of the cron service:**

  ```
  systemctl status crond.service
  ```

- **View active cron jobs in /etc/cron.d:**

  ```
  ls -lh /etc/ | grep cron
  ```

- **View logs in real-time:**

  ```
  tail -f /var/log/cron
  ```

---

## Handling Missed Jobs with Anacron

Anacron ensures that cron jobs scheduled on systems that are not running 24/7 (or when the system is off) are executed once the system is back online.

### Why It’s Important:  
It guarantees that essential tasks (daily, weekly, or monthly maintenance jobs) are not missed even if the system was offline at the scheduled time.

### Usage:  
Anacron jobs are defined in `/etc/anacrontab` and include a delay parameter.

**Example `/etc/anacrontab` Entry:**

```
# period delay job-identifier            command
1      5     cron.daily   run-parts /etc/cron.daily
7      10    cron.weekly  run-parts /etc/cron.weekly
30     15    cron.monthly run-parts /etc/cron.monthly
```

---

## Key Points to Remember

- The system runs scripts from these directories at predefined times.
- Scripts must be executable (`chmod +x script_name`).
- Scripts should not have file extensions (e.g., `.sh`).
- Check execution logs using:

  ```
  cat /var/log/cron
  ```

- Modify the default execution times in `/etc/crontab` if needed.

---

## How Does Cron Identify When to Run the Job?

When cron starts, it reads all cron files from:  
- `/var/spool/cron/crontabs/` (User crontabs)  
- `/etc/crontab`  
- `/etc/cron.d/` (System cron jobs)

It parses the scheduling format (minute, hour, day, month, weekday) and loads them into memory.

The cron daemon (`crond`) constantly checks the current system time:
- Every minute, it compares the current time with the scheduled time.
- If the time matches, it executes the command.
- Cron launches a new shell (`/bin/sh` by default) and executes the scheduled command.

By default, cron logs output to syslog.

---

## Where Can Users Place Cron Jobs?

| **Location**                | **Purpose**                                           | **Who Uses It?**           |
|-----------------------------|-------------------------------------------------------|----------------------------|
| `/var/spool/cron/crontabs/` | Stores per-user cron jobs added via `crontab -e`      | Individual users           |
| `/etc/cron.d/`              | Directory for system-wide cron jobs                   | Root & system services     |
| `/etc/crontab`              | Main system-wide cron file                            | Root (can run as any user) |
| `/etc/cron.hourly/`         | Scripts that run every hour                           | Root (via `/etc/cron.d/0hourly`) |
| `/etc/cron.daily/`          | Scripts that run daily (default: 3:00 AM)             | Root (via anacron)         |
| `/etc/cron.weekly/`         | Scripts that run weekly (default: Sunday 4:00 AM)     | Root (via anacron)         |
| `/etc/cron.monthly/`        | Scripts that run monthly (default: 1st of the month)  | Root (via anacron)         |

---
