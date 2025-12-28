# Linux Keyboard Shortcuts Cheat Sheet  

This cheat sheet provides a quick reference for general terminal commands, navigation, window management, file manager operations, and common browser/app shortcuts. Use it as a productivity boost across your Linux environment!

## General Shortcuts  
| Shortcut         | Description                                                     |
|------------------|-----------------------------------------------------------------|
| Ctrl + C         | Cancel/terminate the currently running process                  |
| Ctrl + D         | Logout of the terminal (or send EOF: End Of File)                |
| Ctrl + L         | Clear the terminal screen                                       |
| Ctrl + S         | Pause terminal output (freeze scrolling)                        |
| Ctrl + Q         | Resume terminal output                                          |
| Ctrl + Z         | Suspend the current process (send it to background)             |
| Ctrl + A         | Move cursor to the beginning of the line                        |
| Ctrl + E         | Move cursor to the end of the line                              |
| Ctrl + U         | Delete text from the cursor to the beginning of the line        |
| Ctrl + K         | Delete text from the cursor to the end of the line              |
| Ctrl + W         | Delete the word before the cursor                               |
| Ctrl + Y         | Paste (yank) the last deleted text                              |
| Ctrl + R         | Reverse search through command history                          |
| Ctrl + G         | Exit history search mode                                        |

──────────────────────────────────────────────  
## Terminal Navigation Shortcuts  
| Shortcut            | Description                                          |
|---------------------|------------------------------------------------------|
| Alt + F             | Move forward one word                                |
| Alt + B             | Move backward one word                               |
| Alt + D             | Delete the word after the cursor                     |
| Alt + Backspace     | Delete the word before the cursor                    |
| Shift + Page Up     | Scroll up in the terminal (view previous output)     |
| Shift + Page Down   | Scroll down in the terminal                        |

──────────────────────────────────────────────  
## Window & Tab Management  
| Shortcut                   | Description                                                      |
|----------------------------|------------------------------------------------------------------|
| Ctrl + Shift + T           | Open a new terminal tab                                          |
| Ctrl + Shift + W           | Close the current terminal tab                                   |
| Ctrl + Shift + N           | Open a new terminal window                                       |
| Alt + Tab                  | Switch between open applications                                 |
| Alt + Shift + Tab          | Switch between open applications (reverse order)                 |
| Super + Left               | Snap/move window to the left half of the screen                  |
| Super + Right              | Snap/move window to the right half of the screen                 |
| Super + Up                 | Maximize the window                                              |
| Super + Down               | Minimize (or restore) the window                                 |

Note: The “Super” key is typically the Windows key or Command key (on some keyboards).

──────────────────────────────────────────────  
## File Manager Shortcuts (GNOME, KDE, etc.)  
| Shortcut             | Description                                                 |
|----------------------|-------------------------------------------------------------|
| Ctrl + N             | Open a new file manager window                              |
| Ctrl + T             | Open a new tab in the file manager                          |
| Ctrl + W             | Close the current tab or window                             |
| Ctrl + Shift + N     | Create a new folder                                         |
| F2                   | Rename the selected file or folder                          |
| Delete               | Move the selected file/folder to Trash                      |
| Shift + Delete       | Permanently delete the file/folder without moving to Trash  |
| Ctrl + X             | Cut the selected file/folder                                |
| Ctrl + C             | Copy the selected file/folder                               |
| Ctrl + V             | Paste the file/folder                                       |
| Ctrl + A             | Select all files/folders                                    |
| Ctrl + Shift + T     | Reopen the last closed tab (supported in some managers)     |

Note: Shortcuts in file managers can vary between GNOME Files, Dolphin, Thunar, etc. Refer to your file manager’s documentation for details.

──────────────────────────────────────────────  
## Browser & Application Shortcuts  
| Shortcut                  | Description                                        |
|---------------------------|----------------------------------------------------|
| Ctrl + T                  | Open a new tab (in browsers and some apps)         |
| Ctrl + W                  | Close the current tab                              |
| Ctrl + Shift + T          | Reopen the last closed tab                         |
| Ctrl + Tab                | Switch to the next tab                             |
| Ctrl + Shift + Tab        | Switch to the previous tab                         |
| Alt + F4                  | Close the active window/application                |


# Command-Line Shortcuts (Aliases)

You can create shortcuts for frequently used commands using aliases.

Example:
```
alias ll='ls -lah'
alias gs='git status'
alias c='clear'
```
To make them permanent, add them to ~/.bashrc or ~/.zshrc and run:

```
source ~/.bashrc
```
or 
```
source ~/.zshrc
```