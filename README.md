<h1>Azure Virtual Network Peering Project</h1>


<h2>Description</h2>
In this project, I created and connected Virtual Networks from different regions which allowed the virtual machines in these networks to communicate with each other. 
<br />

<p align="center">
<img src="https://i.imgur.com/VpZmo5i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h2>Languages and Utilities Used</h2>
- Azure DNS services<br/> 
- Bash<br/> 
- PowerShell<br/> 

<h2>Environment Used</h2>
- Windows Server 2019<br/> 

<p align="center">
<h2>Part 1-Created Virtual Networks and Subnets:</h2>

<p align="center">
Creating virtual Networks and Subnets: <br/>
The 3 virtual networks were created: 1.CoreServices (East US), 2. Manufacturing(West Europe), 3. Research (Southeast Asia)<br/>
<img src="https://i.imgur.com/wf7fMfA.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Subnets that were created for the Coreservices VNet: <br/>
<img src="https://i.imgur.com/u3RQyxL.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">
Subnets that were created for the Manufacturing VNet: <br/>
<img src="https://i.imgur.com/SuNuWnb.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Subnets that were created for the Research VNet: <br/>
<img src="https://i.imgur.com/LCKRoBc.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />



<p align="center">
<h2>Part 2-Configured DNS for company Dannytech :</h2>
<p align="center">
A Private DNS zone was created for Dannytech.com.The VNets were all linked for auto-registration and resolution. When creating the VNet links, it's important to check the "enable autoregistration" box for this feature to work. <br/>
<img src="https://i.imgur.com/niF7kfl.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Created the VNet Links for all 3 VNets <br/>
<img src="https://i.imgur.com/tNjASge.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/1cF69oh.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>



<p align="center">
Two virtual machines were created to test the DNS configurations. <br/>
<img src="https://i.imgur.com/befLjRO.jpg"80%" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
We can see here that A records were created automatically for these VMs showing the auto-registration feature. <br/>
<img src="https://i.imgur.com/bdanQHK.jpg" width="80%" alt="Disk Sanitization Steps"/>

<p align="center">
Remoted into VMs using RDP to confirm that we are able to ping each other. We can see here that the ping attempts from Pvm1 to Pvm2 was successful. <br/>
PS. Microsoft Firewall needs to be turned off. <br/>
<img src="https://i.imgur.com/z3VhYjy.jpg" width="80%" alt="Disk Sanitization Steps"/>

<br />
<br />

<p align="center">
<h2>Part 3-Connected 2 Virtual Networks (Coreservices VNet (East US) to Manufacturing VNet (West Europe) ) :</h2>
<p align="center">
Created a VM (Pvm3) for the Manufacturing VNet which will be used to test the peering. <br/>
<img src="https://i.imgur.com/nltA8tc.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p align="center">
Remoted into Pvm1(Coreservices VNet) and Pvm3(Manufacturing VNet) to test connectivity between VNets. The "Test-NetConnection (target IP) -port 3389" command was used in Powershell to test TCP connectivity between VNets. Here we can see that the connection failed on both VMs. This is expected as no peering link was created. <br/>
<img src="https://i.imgur.com/kcpwb7g.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/><br />
<br />
<p align="center">
Created a Global VNet Peering link in the Coreservices VNet. Selected Peering and created Peering link to Manufacturing VNet as shown below. <br/>
<img src="https://i.imgur.com/2IcdItv.jpg" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Here we can see a successful peering link which shows a "connected" status. <br/>
<img src="https://i.imgur.com/LrKRdb1.jpg" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p align="center">
Retried testing the connectivity between VNets which showed successful results. <br/>
<img src="https://i.imgur.com/mQ2Syeb.jpg" width="80%" alt="Disk Sanitization Steps"/>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
