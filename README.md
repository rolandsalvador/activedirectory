<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
In this lab, I configured Active Directory Domain Services, a domain controller, and a client computer. The domain controller acts as a DHCP server for the virtual machine subnet, VMnet0. The client computer acts as a DHCP client for the doamin controller. The domain controller also contains a NIC for public use to connect to the internet. The network topology is seen below:

<br />
<br />
<p align="center">
<img src="https://i.imgur.com/vCcndHL.png" height="50%" width="50%"/>

In the walkthrough below, I detail many of the steps I took to configure Active Directory for the domain controller and client. Thank you for taking a look!

<h2>Skills Used</h2>

- <b>Active Directory</b> 
- <b>Networking Fundamentals</b>
- <b>DHCP</b>
- <b>Windows Configuration</b>
- <b>Virtualization</b>

<h2>Environments Used </h2>

- <b>Windows Server 2019</b>
- <b>Windows 10 Pro</b>
- <b>VMware Workstation Pro</b>

<h2>Walkthrough</h2>

<!--
<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
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
--!>
