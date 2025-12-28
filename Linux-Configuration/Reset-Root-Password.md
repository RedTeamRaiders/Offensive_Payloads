# Reset Root Password via GRUB Menu at Startup


### **Steps to Edit GRUB and Reset Password:**

1. **When the PC starts, press `e` to edit the GRUB menu.**

2. **Find the keyword `ro` (read-only) and replace it with `rw` (read-write):**
   
3. **Add `init=/sysroot/sbin/sh` at the end of the line.**
   - This enables you to access the root shell 
   -  Press `Ctrl + X` to continue the boot process.   

   - Example line:
     
```bash
load_video 
set gfxpayload=keep 
insmod gzio 
linux ($root)/vmlinuz-5.14.0-522.e19.x86_64 root=UUID=81745846-b7a0-43a5-9e a5-eeb05633f54f `ro`  crashkernel=1G-4G:192M, 4G-64G:256M,64G-:512M resume UUIDS 
=4057a1e9-73f4-42e8-82cb-bf7b380f401b rhgb quiet 
initrd ($root)/initramfs-5.14.0-522.e19.x86_64.img $tuned_initrd 





Minimum Emacs-like screen editing is supported. TAB lists completions. Press Ctrl-x or F10 to boot, Ctrl-c or F2 for a command-line or ESC to discard edits and return to the GRUB menu
```
  
   - Modify it to:


  ```bash
load_video 
set gfxpayload=keep 
insmod gzio 
linux ($root)/vmlinuz-5.14.0-522.e19.x86_64 root=UUID=81745846-b7a0-43a5-9e a5-eeb05633f54f `rw init=/sysroot/sbin/sh`  crashkernel=1G-4G:192M, 4G-64G:256M,64G-:512M resume UUIDS 
=4057a1e9-73f4-42e8-82cb-bf7b380f401b rhgb quiet 
initrd ($root)/initramfs-5.14.0-522.e19.x86_64.img $tuned_initrd 




Minimum Emacs-like screen editing is supported. TAB lists completions. Press Ctrl-x or F10 to boot, Ctrl-c or F2 for a command-line or ESC to discard edits and return to the GRUB menu
```


4. **Change the default root path to access all binaries:**
   - Run the following command:
     ```bash
     chroot /sysroot/
     ```

5. **Update the root password:**
   - To change the root password, run:
     ```bash
     passwd
     ```

6. **(OPTIONAL) If SELinux is enabled, create an autorelabel file:**
   - This step ensures SELinux relabels the files on the next boot:
     ```bash
     touch /.autorelabel
     ```

7. **Reboot the system:**
   - Finally, reboot the system with the following command:
     ```bash
     reboot -f
     ```