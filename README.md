# osticket-prereqs
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>
<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>List of Prerequisites</h2>

- <b>PHP manager for IIS</b> - ensures PHP is correctly configured to run IIS
- <b>Rewrite module </b> - facilitates URL rewriting and redirect users to URLs
- <b>VC_redist.x86</b> (redistributable) - osTicket relies on libraries that are part of Microsoft Visual C++ and ensures the program runs smoothly
- <b>MySQL</b> - for storing data into databases
- <b>HeidiSQL</b> - interface for accessing MySQL 

<h2>Installation Steps</h2>
<p>
Once the Windows 10 VM is set up in Azure, log in using your credentials. Launch Microsoft Edge, download the osTicket-Installation-Files.zip, and extract it. The contents should then be visible.

</p>
<br />

<p>
<img width="854" alt="image" src="https://github.com/user-attachments/assets/45da8645-206f-40c0-be89-3b5b19fff3b3">
</p>

<p>
Next, activate Internet Information Services (IIS). Navigate to Uninstall a Program, click Turn Windows features on or off, and select the checkbox for Internet Information Services. Then, expand World Wide Web Services, go to Application Development Features, and enable CGI.
</p>
<br />

<p>
<img width="842" alt="image" src="https://github.com/user-attachments/assets/053b866d-d2ae-4cb3-b79b-857731529626">
</p>
<br/>
<p>
Now, install the PHP Manager for IIS. Open the file and confirm all default selections by clicking OK.
</p>
<img width="858" alt="image" src="https://github.com/user-attachments/assets/fad528dd-e481-461b-99c4-09f1e2e95925">

<br />

<p>
Next, create a directory named PHP in C:\, resulting in C:\PHP. Open File Explorer by clicking the folder icon on the Taskbar or searching for it. This directory will be used to extract osTicket for PHP configuration.
</p>
<p>
  <img src="https://i.imgur.com/BCMLUId.png" height="80%" width="80%" alt="extract php to c php"/>
</p>
<br/>

<p>
Next, install the Redistributable, accepting all default settings. Then, install MySQL, choose the Standard Configuration, and set both the username and password to "root" for simplicity. In a real-world scenario, a stronger password is recommended.

</p>
<p>
  <img src="https://i.imgur.com/dbDt0um.png" height="50%" width="50%" alt="install redistr and mysql"/>
</p>
<br/>

<p>
Open Internet Information Services by typing "IIS" in the search bar and selecting Run as administrator. Navigate to PHP Manager and choose Register new PHP version. Then, select C:\PHP\php-cgi.exe.

</p>
<p>
<img width="691" alt="image" src="https://github.com/user-attachments/assets/dc2ed70f-18c0-4195-81ba-bab677473e7e">
</p>
<br/>

<p>
Restart IIS by clicking Stop and then Start on the right-hand side. This will ensure the new PHP version is loaded.
</p>
<p>
<img width="168" alt="image" src="https://github.com/user-attachments/assets/5b8d8b85-195a-456c-a51d-cc94479dc41a">
</p>
<br/>

<p>
Extract the osTicket zip file and move the extracted upload folder to C:\inetpub\wwwroot. Rename the upload folder to osTicket (ensure the name is exact).

</p>
<p>
<img width="1691" alt="image" src="https://github.com/user-attachments/assets/2d5e862f-fd5e-42a6-b858-393b9fc0a3d0">
</p>
<br/>

<p>
Restart IIS once more. In the left-hand pane, navigate to Sites and expand the menu until you find osTicket. Then, in the right-hand pane, click Browse. You should see the following result.
</p>
<p>
<img width="1666" alt="image" src="https://github.com/user-attachments/assets/2e5be45b-9943-4a6a-a93a-36bf948f8496">
</p>
<br/>
<p>
Next, enable a few extensions. In the osTicket folder, select PHP Manager in the middle pane. Click Enable or disable an extension, and enable php_imap.dll, php_intl.dll, and php_opcache.dll. Finally, refresh the osTicket webpage to see the changes.
<p>
<img width="827" alt="image" src="https://github.com/user-attachments/assets/f187e79c-4c73-4a4f-abdb-3ad3cfc4b003">
</p>
<br/>
<p>
Rename C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php to C:\inetpub\wwwroot\osTicket\include\ost-config.php. Next, adjust the file permissions. Right-click the file, then go to Properties → Security tab → Advanced. Click Disable inheritance (remove option), then select Add → Select a principal, and type "Everyone" in the box. Click Check Names and then OK. Ensure that Full control is selected.
</p>
<p>
<img width="598" alt="image" src="https://github.com/user-attachments/assets/82f59e2a-c811-492e-854e-9c7b8d3508b3">
</p>
<br/>
<p>
In the osTicket browser window, click Continue and enter your desired login and password for the helpdesk system. Make sure the MySQL database name is osTicket, with both the username and password set to "root".

Before proceeding, navigate to the extracted folder and install HeidiSQL using the default settings. Once installed, create a new session and log in to the SQL database with the username "root" and password "root". Right-click on Unnamed, select Create new → Database, and name it exactly osTicket.
</p>
<p>
<img src="https://i.imgur.com/Lfw0PXJ.png" height="80%" width="80%" alt="heidisql"/>
<img src="https://i.imgur.com/pWKEjjz.png" height="80%" width="80%" alt="create new database in heidisql"/>
</p>
In the browser, click Install Now to finalize the osTicket installation. A confirmation page will appear with links to log into osTicket as a general user (http://localhost/osTicket) or as staff (http://localhost/osTicket/scp).
<br/>
<p>
<img src="https://i.imgur.com/CBKO7Qs.png" height="80%" width="80%" alt="osticket installed"/>
</p>















