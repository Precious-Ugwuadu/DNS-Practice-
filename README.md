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
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
