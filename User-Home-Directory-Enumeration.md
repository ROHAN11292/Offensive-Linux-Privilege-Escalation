# User Home Directory Enumeration

## Introduction
User Home Directory Enumeration involves systematically listing and exploring the contents of user directories in a Linux system to gather information about files, configurations, and potentially sensitive data.

---
## Steps for User Home Directory Enumeration

### List Contents of the Root Directory

**This command provides a detailed recursive listing of all files and directories in the `/root` directory:**
```bash
$ ls -ahlR /root/
```

## List Contents of the Home Directory

**To list all user directories under `/home`, showing files and directories recursively with detailed information:**
```bash
$ ls -ahlR /home/
```

## List other users home directories
```bash
$ ls -ahlR /root/; ls -ahlR /home/
```

## Examine Specific User Directories:

**For each user, navigate into their home directory and list the contents:**
```bash
$ ls -ahlR /home/infosec
		
$ cd /home/infosec
		
$ ls -alh
```
## Common Targets During Enumeration:

**Configuration Files:**

```bash
.bashrc, .bash_profile, .profile       –    Shell configurations.

.ssh/                                  –    SSH keys and configuration files.

.gitconfig                             –    Git configuration.
				
.vimrc, .tmux.conf, .screenrc          –   Configurations for Vim, Tmux, and Screen.
			
.gitconfig, .git-credentials           –     Git settings and potentially stored credentials.
```
```bash
$ cat ~/.bashrc
				
$ cat ~/.bash_profile
				
$ cat ~/.zshrc
```

**User bash history:**

```bash
$ cat ~/.bash_history; cat ~/.nano_history; cat ~/.atftp_history; cat ~/.mysql_history; cat ~/.php_history
```

**User mails:**

```bash
$ cat ~/.bashrc; cat ~/.profile; cat /var/mail/root; cat /var/spool/mail/root
```
**Command History:**

```bash
.bash_history          –        History of executed bash commands.

.mysql_history   	     –        History of executed MySQL commands.
```

**Sensitive Data Files:**

```bash
.ssh/id_rsa             –           Private SSH keys.

id _rsa_bee             –           Custom or renamed SSH keys.
```

**Application Data:**
```bash
.mozilla/firefox/                         –      Firefox user profiles and data.

.config/google-chrome/                    –      Google Chrome user data.
			
.config/filezilla/                        –      FileZilla configuration and saved sites.

.putty/  or  .putty/sessions/             –      PuTTY session configurations.

.thunderbird/ or .mozilla-thunderbird/    –      Thunderbird email client data.
```

### Firefox and Thunderbird Decryption: Use tools like `firefox_decrypt` or `Dumpzilla` to extract saved passwords and other data from Firefox and Thunderbird profiles.

- https://github.com/unode/firefox_decrypt
		
- http://www.dumpzilla.org/

**Authentication and Credentials:**

- SSH Keys: Private and public SSH keys, which could allow unauthorized access if compromised.
```bash
$ cat ~/.ssh/id_rsa

$ cat ~/.ssh/id_rsa.pub
```

- GPG/PGP Keys: GPG private and public keys, which are used for encrypting and signing data.
```bash
$ ls -alh ~/.gnupg/
```
**Network and Connection Details: VPN Client configuration and Credentials.**

- VPN Configurations:
```bash
$ ls -alh ~/.vpn/

$ cat ~/.openvpn/client.conf
```

- Proxy Settings: Custom proxy configurations for applications or environments.
```bash
$ cat ~/.proxy_config
```

**Database Configurations: PostgreSQL password file storing credentials.**

- MySQL/MariaDB: MySQL client configuration, often containing credentials for database access.
```bash
$ cat ~/.my.cnf
```

- PostgreSQL: PostgreSQL password file  storing credentials.
```bash
$ cat ~/.pgpass
```

**Cloud Services and API Keys:**

- AWS Credentials: AWS access keys and secret keys.
```bash
$ cat ~/.aws/credentials
```

- Azure CLI: Azure authentication details.
```bash
$ cat ~/.azure/credentials
```

- Google Cloud SDK: Google Cloud Platform service account credentials.
```bash
$ cat /.config/gcloud/credentials.json
```

**Email and Communication Clients: Profiles containing email settings and stored credentials.**

- Thunderbird/Outlook/Other Email Clients:
```bash
$ cd ~/.thunderbird/

$ cd ~/.mozilla-thunderbird/
```

- Messaging Apps (Slack, Zoom, etc.): Configuration files and session data for communication apps.
```bash
$ ls -alh ~/.config/slack/

$ ls -alh ~/.config/zoom/
```

**Development and Build Systems:**

- Docker Configurations: Docker CLI configuration, including credentials for Docker Hub or other registries.
```bash
$ cat ~/.docker/config.json
```

- Kubernetes Configurations: Kubernetes configuration files containing cluster access information.
```bash
$ cat ~/.kube/config
```

- Ansible: Configuration for Ansible automation tool, often with sensitive details.
```bash
$ cat ~/.ansible.cfg
```

**Virtualization and Containerization:**

- VirtualBox VMs: Virtual machine configurations and disk images.
```bash
$ ls -alh ~/VirtualBox\ VMs/
```

- Docker Compose Files:
```bash			
$ ls -alh ~/docker-compose.yml
```

**Web Browsers and Credentials:**

- Browser Extensions: Installed browser extensions, which may have sensitive data or functionality.
```bash		
$ ls -alh ~/.mozilla/firefox/xxxxxxxx.default/extensions/
```

- Browser Cache and Cookies: Cookies and cached data that could contain session tokens or sensitive information.
```bash		
$ ls -alh ~/.mozilla/firefox/xxxxxxxx.default/cookies.sqlite

$ ls -alh ~/.config/google-chrome/Default/Cookies
```

**Miscellaneous Files:**

- Backup Files: Backup files often contain older versions of configurations or sensitive data.
```bash
$ ls -alh ~/*.bak

$ ls -alh ~/*.old
```

- Custom Scripts: User - defined scripts which might have automtion routines or sensitive logic.
```bash
$ ls -alh ~/bin/
```

- Temporary Files: Temporary files, which may include application caches, logs, or other ephemeral data.
```bash
$ ls -alh /tmp/
```

**Log Files:**
- User-Specific Logs: Logs specific to user sessions and applications.
```bash
$ ls -alh ~/.logs/

$ cat ~/.xsession-errors
```
