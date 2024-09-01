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
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
For the first step, you'll need to download and install the required software. For this project, I used Oracle VirtualBox as my hypervisor (Note: You'll need to download the "Extension Pack", as well), along with Windows Server 2022 and Windows 10 ISOs. Feel free to use the links I've posted above for faster reference. It's advisable to keep your ISOs centrally located so they're easy to find. <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br/> 
<br />
<br />
Now that we've completed that portion, we can begin building our lab. We'll start with Server '22 as this will be our "domain controller". <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/><br/>
Remember to keep your VM's base memory and processor count within the limits of what's available on your own computer.<br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br />
<br />
Before we start our new machine, let's make some changes. First, click the "general" tab, then choose "advanced". Change both the "clipboard" and "drag" options to "bidirectional". This function allows us to copy/paste from host to virtual machine and vice-versa. This will come in handy later on.  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
Next, we'll need to set up our network adapters. Leave adapter 1 as is, enable adapter 2 then choose "internal network". This will provide a connection for our client computer(s). Now, we're ready to start our machine.
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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

