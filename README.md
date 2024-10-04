<h5>Directory</h5> 

<b>[Tech Portfolio Home](https://github.com/Jays1115/Jalen-Smith.git)</b> /
<b>[AWS Projects & Labs](https://github.com/Jays1115/AWS-Projects.git)</b>

# Peering-VPCs

<h2>Description</h2>
Scenario: The organization set up separate virtual private clouds (VPCs) for the Marketing, Development, and Finance departments to enhance security, but this isolation requires Marketing and Development to raise tickets to access Finance reports, reducing productivity. They are seeking solutions to streamline access to these reports without compromising the security of the isolated VPCs.
<br><br>
Solution: Establish a peering connection between the Marketing and Finance VPCs. Similarly, setting up a peering connection between the Development and Finance VPCs.

<h2>Program walk-through:</h2>

<h3 align="center">Peering the Marketing & Finance VPCs</h3>
<h4>Pt. 1 > Testing the Connection</h4>

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

<h4>Pt. 2 > Creating the VPC Peer Connection</h4>

<p align="center">
Returned to the previous tab to view the Market server's instance ID and clicked on it: <br/>
<img src="images/Screenshot 2024-09-19 at 8.19.49 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.19.58 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Clicked on the associated subnet, then accessed the related route table. Navigated to the routes tab to review the existing routes of the Marketing Public Subnet: <br/>
<img src="images/Screenshot 2024-09-19 at 8.22.09 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.24.54 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Used the left sidebar to navigate to Peering Connections page, then proceeded to create a new peering connection: <br/>
<img src="images/Screenshot 2024-09-19 at 8.26.22 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.26.36 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Named the peering connection “Marketing <> Finance,” designating the Marketing VPC as the requestor and the Finance VPC as the acceptor. The peering connection is now pending between the two VPCs: <br/>
<img src="images/Screenshot 2024-09-19 at 8.28.25 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.29.08 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.29.28 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Accepted the VPC peering request and now the peer connection is active: <br/>
<img src="images/Screenshot 2024-09-19 at 8.31.32 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.31.41 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.31.50 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<h4>Pt. 3 > Modifying Subnet Route Tables</h4>

<p align="center">
Navigated back to the Marketing Public Subnet Route Table to modify the routes: <br/>
<img src="images/Screenshot 2024-09-19 at 8.35.30 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.36.52 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.37.48 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Edited the routes to include the newly created peering connection, ensuring proper communication between the Marketing and Finance VPCs: <br/>
<img src="images/Screenshot 2024-09-19 at 8.39.26 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.41.14 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.41.28 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Accessed the Finance Private Subnet Route Table to update the routes: <br/>
<img src="images/Screenshot 2024-09-19 at 8.45.25 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.45.58 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.46.23 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Edited the routes to include the newly created peering connection, ensuring proper communication between the Marketing and Finance VPCs: <br/>
<img src="images/Screenshot 2024-09-19 at 8.48.50 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.50.04 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.50.29 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<h4>Pt. 4 > Updating the Finance Security Group Inbound Rules</h4>

<p align="center">
Navigated to the Finance Server’s Security Group to edit its inbound rules: <br/>
<img src="images/Screenshot 2024-09-19 at 8.57.47 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 8.58.13 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Added a rule to permit ICMP traffic from the 10.10.0.0/16 subnet: <br/>
<img src="images/Screenshot 2024-09-19 at 9.00.12 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.00.20 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
The Marketing server is now able to successfully communicate with the Finance server. This connection allows for seamless data exchange between the two VPCs while maintaining the integrity of security measures, enabling more efficient collaboration between the departments without compromising sensitive information: <br/>
<img src="images/Screenshot 2024-09-19 at 9.01.51 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<h3 align="center">Peering the Development & Finance VPCs</h3>
<h4>Pt. 1 > Creating the VPC Peer Connection</h4>

<p align="center">
Returned to the previous tab to view the Developer server's instance ID and clicked on it. Clicked on the associated subnet, then accessed the related route table. <br/>
<img src="images/Screenshot 2024-09-19 at 9.04.40 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.04.58 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Used the left sidebar to navigate to Peering Connections page, then proceeded to create a new peering connection. Named the peering connection “Developer <> Finance,” designating the Developer VPC as the requestor and the Finance VPC as the acceptor. The peering connection is now pending between the two VPCs: <br/>
<img src="images/Screenshot 2024-09-19 at 9.05.54 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.06.11 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.06.23 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Accepted the VPC peering request and now the peer connection is active: <br/>
<img src="images/Screenshot 2024-09-19 at 9.07.21 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.07.29 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.07.37 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<h4>Pt. 2 > Modifying Subnet Route Tables</h4>

<p align="center">
Navigated back to the Developer Public Subnet Route Table to modify the routes: <br/>
<img src="images/Screenshot 2024-09-19 at 9.08.24 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.08.36 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Edited the routes to include the newly created peering connection, ensuring proper communication between the Developer and Finance VPCs: <br/>
<img src="images/Screenshot 2024-09-19 at 9.08.45 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.10.13 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.10.22 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Accessed the Finance Private Subnet Route Table to update the routes. Edited the routes to include the newly created peering connection, ensuring proper communication between the Marketing and Finance VPCs: <br/>
<img src="images/Screenshot 2024-09-19 at 9.10.41 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.11.11 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.12.10 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.12.18 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<h4>Pt. 3 > Updating the Finance Security Group Inbound Rules</h4>

<p align="center">
Navigated to the Finance Server’s Security Group to edit its inbound rules: <br/>
<img src="images/Screenshot 2024-09-19 at 9.13.02 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.13.19 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
Created an additional rule, similar to the previous one, allowing ICMP traffic from the 172.168.0.0/16 subnet: <br/>
<img src="images/Screenshot 2024-09-19 at 9.14.49 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 1.34.18 PM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.15.13 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<p align="center">
The Developer server is now able to successfully communicate with the Finance server. This connection allows for seamless data exchange between the two VPCs while maintaining the integrity of security measures, enabling more efficient collaboration between the departments without compromising sensitive information: <br/>
<img src="images/Screenshot 2024-09-19 at 9.15.40 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="images/Screenshot 2024-09-19 at 9.16.14 AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

