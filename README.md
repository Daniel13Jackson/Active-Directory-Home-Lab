# Active-Directory-Home-Lab
## Overview 
Windows Active Directory home lab demonstrating AD DS, DNS, DHCP, NAT/routing, PowerShell automation, domain joining, and network troubleshooting.

## Lab Architecture
<img width="817" height="501" alt="DCproject" src="https://github.com/user-attachments/assets/66f2b0d7-7aa8-43e9-93f9-ee20564329e4" />

## Project Overview

This project documents the creation of a virtualized Active Directory environment
designed to simulate a small enterprise network.

The lab consists of a Windows Server domain controller and a Windows client
connected through an isolated internal network. The domain controller provides
Active Directory, DNS, DHCP, and NAT/routing services.

PowerShell was also used to automate the creation of domain user accounts.

## Objectives

- Build a virtualized Windows Server environment
- Configure a Windows Server domain controller
- Install and configure Active Directory Domain Services
- Configure DNS
- Configure DHCP
- Configure NAT and routing
- Create and manage domain users
- Automate user creation with PowerShell
- Configure a Windows client
- Join the client to the Active Directory domain
- Verify network and domain connectivity
- Troubleshoot DHCP and network configuration issues

## Lab Architecture

The lab uses two virtual machines:

| DC01 | Domain Controller, DNS, DHCP, NAT/Routing | NAT + Internal Network |
| CLIENT01 | Windows domain client | Internal Network |

### Network Diagram

<img width="817" height="501" alt="DCproject" src="https://github.com/user-attachments/assets/a766dfb9-7ffb-4609-8ddd-e8f435525db2" />

The Domain Controller contains two network adapters. One provides external connectivity
through NAT, while the second connects to the isolated internal network.

CLIENT01 communicates with DC through the internal network.

## Technologies Used

- Oracle VirtualBox
- Windows Server
- Windows client
- Active Directory Domain Services
- DNS
- DHCP
- NAT
- Routing
- PowerShell
- Windows Command Prompt

## Implementation

### 1. Virtual Machine Configuration

Two virtual machines were created using VirtualBox:

- Domain Controller
- Client 1
<img width="956" height="749" alt="Vbox Vms" src="https://github.com/user-attachments/assets/36eaaaef-0148-4076-b780-39c2470e72aa" />

### 2. Domain Controller Network Configuration

DC01 was configured with two network adapters:

- NAT adapter for external connectivity
- Internal Network adapter for communication with domain clients
<img width="518" height="55" alt="DC Network adapters" src="https://github.com/user-attachments/assets/cd10804c-a1ed-4bde-b538-c6c7a0f3c6da" />

### Static IP for the internal Network to connect to
<img width="398" height="449" alt="DC1 Static ip" src="https://github.com/user-attachments/assets/ba643446-5a87-4912-8ed5-c14be24ed47d" />


### 3. Active Directory Domain Services

Active Directory Domain Services was installed on DC01 and configured
as the domain controller for the lab environment.

<img width="1415" height="1000" alt="AD Domain Controller" src="https://github.com/user-attachments/assets/c5d84e90-e5dc-4727-ae76-c29ae1c3b61e" />

### 4. Administrative Account Configuration

A separate administrative account was created for domain administration
rather than using the standard user account for administrative tasks.

<img width="1412" height="1000" alt="AD Admin" src="https://github.com/user-attachments/assets/71592872-f1ff-4949-a6e8-44e252ae4fc5" />

### 5. DHCP Configuration

DHCP was configured on DC01 to automatically assign IP configuration
to clients on the internal network.

The DHCP scope was configured for the internal 172.16.0.0/24 network.

<img width="719" height="508" alt="DHCP config" src="https://github.com/user-attachments/assets/11c11a1b-36d7-489e-8da0-d72e0d434ff5" />

### 6. PowerShell User Automation

PowerShell was used to automate the creation of domain user accounts within Active Directory. The script was executed and built for the original lab build and the resulting accounts were verified in Active Directory Users and Computers.

