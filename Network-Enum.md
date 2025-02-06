# Network Enumeration Guide

## Introduction
Network Enumeration is the process of gathering information about a system’s network configuration, interfaces, routing, and active connections. This information is crucial for penetration testing, system auditing, or troubleshooting network-related issues.

---
## 1. Checking Network Interfaces & Configuration

### View Active Network Interfaces
```sh
ifconfig
ifconfig -a  # Show inactive interfaces as well
ip a
ip addr
```

### Checking Configuration Files
#### Debian-based systems:
```sh
cat /etc/network/interfaces
```
#### Red Hat-based systems:
```sh
cat /etc/sysconfig/network-scripts/ifcfg-enp0s3
```
#### General network settings:
```sh
cat /etc/sysconfig/network
```

### Checking DNS Information
```sh
cat /etc/resolv.conf
```

### Routing Table
```sh
route
route -n
/sbin/route -ne
```

### Traceroute
```sh
traceroute 192.168.1.6
tracepath 192.168.1.6
```

### ARP Table
```sh
arp -a
arp -e
ip neigh
```

### Network Manager Tool
```sh
nmtui
```

---
## 2. Checking Active Connections & Communication

### List Open Sockets
```sh
lsof -i
lsof -n -i
lsof -i :80
```

### Check Port and Protocol Information
```sh
grep 80 /etc/services
```

### Listing All Network Connections
```sh
netstat -antup
netstat -antpx
netstat -tulpn
netstat -ano
netstat -nltup
```

### Check Listening Ports
```sh
netstat -an | grep -i listen
netstat -nltup | grep -i listen
```

---
## 3. System and User Activity

### List Services & Startup Programs
#### For older systems:
```sh
chkconfig --list
chkconfig --list | grep 3:on
```

---
## 4. Applications & Services Details

### Installed Applications
#### List Executables in Common Directories
```sh
ls -lha /usr/bin/
ls -lha /bin/
ls -lha /usr/sbin/
ls -lha /sbin/
ls -lha /usr/local/bin/
ls -lha /usr/local/sbin/
ls -lha /opt/
```

### Package Management Tools
#### Debian-based Systems (APT)
```sh
dpkg -l
ls -lha /var/cache/apt/archives/
```

#### Red Hat-based Systems (YUM/RPM)
```sh
rpm -qa
ls -lha /var/cache/yum/*
```

#### Find Specific Package Details
```sh
rpm -qa | grep ftp
```

---
## 5. Process Management Commands

### List All Processes
```sh
ps -aux
ps -aux | grep root  # Processes run by root
ps -aux | grep -v root  # Processes not run by root
```

### Process Tree View
```sh
pstree
```

### Detailed Process List Information
```sh
ps -ef
ps -ef | grep root
ps -ef | grep -v root
```

### Real-time Process Monitoring
```sh
top  # Show live processes
htop
```

---
## 6. Service Management Commands

### List All Services
#### Old Linux (SysVinit systems)
```sh
service --status-all
service --status-all | less
service apache2 status
```

#### New Linux (Systemd-based systems)
```sh
systemctl status httpd.service
systemctl list-units --type=service --state=running
systemctl | grep running
```

### Service File Locations
```sh
/etc/init.d/
/usr/lib/systemd/system/
```

#### Example of a systemd service file
```ini
[Unit]
Description=Apache HTTP Server

[Service]
ExecStart=/usr/sbin/apachectl start
ExecStop=/usr/sbin/apachectl stop
Restart=always

[Install]
WantedBy=multi-user.target
```

### Starting & Stopping Services
```sh
systemctl start apache2.service
systemctl stop apache2.service
systemctl enable apache2.service
```

### Old PC (Pre-2015) Service Management
```sh
chkconfig --list
chkconfig --level 3 httpd on  # Enable Apache at runlevel 3
chkconfig --level 3 httpd off
chkconfig httpd on / off  # Enable/Disable services
```

### List Upstart Services
```sh
initctl list
```

### Interactive Service Management Tool
```sh
chkservice
```

---
This guide provides a detailed overview of network enumeration, system monitoring, and service management in Linux environments.



