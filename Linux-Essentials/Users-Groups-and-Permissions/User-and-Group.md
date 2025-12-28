## **What is a User Account?**

A **user account** represents a **user** (e.g., employee) who uses the system regularly. Every person who is allowed to work on the computer must have a **unique user account**. Through this account, all activities and tasks of that person are recorded, and they are given the rights to work on the system.


- **UID (User ID)**: Every user is assigned a unique **UID** (User ID), which helps to identify them in the system.
- **User Information**: Information such as the user’s name, UID, home directory, and shell is stored in the **`/etc/passwd`** file.


## **Types of Users in Linux**

1. **Root User Account**

   The **Root** user is the most powerful account in Linux. This account is created automatically during the system installation and has the highest level of privileges.
   - The **Root user** can perform any task, whether system administration or access any file or service.
   - This account should only be used for **system administration** and should not be used for everyday tasks.
   - The **Root UID** is always **0**, and it cannot be **deleted**, but it can be **disabled** if needed.

2. **Regular User Account**

   This is a regular user account that is used by anyone who is allowed to work on the system.  
   - A **Regular user** has **moderate privileges**, meaning they can only perform tasks for which they have been granted permission.
   - These accounts are used for **routine work** and can be **disabled** or **deleted** if needed.
   - **UID** typically starts from **1000** and can go up to **60000**.

3. **Service/System Accounts**

   **Service accounts** are created to run **services** and **processes** on the system.  
   - These accounts are not used for **routine work**. 
   - Their **UID** usually ranges from **100** to **999**.


## **User's Home Directory**

- **Root User's Home Directory**: The root user's home directory is **`/root`**.
- **Regular User's Home Directory**: Every regular user has a home directory, which is typically **`/home/username`**. For example, if the user’s name is `john`, their home directory will be **`/home/john`**.


## **What is a Group?**

A **group** is a collection of users that allows system administrators to manage multiple users with similar permissions collectively. Instead of assigning permissions to individual users, they can be granted to the group, simplifying access control.