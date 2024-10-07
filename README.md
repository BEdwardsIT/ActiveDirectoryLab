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
![VirtualBox_Server_23_08_2024_14_50_32](https://github.com/user-attachments/assets/a328947c-b77d-42d8-95a0-96c9ceddc9ea)<br/>
<br/>
![VirtualBox_Server_23_08_2024_14_50_55](https://github.com/user-attachments/assets/f96d76cb-e459-42e5-aea6-4b50fa1e96b0)


Let's rename our computer.<br/>
<br/>
Start by right-clicking the "start" tab and going to "system". Click the "Rename this PC" button and choose your PC's new name. Again, the choice is yours. Restart the VM after renaming and we'll be ready for Step 3!<br/>
<br/>
![VirtualBox_Server_23_08_2024_15_31_55](https://github.com/user-attachments/assets/8ab86064-544e-44df-9474-35d17a96a8e6)<br/>
<br/>
![VirtualBox_Server_23_08_2024_15_32_19](https://github.com/user-attachments/assets/2556e009-59d7-4b81-8e58-3d9d5cbc7a63)<br/>
<br/>

</p>
        
</div>
            </div>
            <div class="step" id="step3">
                <h2>Step 3: Networking, Domain Admin Account and Active Directory</h2>
                <p>Now, it's time to set up our VM's networking. For this portion of the project, we'll be assigning an IP address and subnet mask for an internal NIC, creating a Domain Admin account, as well as installing Active Directory.<br/>
                <br/>
Let's begin with the IP address. One will connect to your home router so we'll leave it as is; the other (which we'll need to set up manually) will allow your client computer to connect to the server.<br/>
 <br/>
<img src="https://github.com/user-attachments/assets/8f54c3f2-7ebe-4d75-93dc-e2274447d6f4"><br/>
<br/>
We'll start by clicking the "network" icon at the bottom right corner of your screen, then click "network and internet settings" to open. Next, we'll click on "change adapter options" to open the network connections screen.<br/>
                    
![VirtualBox_Server_23_08_2024_15_10_48](https://github.com/user-attachments/assets/e490d922-15e7-45fc-b2d8-298e4c5fc0cf)<br/>
                    <br/>
Here, you should see your two adapters, "Ethernet" and "Ethernet2". Ethernet2 will serve as the internal connection. Double-click "Ethernet 2", then click "properties". After that, double-click on "Internet Protocol Version 4 (TCP/IPv4)". <br/>
![VirtualBox_Server_23_08_2024_15_24_13](https://github.com/user-attachments/assets/9012d4d3-4d6d-412f-87aa-267664c95be9)<br/>

![VirtualBox_Server_23_08_2024_15_25_12](https://github.com/user-attachments/assets/528d5760-e8d3-47ee-9950-7c1236ca5f02)<br/>

<br/>
This is where we'll assign our new IP address. From here, choose the "Use the following IP address" option and use "172.16.0.1" as your IP address. For the subnet mask, use "255.255.255.0". Leave the default gateway section blank. For the section below, labeled "Use the following DNS server addresses", we can use either the "172" IP address or you can use "127.0.0.1", which is a loopback address. Click "OK" to complete that portion and our IP address setup is now finished.
<br/>

![VirtualBox_Server_23_08_2024_15_27_16](https://github.com/user-attachments/assets/daa0ea6d-1532-42ae-8870-7a4730981806)<br/>

Our next step will be installing Active Directory.<br/>
<br/>
Begin by open your "Server Manager" and clicking on "Add roles and features". Click "Next" until you reach the screen labeled "Select server role", at which point you'll choose "Active Directory Domain Services". Click the "Add Features" button on the pop-up screen and "next" until you reach the "install" button. Click to begin installation. Once that's finished, we can move on to the next step; promoting the server to Domain Controller.<br/>
![VirtualBox_Server_23_08_2024_15_59_07](https://github.com/user-attachments/assets/24588c45-ab18-4faf-96be-1cf5ef74a06c)<br/>

![VirtualBox_Server_23_08_2024_15_59_53](https://github.com/user-attachments/assets/7859283c-7548-4139-8c8c-4b5d7c08b7a1)<br/>
<br/>
Click on the flag icon in the top right corner of your Server Manager, then click on the "Promote this server to a domain controller" option. On the pop-up screen, select "add a new forest", then choose a name for your domain. *For simplicity's sake, I chose "mydomain.com" but you can name yours as you see fit.* On the next screen, you'll be asked to enter a password. You won't use it but you have to enter it in order to move to the next screen so it's best to use the password you used to log in. Click "next" until you reach the "install" button. Click it and your machine will automatically restart.<br/>
![VirtualBox_Server_23_08_2024_16_02_29](https://github.com/user-attachments/assets/65742de1-7b42-4c2d-9e1c-ac9983e24db3)<br/>

![VirtualBox_Server_24_08_2024_11_04_38](https://github.com/user-attachments/assets/ae6dfa5f-42ef-4e50-929f-ea7b251eae4f)<br/>

<br/>
Once your machine restarts, you'll be greeted with a new "MYDOMAIN\Administrator" screen. Sign in to your machine and your account to begin the next portion, where we'll be creating a dedicated domain admin account. <br/>

![VirtualBox_Server '22_24_08_2024_11_50_21](https://github.com/user-attachments/assets/1b7367fb-7fa0-4d5b-bba3-72193a6cf017)<br/>
<br/>
Begin by clicking your "start" icon, choose "Windows Administrative Tools", then "Active Directory Users and Computers". From there, right-click on your domain name and a drop down menu will appear. Go to "New", then "Organizational Unit". Use "ADMINS" as your "new object" name and uncheck the "Protect container..." option then click OK to continue.<br/>
![VirtualBox_Server '22_25_08_2024_15_25_21](https://github.com/user-attachments/assets/69170555-6cd3-48ec-a897-898915462611)<br/>

![VirtualBox_Server '22_25_08_2024_15_29_01](https://github.com/user-attachments/assets/96f017ed-24da-4191-8d14-6985880e5dc0)<br/>
<br/>
Now, right-click "ADMINS", go to "New", then choose "User". We'll fill out our admin information here. Type you first and last name into the appropriate fields and, for "User logon name", format the entry as *a-first initial last name* as shown in the example pic. Click "next" to continue to the password select screen. To keep things simple, just use the password you use to log in to your machine. Make sure the "Password never expires" option is checked and click "Next" to continue, then click "Finish".<br/>

![VirtualBox_Server '22_25_08_2024_15_30_10](https://github.com/user-attachments/assets/2eaaff69-55c1-4d25-99f2-eae1643530ac)<br/>

![VirtualBox_Server '22_25_08_2024_15_31_07](https://github.com/user-attachments/assets/f3e5e15b-8ca3-4aec-b2b7-dc54f0523d77)<br/>


![VirtualBox_Server '22_25_08_2024_15_31_58](https://github.com/user-attachments/assets/d1f3327b-c89c-4eb2-a72f-2b237d7fa222)<br/>

Finally, right-click on your name, then "Properties". Click on "Member Of", which will open a Domain Services Folder. Click "Add" and type "Domain Admins" into the "Enter the object names..." field. Click "Check Names", then "OK". After that, click "Apply" then "OK" to finish. Now, our domain admin account is ready to use. Sign out, then sign in with your new admin account and we can begin the next step.<br/>

![VirtualBox_Server '22_25_08_2024_15_34_14](https://github.com/user-attachments/assets/07ed0a84-06eb-4b52-a93d-2bb0781a3216)<br/>

![VirtualBox_Server '22_25_08_2024_15_38_26](https://github.com/user-attachments/assets/682f7abf-8a2b-4c36-bb84-ef202db9281b)<br/>

![VirtualBox_Server '22_25_08_2024_15_41_10](https://github.com/user-attachments/assets/a1a97237-51db-4541-b641-2fe8e3f162ec)<br/>



</p>
            </div>
            <div class="step" id="step4">
                <h2>Step 4: Install Remote Access Server/Network Address Translation and DHCP Server</h2>
                <p>This is the second half of our networking setup. Installing RAS/NAT will allow for connection to our virtual network and access to the internet while our DHCP Server will give us a range of IP addresses for users and computers to join the network.<br/>

![IP Diagram2](https://github.com/user-attachments/assets/0e69cc75-ab44-4eda-ab3d-f8a780cfe77f)

<br/>
Go to "Add Roles and Features" in your Server Manager, just as you did when you installed Active Directory, and click "Next" until your reach "Select server roles". Choose "Remote Access", click "Next", then choose "Routing" on the "Select role services" screen. Click "Add Features", then "Next" until you reach the "Install" button. Wait through another install session.<br/>

![VirtualBox_Server '22_25_08_2024_15_47_13](https://github.com/user-attachments/assets/17ed72b5-25dd-40fc-a2c7-93901ba426a6)<br/>

![VirtualBox_Server '22_25_08_2024_15_48_02](https://github.com/user-attachments/assets/c2fa2fa6-4e23-4880-bedb-c78140e6d42c)<br/>

<br/>
Once the install is done, go to "Tools" and scroll down to and click "Routing and Remote Access". Right-click on the domain controller name to open a drop-down menu, then choose "Configure and Enable Routing and Remote Access". Click "Next" to open the installation wizard, choose the "NAT" option and click "Next". From here, you should see the two network interfaces that were created earlier. Choose the one labeled "DHCP", click "Next" then "Finish" to complete the setup.<br/>
<br/>

![VirtualBox_Server '22_25_08_2024_15_52_50](https://github.com/user-attachments/assets/76c1c5cd-97ff-4e07-a9cc-0821cf6a1d49)<br/>

![VirtualBox_Server '22_25_08_2024_15_53_26](https://github.com/user-attachments/assets/3466bde7-8077-4ae5-81a1-7d5238df37a9)<br/>

![VirtualBox_Server '22_25_08_2024_16_01_51](https://github.com/user-attachments/assets/111cae35-8857-4518-9892-5036febd4a12)<br/>

![VirtualBox_Server '22_25_08_2024_16_04_02](https://github.com/user-attachments/assets/05aa7c26-5405-4dc7-b53c-fbe77484b266)<br>

 <br/>
**Note: Sometimes, the 'network interface' field will come up empty. If this happens, simply close the wizard then reopen it.**<br/>
                    <br/>
Time for one more install. This time, it's our DHCP Server. we'll follow the same process as our previous install, choosing "DHCP Server" on the "Select server roles" screen. Click "Next" until you reach the "Install" button to complete the process. Once the install is complete, got to "Tools" and choose "DHCP" to open the control panel. Let's set up our DHCP scope and subnet mask.<br/>

![IP Diagram3](https://github.com/user-attachments/assets/b4e02ae6-1d92-4ff7-898b-1d3e242319d4)


![VirtualBox_Server '22_25_08_2024_16_08_15](https://github.com/user-attachments/assets/bba2a923-a16e-4e83-8a48-f8a63c357a02)<br/>


![VirtualBox_Server '22_25_08_2024_16_13_21](https://github.com/user-attachments/assets/aa416a8a-8613-49eb-80bf-b343737d28cd)<br/>

<br/>
From the control panel, click on your domain name then right-click on "IPv4" to open a drop-down menu. Choose "New Scope", then click "Next" to open the scope wizard.<br/>

![VirtualBox_Server '22_25_08_2024_16_16_30](https://github.com/user-attachments/assets/f51f5b2d-4d09-4a4a-b9bc-77af47da6de8)<br/>

Here, you can enter "172.16.0.100-200" as your scope name then click "Next" to continue. On the next screen, you'll enter your IP address range, which will be the same as your scope name. In the "Subnet Mask" field, enter "255.255.255.0" and "Length" should be "24". Click "Next" to continue, again to skip the "Exclusions" screen. For "Lease Duration", you can set it for as long or short as you like. Since we're in a lab environment, it doesn't matter too much. Just be advised that the duration length dictates how long a computer will have that address before it refreshes. Click "Next" to continue, choose "Yes" to confirm DHCP options, then "Next" again. On the next screen (labeled "Router (Default Gateway)"), enter the domain controller's IP address and click the "Add" button. Click "Next" to pass the next two screens as we don't need to change anything with those. Choose the "Yes" option on the "Activate Scope" screen, click "Yes" then "Finish" to complete.<br/>

![VirtualBox_Server '22_25_08_2024_16_18_53](https://github.com/user-attachments/assets/a2258ac9-2fb9-4abe-87a1-230becf09499)<br/>

![VirtualBox_Server '22_25_08_2024_16_25_59](https://github.com/user-attachments/assets/46b3633f-26b4-4687-9659-1f496bec09ad)<br/>
<br/>
Just to make sure your server is working, right-click on your domain name and choose "Authorize" from the drop-down menu. After that, right-click again and choose "Refresh". With that, our DHCP server is active and ready for use.<br/>
                <br/>
</p>
         </div>
            <div class="step" id="step5">
                <h2>Step 5: Disable Internet Security, Run PowerShell Script and Create Users</h2>
                <p>Now that we've set up our networking environment, we can move on to creating our "user accounts". Before we do that, though, let's disable the internet security features on our domain controller so we'll have a smoother browsing experience. In your Server Manager, click on "Configure this local server". Go to "IE Enhanced Security Configuration" and click the "On" button to open the dialog box. From there, turn both Admin and User options off. This will keep us from getting spammed with warnings when we use the internet.<br/>

![VirtualBox_DC_07_10_2024_12_00_02](https://github.com/user-attachments/assets/c8de9413-7c22-42ef-a17c-3e6b4d33e87a)<br/>

![VirtualBox_Server '22_26_08_2024_11_49_19](https://github.com/user-attachments/assets/0fb711a0-0af4-4a34-955d-b9d372213450)<br/>
                 <br/>
Now that that's done, we can begin creating our "user base". We'll be using the .zip file at the top of the page. Click the link to open then left-click on "View Raw" then copy.<br/>

![Screenshot 2024-10-04 185053](https://github.com/user-attachments/assets/547d575d-c24f-4868-812e-1b60a4ccae79)<br/>

Paste the link to your domain controller's internet address bar. Save the newly downloaded .zip file to your desktop so it's easy to find. Left-click to open a drop-down menu and choose "Extract All", then save the contants to your desktop. From your now- accessible folder, open "names", add your name to the top of the list and save. <br/>
![VirtualBox_DC_05_10_2024_11_26_07](https://github.com/user-attachments/assets/609f6308-ca44-44dc-8c28-d98107bd611e)<br/>

![VirtualBox_DC_05_10_2024_11_26_45](https://github.com/user-attachments/assets/acaef224-5c3f-41b5-9153-abcaf1e69d8a)<br/>

![VirtualBox_DC_05_10_2024_11_28_15](https://github.com/user-attachments/assets/5ca5a8d7-57ab-4e59-aa63-25e1b5990e4f)<br/>

![VirtualBox_Server '22_26_08_2024_12_49_08](https://github.com/user-attachments/assets/d1453d40-84a6-40ff-b3d2-d98e15b091eb)<br/>
<br/>
For the next step, we'll be using PowerShell. Open your DC's start menu and left-click "PowerShell ISE". Choose "more", then "Run As Administrator". This is where we'll be using the script.<br/>

![VirtualBox_Server '22_26_08_2024_12_52_59](https://github.com/user-attachments/assets/110c71a5-20ff-480d-bfa5-6e331ce85307)<br/>

<br/>
Click the folder ("Open Script") icon in the top right corner. Find the "AD_PS-master" resource in your desktop and open it. From there, open "1_CREATE_USERS". On Line 2 of the script, change the password to whichever password you chose. Otherwise, your client computer won't be able to sign in. Next, we'll need to run a command that allows us to run all scripts. In the field below, type "Set-ExecutionPolicy Unrestricted", hit enter then answer "Yes To All". Now we can run the script without *you guessed it* restriction. From here, we'll go to the directory where the resource is saved. Type in the highlighted command to open the file's contents. Now, your script is ready to run. Click the "Run Script" icon to begin creating your users. Check "Users and Computers" to see your newly populated list. With that completed, we're ready to create our client machine.<br/>

![VirtualBox_Server '22_26_08_2024_13_11_50](https://github.com/user-attachments/assets/4a129be8-5740-4f4b-88a5-9d5faa8fa070)<br/>

![VirtualBox_DC_05_10_2024_12_27_05](https://github.com/user-attachments/assets/5c041399-75ba-4a2e-8923-06d8a6b4e77c)<br/>

![VirtualBox_Server '22_26_08_2024_13_14_13](https://github.com/user-attachments/assets/f56f3aac-9541-4c52-b48d-c8fd7cd69870)<br/>


<br/>
</p>
                </div>
            <div class="step" id="step6">
                <h2>Step 6: Create Client Machine and Install Windows 10</h2>
                <p>Now, it's time to create our client machine. We'll be installing the Windows 10 ISO. Same procedure as the Server ISO. Be sure to set the network adapter to "Internal Network" as the DC will provide the internet connection. Click "Start" to begin running the machine. Begin the install and choose "I don't have a product key' on the Activate screen. On the next screen, choose one of the "Pro" options as the other don't allow us to join a domain. Choose "Custom Install" when asked. Install as normal. Answer the required set up questions and, on the "connect you to a network" screen, choose "I don't have internet". Choose "Continue with limited setup" on the next screen. Choose a username but you can skip the password. Use your discretion of the "Privacy Features" screen and click "Next" then "Not Now" for Cortana. Your OS will finish installing after that. Install the "Guest Additions" software after that but wait on the restart. </p>
        
</div>
                <div class="step" id="step7">
                <h2>Step 7: Join Client to Domain</h2>                                                <p>Now that our client computer is up and running, we can join it to the domain. Right-click the "Start" menu, choose "System". Scroll down to the bottom and choose "Rename This PC (Advanced)". Click the "Change" button. Here is where you'll rename the PC. Choose your PC name, click "Member of Domain", then enter your domain's name in the field. Click "OK" and wait a few seconds, after which a sign-in screen will appear. Sign in with your admin credentials and you're good to go! Your client computer has successfully joined your domain.<br/>
                <br/>
More importantly, you have just successfully completed your Active Directory Lab. Congratulations!</p>
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

