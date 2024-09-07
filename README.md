<h1>Active Directory Home Lab</h1>

<h2>Description</h2>

Welcome to my Active Directory Home Lab Project! This project is designed to help IT enthusiasts and professionals set up a simulated Active Directory environment. By following this guide, you'll gain hands-on experience with AD administration, user and group management, Group Policy settings, and essential networking services like DNS and DHCP.

Whether you're preparing for certifications, enhancing your skills, or just exploring AD functionalities, this home lab provides a practical and controlled environment to experiment and learn.

Here's a diagram of out lab. As you can see, it outlines all of the tools we'll be using to complete the project. <br/>
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
                </ul>
            </nav>
        </div>
    </header>
    <div class="container">
        <div class="main">
            <div class="step" id="step1">
                <h2>Step 1: Download and Install Oracle VirtualBox, then download Windows ISOs</h2>
                <p>Feel free to use the links I've posted above for faster reference. After downloading VirtualBox, you'll want to download the 'extension pack'. Also, it's best practice to keep your ISO files centrally located so they're easier to find.</p>
                <img src="https://github.com/user-attachments/assets/429472a0-b34f-48d8-be7c-6e56e009ce4b"><br/>
            </div>
            </div>
            <div class="step" id="step2">
                <h2>Step 2: Create Domain Controller and Install Server 2022.</h2>
                <p>The first machine we're going to create is our Server, as this will be our "Domain Controller". When choosing the memory size, remember to work within the limits of your own computer. Click "continue" to confirm the virtual hard drive size, then accept the default choices to finish.
<img src="https://github.com/user-attachments/assets/b1dee45b-b3c8-4461-af4e-a4e97417e86a">
<img src="https://github.com/user-attachments/assets/a77b712b-d4b1-4458-96a0-9167329445d7">


<br/> 

Before we start our new machine, let's make a few changes.<br/> 
                    
First, click the "General" tab, then choose "Advanced". Change both the "clipboard" and "drag" settings to "bidirectional". This function allows us to copy/paste from host to VM and vice versa.<br/>
<img src="https://github.com/user-attachments/assets/d88679e8-0d7a-4351-895a-9c5f341643c3"><br/>

Click "OK" to accept, then go to the "Network" option. Here, you'll need to set up two adapters: one for internet (labeled "NAT") and the other for your internal network (labeled "intnet"). <br/>
<img src="https://github.com/user-attachments/assets/5e9bda54-977a-4d28-9a99-ec3e5116db20">
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
Start by right-clicking the "start" tab and going to "system". Click the "Rename this PC" button and choose your PC's new name. Again, the choice is yours. Restart the VM after renaming and we'll be ready for Step 3!


</p>
        
</div>
            </div>
            <div class="step" id="step3">
                <h2>Step 3: Set Up Networking and Install Active Directory.</h2>
                <p>Install Active Directory on the domain controller and configure IP addressing, DHCP, and routing.</p>
                <img src="images/step3.png" alt="Install Server 2019">
            </div>
            <div class="step" id="step4">
                <h2>Step 4: Create Users with PowerShell</h2>
                <p>Run a PowerShell script to create a thousand users in Active Directory.</p>
                <img src="images/step4.png" alt="Create Users with PowerShell">
            </div>
            <div class="step" id="step5">
                <h2>Step 5: Create Client Virtual Machine</h2>
                <p>Create another virtual machine for the client and install Windows 10 on it.</p>
                <img src="images/step5.png" alt="Create Client Virtual Machine">
            </div>
            <div class="step" id="step6">
                <h2>Step 6: Join Client to Domain</h2>
                <p>Join the client to the domain and log in with a domain account.</p>
                <img src="images/step6.png" alt="Join Client to Domain">
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

