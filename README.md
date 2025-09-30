# osTicket All-In-One Guide - Installation, Post Installation Configuration, and Ticket Lifecycle Examples

<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket. A lot of tutorials just give you a step-by-step to do and don't really break them down any further for those that have no prior experience in this area, my guide will be as detailed and new user friendly as I can make it. Any questions or suggestions for more clarity anywhere just contact me on my linked social accounts.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 Pro, version 22H2 - x64 Gen2</b>

<h2>List of Prerequisites</h2>

- Azure Subscription
- Microsoft Remote Desktop App
- Windows 10 pro Virtual Machine(VM)
- osTicket Zip Files
  
<h2>In Depth Photo Guided Installation Steps</h2>
Step 1
<p> 
<img width="1385" height="475" alt="image" src="https://github.com/user-attachments/assets/b8f13ef5-ef4b-4279-9cd7-c13e45c3ef40" />

</p>
<p>
Please ensure that you have accessed this document from within the virtual machine by entering the URL provided at the top of the page into a web browser inside the VM. Once the document is open in the VM's browser, locate the link included in the document to download the osTicket ZIP files directly onto the virtual machine. Once the file has been downloaded go to your downloads folder in your computer files and you should see the osTicket zip files. From there we'll drag the file straight to the desktop, once it's there right click it and hit extract all, make sure when you hit "extract all" its going to the desktop folder. You should see the file you just extracted on your desktop. We can now just trash the zip file, (NOT THE ONE WE JUST EXTRACTED).
</p>
<br /> 
Step 2
<p> 
<img width="911" height="505" alt="image" src="https://github.com/user-attachments/assets/f7353d12-a194-465e-823e-6dc3c184fd8d" />

</p>
<p>
We're installing the webserver now, to enable IIS we go to the start button and then the Control Panel. From there you should see Programs on the bottom, we're going to click "Uninstall a Program" we won't be doing that it just takes us to the page we need to go. Once in that section we'll go to "Turn Windows Features On or Off" and that's where we'll find "Internet Information Services" . It should have an empty box next to it, we'll go ahead and check it. We also want to install or enable CGI while we're here. CGI is just something osTicket needs, you'll find it under World Wide Web Services, and under Applicant Development Features. Then once both are checked we'll click "OK" and wait while they install. I apologize for the blur on the image but I hope it still gives you an idea of what the place looks like that you should be at in install/enable these features.
</p>
<br />
Step 3
<p> 
<img width="582" height="481" alt="image" src="https://github.com/user-attachments/assets/1d510f2f-19c7-47fc-9452-241857ec075b" />

</p>
<p>
Next, from the osTicket installation files folder, we'll install PHP manager for IIS. PHP is like a backend webserver language, and osTicket runs on PHP. We'll start by going into the osTicket installation file we unzipped on the desktop earlier. Once we've opened the file we should see the PHP manager, double click on it and then just hit "next," "I, agree - Next," and finally just hit "Yes" and it should begin installing. From within the same file we'll install the "Rewrite Module" it will be right under the one we just installed. The rewrite module is used to clean up and simplify URLs, making them more user-friendly, readable, and sometimes more secure.
</p>
<br />
Step 4
<p> 
<img width="513" height="485" alt="image" src="https://github.com/user-attachments/assets/5f578df4-578b-49f2-ac65-9bc310e6e783" />

</p>
<p>
We'll now be creating a directory on the c-drive called PHP. The c-drive can be found when you open file explorer towards the bottom on the left called "Windows (C:)" and once you've opened the c-drive folder right click on it and create a new folder called "PHP". From here we'll go back to the “osTicket-Installation-Files” folder, and unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the PHP folder we just made on the c-drive. So we'll go ahead and right click the zip file PHP which holds the binaries like, the language itself, and click "extract all". and before we extract it we want to click browse and select the PHP folder on the c-drive we just made, then export it.
</p>
<br />
Step 5
<p> 
<img width="811" height="477" alt="image" src="https://github.com/user-attachments/assets/9fa60536-2564-43e5-984b-20978422b800" />

