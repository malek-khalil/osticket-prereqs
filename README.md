<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>Installation of osTicket</h1>
This is a step-by-step tutorial for a help desk ticketing system—in this case, osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Microsoft Remote Desktop (RDP)
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b>

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation files
- Heidi SQL

<h2>Installation Steps</h2>

<p>
To begin, we will create a Virtual Machine using Microsoft Azure (this tutorial assumes that you have an account on Microsoft Azure). The purpose of the VM (virtual machine) is to use a remote computer. We will use the VM to protect our machine from any malfunctions we might encounter, provide a clean slate in case of software conflicts, and facilitate replicating the tutorial. 

  - From the home section of the Azure portal, proceed to create a resource group and name it "osTicket".

![image](https://github.com/user-attachments/assets/67929d78-39f7-4f97-9cb1-2a26ea2e51b3)

</p>
<br />
<p>
  
  - Once that is set up, go to the virtual machine section and create the VM. Set the image to Windows 10 Pro and allocate at least 2-4 CPUs. In this tutorial, we are using 2 CPUs.
  - Create your credential logins, as they will be needed to access the VM.
  
  **IMPORTANT!** Ensure that your virtual machine is in the resource group you just created and the same region.

  ![image](https://github.com/user-attachments/assets/8d53f2d9-5905-4d66-a15a-cfc836b2dd08)

  
 
  - Next, open the search bar and find "Remote Desktop Connection" (RDP). If you are a Mac user, download Microsoft Remote Desktop (RDP).
  - Use the public IP address of your VM (found on the virtual machine page under the "Public IP Address" column in Azure).
  - Use your VM login credentials to access the VM.
</p>
<br />

<p>
  
  ![image](https://github.com/user-attachments/assets/87ee4796-d51c-47de-b868-a146d462c222) 

  - Once connected to your VM, you must enable IIS. In the search bar, access the Control Panel, then select "Uninstall a Program." On the left, select "Turn Windows features on or off." In this list, enable Internet Information Services. Then expand the folder, look for "World Wide Web Services," expand it, look for "Application Development Features," expand it, and enable "CGI." You will need CGI to download the PHP Manager. PHP Manager is a back-end web programming language that allows osTicket to run on a web browser.
  - Once done, press "OK."
    ![image](https://github.com/user-attachments/assets/34afb486-ba19-43b1-adfe-e8789d87b637)

- Now that you have enabled IIS we need to install PHP. IN YOUR VM! Open your browser and use the provided link here: [https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD) That link will provide you with all of the material you need to download to get osTicket up and running.

![image](https://github.com/user-attachments/assets/37176619-20cb-44a1-b570-969a36abd366)

  - Within the link, find "PHPManagerForIIS_V1.5.0.msi" and download it. Install and agree to the terms.
![image](https://github.com/user-attachments/assets/ae9564e6-687b-44e8-8d35-7c1fd2c38472)

  - Return to the link and download "rewrite_amd64_en-US.msi" (the Rewrite Module). Install and agree to the terms.
    ![image](https://github.com/user-attachments/assets/28ba50d9-540d-42e6-8be7-6a7a5f294331)
  - Next, create a PHP directory:
      - Open File Explorer, type "C:" in the search bar, and create a new folder called "PHP."
      - Download "php-7.3.8-nts-Win32-VC15-x86.zip" from the link. Extract the file by right-clicking it and selecting "Extract to the PHP folder" you just created.
![image](https://github.com/user-attachments/assets/05082449-342a-4dac-84ef-64177161f671)
![image](https://github.com/user-attachments/assets/a051be2b-d42a-403a-a03c-a9250d190e2c)
![image](https://github.com/user-attachments/assets/7e7b3436-f2dd-417f-a888-a590f94bf416)

- Back in the link folder, download and install "VC_redist.x86.exe."

![image](https://github.com/user-attachments/assets/d0ba1cf6-c29c-4df7-a533-23c5cb18d2ff)

- Return to the link and download "mysql-5.5.62-win32.msi" (MySQL). For setup, select "Typical Setup," then "Launch Configuration Wizard" after installation.
  Configure with the following:
- Username: root
- Password: root
- Execute the configuration. It should look like this:

![image](https://github.com/user-attachments/assets/89407f0a-a183-4520-9b48-616534aa8a09)

- Open IIS as an Administrator (search for IIS, then right-click and select "Run as Administrator").
- Register PHP in IIS (PHP Manager -> C:\PHP\php-cgi.exe).

![image](https://github.com/user-attachments/assets/9a5a0dae-f98b-4d7b-b1d9-87481a47c70d)
![image](https://github.com/user-attachments/assets/eb5a9a43-994e-4fa2-8d05-ea635b716bf0)

Reload IIS (Stop and Start the server)

![image](https://github.com/user-attachments/assets/57d02887-aa7e-44ab-82c4-299f9b8b042e)

- Back to the link folder, download "osTicket-v1.15.8.zip." Extract the file, then copy the "upload" folder to "C:\inetpub\wwwroot."

![image](https://github.com/user-attachments/assets/95c26b5e-7a2b-453b-a1dc-7d065621478b)

- Rename "upload" to "osTicket."

![image](https://github.com/user-attachments/assets/af376711-8542-4ce0-a10e-785a05514b59)
![image](https://github.com/user-attachments/assets/b604eaed-1c5a-4fb6-81f7-539c5f649f30)

- Reload IIS (Stop and Start the server)

- Navigate to Sites -> Default -> osTicket. On the right, click "Browse *:80."

![image](https://github.com/user-attachments/assets/a90b4039-e470-460f-8a61-91a0a1bc7d6a)

- This opens the setup page.

![image](https://github.com/user-attachments/assets/7494b552-e45f-4c06-81ea-0745874aa898)

- Note that some extensions are not enabled

- Go back to IIS, navigate to Sites -> Default -> osTicket, and double-click PHP Manager.

![image](https://github.com/user-attachments/assets/3ff34d56-d72e-43e5-9219-5a68a0321b32)

- Click “Enable or disable an extension” 
    - Enable: php_imap.dll
    - Enable: php_intl.dll
    - Enable: php_opcache.dll
![image](https://github.com/user-attachments/assets/fc666fc6-aedd-4225-a7dc-d67adabb242f)

- Refresh the osTicket site in your browser, observe the changes.

![image](https://github.com/user-attachments/assets/443d5026-0fe3-4842-a0fc-72de6aab6c65)

- Before we continue we have to rename the sample config to allow configurations
- From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
![image](https://github.com/user-attachments/assets/8cb7988d-9aea-427c-a477-bc7a5cebd5ab)

- To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
![image](https://github.com/user-attachments/assets/a5c18430-9dfa-46e1-9156-576c9c4f4c83)

- Open properties in ost-config.php in there -> Go to Security -> Advanced Settings 
- Disable inheritance -> Remove All:
![image](https://github.com/user-attachments/assets/92c47398-ac63-4a10-8233-16e94a6de44e)

- Add a new permission entrie -> Select a principal and for the purpose of the tutorial let's set everyone -> Once that is done in the basic permisions select "Full Control" and make sure to apply changes. 
![image](https://github.com/user-attachments/assets/063c79a0-33db-4647-ae75-2149be6a6955)

- We go back to the browser to continue the set up for osTicket.
- Name Helpdesk
- Default email (receives email from customers)
![image](https://github.com/user-attachments/assets/680aa46b-ef62-4f5c-8054-2ad177a1604d)

- We go back to the installation files link and we will download and install Heidi SQL.
![image](https://github.com/user-attachments/assets/2807a127-29be-4eb2-8da9-1cf9969f260f)

-Open Heidi SQL
-Create a new session, root/root
![image](https://github.com/user-attachments/assets/93fc70e6-89c9-4dd2-a11b-d59a77c5ad05)

-Connect to the session
-Create a database called “osTicket”
![image](https://github.com/user-attachments/assets/a968b0d1-f81f-45d7-b42f-de699e82b123)

- Back to the browser finish the installation of osTicket.
-MySQL Database: osTicket
-MySQL Username: root
-MySQL Password: root
-Click “Install Now!”

![image](https://github.com/user-attachments/assets/80fec4e7-7934-48b0-b005-a897db29fd36)

- With all that we should get this screen and that will end the tutorial for us.
![image](https://github.com/user-attachments/assets/9f1b9e11-73ee-480a-b731-191549c0fb65)

Congrats!! 
- Browse to your help desk login page: http://localhost/osTicket/scp/login.php
- End Users osTicket URL:
   - http://localhost/osTicket/
