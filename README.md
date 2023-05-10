<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
we will observe various network traffic and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups.
to help have a better view what happens between this two VMs, using some protocols. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)
- powershell

<h2>Operating Systems Used </h2>

- Windows 10 
- Ubuntu Server 20.04 


<h2>Actions and Observations</h2>


The first requirement on the lab is to have set your resource group. including your VM-1 and VM-2 (virtual machine) here is a image below of the topoly and using remote desktop, use IP of your VM-1 and use your VM-1 user information.
</p>
<br />

<p>
<img src="https://i.imgur.com/022sbPa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After Downloading "wireshark" on your VM-1 (Virtual Machine) lets run "ICMP" traffic on "Wireshark" and use "Powershell" to ping private IP Address of VM-2. and see the Request and Reply of both Virtual Machines image below. 
</p>
<br />

<p>
<img src="https://i.imgur.com/LKRw7jO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now lets use a perpetual ping on Powershell to VM-2 to see the traffic between both VMs and open up Azure to use Network Security Group on VM-2 to stop any "ICMP" traffic. lets observe what happens in "Wireshark" and "Powershell".
</p>
<br />

<p>
<img src="https://i.imgur.com/nIjPmY5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Observe the how in "wireshark" the "Request and Reply" changes to "Request" as soon as adding this change in our Network Security Group acting like a Firewall. blocking this "ICMP" traffic, you can see the change in "Powershell" as well. 
  
<p>
<img src="https://i.imgur.com/AGkj9lD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Now going back to Azure to the Network Security Group in VM-2 lets allow "ICMP" now that we blocked this traffic. you can see how the "request" will start to get a reply back. you can see it inside "Wireshark" and "Powershell", images below. ( NOTE: TO STOP PERPETUAL PING USE "Control" + "C" ) 
  
<p>
<img src="https://i.imgur.com/SM3gsve.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 
  
Now lets obeserve SSH traffic, stablishing a connection to VM-2. on "Powershell" lets use "ssh labuser@10.0.0.5" you IP Address is likely to be different. after connecting we are inside VM-2 we can run commands and access files. use exit, to exit VM-2. images below.
  
<p>
<img src="https://i.imgur.com/sVs5SRk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 
  
<p>
<img src="https://i.imgur.com/MY7VTXx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 
  
Lets observe DHCP (Dynamic Host Configuration Protocol) traffic in "wireshark" this protocol issigns IP Addresses. let use "ipconfig /renew" to attempt get a new IP Adress in our VM-1. when i did this my VM-1 lost connection but when rebooting back you can see the request on "Wireshark".
  
<p>
<img src="https://i.imgur.com/gDeXFHY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 
  
Lets observe DNS (Domain Name System) trafic by going into a website using "nslookup" for any website you want. in this example let use www.google.com, and see how "Wireshark" and "Powershell" shows how DNS uses Domain names to match their assigned IP Address. 
  
<p>
<img src="https://i.imgur.com/387ELWE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 
  
 Now lets observe RDP (Remote Desktop Protocol), RDP is used to remotely access and control Windows-based systems. we can see this Network traffic through "Wireshark". we will use  "tcp.port==3389" on "Wireshark" wich is RDPs Port.
  
<p>
<img src="https://i.imgur.com/Rtl9zSi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 
  
  And this concludes this overview! i hope this helped you have better understanding, stay positive and keep learning! 
  
