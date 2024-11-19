![nsg](https://github.com/user-attachments/assets/fdff4930-5379-4764-8e6d-9bac6055282d)

# Network Traffic Analysis and Security Configuration in Azure
This project demonstrates how to use Microsoft Azure for network troubleshooting and security configuration, showcasing technical expertise in managing cloud networking and analyzing data traffic. Follow along as we create and configure Network Security Groups (NSGs), deploy Virtual Machines, and inspect network protocols using Wireshark and PowerShell commands. Detailed explanations and screenshots are included to guide you through each step. 🛠️

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
