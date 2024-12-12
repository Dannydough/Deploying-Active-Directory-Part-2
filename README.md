<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic


<h2>Actions and Observations</h2>

1) Configure Remote Desktop access for non-administrative users on Client-1:
Log in to Client-1 using the credentials: mydomain.com\jane_admin.

<p>
<img src="https://imgur.com/N5hY8gp.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
  
Navigate to System Properties.

<p>
<img src="https://imgur.com/4vVdkqx.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
Select the Remote Desktop tab.

<p>
<img src="https://imgur.com/33K8WUB.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>

2) Click Select Users... under the Remote Desktop section.

<p>
<img src="https://imgur.com/HDY7Bte.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
In the "Remote Desktop Users" window, click Add....

  <p>
<img src="https://imgur.com/I85c2ov.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
Enter Domain Users in the object name field and click Check Names to verify. After that, Click OK to add the group.

  <p>
<img src="https://imgur.com/foCyKJd.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>

You can now log in to Client-1 as a standard, non-administrative user.

For a more scalable approach, this configuration is typically managed using Group Policy, which allows you to apply these settings across multiple systems simultaneously. 


Create multiple additional users and attempt to log in to Client-1 using one of the newly created accounts.

3) To set up the users, follow these steps:

Log in to DC-1 using the credentials: mydomain.com\jane_admin.

  <p>
<img src="https://imgur.com/0cGlorm.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
Open PowerShell ISE as an administrator.

  <p>
<img src="https://imgur.com/KiyJbMN.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>

4) Create a new file in Powershell ISE & then run the provided PowerShell script to create the user accounts. Observe the process as the accounts are generated.

  <p>
<img src="https://imgur.com/BOtwAAv.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>

  <p>
<img src="https://imgur.com/hBRzuiy.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
5) Once the script completes, open Active Directory Users and Computers (ADUC).

  <p>
<img src="https://imgur.com/yRjOe7f.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
6) Navigate to the appropriate organizational unit (OU), _EMPLOYEES. Verify that the newly created accounts are listed in this OU.

  <p>
<img src="https://imgur.com/xQSt9BL.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>

7) Use one of the newly created accounts to attempt logging in to Client-1.
Refer to the password specified in the PowerShell script for the account.
Confirm that the login is successful.

  <p>
<img src="https://imgur.com/Wupga0P.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>

  <p>
<img src="https://imgur.com/5wwuiZz.png" height="80%" width="80%" alt="Configuration Steps"/>
</p>
<p>
  
If the login fails, ensure that:
The account is correctly created and not disabled.
The "Domain Users" group has been added to the Remote Desktop Users on Client-1.
The password entered matches the one defined in the script.
