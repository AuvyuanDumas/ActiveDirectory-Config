# ActiveDirectory-Config
Configuring and Managing Active Directory on Windows Server
# Active Directory Setup

## Overview
This project sets up a lab environment using Oracle VirtualBox with Windows Server 2019 as the Domain Controller (DC) and Windows 10 as a client machine (Client10 VM). The goal is to simulate a corporate network with Active Directory, DHCP, and RAS/NAT for internet access.

<img width="893" alt="image" src="https://github.com/user-attachments/assets/5cef804a-8448-4dd1-b405-715e4de4b2bd" />


## Infrastructure
- **Public Internet → NIC → DC (Active Directory) → NIC → VMWare Network (Corporate Network) → NIC → Client10 VM (Employee Workstation)**
- **Default Gateway:** The Domain Controller (DC) is the default gateway.
- **DC VM:**
  - **Network Adapter 1:** NAT (Internet access)
  - **Network Adapter 2:** Internal Network (Connects to Client10 VM)
  - **Internal NIC Settings:**
    - **IP:** 172.16.0.1
    - **Subnet Mask:** 255.255.255.0
    - **DNS:** 127.0.0.1
- **Client10 VM:**
  - **Network Adapter 1:** Internal Network (Connects to DC, uses it as gateway)

## Domain Controller (Server 2019) Configuration
- Installed and configured **Active Directory Domain Services (AD DS)**
- Created a **Domain Admin account** in AD
- Logged out and back in as Domain Admin
- Installed **RAS/NAT** on DC to allow Client10 VM to access the internet via the DC
- Installed and configured **DHCP** on DC
  - **Scope:** 172.16.0.100 - 172.16.0.200
  - **Subnet Mask:** 255.255.255.0
  - **Gateway:** 172.168.0.1
  - **DNS:** 172.16.0.1

## Active Directory User Management via PowerShell
- Used PowerShell scripts to create and manage **1,000+ users** in AD
- Provisioned and assigned user accounts to Organizational Units (OUs)
- Configured user policies and group memberships through AD

## Summary
- **Client10 VM (Windows 10 Employee Workstation)** uses the **VMWare Network (Corporate Network)** and connects to the **DC (Active Directory)** as its **default gateway**.
- **DHCP and RAS/NAT** ensure network functionality and internet access for internal users.
- **PowerShell automation** efficiently manages large-scale user provisioning in AD.

This project replicates a real-world enterprise environment with centralized user management and controlled network access.

