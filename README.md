# ð§ Linux Commands for DevOps & Cloud Students

<div align="center">

<img src="https://upload.wikimedia.org/wikipedia/commons/a/af/Tux.png" width="180"/>

# ð Linux Complete Commands Guide

### Beginner to Advanced Linux Commands  
### DevOps | Cloud | AWS | Kubernetes | System Administration

![Linux](https://img.shields.io/badge/Linux-Commands-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![AWS](https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge&logo=amazonaws)
![DevOps](https://img.shields.io/badge/DevOps-Automation-blue?style=for-the-badge)
![Shell](https://img.shields.io/badge/Shell-Scripting-green?style=for-the-badge)

</div>

---

# ð Table of Contents

1. Linux Basics
2. File Management
3. Navigation Commands
4. User Management
5. Permissions
6. Process Management
7. Package Management
8. Networking Commands
9. Storage Commands
10. AWS EBS & EFS
11. System Monitoring
12. Service Management
13. Shell Scripting
14. Compression Commands
15. Logging & Auditing
16. Useful DevOps Commands

---

# ð§ 1. Linux Basics

| Command | Description |
|---|---|
| `sudo su -` | Switch to root user |
| `su - username` | Switch user |
| `pwd` | Present working directory |
| `whoami` | Current logged in user |
| `hostname` | Show server hostname |
| `clear` | Clear terminal screen |
| `history` | Show command history |

---

# ð 2. File Management Commands

| Command | Description |
|---|---|
| `touch file` | Create file |
| `mkdir dir` | Create directory |
| `rm -rf file` | Remove file/directory |
| `cp file1 file2` | Copy file |
| `mv old new` | Move/Rename file |
| `cat file` | Read file |
| `cat > file` | Override content |
| `cat >> file` | Append content |
| `echo "hi"` | Print statement |
| `tree` | Show folder structure |
| `find / -name file` | Search file |
| `grep "text" file` | Filter content |

---

# ð 3. Navigation Commands

| Command | Description |
|---|---|
| `cd` | Change directory |
| `cd ..` | One step back |
| `cd ../..` | Two steps back |
| `cd ../../..` | Three steps back |
| `cd ~` | Home directory |
| `ls` | List files |
| `ls -l` | Detailed list |
| `ls -la` | Include hidden files |

---

# ð¤ 4. User Management

| Command | Description |
|---|---|
| `useradd user1` | Create user |
| `passwd user1` | Set password |
| `id user1` | User details |
| `who` | Logged in users |
| `w` | Active users |
| `cat /etc/passwd` | User list |
| `cat /etc/group` | Group list |
| `userdel -r user1` | Delete user |

---

# ð 5. Permissions Management

## Permission Numbers

| Permission | Value |
|---|---|
| Read | 4 |
| Write | 2 |
| Execute | 1 |

---

## Example

```text
7 = Read + Write + Execute
```

---

| Command | Description |
|---|---|
| `chmod 777 file` | Full permissions |
| `chmod 755 file` | Standard permission |
| `chmod -R 755 dir` | Recursive permission |
| `chown user:group file` | Change ownership |


---

# âï¸ 6. Process Management

| Command | Description |
|---|---|
| `ps aux` | Detailed process |
| `ps -ef` | Process list |
| `top` | CPU & RAM usage |
| `top -u user` | User process |
| `kill -9 PID` | Kill process |
| `pkill nginx` | Kill by name |
| `jobs` | Background jobs |
| `fg` | Bring foreground |

---

# ð¦ 7. Package Management

## YUM Commands

| Command | Description |
|---|---|
| `yum repolist` | Enabled repos |
| `yum list installed` | Installed packages |
| `yum search nginx` | Search package |
| `yum install nginx -y` | Install package |
| `yum remove nginx` | Remove package |
| `yum update -y` | Update system |

---

## APT Commands

| Command | Description |
|---|---|
| `apt update` | Update repo |
| `apt upgrade -y` | Upgrade packages |
| `apt install nginx -y` | Install package |

---

# ð 8. Networking Commands

| Command | Description |
|---|---|
| `curl ifconfig.me` | Public IP |
| `hostname -I` | Private IP |
| `ip addr show` | Network interfaces |
| `ss -tuln` | Open ports |
| `ping google.com` | Connectivity test |
| `telnet IP PORT` | Test port |
| `nc -zv IP PORT` | Netcat port test |
| `traceroute google.com` | Route trace |
| `nslookup google.com` | DNS lookup |
| `dig google.com` | Advanced DNS |

---

# ð NMAP Commands

## Scan Common Ports

```bash
nmap <target-ip>
```

---

## Scan Specific Ports

```bash
nmap -p 22,80 <target-ip>
```

---

## Scan All Ports

```bash
nmap -p- <target-ip>
```

---

## Example Output

```text
22/tcp open   ssh
80/tcp open   http
```

---

# ð¾ 9. Storage Commands

| Command | Description |
|---|---|
| `lsblk` | Block devices |
| `df -h` | Disk usage |
| `du -sh *` | Folder size |
| `mount` | Mounted filesystems |
| `umount /mnt/data` | Unmount disk |
| `file -s /dev/xvdf` | Check format |
| `mkfs.ext4 /dev/xvdf` | Format disk |

---

# âï¸ 10. AWS EBS & EFS

# ð EBS Commands

## Format Volume

```bash
mkfs.ext4 /dev/xvdb 
```

---

## Mount Volume

```bash
mount /dev/xvdb /mnt/data
```

---

## Resize Volume
#Because increasing the volume in the AWS console only enlarges the virtual disk device â it does not automatically modify the internal Linux partition table or filesystem.

```bash
growpart /dev/xvda 1 #if ext4 file sysytem
```

``` bash
xfs_growfs /dev/xvda1 #if xfs file system
```

```
# ð EFS Commands

## Install EFS Utils

```bash
yum install -y amazon-efs-utils
```

---

## Create Mount Point

```bash
mkdir -p /mnt/efs
```

---

## Mount EFS

```bash
mount -t efs fs-xxxx:/ /mnt/efs
```

---

# ð EBS vs EFS

| Feature | EBS | EFS |
|---|---|---|
| Type | Block Storage | File Storage |
| Access | Single EC2 | Multiple EC2 |
| Performance | High IOPS | Shared throughput |
| AZ Support | Single AZ | Multi AZ |
| Use Case | Databases | Shared Storage |

---

# ð 11. System Monitoring

| Command | Description |
|---|---|
| `uptime` | System uptime |
| `free -h` | RAM usage |
| `lscpu` | CPU details |
| `htop` | Interactive monitoring |
| `iostat -x 1` | Disk IO |
| `iftop` | Network traffic |
| `last reboot` | Reboot histor

… (truncated)
