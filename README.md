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
- Access Method: SSH
- Port Tested: 443 (HTTPS)

---

## Recovery Process

### Identifying Public IP
The public IPv4 address of the server was obtained from the Hetzner Cloud Console. 
This address was used for SSH access and external connectivity validation.

### SSH Key Generation
An SSH key pair was generated. The public key was uploaded to Hetzner, 
while the private key was securely stored locally for authentication.

### Enabling Rescue Mode
The Rescue System was activated from the Hetzner panel. 
The server was rebooted into a temporary recovery environment to restore access.

### Mounting the Main System
The primary disk partition of the original operating system was mounted 
inside the rescue environment to access and modify system files.

### Restoring SSH Access
A secure SSH key-based authentication setup was configured manually 
inside the original system. After rebooting, access via SSH key was successfully restored.

---

## Service Validation

After restoring access, the server booted into the main Ubuntu system. 
The service was verified to be active, enabled, and running correctly. 
It was confirmed that the application was properly bound to port 443 
and listening for incoming connections.

System logs were reviewed to ensure there were no critical runtime errors.

---

## External Port Validation

External connectivity was tested from a local machine to confirm 
that port 443 was publicly accessible. The successful connection 
confirmed that the service was reachable from the internet 
and not blocked by firewall or network restrictions.

---

## Final Result

- SSH access successfully restored
- Server operating in normal mode
- Service running and enabled
- Port 443 publicly accessible
- No critical errors detected

---

## Skills Demonstrated

- Linux system recovery
- Cloud infrastructure troubleshooting
- SSH key-based authentication configuration
- Service validation and monitoring
- Network accessibility verification
- Secure server configuration
"""
