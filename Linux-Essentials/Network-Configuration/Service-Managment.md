
# **Managing Services in Linux**  

Linux services are background processes that run automatically. They can be managed using `systemctl` (for `systemd` systems) or `service` (for `SysVinit` systems). Below are commands to check, start, stop, enable, and disable services using both methods.  



## **Checking the Status of a Service**  

- **Using `systemctl`**  
  ```bash
  systemctl status service_name
  ```
  Example:  
  ```bash
  systemctl status apache2
  ```

- **Using `service`**  
  ```bash
  service service_name status
  ```
  Example:  
  ```bash
  service apache2 status
  ```



## **Checking if a Service is Active or Enabled**  

- **Check if a service is running:**  
  ```bash
  systemctl is-active service_name
  ```
  ```bash
  service service_name status
  ```

- **Check if a service is enabled at boot:**  
  ```bash
  systemctl is-enabled service_name
  ```



## **Starting, Restarting, and Stopping a Service**  

- **Start a service:**  
  ```bash
  systemctl start service_name
  ```
  ```bash
  service service_name start
  ```

- **Restart a service:**  
  ```bash
  systemctl restart service_name
  ```
  ```bash
  service service_name restart
  ```

- **Stop a service:**  
  ```bash
  systemctl stop service_name
  ```
  ```bash
  service service_name stop
  ```



## **Enabling and Disabling Services at Boot**  

- **Enable a service to start on boot:**  
  ```bash
  systemctl enable service_name
  ```
  ```bash
  chkconfig service_name on
  ```

- **Disable a service from starting on boot:**  
  ```bash
  systemctl disable service_name
  ```
  ```bash
  chkconfig service_name off
  ```



## **Listing Services**  

- **List all active services:**  
  ```bash
  systemctl list-units --type=service --state=active
  ```

- **List all loaded services (active/inactive):**  
  ```bash
  systemctl list-units --type=service
  ```

- **List all services using `service` command:**  
  ```bash
  service --status-all
  ```



## **Viewing Service Logs with `journalctl`**  

- **View logs for a specific service:**  
  ```bash
  journalctl -u service_name
  ```

- **View the last 50 log entries:**  
  ```bash
  journalctl -u service_name -n 50
  ```

- **Follow live logs (like `tail -f`)**  
  ```bash
  journalctl -u service_name -f
  ```