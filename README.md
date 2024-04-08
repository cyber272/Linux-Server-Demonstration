# Linux Server Demonstration

This project showcases the setup and configuration of a Linux server and workstation to demonstrate essential services and functionalities for a local library considering a migration to Linux.

## Project Overview

The goal of this project is to demonstrate the capabilities and reliability of Linux by setting up a server and workstation using virtual machines. The server will provide DHCP, DNS, HTTP, and MariaDB services hosting an internal website (GLPI), while the workstation will feature a desktop environment with essential applications.

## Server Setup

- **DHCP Service:** Configured using `isc-dhcp-server` to provide automatic IP addressing to network clients.
- **DNS Service:** Implemented with `bind` for resolving internal resources and redirecting external resources.
- **HTTP and MariaDB:** Setup to host an internal website (GLPI) using `Apache` and `MariaDB`.
- **Weekly Backup:** Configuration files for each service are backed up weekly into a single compressed archive.
- **Remote Manageability:** SSH access enabled for remote management of the server.

## Workstation Setup

- **Desktop Environment:** Installed with a Linux desktop environment for user interaction.
- **Applications:** Includes essential applications like LibreOffice, GIMP, and Mullvad browser.
- **Automatic Addressing:** Workstation configured for automatic IP addressing.
- **Partition Setup:** `/home` folder located on a separate partition on the same disk for data separation.

## Optional Configurations

- **Backup Placement:** Backup stored on a separate disk partition, mounted for backup and unmounted afterward.
- **Remote User Assistance:** Proposal and implementation of a solution for remote user assistance.

## Performance Criteria

- **Presentation:** Confident demonstration of functionality.
- **Documentation:** Clear, structured documentation covering all configuration elements.
- **Implementation:** Successful setup of all required and optional items.
- **Organization:** Demonstrated planning and organization throughout the project.
- **Testing:** Procedures conducted to ensure functionality and reliability.
- **Knowledge:** Solid understanding of Linux environment exhibited during Q&A.

## Documentation Outline

1. **Server Setup**
   - Installation and configuration of DHCP, DNS, HTTP, and MariaDB services.
   - Weekly backup configuration and SSH remote manageability setup.

2. **Workstation Setup**
   - Installation of desktop environment and essential applications.
   - Automatic addressing configuration and partition setup for `/home`.

3. **Optional Configurations**
   - Backup placement on a separate disk partition.
   - Proposal and implementation of remote user assistance solution.

4. **Testing Procedures**
   - Description of testing procedures conducted for each service.
   - Results and verification of service functionality.


5. **Q&A Preparation**
   - List of potential questions and answers, along with additional resources.

## Conclusion

This project aims to demonstrate the feasibility and functionality of Linux for the local library's IT needs. By showcasing the setup and configuration of essential services on the server and workstation, we aim to provide a reliable and convincing solution for migrating to Linux.

---
---

# DHCP Server Configuration on Kali Linux

This guide outlines the steps to install and configure a DHCP (Dynamic Host Configuration Protocol) server on Kali Linux.

## Installation

1. **Update Package Lists**:
   Ensure your package list is up-to-date before installing the DHCP server:
   ```bash
   sudo apt update
   ```

2. **Install DHCP Server (`isc-dhcp-server`)**:
   Use the following command to install the DHCP server package:
   ```bash
   sudo apt install isc-dhcp-server
   ```

## Configuration

1. **Edit DHCP Configuration File**:
2. Run ip Command:
To view detailed information about your network interfaces, use:

- ifconfig 
- ip addr show
  
<img width="1533" alt="Screenshot 2024-04-08 at 08 54 15" src="https://github.com/cyber272/Linux-Server-Demonstration/assets/155965877/c0334d5d-e7b1-45ed-b773-482f002908eb">

   Edit the DHCP server configuration file `/etc/dhcp/dhcpd.conf` to define your DHCP settings. Use a text editor (e.g., `nano`, `vim`) to open the file:
   ```bash
   sudo vim /etc/dhcp/dhcpd.conf
   ```
   <img width="1533" alt="Screenshot 2024-04-08 at 08 58 12" src="https://github.com/cyber272/Linux-Server-Demonstration/assets/155965877/64593a0a-b6cb-4139-b273-ea6514b3dc69">


Edit the DHCP server defaults file:

sudo nano /etc/default/isc-dhcp-server
   
<img width="1533" alt="Screenshot 2024-04-08 at 08 57 19" src="https://github.com/cyber272/Linux-Server-Demonstration/assets/155965877/c5bac0e2-10cb-4014-a469-617a2a4daaea">

4. **Start and Enable DHCP Server**:
   Start and enable the DHCP server service to apply the configuration changes:
   ```bash
   sudo systemctl start isc-dhcp-server
   sudo systemctl enable isc-dhcp-server
   sudo systemctl restart isc-dhcp-server
   ```

## Verification

1. **Check DHCP Server Status**:
   Verify that the DHCP server is running without errors:
   ```bash
   sudo systemctl status isc-dhcp-server
   ```
<img width="1533" alt="Screenshot 2024-04-08 at 08 46 10" src="https://github.com/cyber272/Linux-Server-Demonstration/assets/155965877/d4ec5e48-ba58-4cc7-b896-0657b98d3cdd">



2. **Monitor DHCP Server Logs** (Optional):
   Monitor DHCP server logs for any issues or troubleshooting:
   ```bash
   sudo journalctl -u isc-dhcp-server.service
   ```
<img width="1533" alt="Screenshot 2024-04-08 at 09 08 42" src="https://github.com/cyber272/Linux-Server-Demonstration/assets/155965877/fbca5baf-0fb6-46b8-a9d0-9e109bd7baa4">


Troubleshooting DHCP (Dynamic Host Configuration Protocol)
- sudo systemctl status dhclient
- sudo netsate -anp | grep dhcp  # for see the port of dhcp how lessan to 
	- sudo netsate -tuln | grep :67 

## Additional Notes

- Customize the DHCP configuration (`dhcpd.conf`) based on your network requirements and IP address ranges.
- Ensure that the DHCP server is running on the correct network interface (`INTERFACESv4` in `/etc/default/isc-dhcp-server`).
- Adjust firewall (e.g., `ufw`) rules to allow DHCP traffic (`UDP ports 67` and `68`) if needed.

---
---
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
---




