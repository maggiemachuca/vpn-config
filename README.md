This tutorial demonstrates how to observe and compare public IP addresses when accessing the internet from your personal machine, an Azure-hosted virtual machine, and a VPN-connected environment. It provides a hands-on approach to understanding IP masking and how VPNs protect online identity and location.

<h1>VPN Tunnel Demonstration Using Azure VM</h1>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure
- Azure Virtual Machine
- Remote Desktop Protocol via Windows App
- VPN Tool: ProtonVPN (free version)
- Web Tools: https://whatismyipaddress.com/
- Command Line Tool: nslookup myip.opendns.com resolver1.opendns.com (for IP check via Command Prompt)

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create a Windows 10 VM in Azure
- Check IP Address of Host Machine (Local Computer)
- Connect to VM using Remote Desktop App
- Download and Install ProtonVPN Inside the VM
- Connect to VPN and Recheck IP
- (Optional): Verified IP using Command Prompt

## Step 1: Create a Virtual Machine in Azure
- Let's create a Windows 10 virtual machine so we can use it to log into in a later step.
- Create a Windows 10 VM in Azure
- <img width="1440" height="533" alt="Screenshot 2025-09-25 at 9 18 43 PM" src="https://github.com/user-attachments/assets/71554926-b1b5-414f-9e6d-f7c6c1cee540" />


## Step 2: Check your IP Address from your Personal Computer (non-VPN connection)
- In this step we are going to look up our IP address **without a VPN**
- We are going to see what our IP address is using https://whatismyipaddress.com/
- Go to this website on your **PERSONAL** computer
- Note the IP address.
- This is the public IP your computer exposes to the internet

<img width="1195" height="472" alt="Screenshot 2025-09-25 at 9 26 20 PM" src="https://github.com/user-attachments/assets/8ecbaac6-f2ca-426a-afc4-034c3a680147" />

## Step 3: Observe IP Address from VM
- Log into your Windows Virtual Machine
- Go to https://whatismyipaddress.com/
- Observe the different IP address that is shown when you are connected to your VM
  
<img width="1200" height="482" alt="Screenshot 2025-09-25 at 9 51 31 PM" src="https://github.com/user-attachments/assets/f541ea7b-589f-4d9f-9531-ffd5cf8a6822" />

- In my case, my VM's public IP address is set to a Data Center in San Francisco.
- This makes sense because Azure is hosting our VM and Azure has many data centers around the country.

## Step 4: Download Proton VPN for Windows within the VM
- We are going to make an account for ProtonVPN (free) for this step.
- Go ahead and go to this website: https://account.protonvpn.com/signup?plan=free&language=en
- Navigate to the Downloads section
- Click Download for Windows

<img width="1416" height="555" alt="Screenshot 2025-09-25 at 10 01 45 PM" src="https://github.com/user-attachments/assets/b8378cbb-a972-49ad-a8eb-09c18fcea18e" />

- Go through the installation wizard
- Once you've installed it a ProtonVPN window should pop up.
- Go ahead and enter the credentials you made earlier

<img width="987" height="643" alt="Screenshot 2025-09-25 at 10 07 17 PM" src="https://github.com/user-attachments/assets/cd25c642-92e2-4e95-bbb0-2efef81d21c8" />

- Once you're logged in you should see a user interface like this (screenshot below)
- You currently are **not connected** to the VPN.

<img width="1440" height="860" alt="Screenshot 2025-09-25 at 10 08 52 PM" src="https://github.com/user-attachments/assets/d9bb351a-9a52-4a38-a7d0-0532abd85dc9" />

- To connect to a VPN server, click Connect

<img width="346" height="169" alt="Screenshot 2025-09-25 at 10 10 17 PM" src="https://github.com/user-attachments/assets/5a034e13-fa04-4f48-b9df-cfdeb28a3731" />

- I connected to a server in the United States. (screenshot below)
- Note: With the free version of ProtonVPN you cannot pick the country you want to connect to. There are about 4 countries you can connect to (the server you get connected to also depends on availability on ProtonVPN's end.

<img width="1437" height="850" alt="Screenshot 2025-09-25 at 10 11 59 PM" src="https://github.com/user-attachments/assets/05f7b998-89d4-4db8-b3d5-ba93c32cdb28" />

## Step 3: Observe IP Address from VM (VPN connection)
- Go to https://whatismyipaddress.com/ from your VM **with the VPN connection** you just made.
- Observe the different IP address that is shown when you connected through a VPN

<img width="1203" height="488" alt="Screenshot 2025-09-25 at 10 15 21 PM" src="https://github.com/user-attachments/assets/1785b6c0-3985-4b4c-ad70-20add36e6ba5" />

## Compare Results

- When we connected to https://whatismyipaddress.com/ you saw the IP address that is shown by your personal computer. You are even shown information about the ISP, services, city, country, and region.
- After connecting remotely to our VM, we checked our IP address again and it changed, depending on where your VM is hosted. In my example it was in San Francisco.
- After installing a VPN client onto the VM and connecting to a VPN server, the IP address **changed again**. This time, my IP address changed to one that existed in Los Angeles.

## Optional:
-  We can look at our IP address on Command Prompt on Windows 10 instead of going to the https://whatismyipaddress.com/ website
-  Open up Command prompt and type in the command **nslookup myip.opendns.com resolver1.opendns.com**
-  Under non-authoritative answer you can see the IP address you currently have.
-  For example, this is my VM's IP address when it is not connected to a VPN.

<img width="227" height="63" alt="Screenshot 2025-09-25 at 10 24 46 PM" src="https://github.com/user-attachments/assets/72d4fcb9-1e49-45fe-ae72-25975ac7baa3" />

## Summary:
- Created a Windows 10 virtual machine in Azure for testing IP visibility in different network conditions.

- Verified the public IP address of the local computer without a VPN using an external lookup tool.

- Remotely connected to the VM via Remote Desktop Protocol (RDP) and observed the VM's public IP (from Azure's data center).

- Installed and configured ProtonVPN inside the VM, then rechecked the IP to confirm it changed to reflect the VPN server's location.

- Compared all three scenarios to understand how IP addresses change across local, cloud, and VPN-based access.

