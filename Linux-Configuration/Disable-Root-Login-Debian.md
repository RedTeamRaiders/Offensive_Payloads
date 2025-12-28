# Enabling Root Login in GUI on Debian (Step-by-Step)

## Step 1: Log in as a Normal User and Open the Terminal
Switch to the root user:

```bash
sudo -i
```

Set a password for the root account (if not already set):

```bash
sudo passwd root
```

Enter and confirm a strong password.

## Step 2: Allow Root Login in the Display Manager
Follow the steps below according to your display manager.

### For GDM (GNOME Display Manager):
Edit the GDM configuration file:

```bash
sudo nano /etc/gdm3/custom.conf
```

Find the `[security]` section and add or modify the following lines:

```ini
[security]
AllowRoot=true
```

Edit PAM settings to allow root login in GDM:

```bash
sudo nano /etc/pam.d/gdm-password
```

Locate the following line:

```sql
auth required pam_succeed_if.so user != root quiet_success
```

Comment it out by adding `#` at the beginning:

```arduino
# auth required pam_succeed_if.so user != root quiet_success
```

Save and exit (Press `CTRL+X`, then `Y`, then `Enter`).

## Step 3: Restart the Display Manager
Run the following command:

```bash
sudo systemctl restart gdm
```

## Step 4: Enable Root Login via SSH (Optional)
By default, Debian disables root login via SSH. To enable it:

Edit the SSH configuration file:

```bash
sudo nano /etc/ssh/sshd_config
```

Check and ensure the following lines are set correctly:

```nginx
PermitRootLogin yes
PasswordAuthentication yes
```

If any of these lines are commented out (`#` at the beginning), remove the `#`, save the file (`CTRL+X`, then `Y`, then `Enter`).

Restart the SSH service:

```bash
sudo systemctl restart ssh
```

## Step 5: Log in as Root
1. Restart your system.
2. At the login screen, select `root` and enter the password.