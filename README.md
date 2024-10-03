<h1>Active Directory Home Lab</h1>

<h2>Introduction</h2>

Welcome to my Active Directory Home Lab Project! This project is designed to help IT enthusiasts and professionals set up a simulated Active Directory environment. By following this guide, you'll gain hands-on experience with AD administration, user creation with PowerShell, and essential networking services like Remote Access Server and Network Address Translation as well as DNS and DHCP.

Whether you're preparing for certifications, enhancing your skills, or just exploring AD functionalities, this home lab provides a practical and controlled environment to experiment and learn.

Here's a diagram of out lab. As you can see, it outlines all of the tools we'll be using to complete the project. <br/>
<br/>
![IP Diagram1](https://github.com/user-attachments/assets/ef52c009-e5f6-4421-8db9-f2e819ba102b)


<br />


<h2>Languages and Utilities Used</h2>

- <b>Active Directory</b>
- <b>PowerShell</b> 
- <b>CMD</b>

<h2>Environments Used </h2>

- <b>Oracle VirtualBox</b>
- <b>Windows 10</b> (21H2)</b>
- <b>Windows Server 2022</b>

<h2>Links</h2>

- <b>Oracle: https://www.virtualbox.org</b>
- <b>Windows 10: https://www.microsoft.com/en-us/software-download/windows10</b>
- <b>Windows Server 2022: https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022</b>

</head>
<body>
    <header>
        <div class="container">
            <h1>Active Directory Lab Walkthrough</h1>
            <nav>
                <ul>
                    <li><a href="#step1">Step 1</a></li>
                    <li><a href="#step2">Step 2</a></li>
                    <li><a href="#step3">Step 3</a></li>
                    <li><a href="#step4">Step 4</a></li>
                    <li><a href="#step5">Step 5</a></li>
                    <li><a href="#step6">Step 6</a></li>
                    <li><a href="#step7">Step 7</a></li>
                </ul>
            </nav>
        </div>
    </header>
    <div class="container">
        <div class="main">
            <div class="step" id="step1">
                <h2>Step 1: Download and Install Oracle VirtualBox and Windows ISOs</h2>
                <p>Feel free to use the links I've posted above for faster reference. After downloading VirtualBox, you'll want to download the 'extension pack'. Also, it's best practice to keep your ISO files centrally located so they're easier to find.</p>
                <img src="https://github.com/user-attachments/assets/429472a0-b34f-48d8-be7c-6e56e009ce4b"><br/>
            </div>
            </div>
            <div class="step" id="step2">
                <h2>Step 2: Create Domain Controller and Install Server 2022</h2>
                <p>The first machine we're going to create is our Server, as this will be our "Domain Controller". When choosing the memory size, remember to work within the limits of your own computer. Click "continue" to confirm the virtual hard drive size, then accept the default choices to finish.<br/>
<img src="https://github.com/user-attachments/assets/b1dee45b-b3c8-4461-af4e-a4e97417e86a">
<img src="https://github.com/user-attachments/assets/a77b712b-d4b1-4458-96a0-9167329445d7">


<br/> 

Before we start our new machine, let's make a few changes.<br/> 
                    
First, click the "General" tab, then choose "Advanced". Change both the "clipboard" and "drag" settings to "bidirectional". This function allows us to copy/paste from host to VM and vice versa.<br/>
<img src="https://github.com/user-attachments/assets/d88679e8-0d7a-4351-895a-9c5f341643c3"><br/>

Click "OK" to accept, then go to the "Network" option. Here, you'll need to set up two adapters: one for internet (labeled "NAT") and the other for your internal network (labeled "intnet"). <br/>
<img src="https://github.com/user-attachments/assets/5e9bda54-977a-4d28-9a99-ec3e5116db20"><br/>
<img src="https://github.com/user-attachments/assets/f58ec5aa-2b3a-406b-b1c9-d644b576208c"><br/>

Now, we're ready to start our machine and install Server 2022. For your installation option, choose "Custom". Then, choose either of the "Desktop Experience" options for your operating system. On the following screen, choose a password (*preferably one that's easy to remember*) and click "finish".<br/>
<img src="https://github.com/user-attachments/assets/6fc43e16-f751-4845-8178-f6ca119f2ddc"><br/>
<br/>
Congratulations! Your machine is now ready to use. You'll be greeted with this screen...<br/>
<img src="https://github.com/user-attachments/assets/36219d6d-c6bb-47c1-a53a-3250a6538517">

and asked to enter "ctrl+alt+del" so navigate up to "input", choose "keyboard", then "ctrl-alt-del".<br/>
<img src="https://github.com/user-attachments/assets/4c07208b-59e2-47a7-a05b-cf9af14e463e">

