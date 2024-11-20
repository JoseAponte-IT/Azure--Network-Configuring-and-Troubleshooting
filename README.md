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

<h2>Step 4: RDP into the Windows 10 VM and install Wireshark</h2>

- Return to the Virtual Machine Dashboard in the Azure portal

![image](https://github.com/user-attachments/assets/b6a3858b-1275-43ee-88ba-5179fc32ce0d)

- Jot down the Public IP adresses of the VM's

![image](https://github.com/user-attachments/assets/4cdd5f04-1314-4984-932b-6fa82d02ff84)

- If on Windows press Windows key -> Open RDP If on MAC download RDP program in APP store and put in the IP adress of the Windows VM

![image](https://github.com/user-attachments/assets/9b260710-4d1f-4651-8753-5f070c26b954)

- Enter the Log in credentials and log in to the machine

![image](https://github.com/user-attachments/assets/db0f4e46-afca-47c4-8273-2efe9ed54ed3)

- Go to Microsoft Edge and search Wireshark and download the x64 option

![image](https://github.com/user-attachments/assets/9d706e04-5697-4090-ae84-5bc115d83651)

- Search Wireshark in the windows search bar on the bottom left and open the program

- Select the Ethernet option [This shows you all the packets of data being transfered throughout the network ]

![image](https://github.com/user-attachments/assets/2a627af3-831c-4174-9883-77dc3a85efd1)

- Type in icmp into the bar on the top to only focus on icmp data flowing throughout the network

![image](https://github.com/user-attachments/assets/e0b008ef-3b26-4bf5-9e1d-35fa7e8424e9)

- Search for PowerShell in the WIndows search bar on the bottom left and open the Program

![image](https://github.com/user-attachments/assets/37f66194-d94a-4ce9-bb72-17b327e9de3a)

- Enter the command ping -t 10.0.0.5 [10.0.0.5 is the Linux machines Local IP adress we jotted down and we are using the ping coommmnd to check for connectivity between the machines while the -t is stating keep repeatedly pinging unless told not to with the command crtl+c ]

![image](https://github.com/user-attachments/assets/83940d61-6b60-4b4e-b6ab-74c1f5e4854f)

- Observe the traffic through the Wireshark Program

![image](https://github.com/user-attachments/assets/f9889636-7bba-4168-8345-b78ea739009d)

- Go back to the Azure portal and configure a NSG Rule (Firewall protocol) to deny all incoming ICMP traffic

![image](https://github.com/user-attachments/assets/5d927f54-8195-45ba-b39e-73ebb76b12f8)

![image](https://github.com/user-attachments/assets/01e3152b-882e-49e2-b785-523839e5a535)

- Return to the windows vm through RDP and observe the traffic on Wireshark[Ping request should be timing out and there is only request traffic visible since we configured the linux vm to deny all inbound ping (ICMP) traffic]

![image](https://github.com/user-attachments/assets/ccd4e64d-e23c-473e-916f-cf42e2e3d629)

- Go back to the Azure portal and reconfigure the Linux VM's NSG (Firewall protocols) back to allowing Icmp traffic

-Select networking -> Network Settings -> then select the Network secuirty group option

 - Find the inbound security rule we configured and remove it 

![image](https://github.com/user-attachments/assets/8f536f1b-df69-4bf7-a9c2-897e9c986487)

![image](https://github.com/user-attachments/assets/efa68286-6f63-4d45-a844-1e59d8879531)


- Return to the Windows VM and observe the traffic return back to the way it was both Request and Recieveing data packets are now visible in the network now that the

![image](https://github.com/user-attachments/assets/bd912225-95b9-41c8-9b75-f1bb0c7f6c11)

- Run the ctrl c command in PowerShell to stop the pings

![image](https://github.com/user-attachments/assets/9b1d88ff-da86-4d28-b9e6-1a0214c985e2)

- 🎉Congrats, You’ve successfully configured a Network Security Group (NSG) and monitored its impact on the network by analyzing individual ICMP (ping) packets using Wireshark. The traffic was generated through PowerShell commands, specifically using ping -t to simulate continuous ICMP requests.