Script Source & Credit:
The PowerShell user-creation script was provided by Josh Madakor as part of his Active Directory home lab tutorial. I used the script as part of my own lab implementation and documented the resulting configuration and validation.

PowerShell Script: [Josh Madakor's AD PowerShell Repository] (https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1)
<img width="1408" height="1004" alt="PowerShell" src="https://github.com/user-attachments/assets/2394326f-3efe-42e1-bcfb-66babf33c3dc" />

### Result
<img width="874" height="713" alt="AD users" src="https://github.com/user-attachments/assets/d4ab00c8-7db2-4c0d-a3ee-903f45108d01" />

### 7. Windows Client Configuration
A Windows client VM was configured on the internal network and obtained
its network configuration from the DHCP server running on DC01.

<img width="1276" height="849" alt="IpconfigC1" src="https://github.com/user-attachments/assets/e9ec5337-c73f-4369-a737-f9369c5d92f2" />

### 8. Domain joining
CLIENT01 joined to the Active Directory domain hosted by Domain Controller.

<img width="1275" height="686" alt="DHCP Address lease" src="https://github.com/user-attachments/assets/d3615130-6c1c-4844-9eea-ddbc12403225" />


<img width="1420" height="928" alt="Domain Authentication" src="https://github.com/user-attachments/assets/b28225a5-21e7-4022-81c8-6a1120861b99" />

## Testing and Validation

The lab was tested using several methods:

- Verified CLIENT01 received an IP address from DHCP
- Verified the correct default gateway was assigned
- Verified DNS resolution
- Tested connectivity to the domain controller
- Tested internet connectivity
- Verified CLIENT01 received a DHCP lease
- Successfully joined CLIENT01 to the Active Directory domain
- Successfully authenticated using a domain account

<img width="1419" height="931" alt="ConnectivityC1" src="https://github.com/user-attachments/assets/d0c854cf-65f0-4993-9fc2-97c3af8923ba" />

## Skills Demonstrated

### Systems Administration
- Windows Server administration
- Active Directory
- Domain Controllers
- User and account management
- Windows client administration

### Networking
- IPv4 addressing
- DHCP
- DNS
- NAT
- Routing
- Internal network segmentation
- Network troubleshooting

### Automation
- PowerShell
- Automated Active Directory user provisioning

### Virtualization
- Oracle VirtualBox
- Virtual machine networking
- Multi-VM lab environments

### Troubleshooting
- `ipconfig`
- `ping`
- DHCP lease verification

## Lessons Learned

This project provided hands-on experience with how Windows systems
interact within a domain environment.

Key lessons included:

- How Active Directory provides centralized user and computer management
- How DNS supports Active Directory
- How DHCP provides client network configuration
- How NAT allows an isolated network to access external resources
- How PowerShell can automate repetitive administrative tasks
- How to properly network the backend of an Active Directory

## Future Improvements

Potential additions to the lab include:

- Add a second Windows client
- Create additional organizational units
- Implement Group Policy Objects
- Create department-specific security groups
- Configure shared network resources
- Implement file-server permissions
- Add additional PowerShell automation
- Create additional troubleshooting scenarios
- Implement Windows Server backup/recovery procedures

## Conclusion

This project provided hands-on experience building and administering
a virtualized Windows domain environment.

The lab demonstrates practical experience with Active Directory,
Windows Server administration, networking, PowerShell automation,
virtualization, domain authentication, and troubleshooting.

## Credits & References
Josh Madakor — Original Active Directory home lab tutorial and PowerShell user-creation script.

YouTube: [ Josh Madakor] (https://www.youtube.com/@JoshMadakor)

PowerShell Script: (https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1)

Tutorial: [https://youtu.be/MHsI8hJmggI?si=OmZJuIVTXHtBkfoO](https://youtu.be/MHsI8hJmggI?si=KszjNUN26s9a1zrG)
This project was independently implemented and documented as a hands-on learning project. The Active Directory lab architecture and PowerShell automation were based on Josh Madakor's tutorial and resources.
