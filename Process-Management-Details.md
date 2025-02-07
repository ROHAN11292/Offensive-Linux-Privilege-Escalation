# Process Management Commands:
## Introduction
### Process management in privilege escalation is when an attacker takes control of running processes to gain higher permissions, like admin access, on a system.
---
### List All Processes:
- Displays all running processes, including system and user processes, along with details like CPU and memory usage.
```bash
$ps -aux
```

**Filter Processes by User:**

- Processes run by root:
```bash
$ ps -aux | grep root
```

- Processes not run by root:
```bash
$ ps -aux | grep -v root
```

- Process Tree View:
```bash
$ pstree
```

**Shows processes in a hierarchical tree format, which is useful for visualizing parent-child relationships.**

- Detailed Process List: Another way to list processes, providing full format details including PID, PPID, and start time.
```bash
$ ps -ef
```

**Filter Detailed Process List:**

- Processes run by root:
```bash
$ ps -ef | grep root
```
- Processes not run by root:
```bash
$ ps -ef | grep -v root
```

### Real-time Process Monitoring:
- Provides a dynamic, real-time view of system processes, resource usage, and system load.
```bash
$ top

$ htop
```


**Service Management Commands**

- List All Services: Lists all available services with their current status (running, stopped, etc.).
```bash
$ service --status-all
```

- Paginate Service List: Useful for viewing long lists of services in a paginated format.
```bash
$ service --status-all | less
```

- Check Specific Service Status: Checks the status of the apache2 service specifically.
```bash
$ service apache2 status
```
