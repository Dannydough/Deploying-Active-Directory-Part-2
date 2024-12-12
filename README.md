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


