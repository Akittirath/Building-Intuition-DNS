<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this lab we will be experimenting with DNS. This lab will help us have a better understanding of DNS.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Active Directory Virtual Machine
- Client Machine joined to your domain

<h2>Lab Steps</h2>
<p>
</p>
<p>
First we will be inspecting DNS A-Records on the server A records are hostname to IP address mappings. We are going to create an A record on DC-1 for "mainframe" and have it point to DC-1's private IP address. If we try to ping mainframe without setting the DNS record it will not work. When we ping "mainframe" Client-1 is checking the DNS cache, checking its local host file and checking the DNS server. To create an A-record go to the AD->Tools->DNS->DC-1->Forward lookup zones->mydomain.com-> right click and create a new A record, title it mainframe. An A record is hostname to ip address mapping. If we go back to the client machine and ping mainframe we will get a reply. 
</p>
<br />

<p>
<img src="https://imgur.com/a/sLF2bdN" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/NDgetB9.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
In this screenshot, you see that we ping "mainframe" and it will still show the ip address as "10.0.0.4". We need to go back to DNS Manager located on DC-1 VM and change the ip address to 8.8.8.8. After we change it to 8.8.8.8, we need to go back to command prompt, close that and click run as administrator command prompt. What we need to do as administrator is flush the dns. This allows the cache to reset and start over. We will now type in, "ipconfig /flushdns". You will then now get the ip address as "8.8.8.8".
</p>
<br />
<img src="https://i.imgur.com/WJ1T88O.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/Ee1aT82.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lastly we will configure a CNAME record that points the host "search" to "www.google.com" If we ping "search" ping will not be able to find the host. we have to go back into the DNS tool on DC-1 and create the CNAME record "search". Once we create the CNAME record is created and we ping "search" it will resolve to www.google.com.
</p>
<br />
<p>
<img src="https://i.imgur.com/fYKKTYk.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<img src="https://i.imgur.com/q6A7BfW.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
