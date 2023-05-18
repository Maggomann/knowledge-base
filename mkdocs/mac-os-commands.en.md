---
category: awesome
sub_category_1: awesome
language: de
tags:
- awesome
---

# Mac OS Command Line Commands

## File Management:

### cd

Change the current directory. For example, `cd ~/Documents` changes the current directory to "Documents" in the home directory.

### ls

Lists the contents of the current directory. For example, `ls -l` shows a list of files and directories in the current directory.

### pwd

Shows the current directory. For example, `pwd` shows the current directory.

### mkdir

Creates a new directory. For example, `mkdir ~/Documents/MyProject` creates a new directory named "MyProject" in the "Documents" directory in the home directory.

### rm

Removes a file or directory. For example, `rm ~/Documents/MyProject` removes the "MyProject" directory in the "Documents" directory in the home directory.

### cp

Copies a file or directory. For example, `cp ~/Documents/MyProject ~/Desktop/MyProject` copies the "MyProject" directory in the "Documents" directory in the home directory to the "MyProject" directory on the desktop.

### mv

Moves a file or directory. For example, `mv ~/Documents/MyProject ~/Desktop/MyProject` moves the "MyProject" directory in the "Documents" directory in the home directory to the "MyProject" directory on the desktop.

### open

Opens a file or directory. For example, `open ~/Documents/MyProject` opens the "MyProject" directory in the "Documents" directory in the home directory.

### find

Finds files and directories. For example, `find ~/Documents -name MyProject` finds files and directories named "MyProject" in the "Documents" directory in the home directory.

### grep

Searches a file or text for a pattern or expression. For example, `grep "error" log.txt` shows all lines in the "log.txt" file that contain the word "error".

### less

Shows the contents of a file. For example, `less log.txt` shows the contents of the "log.txt" file.

### head

Shows the first lines of a file. For example, `head log.txt` shows the first 10 lines of the "log.txt" file.

### tail

Shows the last lines of a file. For example, `tail log.txt` shows the last 10 lines of the "log.txt" file.

### touch

Creates an empty file. For example, `touch log.txt` creates an empty file named "log.txt".

## System Monitoring:

### top

Shows a list of running processes. For example, `top` shows a list of running processes.

### ps

Shows a list of running processes. For example, `ps aux` shows all processes on the system.

### ifconfig

Shows the network configuration. For example, `ifconfig en0` shows the configuration of the "en0" network adapter.

## Network Tools:

### ping

Sends a ping to a host. For example, `ping google.com` sends a ping to "google.com".

### ssh

Connects to a remote server via Secure Shell (SSH). For example, `ssh

## File System Tools

### df

Shows the free space on the file systems. For example, `df -h` shows the free space in a human-readable form.

### du

Shows the size of files and directories. For example, `du -sh` shows the size of the current directory in a human-readable form.

### tar

Creates or extracts a tar archive. For example, `tar -xvf archive.tar` extracts the archive "archive.tar".

### unzip

Unzips a ZIP file. For example, `unzip archive.zip` unzips the ZIP file "archive.zip".

### diskutil

Shows information about the disks. For example, `diskutil list` shows a list of disks.

### ln

Creates a symbolic link. For example, `ln -s ~/Documents/MyProject ~/Desktop/MyProject` creates a symbolic link to the "MyProject" directory in the "Documents" directory in the home directory on the desktop.

### mount

Mounts a file system. For example, `mount -t iso9660 image.iso /mnt/iso` mounts the ISO file "image.iso" to the directory "/mnt/iso".

## Access Rights Tools

### chmod

Changes the access rights for a file or directory. For example, `chmod 755 script.sh` gives the script "script.sh" the permission to be executed.

### chown

Changes the owner of a file or directory. For example, `chown user file.txt` changes the owner of the file "file.txt" to the user "user".

## Root Tools

### sudo

Executes a command as superuser. For example, `sudo reboot` reboots the computer.
