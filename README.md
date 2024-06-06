<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Inspecting Protocol Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines & Wireshark](https://www.youtube.com/watch?v=PPk4E1yfXT0&t=23s)

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

- Create Environment (Azure VM1 & 2)
- Observing ICMP Traffic
- Observing SSH Traffic
- Observing DHCP Traffic
- Observing DNS Traffic
- Observing RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img width="684" alt="vms" src="https://github.com/qjackson14/nsgs/assets/156969011/82dc53e7-5a00-4f86-9087-d0749f79cd5b">
</p>
<p>
Create Virtual Machines
</p>
<br />

<p>
<img src="https://github.com/qjackson14/nsgs/assets/156969011/3ff035f9-303e-4eb2-97ff-99445dafe69d">
</p>
<p>
Login to VM1 via RDP
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Download Wireshark -> Select Capture Packets -> Filter ICMP Traffic
</p>
<br />

<p>
<img width="310" alt="ping vm2" src="https://github.com/qjackson14/nsgs/assets/156969011/d247bdda-d2d4-4dd3-a9cd-249ecd30e1e2"><img width="312" alt="ping google com" src="https://github.com/qjackson14/nsgs/assets/156969011/896d0414-8c24-4fb7-b647-ccb4cfeca990">
</p>
<p>
Ping VM2's private IP -> Ping www.google.com
</p>
<br />

<p>
<img width="559" alt="wireshark icmp" src="https://github.com/qjackson14/nsgs/assets/156969011/0b26dd84-52e0-4641-9749-e646e7c02879">
</p>
<p>
Observe Wireshark ICMP traffic between VM1 & 2 also traffic between VM1 & Google's public IP address
</p>
<br />

<p>
<img width="312" alt="ping -t vm2" src="https://github.com/qjackson14/nsgs/assets/156969011/18a07baa-d1c8-41cc-a085-2cb742d49326">
</p>
<p>
Send continuous ping to VM2 (ping 10.0.0.5 -t)
</p>
<br />

<p>
<img width="177" alt="network settings vm2" src="https://github.com/qjackson14/nsgs/assets/156969011/5d3e1718-8741-4bb5-8f10-4116e17297b6">
</p>
<p>
Go to VM2's Network Settings
</p>
<br />

<p>
<img width="427" alt="deny icmp" src="https://github.com/qjackson14/nsgs/assets/156969011/bc8eee97-a03e-42df-8203-b6d3fb9c5982">
</p>
<p>
Scroll to Network Security Group -> Click Create port rule -> Select Inbound port Rule/ICMP/Deny/Set Priority to be first rule traffic goes through.
</p>
<br />

<p>
<img width="311" alt="imcp blocked traffic" src="https://github.com/qjackson14/nsgs/assets/156969011/fecc3f06-b3d4-4d86-931e-d3d67dab0ab9">
</p>
<p>
View blocked traffic via command prompt from firewall setup in NSG
</p>
<br />

<p>
<img width="312" alt="ssh login" src="https://github.com/qjackson14/nsgs/assets/156969011/14298a50-362b-4939-9772-4822425ea683">
</p>
<p>
Login to VM2 command prompt using SSH
</p>
<br />

<p>
<img width="561" alt="wireshark ssh traffic" src="https://github.com/qjackson14/nsgs/assets/156969011/5080e6e2-1d13-487e-acdd-6c78c6e3c91d">
</p>
<p>
Observe SSH traffic in Wireshark
</p>
<br />

<p>
<img width="311" alt="ipconfig renew" src="https://github.com/qjackson14/nsgs/assets/156969011/ec897896-2707-4a83-8a12-fe6f77b334cf">
</p>
<p>
ipconfig /renew to trigger DHCP traffic
</p>
<br />

<p>
<img width="560" alt="dhcp traffic" src="https://github.com/qjackson14/nsgs/assets/156969011/dad36fdd-b6df-434d-8da9-792ec5096b6d">
</p>
<p>
Observe DHCP traffic in Wireshark.
</p>
<br />

<p>
<img width="313" alt="nslookup" src="https://github.com/qjackson14/nsgs/assets/156969011/d76625e6-00d6-4f67-ab8d-304faedb652b">
</p>
<p>
"nslookup" to trigger DNS traffic
</p>
<br />

<p>
<img width="560" alt="wireshark dns traffic" src="https://github.com/qjackson14/nsgs/assets/156969011/fe505831-7e72-4a83-8367-de67c918e86b">
</p>
<p>
Observe DNS traffic in Wireshark
</p>
<br />

<p>
<img width="560" alt="wireshark rdp traffic" src="https://github.com/qjackson14/nsgs/assets/156969011/b5bd8d11-02c9-4291-8737-4d4b11763863">
</p>
<p>
Filter "tcp port == 3389" to observe RDP traffic in Wireshark
</p>
<br />
