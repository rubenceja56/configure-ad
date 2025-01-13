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

- First, 2 virtual machines. A client and a Domain controller.
- Connect the client virtual machine DNS server to the Domain controller machine's DNS and disable firewall for internal comms.
- Test and confirm connection.
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
  
![DC 1 and Client 1](https://github.com/user-attachments/assets/e3ff5256-f9a5-4a57-8dda-499b37939230)

</p>
<p>
To configure an active directory we will first need 2 virtual machines. One will be our main client and the other will be our domain controller. The domain controller will be our server managing security, identity and granting access to other users. 
</p>
<br />

<p>
  
![Client 1 to DNS and firewall config](https://github.com/user-attachments/assets/3075a7c6-7a14-4630-9c6f-863b1507f6ed)

</p>
<p>
Here we configure the DNS re-route for the "client" virtual machine to re-route to the DNS address of the domain controller. Then we disable the firewall so that we may test that the client 1 and domain controller virtual machines are able to communicate directly with each other. 
</p>
<br />

<p>
  
![Confirming connection](https://github.com/user-attachments/assets/2532b7e9-a991-42bd-aa24-f9c92e3992e2)

</p>
<p>
Now we test that the connection between the client and domain controller's dns server is established. We do this by running windows powershell and doing a simple "Ping" test to the DNS address. We can see that 4 packets were sent to the DNS address and 4 packets were received back confirming the connection. We can also take a look at the "Ethernet adapter" settings by doing a "ipconfig /all" which clearly shows that the clients DNS server is connected to 10.0.0.4 which is the DNS server of the domain controller. 
</p>
<br />

<p>
  
![Config and Promote server](https://github.com/user-attachments/assets/170c0bf5-f6a1-4362-8872-caf15c059f8f)


</p>
<p>
Lastly, we set up the server manager and by clicking on the flag on the top right we also can promote the server to officially be the domain controller. Once we've configured the server manager and promoted it to domain controller we can start creating users, granting access or denying access for users, as well as creating "group policy" and much much more.
</p>
<br />
