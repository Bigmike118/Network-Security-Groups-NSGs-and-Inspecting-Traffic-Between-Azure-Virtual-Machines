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

- Dealing with Account Lockouts
- Navigating Active Directory
- Enabling and Disabling Accounts

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/t2PotvL.png"/>
</p>
<p>

Dealing with Account Lockouts
Using a VM that was created for a Domain Controller (DC-1), log in (For more info, visit this repository https://github.com/Bigmike118/Bigmike118-On-premises-Active-Directory-Deployed-in-the-Cloud-Azure-).

Start -> Active Directory Users and Computers -> mydomain.com -> _Employees -> any generated employee on the list will work.


<p>
<img src="https://i.imgur.com/Dbj1Jha.png"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/bdv2xAI.png"/>
</p>
<p>

  
Start -> Active Directory Users and Computers -> Computer Configuration -> Policies -> Security Settings -> Account Policies -> Account Lockout Policy -> Security Policy Settings

Here, policies revolving around account lockout can be configured. After configuring, open command prompt and type "gpupdate /force" to force the policy updates that were made. Typing "gpupdate /result" will show the results of the "gpupdate /force".


  
Attempt to log into Client-1 with it 10 times with a bad password. If done policies are correct, the account will get locked out.

Next, go back into "Active Directory Users and Computers" and find the user that was locked out. Click on the username and go into "Properties" -> Account -> checkmark "Unlock Account". 

User should be able to log back in 
  
</p>
<br />

<p>
<img src="https://i.imgur.com/aSUTKsj.png"/>
</p>
<p>

Enabling and Disabling Accounts, Resetting Password

Navigate back to the list of users under "_EMPLOYEES" and click on a user. Here, the options of disabling or resetting a password is available, simply click on the option needed.
