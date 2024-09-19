<h5>Directory</h5> 

<b>[Tech Portfolio Home](https://github.com/Jays1115/Jalen-Smith.git)</b>
<b>[AWS Projects](https://github.com/Jays1115/AWS-Projects.git)</b>

# Peering-VPCs

<h2>Description</h2>
Scenario: The organization set up separate virtual private clouds (VPCs) for the Marketing, Development, and Finance departments to enhance security, but this isolation requires Marketing and Development to raise tickets to access Finance reports, reducing productivity. They are seeking solutions to streamline access to these reports without compromising the security of the isolated VPCs.
<br><br>
Solution: Establish a peering connection between the Marketing and Finance VPCs. Similarly, setting up a peering connection between the Development and Finance VPCs.

<h2>Program walk-through:</h2>

<p align="center">
Accessed the “Your VPCs” page in the VPC Dashboard to view all active VPCs: <br/>
<img src="images/Screenshot 2024-09-19 at 8.01.56 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.02.24 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Accessed the running EC2 instances, where each server is named to match its corresponding VPC: <br/>
<img src="images/Screenshot 2024-09-19 at 8.04.57 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.06.17 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Selected the Finance server, copied its IP address, and reviewed its subnet ID: <br/>
<img src="images/Screenshot 2024-09-19 at 8.08.41 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.09.12 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Connected to the marketing server via the Session Manager: <br/>
<img src="images/Screenshot 2024-09-19 at 8.13.20 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.13.52 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.14.20 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Perform this command, "ping 172.31.1.110", to verify that there is no connection from the Marketing server to the Finance server: <br/>
<img src="images/Screenshot 2024-09-19 at 8.17.02 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Returned to the previous tab to view the Market server's instance ID and clicked on it: <br/>
<img src="images/Screenshot 2024-09-19 at 8.19.49 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.19.58 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>
