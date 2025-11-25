# ✨ Daily Learning Update – Linux Fundamentals 🐧

Today I learned Linux fundamentals, and it was a super valuable experience for me as an AWS & DevOps Engineer. 🤗  
I understood how Linux is the backbone of most cloud environments, servers, and container systems like Docker & Kubernetes.  
It provides a secure, stable, and highly customizable platform, making it essential for automation, troubleshooting, and cloud deployment.

Learning Linux is definitely boosting my confidence in building efficient cloud and DevOps solutions. 🚀  
If you found this helpful, share your thoughts, experiences, or tips in the comments — I’d love to learn from you too! 😊

---

## 🐧 History of Linux
Linux was created in 1991 by Linus Torvalds as a free and open-source alternative to UNIX.  
The first Linux kernel was released publicly, allowing global developers to contribute and improve it.  
Today, Linux powers servers, supercomputers, Android devices, and modern cloud platforms like AWS.

---

## 🐧 What is Linux? — Fundamentals
Linux is an open-source, Unix-based operating system widely used in servers, cloud platforms, and DevOps environments.  
It manages hardware resources and provides a secure, stable, and customizable platform for running applications.  
Its hierarchical file system and shell interface enable automation and scripting, making Linux essential for DevOps workflows.

---

## ✔ Pros of Linux
- Free and open source
- Highly secure & stable
- Best performance for servers and cloud workloads
- Flexible & customizable with automation support
- Huge community and support

## ❌ Cons of Linux
- Steeper learning curve for beginners
- Limited compatibility with some commercial software
- More manual configuration required

---

## ⭐ Why Linux is Valuable in AWS DevOps
- Most AWS compute and container services run on Linux
- Supports automation & CI/CD for reliable deployment
- Strong performance, security & troubleshooting capabilities

---
# 📌 Linux Useful Commands 

| **Category** | **Command / Item** | **Description / Purpose** |
|-------------|---------------------|----------------------------|
| **Colors Meaning in Terminal** | Files | White |
| | Folders | Blue |
| | All Permission Granted | Green |
| | Close Editing File | `:q!`, `ctrl + x → Enter` |
| **Package Managers** | `apt-get` | Advanced Package Tool (Debian-based) |
| | `yum / dnf` | Yellowdog Updater Modified (RHEL-based) |
| | `dpkg` | Debian package manager |
| | `rpm` | RedHat Package Manager |
| **File System Operations** | `ls` | List files & folders |
| | `ls -lt`, `ls -ltr` | Permissions, groups, latest first |
| | `ls -l` | Detailed file listing |
| | `pwd` | Show current path |
| | `cat file` | View file content |
| | `touch file` | Create empty file |
| | `touch file{1..10}` | Create multiple files |
| | `nano file` | Create/Edit file |
| | `vi/vim file` | Edit file via VI editor |
| | `cd` | Change directory |
| | `cd ..` | Move back one folder |
| | `cd ../..` | Move back two levels |
| | `mkdir folder` | Create directory |
| | `mkdir -p a/b/c` | Create nested folders |
| | `rm file` | Remove file |
| | `rmdir folder` | Remove directory |
| | `cp file folder/` | Copy file to folder |
| | `mv file folder/` | Move/Cut file |
| | `mv old new` | Rename file or folder |
| | `head -5 file` | Show first 5 lines |
| | `tail -5 file` | Show last 5 lines |
| | `grep "word" file` | Search word |
| | `egrep "a|b"` | Search multiple words |
| | `wc -l file` | Line count |
| | `cmp fileA fileB` | Compare files |
| | `diff fileA fileB` | Show differences |
| | `find ./ -name test.csv` | Find file |
| | `locate file` | Locate file (after `updatedb`) |
| | `history` | Show executed commands |
| | `man ls` | Manual of command |
| | `gzip`, `gunzip`, `tar`, `zip` | Compress/Extract |
| | `wget <url>` | Download file |
| | `uptime` | Server running time |
| | `script` | Record terminal session |
| | `ctrl + d` | Exit & save |
| **Networking & Security** | `ping domain.com` | Check connectivity |
| | `ssh user@ip` | Connect remote |
| | `scp file user@ip:/path` | Transfer files |
| | `netstat -putan` | Check ports |
| | `traceroute url` | Track packet route |
| | `systemctl start/stop/status` | Service management |
| | `chmod`, `chown`, `chgrp` | File permissions & ownership |
| | `pgrep nginx` | Get process ID |
| | `pkill nginx` | Kill process |
| | `reboot`, `shutdown` | Restart / Stop server |
| **User & Group Management** | `useradd`, `userdel` | Add/Delete user |
| | `groupadd`, `groupdel` | Add/Delete group |
| | `passwd user` | Set password |
| | `su user` | Switch user |
| | `cat /etc/group` | View groups |
| **Scheduling** | `at 05:10 PM` | Schedule task |
| | `echo "task" > file` | Apply at schedule |

