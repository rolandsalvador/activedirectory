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
<h3>2. Configuring the domain controller's NICs</h3>
<h3>3. Installing Active Directory Domain Services</h3>
<h3>4. Creating a domain</h3>
<h3>5. Creating an admin user</h3>
<h3>6. Installing and configuring RAS</h3>
<h3>7. Installing and configuring DHCP</h3>
<h3>8. Programmatically creating 1,000 sample users</h3>
<h3>9. Configuring the domain client</h3>
<h3>10. Testing connectivity</h3>
<h3>Next steps</h3>
