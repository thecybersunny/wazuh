# Wazuh SIEM Installation on VirtualBox

## What is Wazuh?

[Wazuh Official Website](https://wazuh.com/?utm_source=chatgpt.com)

Wazuh is an open-source SIEM and XDR platform used for:

* Security Monitoring
* Threat Detection
* Log Analysis
* File Integrity Monitoring
* Vulnerability Detection
* Incident Response

---

# Lab Requirements

### Host Machine

* Windows 10/11
* 8 GB RAM minimum
* 50 GB free disk space

### Software

* [VirtualBox](https://www.virtualbox.org/?utm_source=chatgpt.com)
* Ubuntu Server 22.04 LTS ISO
* Internet Connection

---

# Create Virtual Machine

### VM Configuration

| Setting | Value           |
| ------- | --------------- |
| Name    | Wazuh           |
| OS      | Ubuntu (64-bit) |
| RAM     | 4096 MB         |
| CPU     | 2 Core          |
| Disk    | 50 GB           |

---

# Ubuntu Update

```bash
sudo apt update
sudo apt upgrade -y
```

---

# Install Wazuh (All-in-One)

Official quick-start installation:

```bash
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh

sudo bash ./wazuh-install.sh -a
```

The installer automatically installs:

* Wazuh Server
* Wazuh Indexer
* Wazuh Dashboard
* Filebeat

After installation, Wazuh displays the dashboard URL and generated credentials. ([Wazuh Documentation][1])

---

# Check Services

```bash
sudo systemctl status wazuh-manager

sudo systemctl status wazuh-indexer

sudo systemctl status wazuh-dashboard

sudo systemctl status filebeat
```

---

# Find Server IP

```bash
ip a
```

Example:

```bash
192.168.1.100
```

Open:

```text
https://192.168.1.100
```

in your browser. ([Wazuh Documentation][2])

---

# Get Dashboard Username and Password

The installation script generates credentials automatically.

Default username:

```text
admin
```

To display saved passwords:

```bash
sudo tar -O -xvf wazuh-install-files.tar \
wazuh-install-files/wazuh-passwords.txt
```

This prints all generated passwords. ([Wazuh Documentation][2])

---

# VirtualBox Useful Commands

### Check IP Address

```bash
ip a
```

### Check Network Connectivity

```bash
ping google.com
```

### Restart Networking

```bash
sudo systemctl restart NetworkManager
```

### Reboot VM

```bash
sudo reboot
```

### Shutdown VM

```bash
sudo shutdown now
```

### Check Running Services

```bash
systemctl --type=service --state=running
```

### Check Disk Usage

```bash
df -h
```

### Check Memory

```bash
free -h
```

### Check CPU Information

```bash
lscpu
```

---

# Access Wazuh Dashboard

Open browser:

```text
https://<SERVER_IP>
```

Login:

```text
Username: admin
Password: <generated_password>
```

The credentials are shown after installation and stored in `wazuh-passwords.txt`. ([Wazuh Documentation][2])

---

# Security Recommendation

After first login, change the default/generated passwords and create separate users for administration and monitoring. Wazuh recommends updating credentials after deployment. ([Wazuh Documentation][3])

---

# Repository Structure

```text
wazuh-cyber-tools/
│
├── README.md
├── screenshots/
├── installation-guide/
├── virtualbox-setup/
├── commands/
└── docs/
```

## Screenshots to Add

* VirtualBox VM Settings
* Ubuntu Installation
* Wazuh Installation Terminal
* Dashboard Login Page
* Agent Management Page
* Security Events Dashboard

This will make the repository look professional for cybersecurity portfolios and SOC analyst projects.

[1]: https://documentation.wazuh.com/current/quickstart.html?utm_source=chatgpt.com "Quickstart · Wazuh documentation"
[2]: https://documentation.wazuh.com/current/installation-guide/wazuh-dashboard/installation-assistant.html?utm_source=chatgpt.com "Installing the Wazuh dashboard using the assisted installation method"
[3]: https://documentation.wazuh.com/current/deployment-options/offline-installation/step-by-step.html?utm_source=chatgpt.com "Install Wazuh components step by step - Offline installation guide"
