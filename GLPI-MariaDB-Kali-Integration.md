### Setting up an internal website running GLPI with HTTP (Apache) and MariaDB.

---
### Step 1: Install Required Software.
1. Install Apache (HTTP Server):
  ```bash
  sudo apt update
  sudo apt install apache2
  ```
-  debug:
  ```bash
  sudo apache2ctl configtest
  ``` 

2. Install MariaDB (Database Server):
  ```bash
  sudo apt install mariadb-server mariadb-client
  sudo mysql_secure_installation
  ```
3. Install PHP and necessary PHP modules:
```bash
  sudo apt install php libapache2-mod-php php-mysql php-{cli,curl,gd,imap,json,ldap,mbstring,xml,xmlrpc,zip}
  ```
--- 

### Step 2: Configure MariaDB.
1. Secure MariaDB Installation:
   - Follow the prompts to set the root password, remove anonymous users, disallow remote root login, and remove test databases.
     - After installation, secure your MariaDB installation:
  ```bash
   sudo mysql_secure_installation
  ```
  ```bash
   sudo systemctl  status mariadb
  ```
  ![Screenshot 2024-04-13 at 19.45.34.png](..%2F..%2F..%2FDownloads%2FScreenshot%2FScreenshot%202024-04-13%20at%2019.45.34.png)

2. Create Database and User for GLPI:
- Log in to MariaDB as the root user.
  ```bash    
  sudo mysql -u root -p
  ```
- Create a new database for GLPI.
  ```
    CREATE DATABASE glpidb CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
    CREATE USER 'glpiuser'@'localhost' IDENTIFIED BY 'your_password_here';
    GRANT ALL PRIVILEGES ON glpidb.* TO 'glpiuser'@'localhost';
    FLUSH PRIVILEGES;
    EXIT;
  ```

### Step 3: Download and Install GLPI.
1. Download GLPI:
- Navigate to the GLPI website and download the latest stable version.
  - cd /var/www/html
  ```bash
  sudo wget https://github.com/glpi-project/glpi/releases/download/10.0.12/glpi-10.0.12.tgz
  ```
  - Extract the downloaded archive:
  ```bash
  sudo tar -xvf glpi-10.0.12.tgz
  ``` 
- Adjust ownership and permissions:
  ```bash
  sudo chown -R www-data:www-data /var/www/html/glpi
  sudo chmod -R 755 /var/www/html/glpi
  ```
### **Step 4: Configure Apache**  
- Enable the rewrite module for Apache.
  ```bash
  sudo a2enmod rewrite
  ````
- Create a new virtual host configuration file for GLPI:
  ```bash
    sudo nano /etc/apache2/sites-available/glpi.conf
    ``` 
  - Add the following configuration:
  ```
  <VirtualHost *:80>
        ServerAdmin admin@example.com
        DocumentRoot /var/www/html/glpi
        ServerName your_domain_or_IP
    
        <Directory /var/www/html/glpi/>
            Options FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>
    
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>
  ```
- Replace `your_domain_or_IP` with your actual domain name or server IP address.
- Enable the virtual host and Apache rewrite module:
    ```bash
    sudo a2ensite glpi.conf 
    sudo a2enmod rewrite
    sudo systemctl restart apache2
    ```
  ![Screenshot 2024-04-13 at 19.21.53.png](..%2F..%2F..%2FDownloads%2FScreenshot%2FScreenshot%202024-04-13%20at%2019.21.53.png)
---

### **Step 5: Complete Installation** 
- Open a web browser and navigate to `http://your_domain_or_IP/glpi/` to complete the installation process.
  - Follow the on-screen instructions to configure GLPI with the database credentials you created earlier.
![Screenshot 2024-04-14 at 13.45.11.png](..%2F..%2F..%2FDownloads%2FScreenshot%2FScreenshot%202024-04-14%20at%2013.45.11.png)

  ```bsh
  sudo rm -rf /var/www/html/glpi/installer
  ```
- That's it! GLPI should now be installed and accessible via your web browser. You can log in with the default credentials (username: `glpi`, password: `glpi`). Remember to change the default password after logging in for the first time.
- This step-by-step guide for setting up GLPI on a Linux system.
- Adjust paths and configurations as necessary based on your specific environment and requirements.