Enter your newly created (and, hopefully, easy) password to sign in.<br/>
<img src="https://github.com/user-attachments/assets/78992384-7bb6-4c64-a0e6-b15248c56301"><br/>
Before proceeding to the next step, let's run the "Guest Additions" CD image. This will make our VM run more efficiently. To do this, click "devices", then "insert Guest Additions CD image".<br/>
<img src="https://github.com/user-attachments/assets/ec63c3e0-1b10-4abc-8df0-1307d853d9de"><br/>
From here, you'll want to head to file explorer. You'll see the disc image in your "D drive". Double-click the "amd-64" version and follow the prompts to begin installing. Once that's done, you'll be asked if you want to reboot. You (obviously) can if you choose to but there's one more thing to do heading to Step 3 that will also require a reboot.<br/>

Let's rename our computer.<br/>
<br/>
Start by right-clicking the "start" tab and going to "system". Click the "Rename this PC" button and choose your PC's new name. Again, the choice is yours. Restart the VM after renaming and we'll be ready for Step 3!


</p>
        
</div>
            </div>
            <div class="step" id="step3">
                <h2>Step 3: Networking, Domain Admin Account and Active Directory</h2>
                <p>Now, it's time to set up our VM's networking. For this portion of the project, we'll be assigning an IP address and subnet mask for an internal NIC, creating a Domain Admin account, as well as installing Active Directory.<br/>
                <br/>