</p>
<p>
Next we'll install VC_redist.x86.exe. from the osTicket installation folder. Once you see it go ahead and double click on it. It'll open a little window before it installs, just click agree and hit install, then click yes on the next page. Now we'll install MySQL, this is simply a database for osTicket, it stores all user accounts, all the ticketing information, everything osTicket spits out or receives from users will be put in this database on the backend. In the very same folder osTicket installation we'll double click on MySQL and just hit next and agree on whatever it prompts, until you get to the screen where it asks you to choose a setup type. Once we get to this page just make sure you have it on "Typical" setup, then click install and then click yes. It'll prompt you yet again, make sure the box to "Launch the MySQL Instance Configuration Wizard" is checked, then just click "finish". We'll then be brought to another page, click yes, then next. It will ask you to select a configuration type, it should default to "Detailed Configuration" . We want to change that to "Standard Configuration" then click next, leave the next page alone and click next again. This next part is VERY IMPORTANT! Make sure you input "ROOT" for the password, exactly how it looks in the quotation 
</p>
<br />
Step 6
<p> 
<img width="406" height="292" alt="image" src="https://github.com/user-attachments/assets/84927470-e6a9-4028-926b-b37dd65eaff2" />
  
</p>
<p>
This next part is VERY IMPORTANT! Make sure you input "ROOT" for the password, EXACTLY how it looks in the quotation. In a real life setup, this isn't what you would want to do but for lab purposes we will have this as the password. If you follow along with what I'm doing you won't need to remember this password, you can just come back to this section of the guide and see what I had you set as the password, so don't stress about not being able to remember it later. After that just click "next" then "execute" and wait for it to configure, then lastly, click "finish". 
</p>
<br />
Step 7
<p> 
<img width="616" height="501" alt="image" src="https://github.com/user-attachments/assets/78b0a7e1-298b-417b-a659-e2ed7ca552c6" />

</p>
<p>
Next we'll open IIS as an admin. So just click the windows icon in the bottom left and you should just be able to search "IIS" and once you see it, right click on it and click "open as admin" it should just take a second to open. We're going to register PHP from within IIS, this means we're making the web server aware of the existence of PHP on the computer and we're telling it where it is. When IIS is open you will be able to see an icon labeled "PHP Manager" and we're gonna go ahead and open it, once it's open click "Register new PHP version" and when that page opens we'll click the three dots to browse for our file, if you remember we put it on the c-drive. So from browsing we'll open the PHP folder from within the c-drive folder, once the folder is open we'll double click on "php-cgi" and it should auto-fill the textbox with that file. Once it has, we'll click "ok" and it will register our PHP. Now we'll reload IIS, by stopping and restarting the web server. On the left side of the IIS page, you should see the drop down bar labeled "osticket-vm (osticket-vm\lab)" go ahead and right click it and then click "stop", wait a few seconds and then right click again and hit "start" to reload the server.
</p>
<br />
Step 8
<p> 
<img width="591" height="373" alt="image" src="https://github.com/user-attachments/assets/e59f04af-4351-48bc-aaa4-9f3c6b3525c2" />

</p>
<p>
Now we'll install osTicket v1.15.8 from the osTicket-Installation-Files folder. To make things a little less cluttered we can minimize the IIS page so it's not in our way. Back in our osTicket-Installation-Files folder we're gonna unzip our osTicket v1.15.8 by right clicking on it and clicking "Extract All..." and it should default to extracting to the desktop, and that's ok, we'll have it just go to the desktop, so just click extract now. If you see in your osTicket-Installation-Files folder it made the same file we just extracted, but it's no longer a zip file. This extraction should take a little bit of time. After it's done it should auto open the folder, but you can just close it because you probably have a lot of file windows open and we don't need it opened from another window. From the same window we extracted it and you can open the unzipped osTicket v1.15.8 from there. You should see two files, "scripts" and "upload" we are going to copy the upload file into “c:\inetpub\wwwroot" so open another window in file explorer if one isn't already open, and go to c-drive, then "inetpub", then wwwroot. Once there go back to the unzipped osTicket-Installation-Files folder and drag the "upload" file over to the other window in the wwwroot folder. Once it's copied in the new folder, rename "upload" to "osTicket" (IN THE wwwroot FOLDER). Now we'll reload IIS again, go ahead and right click labeled "osticket-vm (osticket-vm\lab)" and then click "stop", wait a few seconds and then right click again and hit "start" to reload the server. 
</p>
<br />
Step 9
<p> 
<img width="831" height="746" alt="image" src="https://github.com/user-attachments/assets/fc2a407a-f0c5-4314-a0e6-7cbd3d7b50f5" />

