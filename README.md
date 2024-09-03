<h1>Active Directory Home Lab</h1>

<h2>Description</h2>

Welcome to my Active Directory Home Lab Project! This project is designed to help IT enthusiasts and professionals set up a simulated Active Directory environment. By following this guide, you'll gain hands-on experience with AD administration, user and group management, Group Policy settings, and essential networking services like DNS and DHCP.

Whether you're preparing for certifications, enhancing your skills, or just exploring AD functionalities, this home lab provides a practical and controlled environment to experiment and learn.



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


<h2>Program walk-through:</h2>

<p align="center">
Here's our project diagram. This outlines everything we'll be building today.: <br/>
<img src="https://github.com/user-attachments/assets/4473f618-d5dd-456b-ae97-5b8d7f37140c"/><br/>
<br />
<br />
For the first step, you'll need to download and install the required software. For this project, I used Oracle VirtualBox as my hypervisor (Note: You'll need to download the "Extension Pack", as well), along with Windows Server 2022 and Windows 10 ISOs. Feel free to use the links I've posted above for faster reference. It's advisable to keep your ISOs centrally located so they're easy to find. <br/>
 
<br />
<br />
Now that we've completed that portion, we can begin building our lab. We'll start with Server '22 as this will be our "domain controller". <br/>
<img src="https://github.com/user-attachments/assets/e0c42c92-0a14-481f-9ff4-72bab482f045"/><br/>
<br/>
Remember to keep your VM's base memory and processor count within the limits of what's available on your own computer.<br/>
<img src="https://github.com/user-attachments/assets/45d3c212-faab-4b1e-8499-973bc8a0f3ec"/><br/>
<img src="https://github.com/user-attachments/assets/603468c1-fb13-406a-8fa4-6e92a6c77615"/><br/> 
<br />
<br />
Before we start our new machine, let's make some changes. First, click the "general" tab, then choose "advanced". Change both the "clipboard" and "drag" options to "bidirectional". This function allows us to copy/paste from host to virtual machine and vice-versa. This will come in handy later on.  <br/>
<img src="https://github.com/user-attachments/assets/9a7db6bf-8564-4b06-ac17-255696ca2835"/><br/>
Next, we'll need to set up our network adapters. Leave adapter 1 as is, enable adapter 2 then choose "internal network". This will provide a connection for our client computer(s). Now, we're ready to start our machine.
<img src="https://github.com/user-attachments/assets/c0309f83-ce3c-4b9f-a68b-000e7cd861ac"/><br/>
<img src="https://github.com/user-attachments/assets/e7c42183-bc2a-49b6-9bd2-d1a862756ee9"/><br/>
<br />
<br />
With those steps completed, we can begin installation of our Server ISO. Just follow the on-screen prompts until you reach this screen and choose either of the "desktop experience" options. Otherwise, you'll only have a command line. After that, choose the "custom install", as this is a new machine.<br/>
<img src="https://github.com/user-attachments/assets/b5cf429e-08db-4ca6-a13b-ff03b4023483"/><br/>
<img src="https://github.com/user-attachments/assets/612f865e-2791-4f97-bcb2-0b1ada95c0e6"/><br/>
<br />
<br />
From there, you'll get this screen. Best practice is to choose a password that's easy to remember. Since this is a lab environment, security isn't an issue. Once you've done that, click "finish".  <br/>
<img src="https://github.com/user-attachments/assets/c144e70e-4ec0-4391-bb7c-f55af067ce1e"/><br/>
<br />
<br />
Congratulations! Your server is now built and ready for use.  Let's get signed in.  <br/>
<img src="https://github.com/user-attachments/assets/1e3ea6ca-5a6f-4ae9-82bb-f80684e012f0"/>
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

