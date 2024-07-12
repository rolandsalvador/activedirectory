<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
In this lab, I configured Active Directory Domain Services, a domain controller, and a client computer. The domain controller acts as a DHCP server for the virtual machine subnet, VMnet0. The domain controller also contains a NIC for public use to connect to the internet. The network topology is seen below. Thank you for taking a look!

<br />
<br />
<p align="center">
<img src="https://i.imgur.com/vCcndHL.png" height="50%" width="50%"/>

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
The domain controller is a Windows Server 2019 machine. Two NICs are configured on it, one NAT for internet connection, and one internal for VMnet0.
<br />
<br />
<img src="https://i.imgur.com/GngsHag.png"/>
The domain client is a Windows 10 Pro machine. Only an internal VMnet0 NIC is configured on it.
<br />
<br />
<img src="https://i.imgur.com/mvj6j9j.png"/>

[Back to top](#active-directory-home-lab)

<h3>2. Configuring the domain controller's NICs</h3>
Originally, the external NIC on the domain controller had “Obtain an IP address automatically” chosen in the settings, indicating that it’s the NAT interface. This IP address will be used to connect to the internet, and my physical home router will assign the address.
<br />
<br />
<img src="https://i.imgur.com/9cB4OmC.png"/>
The internal NIC originally had a 169.254.196.xxx link-local address, indicating that it's the virtual network interface. I manually set the IP address of this interface to 172.16.0.1.
<br />
<br />
<img src="https://i.imgur.com/D6H3fNc.png"/>
On both NICs, the DNS server address set to the loopback address, 127.0.0.1, because the domain controller will act as the DNS server.
<br />
<br />

[Back to top](#active-directory-home-lab)

<h3>3. Installing Active Directory Domain Services</h3>
After figuring out which NIC is which, I installed Active Directory Domain Services through the Add Roles and Features menu. Since I already have the domain set up, it appears in the list like this. However, “DomainController” was the option available upon initial setup.
<br />
<br />
<img src="https://i.imgur.com/Pzk3C1n.png"/>
Afterwards, I selected the Active Directory Domain Services role from the list.
<br />
<br />
<img src="https://i.imgur.com/BOCWNF9.png"/>

[Back to top](#active-directory-home-lab)

<h3>4. Creating a domain</h3>
Post-installation, I was prompted by Server Manager to promote this machine to a domain controller and create the domain. I selected “Add a new forest” and configured the name as “mydomain.com”
<br />
<br />
<img src="https://i.imgur.com/bdi0gSC.png"/>

[Back to top](#active-directory-home-lab)

<h3>5. Creating an admin user</h3>
In the Active Directory Users and Computers menu, I added an organizational unit named “_ADMINS” and created the “a-rsalvador” user as a member of the Domain Admins group. From this point on, I’ll be using this admin user to log into the domain controller instead of the actual administrator account.
<br />
<br />
<img src="https://i.imgur.com/BG5DE16.png"/>

[Back to top](#active-directory-home-lab)

<h3>6. Installing and configuring RAS</h3>
Next, I installed and configured RAS using the Add Roles and Features menu. This will let our client computer access the internet. When selecting “Remote Access,” “DirectAccess and VPN (RAS)” and “Routing” are automatically selected too.
<br />
<br />
<img src="https://i.imgur.com/upouICj.png"/>
I opened the Routing and Remote Access menu to use the setup wizard. Here we can see the two NICs that I configured previously. The public NIC must be selected.
<br />
<br />
<img src="https://i.imgur.com/VKtPrlO.png"/>

[Back to top](#active-directory-home-lab)

<h3>7. Installing and configuring DHCP</h3>
Afterwards, I installed the DHCP server role. This enables the domain controller to lease IP addresses to the client computers.
<br />
<br />
<img src="https://i.imgur.com/OOBBf5L.png"/>
Like I did for RAS, I opened the DHCP setup wizard. Since the DNS server will be the domain controller, I entered it’s IP address of 172.16.0.1.
<br />
<br />
<img src="https://i.imgur.com/Ed3iI4C.png"/>
The scope, or list of leasable addresses, that I selected ranges from 172.16.0.100 to 172.16.0.200.
<br />
<br />
<img src="https://i.imgur.com/jTciWaN.png"/>

[Back to top](#active-directory-home-lab)

<h3>8. Programmatically creating 1,000 sample users</h3>
In this step, I programmatically created 1,000 sample users in my domain. The script was graciously provided by Josh Madakor in his Active Directory
<a href="https://www.youtube.com/watch?v=MHsI8hJmggI"> setup video</a>. Each user is created with a randomly generated name taken from a text file. In addition, I created a user named "rsalvador" for my own login to the client computer later.
<br />
<br />
<img src="https://i.imgur.com/K6QSL9Y.png"/>
After running the script, we can see that there are a lot of users in the database now. I wanted to create this many users for when I expand this project further, such as when automating account configuration and group policies through scripting.
<br />
<br />
<img src="https://i.imgur.com/qbkx0Ws.png"/>

[Back to top](#active-directory-home-lab)

<h3>9. Configuring the domain client</h3>
I fired up the client computer, and the first thing I did was add it to the mydomain.com domain through Advanced System settings. I named the computer "CLIENT1."
<br />
<br />
<img src="https://i.imgur.com/bNfQMSx.png"/>
After restarting the machine, I checked the IP configuration in the command prompt. It was leased the IP address 172.16.0.101, which is in the DHCP scope I set earlier. Note that I was able to log into this machine using my regular “rsalvador” user.
<br />
<br />
<img src="https://i.imgur.com/TqHdGMQ.png"/>
The default gateway is set to 172.16.0.1, which is the domain controller’s virtual network IP address.
<br />
<br />
<img src="https://i.imgur.com/hDQk8Ls.png"/>

[Back to top](#active-directory-home-lab)

<h3>10. Testing connectivity</h3>
Finally, I tested the connectivity of the client computer. Back on the domain controller, we can now see “CLIENT1” in the Active Directory Users and Computers menu. Additionally, we can see the 172.16.0.101 IP address lease in the DHCP menu.
<br />
<br />
<img src="https://i.imgur.com/w1NJ0HX.png"/>
Back on the client computer, I pinged google.com to test internet connectivity. Thankfully, all the pings worked, confirming that everything was set up correctly.
<br />
<br />
<img src="https://i.imgur.com/EY5yUyd.png"/>

[Back to top](#active-directory-home-lab)

<h3>Next steps</h3>
That concludes my basic setup of Active Directory in a virtualized environment! 
<br />
<br />
There’s a lot more things that I want to do with this lab to expand it further. As mentioned before, I want to write PowerShell and Python scripts to automate tasks such as user account configuration. In addition, I want to configure multiple domain sites and create subforests of my current domain.
<br />
<br />
I had fun working on this project, so I want to continue learning about Active Directory. If you’ve made it this far, thank you again for taking a look!
<br />
<br />

[Back to top](#active-directory-home-lab)
