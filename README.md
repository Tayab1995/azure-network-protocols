<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, DHCP, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04


<h2>Actions and Observations</h2>
<h3> Step 1 Create resource groups and virtual machines</h3>

- In Microsoft Azure, create a resource group and two virtual machines. Creating the VM will also allow you to create a new virtual network aka (Vnet).
- Create a - Windows 10 client virtual machine and an Linux (Ubuntu) server. Use the same Vnet that was created for your Windows VM.

<p>
<img src="https://i.imgur.com/qjHm1Fd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

 <h3> Step 2 Install “download” and Run Wireshark</h3>
  
  - Log in into your Remote Desktop Windows Virtual Machine and open your internet browser and search "download Wireshark" and download it from the actual website.  -   
  - Wireshark is a network protocol analyzer. It is the most widely used network analyzer “like sniffing traffic.”
  
<p>
<img src="https://i.imgur.com/o044LwN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

 <h3> Step 3 Inspect IMCP Traficc on Wireshark</h3>

- Open Wireshark and click on the blue fin icon located right under the file menu.  Once you click on that icon, Wireshark will start analyzing all network traffic on the virtual machine.
 
 - Using Remote Desktop Windows 10 Virtual Machine go to Wireshark to filter traffic for ICMP by typing it in the filter bar and clicking on the blue arrow button to the right to start the filter.
 
- Retrieve the private IP address of the Linux (Ubuntu) virtual machine and ping it in the Windows 10 virtual machine.

- From the Windows 10 virtual machine open PowerShell and attempt to ping the private IP address of VM 2 server and observe the requests and replies within Wireshark.

- From the Windows 10 virtual machine, open PowerShell and attempt to ping www.google.com and observe the traffic in Wireshark. 

- From the PowerShell, you can see the packets of data sent and the statics at the bottom.  

<p>
<img src="https://i.imgur.com/8RqVyag.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

 <h3> Step 4 To Deny IMCP Ping Request on NSG </h3>

- To deny the ICMP ping request, you need to add this rule to our Network Security Group inside the Virtual Machine and once we've added this rule to “Linux (Ubuntu) Virtual machine 2”, we can see that the traffic times out in PowerShell along with Wireshark displaying a reply to this request Timed out. 

<p>
<img src="https://i.imgur.com/b2XxbEq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

 - Wireshark and PowerShell will timed out after denying ICMP (ping) traffic.

<p>
<img src="https://i.imgur.com/6ZfV5am.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>


 - In Microsoft Azure network security group settings. Select “Deny ICMP” settings and “Allow ICMP“ traffic to resume. 

<p>
<img src="https://i.imgur.com/u1seycF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

 
- In your Windows 10 virtual machine, observe your “Linux Ubuntu” server Virtual Machine 2 and inspect the packets.
 
 - You should see traffic resuming again 

<p>
<img src="https://i.imgur.com/HWtMNNU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Congratulations !!