# 📡 Linux Networking, Services, Processes & Permissions

| **Category** | **Command / Item** | **Description / Purpose** |
|-------------|---------------------|----------------------------|
| **Networking** | `ifconfig` | Configure network interfaces |
| | `ping` | Check network connectivity |
| | `netstat` | Display network statistics |
| | `traceroute` | Trace the route of packets |
| | `iptables` | Configure firewall rules |
| | `dig` | DNS lookup and query tool |
| | `ip` | Check network IP details |
| **System Service** | `systemctl` | Control system services |
| | `service` | Manage system services |
| | `chkconfig` | Run-level service management |
| **Process Management** | `ps` | Display running processes |
| | `ps -ef | grep java` | Check specific service |
| | `ps -u` | Show detailed process info |
| | `ps -A` | List all running & stopped processes |
| | `top` | Monitor system performance |
| | `du` | Disk usage of directories/files |
| | `kill` | Terminate a process |
| | `killall` | Kill processes by name |
| **Shell Scripting Tools** | `bash` | Bourne Again Shell |
| | `sh` | Bourne Shell |
| | `awk` | Pattern scanning & processing |
| | `tac` | Reverse output of `cat` |
| | `grep` | Search lines by keyword |
| | `sed` | Stream editor for text processing |
| | `wc` | Word/line/byte count |
| | `tr` | Translate/replace characters |
| | `sort` | Sort lines of text |
| | `diff` | Compare differences between files |
| | `tee` | Split output to display + save |
| **System Information** | `uname` | System information |
| | `df`, `df -h` | Disk storage usage |
| | `free` | Memory usage |
| | `hostname` | View or set hostname |
| | `nslookup` | DNS troubleshooting |
| | `systeminfo` | System hardware/software info |
| | `lscpu` | CPU & cores information |
| | `lsblk` | Block storage devices |
| | `uname -a`, `cat /etc/os-release` | OS information |
| **File Permissions** | `chmod` | Change permissions |
| | `chmod +x file` | Add execute permission |
| | `chown user file` | Change ownership |
| | `chgrp group file` | Change group ownership |
| | `umask` | Set default permissions |
| | `getfacl file` | Show ACL permissions |
| **Octal Permission Reference** | `0` | --- No permissions |
| | `1` | --x Execute only |
| | `2` | -w- Write only |
| | `3` | -wx Write + execute |
| | `4` | r-- Read only |
| | `5` | r-x Read + execute |
| | `6` | rw- Read + write |
| | `7` | rwx Read, write, execute |
| **User & Group Management** | `useradd john` | Add new user |
| | `usermod -aG sudo john` | Modify user & add to group |
| | `userdel john` | Delete user |
| | `groupadd admins` | Create group |
| | `groupmod -n developers devs` | Rename group |
| | `groupdel devs` | Delete group |

#… Thank You …

#DevOps #AWS #Linux #LearningJourney #CloudComputing #Automation #CareerGrowth #DevOpsEngineer

### Name – Sudarshan Yadav, Contact - 7709877817
### Email Id – sudarshanyadav4080@gmail.com
GitHub: https://github.com/Sudarshanydv
Dev.to Blog: https://dev.to/sudarshan_yadav
LinkedIn: https://www.linkedin.com/in/sudarshan-yadav
Resume (Drive) - https://drive.google.com/file/d/1jas-UeQuCSR6OZCP6pAPTnLiWcJiAVk1/view?usp=drive_link
