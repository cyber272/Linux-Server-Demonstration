### To install and configure a DNS server on your Kali Linux system (with IP address 10.0.2.7)

---
### Step 1: Install BIND
- sudo apt update
- sudo apt update
- sudo apt install bind9 bind9utils 
- To view your IP address using the (`ifconfig`) command,

![Screenshot 2024-04-13 at 14.39.25.png](..%2F..%2F..%2FDownloads%2FScreenshot%2FScreenshot%202024-04-13%20at%2014.39.25.png)

### Step 2: Configure BIND
1. Edit named.conf.options:
   - sudo nano /etc/bind/named.conf.options

options {
    directory "/var/cache/bind";

    forwarders {
        8.8.8.8;  // Google DNS
        8.8.4.4;  // Google DNS
    };

    listen-on port 53 { any; }; // Listen on all interfaces
    allow-query { any; };      // Allow queries from any IP address
};

2. Edit named.conf.local:
   - sudo nano /etc/bind/named.conf.local

![Screenshot 2024-04-13 at 13.43.11.png](..%2F..%2F..%2FDownloads%2FScreenshot%2FScreenshot%202024-04-13%20at%2013.43.11.png)

### Stop 3: Create Zone Files:
1. sudo nano /etc/bind/db.library.com. forward zones.

![Screenshot 2024-04-13 at 13.39.29.png](..%2F..%2F..%2FDownloads%2FScreenshot%2FScreenshot%202024-04-13%20at%2013.39.29.png)

2. sudo nano /etc/bind/db.2.0.10. reverse zones.

![Screenshot 2024-04-13 at 13.39.01.png](..%2F..%2F..%2FDownloads%2FScreenshot%2FScreenshot%202024-04-13%20at%2013.39.01.png)

### **Step 4: Restart BIND**
- sudo systemctl restart named
- sudo systemctl start bind9
- sudo systemctl enable bind9
- you have to install and enable (`ufw`) if you don't installed already 
  - sudo ufw status
  - sudo ufw enable 
  - sudo ufw allow bind9
  - sudo ufw reload
  - sudo ufw status
  ![Screenshot 2024-04-13 at 14.32.27.png](..%2F..%2F..%2FDownloads%2FScreenshot%2FScreenshot%202024-04-13%20at%2014.32.27.png)
- sudo systemctl status named.

![Screenshot 2024-04-13 at 12.48.19.png](..%2F..%2F..%2FDownloads%2FScreenshot%2FScreenshot%202024-04-13%20at%2012.48.19.png)

- nslookup library.com 10.0.2.7

![Screenshot 2024-04-13 at 13.30.03.png](..%2F..%2F..%2FDownloads%2FScreenshot%2FScreenshot%202024-04-13%20at%2013.30.03.png)

- dig library.com

![Screenshot 2024-04-13 at 13.28.38.png](..%2F..%2F..%2FDownloads%2FScreenshot%2FScreenshot%202024-04-13%20at%2013.28.38.png)

And voilà! Congratulation, You have configured the DNS server.
