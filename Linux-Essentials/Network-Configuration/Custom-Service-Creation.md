# Custom Services in Linux: Complete Guide

This comprehensive guide is designed for those looking to understand and implement custom services (daemons) in Linux using systemd. It covers theoretical background, detailed practical instructions, advanced customization, troubleshooting, and best practices. Use this guide as a complete reference for your GitHub repository and Linux study course.

---

## 1. Theory: Understanding Linux Services and Systemd

### What Is a Service?

- **Definition:**  
  A service (or daemon) is a background process that performs specific functions such as networking, logging, system monitoring, or scheduled tasks without direct user interaction.

- **Why Use Services?**  
  - Run tasks continuously in the background.
  - Start automatically on boot to ensure essential processes are always available.
  - Allow centralized management (start, stop, restart, and monitor) via a common interface.

### Introduction to Systemd

- **Systemd Overview:**  
  Systemd is the default initialization system and service manager in most modern Linux distributions. It replaces older init systems like SysVinit and Upstart with more efficient, parallel startup and robust dependency handling.

- **Unit Files:**  
  Systemd utilizes plain-text configuration files known as "unit files" (typically with a `.service` extension) to define how services are managed, including their startup options, dependencies, and behavior.

- **Advantages of Using Systemd:**  
  - **Parallel Startup:** Services start in parallel for faster boot times.
  - **Dependency Management:** Directives such as `After=`, `Before=`, `Requires=`, and `Wants=` manage the service startup order.
  - **Centralized Logging:** All service logs are collected via `journalctl` for easy debugging.
  - **Uniform Management:** Consistent commands (e.g., `systemctl start/stop/status`) simplify controlling services.

*Glossary Note:*  
- **Daemon:** A background process that runs without direct user input.  
- **Unit File:** A configuration file used by systemd to manage and define services.

---

## 2. Anatomy of a Systemd Service File

A typical service file is divided into several sections and is usually stored in `/etc/systemd/system` for custom services. Below is a sample service file example to help you correlate the explanations with a practical layout:

```
[Unit]
Description=My Custom Background Service
After=network.target

[Service]
Type=simple
ExecStart=/usr/local/bin/custom_service.sh
ExecStop=/bin/kill -SIGTERM $MAINPID
ExecReload=/bin/kill -HUP $MAINPID
Restart=on-failure
User=nobody
Group=nogroup
ProtectSystem=full
ProtectHome=yes
NoNewPrivileges=yes

[Install]
WantedBy=multi-user.target
```

**Explanation of Key Directives:**

- **[Unit] Section:**
  - `Description`: A brief summary of the service.
  - `After=network.target`: Ensures the service starts only after network services are up.

- **[Service] Section:**
  - `Type=simple`: Indicates that the process started by the `ExecStart` command is the main process.
  - `ExecStart`: Specifies the command or script to start the service.
  - `ExecStop`: (Optional) Provides a command to gracefully stop the service. In this example, it sends a SIGTERM signal to the main process.
  - `ExecReload`: (Optional) Specifies how to reload the service configuration without a full restart – it sends a HUP signal.
  - `Restart=on-failure`: Configures systemd to automatically restart the service if it crashes or exits unexpectedly.
  - `User` and `Group`: Run the service under a non-privileged account for security.
  - **Security Options:**
    - `ProtectSystem=full`: Restricts write access to the system.
    - `ProtectHome=yes`: Limits access to users’ home directories.
    - `NoNewPrivileges=yes`: Prevents the service from gaining new privileges.
  
- **[Install] Section:**
  - `WantedBy=multi-user.target`: Associates the service with the multi-user run level so that it starts during a normal boot.

---

## 3. Practical: Creating a Custom Service

This section provides step-by-step instructions covering every necessary command to successfully create, test, and manage your custom service.

### Step A: Create Your Custom Script

1. **Write a Simple Script:**  
   Create a file named `/usr/local/bin/custom_service.sh` with the following content:
   ```
   #!/bin/bash
   # Custom Service Script: Logs the current timestamp every minute.
   while true; do
       echo "Custom service running at $(date)" >> /var/log/custom_service.log
       sleep 60
   done
   ```
   *Note:* This basic example demonstrates continuous operation and logging. Enhance error handling and logging as needed for your environment.

2. **Make the Script Executable:**  
   Run the command:
   ```
    chmod +x /usr/local/bin/custom_service.sh
   ```

### Step B: Create a Systemd Service File

