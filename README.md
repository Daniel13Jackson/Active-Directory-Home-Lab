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

## Network Diagram

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
!<img width="956" height="749" alt="Vbox Vms" src="https://github.com/user-attachments/assets/36eaaaef-0148-4076-b780-39c2470e72aa" />


