
# How to Install and Use UFW (Uncomplicated Firewall)

This guide provides instructions on installing and using UFW (Uncomplicated Firewall) on a Debian-based Linux system such as Kali Linux.

## Installation

1. **Update Package Repositories**:
   ```bash
   sudo apt update
   sudo apt install ufw
   ```

2. To enable and disable the firewall also Check Firewall Status:
- sudo ufw enable
- sudo ufw disable
- sudo ufw status
   
3. Allow Incoming SSH Connections and Allow Other Services:
- sudo ufw allow ssh
- sudo ufw allow service_name
   - sudo ufw allow 53

Deny Incoming Connections:
- sudo ufw deny 1234

To allow only TCP or UDP specifically, you can use:
- sudo ufw allow 53/tcp

---