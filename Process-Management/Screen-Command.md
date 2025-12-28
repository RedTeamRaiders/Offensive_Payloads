# Screen Command Guide

Screen is a terminal multiplexer that allows you to run processes in the background while managing multiple terminal sessions within a single window. This guide covers installation, basic usage, multi-window management, split screen, logging, multiuser mode, auto-start on SSH login, and advanced usage.

---

## Installation

### On RHEL/CentOS
Install using yum:
  
```
yum install screen
```

### On Debian/Ubuntu
Install using apt:

```
apt install screen
```

---

## Displaying Help

To show help information about screen usage:

```
screen --help
```

---

## Basic Screen Commands

### Start a Screen Session
Start a new session by simply invoking:

```
screen
```

This opens a new screen session where you can run your commands.

### Start a Named Screen Session
Run a named session for easier management:

```
screen -S <session_name>
```

**Example:**

```
screen -S mysession
```

### Run a Command in the Background within a Named Screen Session
Launch a background screen session running a specific command:

```
screen -S <session_name> -dm <command>
```

**Example (ping command):**

```
screen -S ping -dm ping 8.8.8.8
```

---

## Managing Screen Sessions

### List Active Screen Sessions
To list all active screen sessions:

```
screen -ls
```

Each session displays a unique session identifier along with its name if set.

### Reattach to the Last Detached Session
To reconnect to the most recently detached screen session:

```
screen -r
```

### Reattach to a Specific Screen Session
Reattach using the session name (or session ID):

```
screen -r <session_name>
```

**Example:**

```
screen -r mysession
```

### Force Reattach to a Session
If a session is still marked as attached in another terminal, force detach and reattach:

```
screen -d -r mysession
```

### Detach from a Screen Session (Background Mode)
While inside a screen session, detach by pressing:

```
Ctrl + A, then D
```

The session remains active in the background.

### Kill a Specific Screen Session
Terminate a session by sending the quit command:

```
screen -S mysession -X quit
```

The `-X` option tells screen to execute the specified command within the session.

---

## Multi-Window Management in Screen

Screen allows you to create and manage multiple windows (terminal sessions) within a single screen session.

### Create a New Window
Create a new terminal window:

```
Ctrl + A, then C
```

### Switch Between Windows
Move to the next or previous window:

```
Ctrl + A, then N   (Next Window)
```

```
Ctrl + A, then P   (Previous Window)
```

### List All Windows
Display a list of all open windows:

```
Ctrl + A, then "
```

### Rename a Window
Rename the current window for better identification:

```
Ctrl + A, then A
```

### Close a Window
Simply exit the window by typing `exit` at the shell prompt.

---

## Split Screen Mode

Screen can divide your terminal into multiple panes.

### Split Horizontally
Create a horizontal split (initially without a terminal in the new pane):

```
Ctrl + A, then S
```

After splitting, open a new terminal in the new pane by pressing:

```
Ctrl + A, then C
```

### Split Vertically
Create a vertical split:

```
Ctrl + A, then |
```

Again, open a new terminal in the new pane by pressing:

```
Ctrl + A, then C
```

### Switch Between Panes
Navigate between split panes:

```
Ctrl + A, then Tab
```

### Close a Pane
Remove the current split pane:

```
Ctrl + A, then X
```

---

## Logging in Screen

Enable session logging to save a record of your screen output:

```
Ctrl + A, then H
```

A log file named `screenlog.0` is created in the current directory. This is useful for debugging or monitoring long-running commands.

---

## Screen Sharing (Multiuser Mode)

Screen can be shared between multiple users, which is beneficial for pair programming or remote troubleshooting.

### Enable Multiuser Mode
Inside an active session, enable multiuser support by typing:

```
Ctrl + A, then :multiuser on
```

### Add a User to the Session
Allow another user to connect by adding them to the access control list:

```
Ctrl + A, then :acladd <username>
```

### Join a Shared Screen Session
Another user can join the session using the following command:

```
screen -x <username>/<sessionname>
```

---

## Auto-Starting a Screen Session on SSH Login

To automatically start or reattach a screen session upon SSH login, add the following snippet to your `~/.bashrc`:

```
if [[ -z "$STY" ]]; then
    screen -xR mysession
fi
```

This ensures your persistent session is automatically resumed with each login.

---

## Advanced Usage

### Run a Custom Script in the Background
You can run a custom script in a detached screen session. For example, suppose you want to run a pentesting script:

```
screen -S nmapver -dm /home/sachin/nmap-warrior.sh -u 192.168.1.1 -pvs -o 192.168.1.1
```

Make sure to adjust the command options according to your script’s requirements. (Note: The original example had typos which are now corrected.)

---

## Applications  
- screen is widely used in remote servers, pentesting, and troubleshooting where long-running processes need persistence.

---
