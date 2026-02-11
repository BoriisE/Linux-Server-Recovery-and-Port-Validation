# Linux-Server-Recovery-and-Port-Validation
## Project Overview

This project demonstrates a complete recovery cycle of a Linux cloud server hosted on Hetzner.
The objective was to restore SSH access using Rescue Mode, configure secure SSH key-based authentication,
verify service operation, and validate external port accessibility.

---

## Infrastructure

- Cloud Provider: Hetzner Cloud
- Server Type: CPX22
- Operating System: Ubuntu 22.04
- Access Method: SSH (PuTTY)
- Port Tested: 443 (HTTPS)

---

## Recovery Steps

### 1. Identifying Public IP
Checked networking configuration in Hetzner Console to obtain the public IPv4 address used for SSH access and validation.

### 2. SSH Key Generation
Generated an SSH key pair using PuTTYgen.
Uploaded the public key to Hetzner and stored the private key locally.

### 3. Enabling Rescue Mode
Activated Rescue System in Hetzner.
Performed a power cycle and logged into the rescue environment as root.

### 4. Mounting the Main System
Mounted the main disk partition:

lsblk
mount /dev/sda1 /mnt

Accessed the original filesystem structure.

### 5. Restoring SSH Access
Created SSH directory and authorized_keys file:

mkdir -p /mnt/root/.ssh
touch /mnt/root/.ssh/authorized_keys
chmod 600 /mnt/root/.ssh/authorized_keys

Inserted the public SSH key and rebooted the server.

Result: SSH access restored via key-based authentication.

---

## Service Validation

Checked service status:

systemctl status <service-name>

Verified listening port:

ss -tulpn | grep 443

Checked service logs:

journalctl -u <service-name> -f

---

## External Port Validation

From local machine (PowerShell):

Test-NetConnection <SERVER_IP> -Port 443

Result:
TcpTestSucceeded : True

Confirmed that port 443 is publicly accessible.

---

## Final Result

- SSH access successfully restored
- Server booted into normal mode
- Service running and enabled
- Port 443 publicly accessible
- No critical errors in logs

---

## Skills Demonstrated

- Linux system recovery
- Disk mounting in rescue environment
- SSH key-based authentication setup
- systemd service management
- Network socket inspection
- External connectivity validation
- Cloud infrastructure troubleshooting
"""
