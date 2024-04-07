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
