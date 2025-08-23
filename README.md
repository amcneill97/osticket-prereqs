<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Installation (post prerequisite completion)</h1>

This tutorial outlines the installation process for the osTicket help desk ticketing system.<br />

While not required, a virtual machine is helpful if:

You want to isolate osTicket from your host OS.

You're testing or developing in a sandboxed environment.

You’re deploying in a larger infrastructure that uses virtualization or cloud.

### Operating System
- Windows 10 (21H2)

### List of Prerequisites
- Apache Web Server (via XAMPP or manual install)
- PHP 8.0 or 8.1 with required extensions:
  - `mysqli`, `gd`, `imap`, `mbstring`, `intl`, `json`, `xml`, `fileinfo`, `openssl`, `phar`, `curl`
- MySQL 5.5+ (or MariaDB 10.0+)
- osTicket installation files (from [osTicket.com](https://osticket.com/download))


<h2>Installation Steps</h2>
⚠️ This guide assumes that a web server (e.g., Apache or IIS), PHP 8.0/8.1, and MySQL are already installed and configured on the system.

1. **Download osTicket**
   - Go to [https://osticket.com/download](https://osticket.com/download).
   - Download the latest **osTicket Core (Self-Hosted)** zip file.
   - Extract the zip and copy all contents from the `upload/` folder to:
     ```
     C:\xampp\htdocs\osticket\
     ```
     <img width="810" height="143" alt="image" src="https://github.com/user-attachments/assets/d0e8000a-f339-4c13-bfdc-4fabfd74fd44" />


2. **Enable PHP Extensions**
   - Open `C:\xampp\php\php.ini` in a text editor.
   - Uncomment (remove the `;` from) the following extensions if they are commented out:
     ```ini
     extension=mysqli
     extension=gd
     extension=imap
     extension=mbstring
     extension=intl
     extension=json
     extension=xml
     extension=fileinfo
     extension=openssl
     extension=phar
     extension=curl
     ```
   - Save the file and **restart Apache** in XAMPP Control Panel.

3. **Create MySQL Database**
   - Open your browser and visit: `http://localhost/phpmyadmin`
   - Click the **Databases** tab.
   - Create a new database (e.g., `osticket`).
   - Optional: Create a MySQL user and assign full privileges to the new database.

4. **Run the Web Installer**
   - In your browser, go to: `http://localhost/osticket/`
   - Follow the installation wizard:
     - Set site name, default email, and admin credentials.
     - Enter the database name (`osticket`), username, and password.
     - Complete the installation.

5. **Post-Installation Cleanup**
   - Delete the `/setup` directory:
     ```
     C:\xampp\htdocs\osticket\setup
     ```
   - Ensure the config file is writable:
     ```
     C:\xampp\htdocs\osticket\include\ost-config.php
     ```
     (In Windows, this is usually already writable.)

6. **Access Your Helpdesk**
   - Go to: `http://localhost/osticket/`
   - Log in using the admin credentials you created during installation.
