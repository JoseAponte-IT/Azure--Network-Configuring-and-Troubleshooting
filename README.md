![nsg](https://github.com/user-attachments/assets/fdff4930-5379-4764-8e6d-9bac6055282d)

# Network Traffic Analysis and Security Configuration in Azure
This project demonstrates how to use Microsoft Azure for network troubleshooting and security configuration, showcasing technical expertise in managing cloud networking and analyzing data traffic. Follow along as we create and configure Network Security Groups (NSGs), deploy Virtual Machines, and inspect network protocols using Wireshark and PowerShell commands. Detailed explanations and screenshots are included to guide you through each step. 🫡

<h2>Tools & Technology Used</h2>

- Azure Portal & Azure CLI

- Powershell

- Wireshark

- Networking Protocols; ICMP, SSH, RDP, DNS, DHCP

<h2>Key Objectives:</h2>

- Azure Resource Management:
  - Created and configured Resource Groups, Virtual Networks, and Subnets.<br>
  - Deployed Virtual Machines with custom configurations.<br>
  - Configured Azure Network Security Groups (NSGs) to control inbound and outbound traffic.

- Network Traffic Analysis:
   - Used Wireshark to capture and analyze network packets between two Virtual Machines.<br>
   - Simulated network traffic with PowerShell commands, including:<br>
     - ping -t to analyze ICMP traffic.<br>
     - SSH for port 22 traffic.<br>
     - RDP for port 3389 traffic.<br>
     - nslookup for DNS traffic (port 53).<br>
     - ipconfig /renew to monitor DHCP traffic on ports 67 and 68.

- Security Enhancements:<br>
  - Configured NSGs to selectively allow or deny specific types of traffic, ensuring secure      communication across the network.

<h2>Prerequisites</h2>

- An active Microsoft Azure Subscription

- Microsoft RDP: If on MAC go to APP Store and download Microsoft RDP

# Project Overview
<h2>Step 1: Create a Resource Group</h2>

![image](https://github.com/user-attachments/assets/19033fc3-cbff-45ca-898a-f9048e89abac)

- Name the Resource Group and presss Review + Create

![image](https://github.com/user-attachments/assets/1d1eda60-c122-4f46-adc7-7b29b9671601)

![image](https://github.com/user-attachments/assets/a96a8ab2-5ca6-4c61-89df-415fc357c15d)




<h2>Step 2 Create/Configure our first Virtual Machine and Virtual Network Resource:</h2>

- Return to the Azure Portal and find the "Virtual Machines" option (You can search it in the searchbar if you cant find the option in the dashboard) 

![image](https://github.com/user-attachments/assets/37ac9f7a-e86c-44b7-aa37-d125469a692f)

- Create a virtual machine resource 

![image](https://github.com/user-attachments/assets/64829dcf-3278-4353-a19d-dc6f9425a77f)

- Assign the VM to the Resource Group that was created

![image](https://github.com/user-attachments/assets/c9b229b0-2c9e-46b2-b484-051561735444)

- Fill out these details:<br> 
-Virtual Machine Name<br>
-Region [!!IMPORTANT!! Make sure that the region used to create the resource group is the same as the region as the VM you are creating, might run into issues otherwise] <br>
-Image [we are going to make a Windows 10 VM so make sure to select the Windows 10 pro option for image]<br>

![image](https://github.com/user-attachments/assets/1b1fdc24-9661-4399-ad14-db487c1723b8)


- For optimal performance I will use 2cpus as the standard size<br>

![image](https://github.com/user-attachments/assets/eccde4e3-b136-4d1e-8d22-a35dc2e6fb31)

- Create Username and password 

![image](https://github.com/user-attachments/assets/5f0a911f-3f21-461f-8142-efa246151fd9)

- Confirm Licensing 

![image](https://github.com/user-attachments/assets/24f0e9e2-a57d-41b0-8d12-e96a6d2d896e)

- Navigate to the "Networking" tab at the top of the screen

![image](https://github.com/user-attachments/assets/9b2c4cec-909f-4359-94ad-de47057ec954)

- Create a new Virtual Network and allow it to create a subnet

![image](https://github.com/user-attachments/assets/8c074e4a-e818-4978-b472-2fc4f4886109)

- Name your Vnet and press ok

![image](https://github.com/user-attachments/assets/3df2b14f-791c-4c76-84b7-79805a84f4a3)


- Review and Create

![image](https://github.com/user-attachments/assets/b8e74567-72c3-4a6c-be00-c14e1d85b6fa)

![image](https://github.com/user-attachments/assets/9da5b2ee-d295-40c0-9800-e45f4269eb3f)


<h2>Step 3 Creating/Configuring our Second Virtual Machine and Virtual Netwrok Resource</h2>

- Repeat same Steps as before to create our second VM(Linux Ubuntu server):<br>
  - Place vm in the same resource group as the other VM we made
    
  - Name VM
  
  - Use the same Region as the resource group
    
  - Choose 2cpus for the size for optimal performance
    
  - Select Authentication Type: Password
    
  - Create a Username and password
  
  - Navigate to the "Networking" tab at the top of the screen

  - Join the previously created Vnet that we configured when we created the windows-vm

   - Review and Create

![image](https://github.com/user-attachments/assets/fed42634-ef8f-4a60-bbdd-6e4fb193b59a)

![image](https://github.com/user-attachments/assets/c6e8b5dd-d770-4e7f-a960-c8c513e3096c)

![image](https://github.com/user-attachments/assets/f40dadde-e557-405c-a1c8-e47911f8ed7d)

![image](https://github.com/user-attachments/assets/88826cad-f2de-4b12-85c0-c46518bcb5e4)

![image](https://github.com/user-attachments/assets/ff9e4224-7499-4a36-bb41-afba26e553f2)

![image](https://github.com/user-attachments/assets/15bf5be0-5d2c-4abc-8298-97c7231efe3c)

- Virtual Machine (Linux Ubuntu) Successfully Created <br>
🎉 Congrats you have now made 2 Virtual Machine resources on the same virtual network using the cloud

![image](https://github.com/user-attachments/assets/f07039f0-dcd7-46eb-9e25-755f1d2c7ea6)

![image](https://github.com/user-attachments/assets/de561cf7-27dc-431c-af73-496667a2a4d1)

![image](https://github.com/user-attachments/assets/0b94ac5c-75df-4e97-a4f2-7c17c08e7ea8)

![image](https://github.com/user-attachments/assets/2f995d5d-2d57-45f6-a48e-e66022f901b6)

<h2>Step 4:</h2>