Let's begin with the IP address. One will connect to your home router so we'll leave it as is; the other (which we'll need to set up manually) will allow your client computer to connect to the server.<br/>
               <br/>
We'll start by clicking the "network" icon at the bottom right corner of your screen, then click "network and internet settings" to open. Next, we'll click on "change adapter options" to open the network connections screen. Here, you should see your two adapters, "Ethernet" and "Ethernet2". Ethernet2 will serve as the internal connection. Double-click "Ethernet 2", then click "properties". After that, double-click on "Internet Protocol Version 4 (TCP/IPv4)". This is where we'll assign our new IP address. From here, choose the "Use the following IP address" option and use "172.16.0.1" as your IP address. For the subnet mask, use "255.255.255.0". Leave the default gateway section blank. For the section below, labeled "Use the following DNS server addresses", we can use either the "172" IP address or you can use "127.0.0.1", which is a loopback address. Click "OK" to complete that portion and our IP address setup is now finished.<br/>
                
Our next step will be installing Active Directory.<br/>
<br/>
Begin by open your "Server Manager" and clicking on "Add roles and features". Click "Next" until you reach the screen labeled "Select server role", at which point you'll choose "Active Directory Domain Services". Click the "Add Features" button on the pop-up screen and "next" until you reach the "install" button. Click to begin installation. Once that's finished, we can move on to the next step; promoting the server to Domain Controller.<br/>
<br/>
Click on the flag icon in the top right corner of your Server Manager, then click on the "Promote this server to a domain controller" option. On the pop-up screen, select "add a new forest", then choose a name for your domain. *For simplicity's sake, I chose "mydomain.com" but you can name yours as you see fit.* On the next screen, you'll be asked to enter a password. You won't use it but you have to enter it in order to move to the next screen so it's best to use the password you used to log in. Click "next" until you reach the "install" button. Click it and your machine will automatically restart.  <br/>
<br/>
Once your machine restarts, you'll be greeted with a new "MYDOMAIN\Administrator" screen. Sign in to your machine and your account to begin the next portion, where we'll be creating a dedicated domain admin account. <br/>
<br/>
Begin by clicking your "start" icon, choose "Windows Administrative Tools", then "Active Directory Users and Computers". From there, right-click on your domain name and a drop down menu will appear. Go to "New", then "Organizational Unit". Use "ADMINS" as your "new object" name and uncheck the "Protect container..." option then click OK to continue. Now, right-click "ADMINS", go to "New", then choose "User". We'll fill out our admin information here. Type you first and last name into the appropriate fields and, for "User logon name", format the entry as *a-first initial last name* as shown in the example pic. Click "next" to continue to the password select screen. To keep things simple, just use the password you use to log in to your machine. Make sure the "Password never expires" option is checked and click "Next" to continue, then click "Finish". Finally, right-click on your name, then "Properties". Click on "Member Of", which will open a Domain Services Folder. Click "Add" and type "Domain Admins" into the "Enter the object names..." field. Click "Check Names", then "OK". After that, click "Apply" then "OK" to finish. Now, our domain admin account is ready to use. Sign out, then sign in with your new admin account and we can begin the next step.

</p>
                <img src="images/step3.png" alt="Install Server 2019">
            </div>
            <div class="step" id="step4">
                <h2>Step 4: Install Remote Access Server/Network Address Translation and DHCP Server</h2>
                <p>This is the second half of our networking setup. Installing RAS/NAT will allow for connection to our virtual network and access the internet while our DHCP Server will give us a range of IP addresses for users and computers to join the network.<br/>
               <br/>
Go to "Add Roles and Features" in your Server Manager, just as you did when you installed Active Directory, and click "Next" until your reach "Select server roles". Choose "Remote Access", click "Next", then choose "Routing" on the "Select role services" screen. Click "Add Features", then "Next" until you reach the "Install" button. Wait through another install session.<br/>
                <br/>
Once the install is done, go to "Tools" and scroll down to and click "Routing and Remote Access". Right-click on the domain controller name to open a drop-down menu, then choose "Configure and Enable Routing and Remote Access". Click "Next" to open the installation wizard, choose the "NAT" option and click "Next". From here, you should see the two network interfaces that were created earlier. Choose the one labeled "DHCP", click "Next" then "Finish" to complete the setup.<br/>
                    <br/>
**Note: Sometimes, the 'network interface' field will come up empty. If this happens, simply close the wizard then reopen it.**<br/>
                    <br/>
Time for one more install. This time, it's our DHCP Server. we'll follow the same process as our previous install, choosing "DHCP Server" on the "Select server roles" screen. Click "Next" until you reach the "Install" button to complete the process. Once the install is complete, got to "Tools" and choose "DHCP" to open the control panel. Let's set up our DHCP scope and subnet mask.<br/>
                <br/>
From the control panel, click on your domain name then right-click on "IPv4" to open a drop-down menu. Choose "New Scope", then click "Next" to open the scope wizard. Here, you can enter "172.16.0.100-200" as your scope name then click "Next" to continue. On the next screen, you'll enter your IP address range, which will be the same as your scope name. In the "Subnet Mask" field, enter "255.255.255.0" and "Length" should be "24". Click "Next" to continue, again to skip the "Exclusions" screen. For "Lease Duration", you can set it for as long or short as you like. Since we're in a lab environment, it doesn't matter too much. Just be advised that the duration length dictates how long a computer will have that address before it refreshes. Click "Next" to continue, choose "Yes" to confirm DHCP options, then "Next" again. On the next screen (labeled "Router (Default Gateway)"), enter the domain controller's IP address and click the "Add" button. Click "Next" to pass the next two screens as we don't need to change anything with those. Choose the "Yes" option on the "Activate Scope" screen, click "Yes" then "Finish" to complete.<br/>
                    <br/>
Just to make sure your server is working, right-click on your domain name and choose "Authorize" from the drop-down menu. After that, right-click again and choose "Refresh". With that, our DHCP server is active and ready for use.<br/>
                <br/>
</p>
                <img src="images/step4.png" alt="Create Users with PowerShell">
            </div>
            <div class="step" id="step5">
                <h2>Step 5: Disable Internet Security, Run PowerShell Script and Create Users</h2>
                <p>Now that we've set up our networking environment, we can move on to creating our "user accounts". Before we do that, though, let's disable the internet security features on our domain controller so we'll have a smoother browsing experience. In your Server Manager, click on "Configure this local server". Go to "IE Enhanced Security Configuration" and click the "On" button to open the dialog box. From there, turn both Admin and User options off. This will keep us from getting spammed with warnings when we use the internet.<br/>
                <br/>
Now that that's done, we can begin creating our "user base". We'll be using the "Names" and "Create User" resources at the very top of the page. Start by opening the "names.txt" option. Here, you'll find your list of user names. Click "Raw", then "Select All" and we'll copy and paste the list into a text file on your domain controller using notepad. Remember to add your name at the top of the list. After that, save the file to your desktop under "Names".</p>
                <img src="images/step5.png" alt="Create Client Virtual Machine">
            </div>
            <div class="step" id="step6">
                <h2>Step 6: Create Client Machine and Install Windows 10</h2>
                <p>Join the client to the domain and log in with a domain account.</p>
                <img src="images/step6.png" alt="Join Client to Domain">
                <div class="step" id="step6">
                <h2>Step 7: Join Client to Domain</h2>
                <p>Join the client to the domain and log in with a domain account.</p>
                <img src="images/step7.png" alt="Join Client to Domain">
                <div class="step" id="step7">     
            </div>
        </div>
    </div>
    <footer>
        <p>© 2024 Active Directory Lab Walkthrough</p>
    </footer>
</body>
</html>


</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

