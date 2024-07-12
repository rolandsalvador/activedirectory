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

<h2>Contents</h2>

[1. Setting up the virtual machines](#1-setting-up-the-virtual-machines)<br />
[2. Configuring the domain controller's NICs](#2-configuring-the-domain-controllers-nics)<br />
[3. Installing Active Directory Domain Services](#3-installing-active-directory-domain-services)<br />
[4. Creating a domain](#4-creating-a-domain)<br />
[5. Creating an admin user](#5-creating-an-admin-user)<br />
[6. Installing and configuring RAS](#6-installing-and-configuring-ras)<br />
[7. Installing and configuring DHCP](#7-installing-and-configuring-dhcp)<br />
[8. Programmatically creating 1,000 sample users](#8-programmatically-creating-1000-sample-users)<br />
[9. Configuring the domain client](#9-configuring-the-domain-client)<br />
[10. Testing connectivity](#10-testing-connectivity)<br />
[Next steps](#next-steps)<br />

<h2>Walkthrough</h2>

<h3>1. Setting up the virtual machines</h3>
<br />
<br />
<img src="https://i.imgur.com/GngsHag.png"/>

<br />
<br />
<img src="https://i.imgur.com/mvj6j9j.png"/>

<h3>2. Configuring the domain controller's NICs</h3>
<br />
<br />
<img src="https://i.imgur.com/9cB4OmC.png"/>

<br />
<br />
<img src="https://i.imgur.com/D6H3fNc.png"/>

<h3>3. Installing Active Directory Domain Services</h3>
<br />
<br />
<img src="https://i.imgur.com/Pzk3C1n.png"/>

<br />
<br />
<img src="https://i.imgur.com/BOCWNF9.png"/>

<h3>4. Creating a domain</h3>
<br />
<br />
<img src="https://i.imgur.com/bdi0gSC.png"/>

<h3>5. Creating an admin user</h3>
<br />
<br />
<img src="https://i.imgur.com/BG5DE16.png"/>

<h3>6. Installing and configuring RAS</h3>
<br />
<br />
<img src="https://i.imgur.com/upouICj.png"/>

<br />
<br />
<img src="https://i.imgur.com/VKtPrlO.png"/>

<h3>7. Installing and configuring DHCP</h3>
<br />
<br />
<img src="https://i.imgur.com/OOBBf5L.png"/>

<br />
<br />
<img src="https://i.imgur.com/Ed3iI4C.png"/>

<br />
<br />
<img src="https://i.imgur.com/jTciWaN.png"/>

<h3>8. Programmatically creating 1,000 sample users</h3>
<br />
<br />
<img src="https://i.imgur.com/K6QSL9Y.png"/>

<br />
<br />
<img src="https://i.imgur.com/qbkx0Ws.png"/>

<h3>9. Configuring the domain client</h3>
<br />
<br />
<img src="https://i.imgur.com/bNfQMSx.png"/>

<br />
<br />
<img src="https://i.imgur.com/TqHdGMQ.png"/>

<br />
<br />
<img src="https://i.imgur.com/hDQk8Ls.png"/>

<h3>10. Testing connectivity</h3>
<br />
<br />
<img src="https://i.imgur.com/w1NJ0HX.png"/>

<br />
<br />
<img src="https://i.imgur.com/EY5yUyd.png"/>

<h3>Next steps</h3>

