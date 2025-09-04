<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# ✅ osTicket Installation Guide

This guide shows you how to install **osTicket v1.15.8** along with its prerequisites for lab/testing purposes on **Windows 10 (21H2)**.

---

## 📁 1. Prepare the Installation Files

- Download and extract `osTicket-Installation-Files.zip`
  
- Extract the file to your **Desktop**
   
- The folder should be named: `C:\Users<YourUsername>\Desktop\osTicket-Installation-Files`

---

## 🌐 2. Install IIS with CGI

- Open `Control Panel` → `Programs` → `Turn Windows features on or off`
  
- Enable the following:
   - `Internet Information Services`
   - `World Wide Web Services`
   - `Application Development Features`
   - `[X] CGI`

    <p></p>

    <img width="191" height="170" alt="Image" src="https://github.com/user-attachments/assets/affb4339-163c-44eb-aeca-ce90f4464aa3" />


---

## 🧩 3. Install Required Components

 From the `osTicket-Installation-Files` folder:

  - **Install PHP Manager for IIS**
    
 File: `PHPManagerForIIS_V1.5.0.msi`

  - **Install URL Rewrite Module**
   
 File: `rewrite_amd64_en-US.msi`

  <p></p>

   
  <img width="318" height="178" alt="Image" src="https://github.com/user-attachments/assets/5869ca90-e257-40f7-bf3b-0e76c7688026" />

  
  - **Create PHP Directory:** `C:\PHP` 

  - **Unzip PHP 7.3.8**  ~~ <img width="119" height="11" alt="Image" src="https://github.com/user-attachments/assets/88bb06ac-46a0-42e8-b538-790dba4f58ff" />

  File: `php-7.3.8-nts-Win32-VC15-x86.zip`

  - Extract into: `C:\PHP`
  

- **Install 'Visual C++ Redistributable'**
     
- File: `VC_redist.x86.exe`

- **Install 'MySQL 5.5.62'**
   
- File: `mysql-5.5.62-win32.msi`
  
- Use `Typical Setup`
  
- After installation, run the `MySQL Configuration Wizard`
  
- Choose: `Standard Configuration`
  - Set username: `root`
  - Set password: `root`

---

## ⚙️ 4. Configure IIS and PHP

- Open `IIS Manager` as Administrator

- Register PHP with IIS: 
   - Click your server name
   - Open `PHP Manager`
   - Click: `Register new PHP version`
   - Path:  `C:\PHP\php-cgi.exe`

    <p></p>

  <img width="332" height="271" alt="Image" src="https://github.com/user-attachments/assets/106d3d73-476a-4005-aff1-e72122c07e5e" />

- Reload IIS:
  - Click `IIS Manager`:
  - Right-click your server → click `Stop`
  - Then `Start`

---

## 📦 5. Install osTicket v1.15.8

- From `osTicket-Installation-Files` folder, unzip: `osTicket-v1.15.8.zip`

- Copy the `upload` folder to: `C:\inetpub\wwwroot\`

     <img width="206" height="76" alt="Image" src="https://github.com/user-attachments/assets/c9ac6a40-014e-41a9-b2f3-44f25a1f6f3c" />

- Rename: `C:\inetpub\wwwroot\upload` → `C:\inetpub\wwwroot\osTicket`


- Reload IIS again 

  - Click `Start` → `Stop`

---

## 🌍 6. Launch osTicket in Browser

- Click `IIS Manager`
  
- Expand `Sites` → `Default Web Site` → `osTicket`
  
- On the right, click: `Browse *:80 (http)`

  <img width="428" height="206" alt="Image" src="https://github.com/user-attachments/assets/96f526ac-4415-4e49-90a6-873079901159" />

   *In the browser, you’ll see some missing PHP extensions**

---

## 🧠 7. Enable Missing PHP Extensions

- Click `IIS Manager`
  
- Go to: `Sites` → `Default Web Site` → `osTicket`
  
- Double-click `PHP Manager`
  
- Click: `Enable or disable an extension`

  <img width="189" height="79" alt="Image" src="https://github.com/user-attachments/assets/e3c6b456-0be0-4bc5-8c31-2073c81b84d5" />


- Enable the following:
   - `php_imap.dll`
   - `php_intl.dll`
   - `php_opcache.dll`

- Refresh the osTicket browser page to verify changes

---

## 📝 8. Rename the Configuration File

- Rename From:
`C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`

- To:
`C:\inetpub\wwwroot\osTicket\include\ost-config.php`


---

## 🔒 9. Set Permissions on the Configuration File

- Right-click `ost-config.php` → `Properties` → `Security`
  
- Click `Advanced`
  
- Click `Disable inheritance` → `Remove all entries`

    <img width="353" height="239" alt="Image" src="https://github.com/user-attachments/assets/a1ecc6dd-a472-4ddc-9169-df179e748551" />

   
- Add new permission:
   - User: `Everyone`
   - Permission: `Full Control`
  


---

## 🛠️ 10. Continue osTicket Setup in Browser

- Back in your browser, click `Continue`
  
- Fill out:
   - `Helpdesk Name`
   - `Default email address` (used to receive tickets)
     
    <p>
    <img width="368" height="119" alt="Image" src="https://github.com/user-attachments/assets/8841956c-7557-4e36-955a-6b04ef177e77" />

---

## 🗄️ 11. Create MySQL Database using HeidiSQL

- Install `HeidiSQL` from the `osTicket-Installation-Files` folder
  
- Open `HeidiSQL`

  <img width="317" height="221" alt="Image" src="https://github.com/user-attachments/assets/83d83473-5319-4ec8-a21f-d77d08f3249b" />

- Create a new session:
   - Username: `root`
   - Password: `root`
     
- Click `Connect`
  
- Click `Create a database`


---

## 🧪 12. Complete Web Installer

- Return to the **'osTicket web setup'**
   
- Use:
  - **Database Name:** `osTicket`
  - **Username:** `root`
  - **Password:** `root`

  <p></p>
  <img width="371" height="167" alt="Image" src="https://github.com/user-attachments/assets/b25a48fa-eb25-46b1-a147-aef3ec5db328" />

  
- Click `Install Now`

---

## 🎉 13. Final URLs

- Admin Panel: http://localhost/osTicket/scp/login.php
  
- End User Ticket Portal: http://localhost/osTicket/

## 🧹 14. Cleanup

- **Delete setup folder:**
  
  `C:\inetpub\wwwroot\osTicket\setup`

- **Set permissions to "Read" only on:** `C:\inetpub\wwwroot\osTicket\include\ost-config.php`

✅ **Tutorial Completed** ~~ osTicket is now fully installed, configured, and ready to use!