1. **Create the Service File:**  
   Use your preferred text editor (e.g., vi, nano) to create the file `/etc/systemd/system/custom_service.service` with the following content:
   ```
   [Unit]
   Description=My Custom Background Service
   After=network.target

   [Service]
   Type=simple
   ExecStart=/usr/local/bin/custom_service.sh
   ExecStop=/bin/kill -SIGTERM $MAINPID
   ExecReload=/bin/kill -HUP $MAINPID
   Restart=on-failure
   User=nobody
   Group=nogroup
   ProtectSystem=full
   ProtectHome=yes
   NoNewPrivileges=yes

   [Install]
   WantedBy=multi-user.target
   ```
   **Key Points:**
   - Use clear and descriptive directives.
   - Security options (`ProtectSystem=full`, `ProtectHome=yes`, `NoNewPrivileges=yes`) help prevent accidental changes to system files.
   - `ExecStop` and `ExecReload` are optional but recommended for graceful service control.

### Step C: Reload, Start, Enable, Restart, and Test Your Service

1. **Reload Systemd Manager Configuration:**  
   Reload the service manager configuration to incorporate your new service file:
   ```
    systemctl daemon-reload
   ```

2. **Start the Service Immediately:**  
   Launch your custom service:
   ```
    systemctl start custom_service.service
   ```

3. **Check Service Status:**  
   Verify that the service is running without issues:
   ```
    systemctl status custom_service.service
   ```

4. **View Service Logs:**  
   Monitor the service logs for troubleshooting:
   ```
    journalctl -u custom_service.service
   ```
   For real-time log output:
   ```
    journalctl -u custom_service.service -f
   ```

5. **Restart the Service:**  
   If you modify the service file or the custom script, restart the service to apply changes:
   ```
    systemctl restart custom_service.service
   ```

6. **Enable the Service at Boot:**  
   Ensure that your service starts automatically when the system boots:
   ```
    systemctl enable custom_service.service
   ```

*Practical Tip:* Always test your service manually before enabling it at boot. This helps catch any potential issues early.

---

## 4. Advanced Customization Options

### A. Service Dependencies and Order

- **Using Dependencies:**  
  Define startup order and dependencies with directives like `Before=`, `After=`, `Requires=`, and `Wants=`.
  
  *Example:*
  ```
  After=network.target mysql.service
  Requires=mysql.service
  ```

### B. Service Type Variations

- **Type=forking:**  
  Use this type for daemons that fork into the background. Ensure you include a `PIDFile=` directive if needed.
- **Type=oneshot:**  
  Ideal for tasks that run once and exit, such as initialization scripts.

### C. Environment Variables and Files

- **Inline Variables:**  
  ```
  Environment=VAR_NAME=value
  ```
- **Load from a File:**  
  ```
  EnvironmentFile=/etc/default/yourapp
  ```

### D. Timeout and Restart Settings

- **Timeouts:**  
  Configure:
  ```
  TimeoutStartSec=30
  TimeoutStopSec=30
  ```
  to control systemd's wait time.
- **Restart Delay:**  
  Add a delay before restart:
  ```
  RestartSec=10
  ```

### E. Logging and Output Redirection

- **Custom Output:**  
  To redirect output to journals or files:
  ```
  StandardOutput=journal
  StandardError=journal
  ```
  Or, to dedicated log files:
  ```
  StandardOutput=file:/var/log/custom_service.out
  StandardError=file:/var/log/custom_service.err
  ```

---

## 5. Troubleshooting Custom Services

### Common Issues and Solutions

- **Service Fails to Start:**  
  - Check the service status:
    ```
     systemctl status custom_service.service
    ```
  - Review logs:
    ```
     journalctl -u custom_service.service
    ```
  - Verify script permissions, syntax, and correct file paths.

- **Dependency Problems:**  
  Ensure required services (like `network.target`) are active. Adjust dependencies as needed.

- **Logging Issues:**  
  Validate your logging directives and check the output using `journalctl`.

### Debugging Tips

- **Manual Script Test:**  
  Run the script directly:
  ```
  /usr/local/bin/custom_service.sh
  ```
- **Increase Verbosity:**  
  Add debug statements to your script to follow execution flow.
- **Permissions Check:**  
  Confirm the service’s user (e.g., `nobody`) has access to all required files and resources.

---

## 6. Best Practices

- **Store Custom Files Properly:**  
  Place custom service files in `/etc/systemd/system` to avoid conflicts with vendor services.
- **Document Configurations:**  
  Include clear comments and descriptions in both your scripts and service files.
- **Always Reload After Changes:**  
  Run:
  ```
   systemctl daemon-reload
  ```
  after modifying service files, then restart the service.
- **Monitor Regularly:**  
  Use `systemctl status` and `journalctl` to continuously monitor your services.
- **Apply Least Privilege:**  
  Run services with non-privileged users to enforce security.

---