</p>
<p>
Now, we'll open another window in file explorer if one isn't already open, and go to c-drive, then "inetpub", then wwwroot. Once there go back to the unzipped osTicket-Installation-Files folder and drag the "upload" file over to the other window in the wwwroot folder. Once it's moved in the new folder, rename "upload" to "osTicket" (IN THE wwwroot FOLDER). Now we'll reload IIS again, (If you don't remember how to get there go to step 7), go ahead and right click labeled "osticket-vm (osticket-vm\lab)" and then click "stop", wait a few seconds and then right click again and hit "start" to reload the server. From here if followed along to a T you should be able to load the osTicket site.
</p>
<br />
Step 10
<p> 
<img width="1312" height="622" alt="image" src="https://github.com/user-attachments/assets/98ef953f-7f65-48d2-b1d8-1c0af99b81c8" />

</p>
<p>
In the same window (IIS) we want to make sure "osticket-vm (osticket-vm\lab)" is expanded, from there expand "sites" and lastly "Default Web Site" we should see osTicket go ahead and click on it and when it opens, on the far right of the screen we should see under "Browse Folder" a link to the osTicket site called “Browse *:80” click it, and it should open the osTicket (Installer) site. If it doesn't load for you for whatever reason, you can use the steps above and try to troubleshoot it a little (It might be faster to just restart unfortunately). For right now we can minimize IIS to clear up your screen. From the image provided above or from your own screen if your following along you should notice that some of the extensions are not enabled, we are going to enable some of them, now we aren't going to enable all of them, but we will enable, php_imap.dll, php_intl.dll, php_opcache.dll for this lab.
</p>
<br />
Step 11
<p> 
<img width="532" height="478" alt="image" src="https://github.com/user-attachments/assets/1095a617-6139-4770-bb46-6f0468e1a0ed" />

</p>
<p>
We will now, be going back to IIS to make some configurations. We can reopen IIS from minimizing earlier (If you closed it no biggie refer to step 7 if you forgot how to open it). From IIS we should already be open to osTicket, if you aren't expand "osticket-vm (osticket-vm\lab)", from there expand "sites" and lastly "Default Web Site" we should see osTicket. With that open we will double click "PHP Manager" and when that opens look under "PHP Extensions" you should see something called "Enable or disable extension" go right ahead and click on that. Now we will enable 3 extentions called, (php_imap.dll), (php_intl.dll), (php_opcache.dll). They are kind of just mixed in with the rest of the disabled extensions, so once you find them just click on it and click "enable" and once all three are enabled go back to the osTicket (Installer) site and reload it to see if the changes went through. There should only be two extensions not enabled at the bottom.
</p>
<br />
Step 12
<p> 
<img width="507" height="477" alt="image" src="https://github.com/user-attachments/assets/43e4ad09-0b0a-4bd9-959f-433c0e1a8fbf" />

</p>
<p>
So we're going to now rename a file in the hard drive that osTicket uses to make configurations. In the c-drive there's a file called (ost-sampleconfig.php) we will rename it from that to (ost-config.php) simply changing it from "sampleconfig" to "config" and then make sure that osTicket has access to make changes to it. To do that we're going to go ahead and open up file explorer if it is not already open and go to the c-drive, then inetpub, then wwwroot, then osticket, and finally from there open the "include" file. Once there we will have to scroll down until we find it, once we do, carefully rename it (right click the file to find the rename option), making sure to not misspell anything (it should be "ost-config.php" exactly spelled like that). After it's changed, we're now going to give osTicket access to make changes on the back end, so right click on the newly named file, go to "properties", then security, from there, click "Advanced" and then you should see something called "Disable Inheritance" click on that to strip all current permissions, it will open a prompt make sure to click "remove all inherited permissions from this object" which should wipe out all permissions. From the same page we'll hit "Add" so we can add our own permissions, once that's open click "Select a Principal" as that opens you should see a box labeled above as "Enter the object name to select (Examples)" In the box you wanna type "everyone" (this is not a good thing to do in real life but for lab purposes that's what we'll do) and then click "ok" and lastly below what we just did check the box that says "Full Control" then click "ok" once more. You should after all that only see one thing in the permissions section, and it should say, "Allow-- Everyone-- Full control-- None" and if it does at the bottom click "apply" and then "ok" to the next screen, to make sure everything we did is active.
</p>
<br />
Step 13
<p> 
<img width="641" height="730" alt="image" src="https://github.com/user-attachments/assets/94e9a3d3-ea24-447c-aa0a-072aec774ae8" />

</p>
<p>
Now we will go back to the osTicket (Installer) site and click "continue" at the bottom, to continue the setup. Now, on this page it's pretty much just naming the Helpdesk, and admin overseeing the tickets. So for the Helpdesk name I would put something like "Nick's Helpdesk" but if your name was Lori or Kyle you would obviously substitute your name over mine. Next would be the email address and I don't think it matters if you use a real or fake one. I just put in my work email. For the Admin section just put your name and the email address from the top can't be the same as the admin one. For the username and password, I like to keep it simple and bland as it's just a lab. I put "adminuser" for the user and "Password1" for the password, exactly as it's typed out. Now before we go to the next step we have to make sure to fill out the database correctly.
</p>
<br />
Step 14
<p> 
<img width="526" height="353" alt="image" src="https://github.com/user-attachments/assets/6ca68ced-a2c1-46fa-bf95-762b56bb10fa" />

</p>
<p>
We already created a database earlier so now we just have to login to it and create another database specific to osTicket and provide the credentials to osTickets installer site. So we're gonna go back to osTicket-Installation-Files folder on the desktop, we're gonna open it, then open the folder named the same as the last one and we're gonna install a file called HeidiSQL_12.3.0.6589_Setup which basically allows us to make a connection to our database, configure it and just do stuff in there. So go ahead and double click the file and when it gives you a prompt click "yes" and then click "I accept" the next, next, next until you get to install then click "install" and wait for it to process. It'll prompt you once more, there should be a box that says "launch HeidiSQL" make sure it's checked, and hit finish. When it launches it'll prompt you, just hit "skip", and click "new" it will ask you for a username and password but remember we set it to "ROOT", and "ROOT" for both, after you input the credentials click open (If the username or password fails, you might've did it in lowercase, so try it again like that). So that opened a connection to the database, from here we want to open a database named osTicket. Now there's a a drop-down folder on the left labeled "Unnamed" with a little dolphin kinda logo, we're gonna right click on it, and select "Create New" and then database then when we go to name it it needs to be exactly "osTicket" and no variation of that, then click "ok". You should now see it on the left, it will look like "osticket" but don't worry that's just how it appears.
</p>
<br />
Step 15
<p> 
<img width="372" height="277" alt="image" src="https://github.com/user-attachments/assets/7ea50d17-c2f1-456e-8511-d2c6cc810308" /> --> <img width="333" height="180" alt="image" src="https://github.com/user-attachments/assets/3e296d4f-22b6-48b0-9be5-141b2d83a6f7" />

</p>
<p>
Now we will enter the credentials into the osTicket (Installer) site, (this window should still be open, if it's not refer to step 9) there are five text boxes and they should say (from the top down) "ost_", "localhost", "osTicket", "ROOT(lowercase, maybe)", "ROOT (lowercase, maybe)" and if every box says what I have we are ready to install! After it's done "doing Stuff" it'll bring you to a screen and it will say "Congratulations!" because yeah, you did it! On that page there will be many different links that will take you to osTicket but as different users, like the admin or the end user. From those links we will start our next section! As the screen said, Congratulations you successfully installed osTicket on your Virtual Machine! 
</p>
<br />
(Optional) Step 16
<p> 
<img width="1375" height="412" alt="image" src="https://github.com/user-attachments/assets/c2cb16cf-340e-4156-a3fd-cc4fcb27970c" />


</p>
<p>
If you happen to be taking a break in-between sections and don't want your VM's to be racking up some charges you can go to Azure and just stop them from running until you wanna get started on the next section! My VM's in the image above are a little different, they are for another project I'm working on right now but it should show you how to do it and what the status should look like if you have successfully stopped them.
</p>
<br />

</p>

<h1>osTicket - Post-Install Configuration</h1>
This tutorial outlines the post-install configuration of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 Pro, version 22H2 - x64 Gen2

<h2>Post-Install Configuration Objectives</h2>

- Configure Agents/Users
- Configure Teams/Departments/Roles
- Configure SLA (Which is basically a ticket priority system)
- Configure Help Topics
- Set Permissions For Our Users and Agents

<h2>In Depth Photo Guided Configuration Steps</h2>
Step 1
<p>
<img width="155" height="21" alt="image" src="https://github.com/user-attachments/assets/f82c21ef-d237-4c43-b08a-bbe175cdec9e" /> <img width="150" height="17" alt="image" src="https://github.com/user-attachments/assets/c9f3d5cc-b752-49ec-9f8b-875e394fce4b" />



</p>
<p>
We're gonna start with some important links. http://localhost/osTicket/scp/login.php is the URL that will take you to the Admin/Agent login page, where you can log in and close tickets opened by the users. Now this URL (http://localhost/osTicket) will take you to the user login where you would submit tickets as the customer. We're going to learn how to navigate these as well as create Agents and Users alike to help bring this lab a little reality. To start we will get logged in as the Admin. Once logged in you will see in the upper-right-hand corner it should say "hi..." followed by your name and next to it should say Admin Panel or Agent Panel. These two panels are how you as an admin navigate osTicket, in the Agent Panel you will see pretty much what your agents see, it will be the where they spend most of their day responding to and closing tickets. The Admin Panel is where we will create departments, teams, and roles, as well as move agents around within them etc.. 
</p>
<br />
Step 2
<p>
<img width="707" height="285" alt="image" src="https://github.com/user-attachments/assets/8d2da101-6b6f-49e9-a56f-0df63e77b949" />
</p>
<p>
First thing we'll do is configure roles, which basically allows us to group people and give certain people certain abilities. To get to that section we'll go to the Admin Panel, then click the Agents tab, and in the tabs under agents you should see roles go ahead and click that. You should see the basic roles already there, like "All Access", "Expanded Access", "Limited Access", and "View Only". So if you want to get an understanding of that you can click "all access" and "view only" then go to permissions and see the difference in permission checked to each role. We are going to create a new role, so go over to the tab labeled "Add New Role", we'll name it "Supreme Admin" and in permissions we'll check every box we can then click "Add Role". 
</p>
<br />
Step 3
<p>
<img width="697" height="257" alt="image" src="https://github.com/user-attachments/assets/3df22055-463d-4b25-9e30-3643912d351e" />
</p>
<p>
Next we're going to head over to the departments tap, where you should see the default departments, Maintenance, and Support. Departments have unique rules as compared to agents. If a ticket is assigned to the Support Dept. and lets say "Tyler" opened it but his role was View Only he couldn't do the ticket in the site, but if someone else in that dept. had "All Access" then they would be able to complete the ticket. We will be adding a new Dept. called the "SysAdmins" and the "Add New Department" button is in the same place roles was. To start creating SysAdmins we want to make sure the "Parent" option at the top is set to "Top Level Department" and we'll name it SysAdmins obviously, and we can leave the rest default for right now, and we'll head over to the "Access" tab. The access tab is where we would add agents but we don't have any yet, so we'll just click "Create Dept"
</p>
<br />
Step 4
<p>
<img width="702" height="307" alt="image" src="https://github.com/user-attachments/assets/f288628f-1e15-4861-b1be-91df9772de07" />
</p>
<p>
Now, we'll head over to teams, and teams are basically anybody qualified from any department can be put on the corresponding team. For example if 3 people from the maintenance and 1 person from the support team know how the online banking system works they could all be put on the "Online banking" team. So, we'll head over to the teams tab, and click "add new team". We'll name this new team, "Online Banking" and leave the rest default for now, simply click "create team". 
</p>
<br />
Step 5
<p>
<img width="497" height="437" alt="image" src="https://github.com/user-attachments/assets/b7b1027c-e90e-4a5b-86b3-f0160ec9fd66" />
</p>
<p>
We will now change the setting so anyone can create a ticket even if they're not registered in the system. So from the Admin Panel, we'll go to the settings tab and then "Users" and just make sure the "Registration Required" box isn't checked. It is a very simple step that I see a lot of people just forget or accidently mess up on, so once you see that the box isn't checked just click "Save changes" and we'll jump to the next step!
</p>
<br />
Step 6
<p>
<img width="522" height="296" alt="image" src="https://github.com/user-attachments/assets/8663050b-4d2f-4473-bcce-2df1fd4b64a2" /> <img width="715" height="297" alt="image" src="https://github.com/user-attachments/assets/d7b89f19-9216-45c9-9200-f8b3399bbb9d" />
</p>
<p>
Now we will configure some agents to work on some tickets with! For my lab I will call my agents "Jane Doe" and "John Doe", in the same panel as the last step we're going to click the "agents" tab and you should see the default agent is just you. Now we'll go to "add new agent" on the right hand side of the screen, and I'll name mine "Jane Doe" with a fake email address, leave the rest blank until we get to "Username" and I'll put just "jane" for my user, then we'll click "set password" and uncheck the box in the prompt then set the password as "Password1". Now under the access tab we'll put her in the SysAdmins department and give her the "Supreme Admin" role we made earlier. Then we can go to the teams tab and assign her to the "Online Banking" team. Then we'll hit "Create" and Jane will be added to the system. Now we'll John, go to "add new agent" on the right hand side of the screen, and I'll name mine "John Doe" with a fake email address, leave the rest blank until we get to "Username" and I'll put just "john" for my user, then we'll click "set password" and uncheck the box in the prompt then set the password as "Password1". Now under the access tab we'll put him in the "Support" Department, and give him "All Access" and we can just leave the rest blank. Now we can click "create" and it will add john to the system as well.
</p>
<br />
Step 7
<p>
<img width="502" height="313" alt="image" src="https://github.com/user-attachments/assets/14aeede4-6e0b-4b26-929d-f71b5ce75df6" />
</p>
<p>
Now we can go to the Agent Panel, and from there click "Users" and on the right side we'll click "add new user". This is where we will add our customers or our "users" who will be creating tickets for our agents. After you click add new user we will input the fake email and full name of our user. My user will be just Karen, once you input the fake email and "Karen" for the name you can simply click "add user" (Make sure you keep track of Karen's Email).
</p>
<br />
Step 8
<p>
<img width="492" height="222" alt="image" src="https://github.com/user-attachments/assets/c3342b87-5df0-4615-a6f5-bc8c07e41cad" />
</p>
<p>
Next we'll configure our SLA's (which is basically a ticket priority system). We'll switch back to our Admin Panel, then go to the manage tab and click "Add New SLA Plan". We will create 3 new SLA Plans, first we'll start with Sev-A which in our case we'll make it the most urgent (Urgency is usually scaled on overall business impact), for name obviously we'll put "Sev-A", for "Grace period" we'll do 1 hour, and for schedule we'll do "24/7" so when a ticket like this gets posted the Help Desk has 1 hour to respond and needs to be ready 24/7. The next SLA will be Sev-B which in our case we'll make it the second most urgent, for name obviously we'll put "Sev-B", for "Grace period" we'll do 4 hour, and for schedule we'll do "24/7" so when a ticket like this gets posted the Help Desk has 4 hour to respond and needs to be ready 24/7. For our last SLA it'll be Sev-C which in our case we'll make it the least urgent, for name obviously we'll put "Sev-C", for "Grace period" we'll do 8 hour, and for schedule we'll do "Mon - Fri 8am - 5pm with U.S. Holiday" so when a ticket like this gets posted the Help Desk has 8 hours to respond within business hours. 
</p>
<br />
Step 9
<p>
<img width="645" height="397" alt="image" src="https://github.com/user-attachments/assets/ec66eefb-1e2c-4e21-8684-505f2c66008b" />
</p>
<p>
Finally from the same place as the last step we will configure Help Topics. Under the manage tab in the Admin Panel, we will select "Help Topics" and then we'll click "add new help topic" (we'll be creating 5 different help topics). Once that's open we will put "Business Critical Outage" as the topic and the parent topic will be "Report a Problem" then click "Add Topic" and then go back under the help topics tab. Next we'll create another one and we will put "Personal Computer Issues" as the topic and the parent topic will be "Report a Problem" then click "Add Topic" again. Next we'll create another one and we will put "Equipment Request" as the topic and the parent topic will be "General Inquiry" then click "Add Topic" once more. Next we'll create another one and we will put "Password Reset" as the topic and the parent topic will be "Report a Problem" then click "Add Topic" again. Lastly we'll create another one and we will put "Other" as the topic and the parent topic will be "General Inquiry" then click "Add Topic". 
</p>
<br />
Step 10
<p>
<img width="1375" height="412" alt="image" src="https://github.com/user-attachments/assets/41ec249a-1d7f-406b-b7b3-b8f1c0497683" />
</p>
<p>
That's it for this section, as a recap we created some roles, departments, teams, and agents who will resolve tickets in the next lab, and users who will be making some tickets in the next lab as well. We also set up some SLA's and help topics to help the agents navigate the tickets posted. We are now ready to begin making and closing fake tickets in the next section! If you happen to be taking a break in-between sections and don't want your VM's to be racking up some charges you can go to Azure and just stop them from running until you wanna get started on the next section! My VM's in the image above are a little different, they are for another project I'm working on right now but it should show you how to do it and what the status should look like if you have successfully stopped them.
</p>
<br />


</p>

<h1>osTicket - Ticket Lifecycle: Intake Through Resolution</h1>
This tutorial outlines the lifecycle of a ticket from intake to resolution within the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 Pro, version 22H2 - x64 Gen2

<h2>Ticket Lifecycle Stages</h2>

- Intake (Receive Ticket)
- Assignment and Communication (Assigning the Ticket Appropriately)
- Working the Issue (Work Through the Ticket Giving Updates to the Customer)
- Resolution (Close the Ticket)

<h2>In Depth Photo Guided Lifecycle Stages</h2>
Step 1
<p>
<img width="697" height="206" alt="image" src="https://github.com/user-attachments/assets/a6ce258a-cec0-46cf-be7d-452f6901c4ab" />
</p>
<p>
Before we begin creating tickets for us to "solve" we are going to delete the maintenance department because when we start creating tickets they for some reason get defaulted to this even if we deactivate it, so we're just going to delete it. To do that go to the admin panel, then agents, and then departments so from there just check the box next to "maintenence" and on the right side you should see a "more" tab click the drop down menu and hit delete so we don't have to worry about it bothering the lab later on. Now that page if you remember we accessed from this (http://localhost/osTicket/scp/login.php) URL, we are now going to step out of the admin/agent site and go to our users site to create some tickets for us to "work" on. The URL if you don't have it, is (http://localhost/osTicket) and this will take you to where we create some tickets!
</p>
<br />
Step 2
<p>
<img width="643" height="376" alt="image" src="https://github.com/user-attachments/assets/13ea3874-4438-4233-b7b8-7b7c83563fe3" />
</p>
<p>
Once we get to the new site we will go to the "Open a New Ticket" tab at the top, and use the credentials you should have saved from the previous lesson. From here you will enter your fake email address associated with the user account, my user is Karen, and after I enter her credentials I will choose the help topic she will base the ticket around. For the this ticket set the help topic to "report a problem" and put "Entire mobile/online banking system is down" under the 'issue Summary' now for the large text box just detail what is happening, like "Our customers and agents haven't been able to load the banking portal, and anyone who can load it their login creds don't work." that will give the agent (you) more information to go off of, you'll still likely have to call the customer and follow up with any additional detail they may be able to provide, after you put all the information in click "create ticket". Now we'll log back into the agent portal but this time as John (you should have the credentials saved somewhere), and find the ticket we just made. 
</p>
<br />
Step 3
<p>
<img width="726" height="391" alt="image" src="https://github.com/user-attachments/assets/493edfea-5754-4120-9fcc-8e4284d91acf" />
</p>
<p>
The ticket we just made will be under the tickets tab and if it isn't, make sure you fully deleted the "maintenance" department so it will go to the support team where John can see it. Now click on the ticket to open it, from here we'll review the ticket and if this were a real person we'd give the user a call or shoot an email to clarify anything you're unsure of. Now that we have all the information as of right now, we will change the ticket to match the situation. On the ticket, start by clicking "SLA Plan" and change it to Sev-A, since this problem is so wide spread and it is affecting every banking customer this would be considered to have a serious impact on the business. Now we want to change the help topic, so we'll do that by clicking "Help Topic" and changing it to "Report a Problem/ Business Critical Outage", in your job you will do this a lot where the user input information that will need to be updated based on how you understand the problem and its severity. At the bottom of the ticket there will be a place where you can see a 'history' of changes made to the ticket and by who, as well as communicate directly to the user updating them on the progression of their problem. With every ticket we want to give an update pretty regularly, more frequent with larger problems but still on the ball with smaller problems, even if no progress has been made we want them to know we haven't forgotten about them and we are working on their issue.
</p>
<br />
Step 4
<p>
<img width="710" height="222" alt="image" src="https://github.com/user-attachments/assets/294feb72-21eb-47d4-a143-ba31bfb94ebb" />
</p>
<p>
One of the last steps for this ticket is after updating all the information we'll assign the ticket to the appropriate teams, and since this is a banking issue we'll assign it to the online banking team (To ensure you see this as an option make sure you have agents assigned to these teams.(you can do so in the admin panel under agents and teams click on "Online Banking" and add agents to it). Sometimes when the person who receives the ticket isn't qualified to handle it they will assign it outside their team or even department (to the admins perhaps) and it will remove them from having access to modify the ticket afterwards. Once that happens the online banking team will resolve the ticket, but since it's just a lab we'll go through how to close the ticket on our own. So let's say we were able to resolve the ticket, now we'd go to status and click "Open" we would change it to "Resolved" and that would be our first ticket done. (Just as a side note, sometimes you might come across high profile people like CFOs, Executive Staff, etc. making tickets, and you'll think it's always a Sev-A because of their position but sometimes they aren't as important on a business impact scale, so its always important to remember business impact)
</p>
<br />
Step 5
<p>
<img width="507" height="417" alt="image" src="https://github.com/user-attachments/assets/937b9173-7b7c-49d7-97d7-a289923a563c" />
</p>
<p>
I wanted to make this lab with just one OMNI-Ticket that shows you all the mechanics from creating a ticket, to communicating with someone about the ticket, then correcting the ticket itself and appropriately assigning it to the right team, to lastly closing/resolving a ticket. You can now mess around with what we just walked through together and make some new diverse tickets and practice closing them after you've corrected them. If you close a ticket you want to review afterwards login as an admin and they will show all past tickets closed or resolved as well as their history.
</p>
<br />
Step 6
<p>
<img width="333" height="180" alt="image" src="https://github.com/user-attachments/assets/350f382d-9963-4225-ae27-20f97658288e" />
</p>
<p>
Now we have officially reached the end of the lab, if you wish to keep this VM's open to work on tickets then remember to stop them when you are not working on them in Azure, but if you do plan to delete the VM's I personally find it fast to go to the resource group that houses the VM and take the both out from there. Always double check everything is deleted before you walk away. These VM's can get expensive if left on for a long period of time. Thank all of those who chose to dedicate some time to my guides and I hope they were helpful as you progress your IT career!
</p>
<br />
