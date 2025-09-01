<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# ✅ osTicket Installation Guide (IIS, PHP 7.3, MySQL 5.5)

This guide shows you how to install **osTicket v1.15.8** along with its prerequisites for lab/testing purposes on **Windows 10**.

---

## 📁 1. Prepare the Installation Files

- Download and extract the file:  
  `osTicket-Installation-Files.zip`  
- Extract it to your **Desktop**  
- The folder should be named: `C:\Users<YourUsername>\Desktop\osTicket-Installation-Files`

---

## 🌐 2. Install IIS with CGI

1. Open `Control Panel` → `Programs` → `Turn Windows features on or off`
  
2. Enable the following:

   - `Internet Information Services`

   - `World Wide Web Services`

   - `Application Development Features`

   - `[X] CGI`

    <img width="191" height="170" alt="image" src="https://github.com/user-attachments/assets/82b80238-65f2-4c38-9184-68bd8204497a" />


---

## 🧩 3. Install Required Components

From the `osTicket-Installation-Files` folder:

1. **Install PHP Manager for IIS**  
File: `PHPManagerForIIS_V1.5.0.msi`

2. **Install URL Rewrite Module**  
File: `rewrite_amd64_en-US.msi`

    <img width="318" height="178" alt="image" src="https://github.com/user-attachments/assets/57feac8a-5417-4dbf-914c-8a6e4cb98fc7" />


3. **Create PHP Directory:** `C:\PHP` 


4. **Unzip PHP 7.3.8**  ~~ <img width="150" height="15" alt="image" src="https://github.com/user-attachments/assets/43588072-be45-4002-a9c3-5f6a1004305c" />
- File: `php-7.3.8-nts-Win32-VC15-x86.zip`

- Extract into: `C:\PHP`
  

5. **Install 'Visual C++ Redistributable'**  
File: `VC_redist.x86.exe`

6. **Install 'MySQL 5.5.62'**
   
- File: `mysql-5.5.62-win32.msi`
  
- Use `Typical Setup`
  
- After installation, run the `MySQL Configuration Wizard`
  
  - Choose: `Standard Configuration`
  - Set username: `root`
  - Set password: `root`

---

## ⚙️ 4. Configure IIS and PHP

1. Open `IIS Manager` as Administrator

2. Register PHP with IIS:
   
- Click your server name
- Open `PHP Manager`
- Click: `Register new PHP version`
- Path:  `C:\PHP\php-cgi.exe`

  <img width="332" height="271" alt="image" src="https://github.com/user-attachments/assets/f764d6fd-17f2-4436-8536-a1cbbfb05a26" />


3. Reload IIS:
   
  - In `IIS Manager`:
  - Right-click your server → click `Stop`
  - Then `Start`

---

## 📦 5. Install osTicket v1.15.8

1. From `osTicket-Installation-Files` folder, unzip: `osTicket-v1.15.8.zip`

2. Copy the `upload` folder to: `C:\inetpub\wwwroot\`

     <img width="206" height="76" alt="image" src="https://github.com/user-attachments/assets/175d3833-6ecc-4dd7-a4eb-800870e10a0a" />

3. Rename: `C:\inetpub\wwwroot\upload` → `C:\inetpub\wwwroot\osTicket`


4. Reload IIS again 

  - Click `Start` → `Stop`

---

## 🌍 6. Launch osTicket in Browser

1. In `IIS Manager`:
- Expand `Sites` → `Default Web Site` → `osTicket`
- On the right, click: `Browse *:80 (http)`

  <img width="428" height="206" alt="image" src="https://github.com/user-attachments/assets/600175ac-8fcc-4732-ac53-68c2b04c7e3e" />


- In the browser, you’ll see some missing PHP extensions.

---

## 🧠 7. Enable Missing PHP Extensions

1. Click `IIS Manager`:
- Go to: `Sites` → `Default Web Site` → `osTicket`
- Double-click `PHP Manager`
- Click: `Enable or disable an extension`

  <img width="189" height="79" alt="image" src="https://github.com/user-attachments/assets/a2025fde-7cae-4876-9724-ef39b8a884f1" />


2. Enable the following:
- `php_imap.dll`
- `php_intl.dll`
- `php_opcache.dll`

3. Refresh the osTicket browser page to verify changes.

---

## 📝 8. Rename the Configuration File

Rename From:
`C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`

To:
`C:\inetpub\wwwroot\osTicket\include\ost-config.php`


---

## 🔒 9. Set Permissions on the Configuration File

1. Right-click `ost-config.php` → `Properties` → `Security`
2. Click `Advanced`
3. Click `Disable inheritance` → `Remove all entries`

    <img width="353" height="239" alt="image" src="https://github.com/user-attachments/assets/f1d9c2d2-a7fe-4671-af4b-184ae921eb18" />

   
4. Add new permission:
   - User: `Everyone`
   - Permission: `Full Control`
  


---

## 🛠️ 10. Continue osTicket Setup in Browser

1. Back in your browser, click `Continue`
2. Fill out:
   - `Helpdesk Name`
   - `Default email address` (used to receive tickets)

---

## 🗄️ 11. Create MySQL Database using HeidiSQL

1. Install `HeidiSQL` from the `osTicket-Installation-Files` folder
2. Open `HeidiSQL`
3. Create a new session:
   - Username: `root`
   - Password: `root`
4. Connect
5. Click `Create a database`


---

## 🧪 12. Complete Web Installer

1. Return to the **'osTicket web setup'**
   
2. Use:
   
- **Database Name:** `osTicket`
- **Username:** `root`
- **Password:** `root`
  
3. Click `Install`

---

## 🎉 13. Final URLs

- Admin Panel: http://localhost/osTicket/scp/login.php
- End User Ticket Portal: http://localhost/osTicket/

## 🧹 14. Cleanup

1. **Delete setup folder:**
`C:\inetpub\wwwroot\osTicket\setup`

2. **Set permissions to "Read" only on:** `C:\inetpub\wwwroot\osTicket\include\ost-config.php`

✅ **Done!** Your osTicket helpdesk is now fully installed, configured, and ready to use.
