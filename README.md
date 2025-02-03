<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines. It guides you through setting up Active Directory Domain Services (AD DS) in Azure using Windows Server VMs, covering the installation and promotion of a domain controller, the creation of organizational units (OUs), domain user management, and the process of joining a client machine to the domain. Additionally, it includes configuring remote desktop access for domain users, ensuring a functional Active Directory environment within an Azure-based infrastructure.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1:  Install Active Directory
- Step 2:  Create Organizational Units (OUs)
- Step 3:  Join Client-1 to Domain
- Step 4:  Configure Remote Desktop
- Step 5:  Create Additional Users

<h2>Deployment and Configuration Steps</h2>

<h3>Step 1:  Install Active Directory</h3>
 
  Log into DC-1 and install Active Directory Domain Services. Promote the server to a Domain Controller (DC) and set up a new forest (e.g., mydomain.com). Restart and log back into DC-1 as mydomain.com\labuser.

<h3>Step 2:  Create Domain Admin User</h3>

  In Active Directory Users and Computers (ADUC), create two Organizational Units (OUs): _EMPLOYEES and _ADMINS. Add a user named Jane Doe with the username jane_admin. Set the password as Cyberlab123! and add jane_admin to the Domain Admins group. Log in as jane_admin    for future administrative tasks.

<h3>Step 3:  Join Client-1 to Domain</h3>

  Set Client-1’s DNS settings to DC-1’s private IP in the Azure Portal. Restart Client-1 and join it to the domain mydomain.com. Verify the domain join by checking ADUC and create a new OU called _CLIENTS, moving Client-1 into it.

<h3>Step 4:  Configure Remote Desktop</h3>

  Log into Client-1 as jane_admin and enable Remote Desktop for domain users through system properties. Now, non-administrative users can log into Client-1. For more systems, this setup can be automated via Group Policy.

<h3>Step 5:  Create Additional Users</h3>

  Use PowerShell to create multiple users under the _EMPLOYEES OU. After the script runs, verify the accounts in ADUC and attempt to log into Client-1 using one of the new user accounts.
