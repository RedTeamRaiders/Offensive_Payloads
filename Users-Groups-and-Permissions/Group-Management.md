# **User Groups in Linux**  

**Groups** are used to manage user permissions and access to files, directories, and system resources. A user can belong to multiple groups, and groups help in defining shared access privileges.  



## **`groupadd`** – Add a New Group  

The `groupadd` command creates a new group in the system.  

### **Switches**  
- `-f` → Force the creation of a group (even if it exists).  
- `-g` → Specify a custom Group ID (GID).  
- `-o` → Allow non-unique GID.  
- `-p` → Set a hashed password for the group.  
- `-r` → Create a system group.  
- `-R` → Create a root-level group.  

### **Examples**  
- Create a group with a specific GID:  
  ```bash
  groupadd -g 1001 developers
  ```
- Create a group with a duplicate (non-unique) GID:  
  ```bash
  groupadd -o -g 1002 testers
  ```
- Create a group with a hashed password:  
  ```bash
  groupadd -p 'hashed_password_value' hr_team
  ```

## **`groupmod`** – Modify an Existing Group  

The `groupmod` command is used to change group attributes.  

### **Switches**  
- `-g` → Change the Group ID (GID).  
- `-o` → Allow a duplicate (non-unique) GID.  
- `-p` → Change the group password (hashed).  

### **Examples**  
- Change the GID of a group:  
  ```bash
  groupmod -g 2001 developers
  ```
- Change GID to a non-unique value:  
  ```bash
  groupmod -o -g 3001 testers
  ```
- Set or change the group password:  
  ```bash
  groupmod -p 'new_hashed_password' hr_team
  ```

## **`gpasswd`** – Manage Group Memberships  

The `gpasswd` command is used to administer `/etc/group` and manage group members.  

### **Switches**  
- `-a` → Add a user to a group.  
- `-d` → Remove a user from a group.  
- `-r` → Remove the group password.  
- `-M` → Add multiple users to a group.  
- `-A` → Assign administrators to the group.  

### **Examples**  
- Add a user to a group:  
  ```bash
  gpasswd -a user1 developers
  ```
- Remove a user from a group:  
  ```bash
  gpasswd -d user1 testers
  ```
- Remove the password of a group:  
  ```bash
  gpasswd -r hr_team
  ```
- Add multiple users to a group:  
  ```bash
  gpasswd -M user1,user2,user3 finance
  ```
- Make a user an administrator of a group:  
  ```bash
  gpasswd -A admin_user marketing
  ```

## **`groupdel`** – Delete a Group  

The `groupdel` command removes a group from the system.  

### **Switches**  
- `-f` → Forcefully delete a group.  

### **Examples**  
- Delete a group:  
  ```bash
  groupdel developers
  ```
- Forcefully delete a group:  
  ```bash
  groupdel -f testers
  ```