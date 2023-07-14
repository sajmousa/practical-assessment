<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Azure Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create a Virtual Machine in Azure
- Install/Enable IIS in Windows
- Install/Register PHP Manager within IIS
- Install additional applications: Rewrite Module, VC Redist, and MySQL
- Install and configure osTicket
- Install Heidi SQL to complete osTicket installation
  
  

<h2>Installation Steps</h2>

<p>
First, start by creating a Resource Group in Azure.
<img src="https://i.imgur.com/v5RbpS8.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
Next, select the Resource Group folder that was created and create a Windows 10 Virtual Machine (VM) with 3-4 Virtual CPUs. The Virtual Name, Username and Password, can be anything since we will be using this information to remote in with our main computer.   
<img src="https://i.imgur.com/W97fZD6.png" height="65%" width="65%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/1K86mqH.png" height="65%" width="65%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/nHaCAmZ.png" height="65%" width="65%" alt="Disk Sanitization Steps"/>
</p>

Then click on networking tab, which will then show that when the new Virtual Machine is created, it will also create a new Virtual Network. Click on the Review + Create button and it will then create the Virtual Machine.
<img src="https://i.imgur.com/aJsnpT7.png" height="65%" width="65%" alt="Disk Sanitization Steps"/>
<p>
</p>
<br />

<p>
Once the virtual machine has been created you are now going to connect with it by using the public ip address of the Virtual Machine. To connect with the Virtual Machine you will use the remote desktop connection application. Please note that once you have input the Virtual Machines public ip address you will be using the username and password that you have created for the virtual machine. 
<img src="https://i.imgur.com/evBU9PS.png" height="65%" width="65%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/u8Y64kj.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/WtmNaBe.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
Once your connected to the Virtual Machine click on the windows start button and search for the control panel. Then on the control panel select programs, and then select turn windows features on and off.
<img src="https://i.imgur.com/aUvqnEo.png" height="55%" width="55%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/KGnHx8z.png" height="55%" width="55%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

Next install / enable IIS in Windows with CGI and Common HTTP Features
- World Wide Web Services -> Application Development Features -> 
[X] CGI 
[X] Common HTTP Features

Then install / enable IIS Management Console
- Internet Information Services -> Web Management Tools -> IIS Management Console 
[X] IIS Management Console
<p>
<img src="https://i.imgur.com/vR4CZ70.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/iHe8OtQ.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

Please note that all Common HTTP Features needs to be checked. After IIS has been installed/enabled go to your browser and input 127.0.0.1 the page below will display on your screen. If not go back to the control panel and check all configurations
<p>
<img src="https://i.imgur.com/GywYU1M.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />

Next you will now download, and install PHP manager for IIS, Rewrite Module, PHP 7.3.8, VC_redist.x86.exe, MySQL 5.5.62 and then create a directory for PHP on the c drive.
<p>
<img src="https://i.imgur.com/sQbHJbE.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />

When installing MySQL please note that you that username will be "Root" and you will need to create a new password. This information will be used on osTicket, see below for installation guide.
<p>
<img src="https://i.imgur.com/clw9OE1.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/lXxaiSw.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/GTgbRZe.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />

After all programs have been downloaded and installed click on the search bar an open up IIS. Once opened you are now going to register PHP, and when registering PHP it will prompt to provide a path to the php executable file(php-cgi.exe).
<p>
<img src="https://i.imgur.com/XP42V4w.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/dVimGBX.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/Hs2Mk2r.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/98NFpmp.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/5WQYjiC.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />

Now you will need to restart the IIS server, then download and install oSTicket. Once the file has been downloaded, extract and copy "upload" folder to c:\inetpub\wwwroot -Within c:\inetpub\root, Rename the "upload" folder to "osTicket". Then go back to the IIS manager and click "Browse *:80"  
<p>
<img src="https://i.imgur.com/VKkwMqm.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/H5D4kJ2.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/EMI6aw0.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 

The osTicket browser will populate and please note that if this does not populate you will need to go back and review all steps to be sure everything has been completed up to this point. 
<p>
<img src="https://i.imgur.com/G1Uxrnd.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 

On the osTicket browser above some extensions are not enabled. To enable these extensions go back to IIS, then click on the php manager, scroll down to PHP extensions and select "Enable or disable an extension".  
Extensions that need to be enabled are:
- php_imap.dll

- php_intl.dll

- php_opcache.dll
<p>
<img src="https://i.imgur.com/AbTytF0.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/y3ZMoGR.png" height="35%" width="35%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/Cmrqj2B.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />

After the osTicket extension has been enabled, you will need to rename one of the file in the oSticket folder. Head over to the file explorer and search C;\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php. File that needs to be renamed is ost-sampleconfig.php, and it will need to be renamed to ost-config.php. 

Next you will need to add new permissions to ost-config.php. Right click on the ost-config.php folder then click on properties. Then on the tab above click security, click on advance, and click on disable inheritance. Once you have selected that it will then prompt another selection and then you will select "Remove all inherited permissions from this object."

Once you have completed that you are now going to add new permissions. You will click on add and then select a principal. On the "Enter object name to select" type in "Everyone", and check all boxes giving full control to everyone. Then click on apply and ok to apply the new permissions. Below are the screenshots of adding the new permissions.
<p>
<img src="https://i.imgur.com/z4ceG0E.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/YyyFl1G.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/CHFAW67.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/qDa3klR.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/0MaOVVE.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />

After completing the new permissions you will now return back to setup osTicket in the browser. Click on the osTicket browser page and click continue. You will need to fill out the required information but will need to stop at the database settings. 
Next you will now install Heidi SQL, create a new session in the program, and as I noted earlier when installing MySQL, the username will be "Root" and the password would be whatever you had created at the time. Then click on open, and then you will be logged in the database. Next you will right click on the "Unamed" on the left hand side, and then select "create new", then select database. The new database will be osTicket, and once that has been created you will now return back to osTicket and complete the database settings.
<p>
<img src="https://i.imgur.com/DOhceCL.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/xdodmoK.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/4lFRfjV.png" height="35%" width="35%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/ud5hoLD.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />

The osTicket has now been completely installed, and before testing the program some clean up will be needed. You will need to delete setup in C:\inetpub\wwwroot\osTicket\setup. Then you will need to reset the permissions to "read only" in ost-config.php file. 
<p>
<img src="https://i.imgur.com/Fb2pD2w.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/3eASHba.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/iFHe4h4.png" height="35%" width="35%" alt="Disk Sanitization Steps"/> 
</p>
<p>
</p>
<br />

Next login to osTicket, and if you were able login congratulations! You have successfully installed osTicket!
<p>
<img src="https://i.imgur.com/z5eEIPA.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />
