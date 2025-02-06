# User Home Directory Enumeration

## Introduction
User Home Directory Enumeration involves systematically listing and exploring the contents of user directories in a Linux system to gather information about files, configurations, and potentially sensitive data.

---
## Steps for User Home Directory Enumeration

### List Contents of the Root Directory

This command provides a detailed recursive listing of all files and directories in the `/root` directory:

```bash
$ ls -ahlR /root/

## List Contents of the Home Directory

**To list all user directories under `/home`, showing files and directories recursively with detailed information:**

```sh
$ ls -ahlR /home/

## List Other Users' Home Directories

**To list the contents of the root directory and other users' home directories:**

```sh
$ ls -ahlR /root/; ls -ahlR /home/

## Examine Specific User Directories

**For each user, navigate into their home directory and list the contents:**

```sh
$ ls -ahlR /home/infosec
