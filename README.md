<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

![active 1](https://github.com/user-attachments/assets/7c63d076-3fec-4f23-a179-10c194d241f3)

<p>
To begin, I created a Resource Group titled 'Active Directory'. I then made 2 virtual machines (one titled DC-1 & then other titled Client-1) and placed them in that resource group. I set DC-1's Private Address as Static & set Client-1’s DNS settings to DC-1’s Private IP address.
</p>
<br />

![active 3](https://github.com/user-attachments/assets/07534632-60ba-4414-a498-774a245d805c)

<p>
I Logged into the VM for DC-1 and disabled the Windows Firewall (for testing connectivity) by typing in the 'Run' section 'wf.msc'
</p>
<br />

![active 3](https://github.com/user-attachments/assets/07534632-60ba-4414-a498-774a245d805c)

<p>
I restarted Client-1's VM, then I attempted to ping DC-1’s private IP address, which succeeded. And ran ipconfig /all on PowerShell. The output for the DNS settings showed DC-1’s private IP Address which was successful as well.

</p>
<br />

![active 1](https://github.com/user-attachments/assets/7c63d076-3fec-4f23-a179-10c194d241f3)

<p>
I installed Active Directory Domain Services on DC-1 & setup a new forest as 'mydomain.com' (can be anything) Then I restarted the VM and logged back in DC-1 as user: mydomain.com\labuser

</p>
<br />

![active 5](https://github.com/user-attachments/assets/adb80dd2-f18a-4c80-a622-7b8a8391cba2)


<p>
In Active Directory Users and Computers (ADUC), I created 2 Organizational Units (OU), called “_EMPLOYEES” & “_ADMINS”. Also, I created a new employee named “Jane Doe” with the username of “jane_admin” & added jane_admin to the “Domain Admins” Security Group. Then I logged back into the DC-1 VM as “mydomain.com\jane_admin”.

</p>
<br />

![Active 6](https://github.com/user-attachments/assets/99d8df8f-1380-4385-a71b-71c5ef0394ec)

<p>
Lastly, I Logged into Client-1 as the original local admin (labuser) and joined it to the Active Directory Domain. Then, I Logged back into the Domain Controller and verified Client-1 shows up in the ADUC and is now a useable computer for the Active Directory.

</p>
<br />
