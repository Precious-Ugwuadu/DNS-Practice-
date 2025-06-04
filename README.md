# DNS-Practice
<p align="center">
  
![image](https://github.com/user-attachments/assets/f252cd1b-789a-47c2-9fc3-e420490c815f)

</p>

<h1>DNS - Prerequisites and Installation</h1>
This tutorial demonstrates how to create and manage DNS A and CNAME records in Active Directory, test DNS resolution, and work with local DNS caching on a Windows Server environment.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>List of Prerequisites</h2>

- Windows Server VM (DC-1)
- Windows Client VM (Client-1)
- Functional Active Directory Domain
- Basic Network Tools Available
- Administrative Privileges

<h2>A-Record Exercise</h2>

<p>
  
![image](https://github.com/user-attachments/assets/a9fc5771-0045-4f64-8e01-551feec7e98f)

To begin, Log in to DC-1 using your domain administrator account (mydomain.com\jane_admin).

![image](https://github.com/user-attachments/assets/c60d2e05-8fc2-4810-9db0-04b37d639431)

Then, log in to Client-1 using an account with administrative privileges (mydomain\jane_admin).

![image](https://github.com/user-attachments/assets/e7a6b86f-0cfd-4e69-828f-12fc8c8e72fa)

From Client-1, attempt to ping "mainframe" and observe that the request fails.
HOW TO:
On Client-1, Open powershell > Type: ping mainframe > Press Enter and observe the failure message.

![image](https://github.com/user-attachments/assets/b3ba09f6-336a-4d5a-9041-c6c02ecb1956)

Run nslookup mainframe on Client-1 and observe that it fails, indicating there's no DNS record found for "mainframe".

</p>
<p>

![image](https://github.com/user-attachments/assets/9d78c547-4f2f-4430-ad1f-52ccb9cb2227)
  
On DC-1, add a DNS A record for "mainframe" and set it to point to DC-1’s private IP address.
HOW TO:
On DC-1, Open DNS Manager > Expand dc-1 > Forward Lookup Zones > mydomain.com > Right click  > New Host (A or AAAA) > (set up name and IP address) mainframe > 10.0.0.4 > Add Host. 

![image](https://github.com/user-attachments/assets/f4af5c1a-5f0b-49d1-ad4e-50ebce6fe2e3)

Go back to Client-1 and try to ping it. Observe that it works

<h2>Local DNS Cache Exercise</h2>

</p>
<br />

<p>

![image](https://github.com/user-attachments/assets/532791cb-b44d-448c-90e2-074cd5208c8a)
  
Return to DC-1 and update the mainframe DNS A record to point to 8.8.8.8 instead of its original IP address.

![image](https://github.com/user-attachments/assets/25233fd8-9050-4150-b933-14a9b8c7e794)

On Client-1, ping "mainframe" again and notice that it still responds with the old IP address (10.0.0.4).
WHY?
It still pings the old IP address because Client-1 has cached the previous DNS record locally. The system uses this cached entry instead of querying the DNS server again. This is known as the local DNS cache, and it remains valid until it expires or is manually cleared. 

![image](https://github.com/user-attachments/assets/76ab5726-e04d-4d98-b039-cfb46ba967ed)

Check the local DNS cache by running ipconfig /displaydns > dns.txt > Enter > notepad dns.txt to view stored DNS entries on the system.

![image](https://github.com/user-attachments/assets/7f580c39-cb11-4755-afaf-4cc43918b705)

Run the command ipconfig /flushdns and ipconfig /displaydns to clear the saved DNS records on your computer, so it can fetch updated IP addresses from the DNS server. (Make sure to run this as an Admin). running ipconfig /flushdns cleared all previously stored DNS records. So when you run ipconfig /displaydns afterward, the cache appears empty since it was just wiped clean.

![image](https://github.com/user-attachments/assets/4e76f5b1-8834-4787-89a6-83d8636e5fe7)

Ping "mainframe" again and notice that the response now shows the updated IP address (8.8.8.8) from the new DNS record.
WHY?
Because the DNS cache was cleared, the system had to query the DNS server again. This time, it retrieved the updated A-record for “mainframe,” which reflects the new IP address you set.
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
