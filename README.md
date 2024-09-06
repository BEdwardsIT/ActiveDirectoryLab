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
                <img src="https://github.com/user-attachments/assets/be54b919-64a0-48cb-97b1-861ba9dc5aaa"><br/>
            </div>
            </div>
            <div class="step" id="step2">
                <h2>Step 2: Create Domain Controller and Install Server 2022.</h2>
                <p>The first machine we're going to create is our Server, as this will be our "Domain Controller". When choosing the memory size, remember to work within the limits of your own computer. Click "continue" to confirm the virtual hard drive size, then accept the default choices to finish.
<img src="https://github.com/user-attachments/assets/a6110afa-fde1-460a-8309-b79c4db4436d">
<img src="https://github.com/user-attachments/assets/c5b4f7d2-dcbd-40f1-bac3-1d7bb57e8de0">


<br/> 

Before we start our new machine, let's make a few changes.<br/> 
                    
First, click the "General" tab, then choose "Advanced". Change both the "clipboard" and "drag" settings to "bidirectional". This function allows us to copy/paste from host to VM and vice versa.<br/>
<img src="https://github.com/user-attachments/assets/d88679e8-0d7a-4351-895a-9c5f341643c3"><br/>

Click "OK" to accept, then go to the "Network" option. Here, you'll need to set up two adapters: one for internet (labeled "NAT") and the other for your internal network (labeled "intnet"). <br/>
<img src="https://github.com/user-attachments/assets/5e9bda54-977a-4d28-9a99-ec3e5116db20">
<img src="https://github.com/user-attachments/assets/f58ec5aa-2b3a-406b-b1c9-d644b576208c"><br/>

Now, we're ready to start our machine and install Server 2022.

</p>
        
</div>
            </div>
            <div class="step" id="step3">
                <h2>Step 3: Install Active Directory and Set Up Routing Scheme.</h2>
                <p>Install Windows Server 2019 on the domain controller and configure IP addressing, the name, Active Directory, DHCP, and routing.</p>
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

