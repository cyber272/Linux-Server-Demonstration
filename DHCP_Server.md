
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
