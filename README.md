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




Certainly! Below is a README section specifically focusing on DHCP (Dynamic Host Configuration Protocol) setup and configuration for your Kali Linux machine. This guide will help users understand how to install and configure a DHCP server on Kali Linux.

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
   Edit the DHCP server configuration file `/etc/dhcp/dhcpd.conf` to define your DHCP settings. Use a text editor (e.g., `nano`, `vim`) to open the file:
   ```bash
   sudo vim /etc/dhcp/dhcpd.conf
   ```

2. **Sample DHCP Configuration**:
   Configure the DHCP server with a sample configuration.
<img width="1635" alt="Screenshot 2024-04-07 at 13 53 21" src="https://github.com/cyber272/Linux-Server-Demonstration/assets/155965877/059b991e-1e0d-4af7-956e-8fd54434ac22">

3. **Start and Enable DHCP Server**:
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
<img width="1635" alt="Screenshot 2024-04-07 at 13 13 54" src="https://github.com/cyber272/Linux-Server-Demonstration/assets/155965877/7afa81a9-3e7c-42ef-9c16-fd0eb12ca698">

2. **Monitor DHCP Server Logs** (Optional):
   Monitor DHCP server logs for any issues or troubleshooting:
   ```bash
   sudo journalctl -u isc-dhcp-server.service
   ```

## Additional Notes

- Customize the DHCP configuration (`dhcpd.conf`) based on your network requirements and IP address ranges.
- Ensure that the DHCP server is running on the correct network interface (`INTERFACESv4` in `/etc/default/isc-dhcp-server`).
- Adjust firewall (e.g., `ufw`) rules to allow DHCP traffic (`UDP ports 67` and `68`) if needed.

---

Feel free to customize and expand upon this DHCP configuration guide based on your specific network setup and requirements. Save this content into a file named `README.md` within your GitHub repository or documentation for easy reference and sharing.

In the next sections of your README, you can include similar guides for configuring UFW (Uncomplicated Firewall), DNS (Domain Name System), MariaDB (MySQL), and HTTP services on your Kali Linux machine.
