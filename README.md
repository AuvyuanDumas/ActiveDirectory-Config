# ActiveDirectory-Config
Configuring and Managing Active Directory on Windows Server


## Overview
This project sets up a lab environment using Oracle VirtualBox with Windows Server 2019 as the Domain Controller (DC) and Windows 10 as a client machine (Client10 VM). The goal is to simulate a corporate network with Active Directory, DHCP, and RAS/NAT for internet access.

<img width="893" alt="image" src="https://github.com/user-attachments/assets/5cef804a-8448-4dd1-b405-715e4de4b2bd" />


## Infrastructure
- **Public Internet → NIC → DC (Active Directory) → NIC → VMWare Network (Corporate Network) → NIC → Client10 VM (Employee Workstation)**
- **Default Gateway:** The Domain Controller (DC) is the default gateway.
- **DC VM (Windows Server 2019):**
  
![Screenshot 2024-11-27 144914](https://github.com/user-attachments/assets/dcfb6c27-b9f8-41f6-9b6e-ceca0c83c8ac)

![Screenshot 2024-11-27 145034](https://github.com/user-attachments/assets/9496b7b2-bbe9-42f7-8db2-5a39ee0ae38a)

![Screenshot 2024-11-27 145901](https://github.com/user-attachments/assets/d5c58cf9-dfa9-4cf0-8f23-fd89c29f9f25)

![Screenshot 2024-11-27 150122](https://github.com/user-attachments/assets/1367e662-369b-4f0b-8f32-fdcae2a5baca)

![Screenshot 2024-11-27 150251](https://github.com/user-attachments/assets/3f9784f2-39c0-4fb4-b8f5-79499d631c1c)

![Screenshot 2024-11-27 150350](https://github.com/user-attachments/assets/8ed9ef84-ce35-47c6-8a5e-c91648264e41)


- **Network Adapter 1:** NAT (Internet access)
- **Network Adapter 2:** Internal Network (Connects to Client10 VM)
- **Internal NIC Settings:**
    - **IP:** 172.16.0.1
    - **Subnet Mask:** 255.255.255.0
    - **DNS:** 127.0.0.1
      
![Screenshot 2024-11-27 145725](https://github.com/user-attachments/assets/ac998078-e36c-473f-9055-ae59daf2e3b7)
 
 ![Screenshot 2024-11-27 151004](https://github.com/user-attachments/assets/e253816e-f7f6-414a-ad8e-4144968e18f1)
 
   
- **Client10 VM (Windows 10):**
  - **Network Adapter 1:** Internal Network (Connects to DC, uses it as gateway)
  
![Screenshot 2024-11-27 235444](https://github.com/user-attachments/assets/6aa582d3-6594-4230-90c5-fe33b7fc8b36)

![Screenshot 2024-11-27 235614](https://github.com/user-attachments/assets/b215d5e8-66f9-4a3c-a12e-096530b076d6)

![Screenshot 2024-11-27 235841](https://github.com/user-attachments/assets/1f91a37f-3199-4505-9d8b-6ec56329e54d)

![Screenshot 2024-11-27 235911](https://github.com/user-attachments/assets/a8d24236-9df1-4b7e-9b36-4e4948636ec7)

![Screenshot 2024-11-28 000101](https://github.com/user-attachments/assets/04d2dbf8-7e37-4ef2-a159-469ccc3f8574)


## Domain Controller (Server 2019) Configuration
- Installed and configured **Active Directory Domain Services (AD DS)**
  
![Screenshot 2024-11-27 151617](https://github.com/user-attachments/assets/b437dcb6-65b5-49d8-b53f-c756766938bb)

![Screenshot 2024-11-27 151750](https://github.com/user-attachments/assets/fb13e640-5a5e-4d55-a6c6-373cde830c5e)

![Screenshot 2024-11-27 152154](https://github.com/user-attachments/assets/d82a0a93-0073-41f0-9d8a-c8a89794b1ba)

![Screenshot 2024-11-27 152345](https://github.com/user-attachments/assets/a1dffae8-8872-4203-a6ff-86833422b953)

![Screenshot 2024-11-27 153027](https://github.com/user-attachments/assets/89a9dda4-e1e8-4741-bd28-27af0c80464a)

![Screenshot 2024-11-27 153449](https://github.com/user-attachments/assets/57e9c630-bc88-4db0-8b98-9b4d9a46209a)


- Created a **Domain Admin account** in AD
  
![Screenshot 2024-11-27 153716](https://github.com/user-attachments/assets/46e660d0-f92c-4f3f-bd4f-659f67495eeb)

![Screenshot 2024-11-27 153859](https://github.com/user-attachments/assets/08914ab9-e743-4112-967e-1e2a9d1eabd8)

![Screenshot 2024-11-27 154121](https://github.com/user-attachments/assets/9af9e80d-e641-40c5-9229-3f63da394796)

![Screenshot 2024-11-27 154432](https://github.com/user-attachments/assets/b49ca7dd-2c98-4d9e-ba4a-58f06a72357c)

![Screenshot 2024-11-27 154719](https://github.com/user-attachments/assets/9f5b6ae8-0e09-4d1c-86dd-ba2d4eb23de5)


- Logged out and back in as Domain Admin
- Installed **RAS/NAT** on DC to allow Client10 VM to access the internet via the DC

![Screenshot 2024-11-27 155000](https://github.com/user-attachments/assets/8fb58bd9-652a-4665-818f-cbb3c0a2909d)

![Screenshot 2024-11-27 155058](https://github.com/user-attachments/assets/cc66dda4-52e2-4c41-a0b4-e6408fa60b66)

![Screenshot 2024-11-27 155418](https://github.com/user-attachments/assets/7d3b786b-6566-4e53-81ae-9b8fca5b6eb0)

![Screenshot 2024-11-27 155540](https://github.com/user-attachments/assets/bfde1d64-c4fc-41c7-a026-be1928099e0d)

![Screenshot 2024-11-27 155731](https://github.com/user-attachments/assets/b61d58ad-8486-4f10-a6ee-4762420fb149)

![Screenshot 2024-11-27 155811](https://github.com/user-attachments/assets/9c06c8d7-f1ce-4a47-ac93-d9f5a4acd3dc)

![Screenshot 2024-11-27 155900](https://github.com/user-attachments/assets/0ab51489-1dc7-41bd-be86-8c3e5bb24393)


- Installed and configured **DHCP** on DC
  - **Scope:** 172.16.0.100 - 172.16.0.200
  - **Subnet Mask:** 255.255.255.0
  - **Gateway:** 172.168.0.1
  - **DNS:** 172.16.0.1
    
![Screenshot 2024-11-27 160208](https://github.com/user-attachments/assets/dd5a4a26-788f-421b-8471-3e3cb15afebb)

![Screenshot 2024-11-27 160326](https://github.com/user-attachments/assets/4c6d234c-1032-48b9-a105-a8810ac2f68f)

![Screenshot 2024-11-27 160838](https://github.com/user-attachments/assets/072470f3-47e2-40ae-bbd2-0abde525554b)

![Screenshot 2024-11-27 161000](https://github.com/user-attachments/assets/bb00b6ee-aa32-4ad4-94f9-985c09affc0e)

![Screenshot 2024-11-27 161102](https://github.com/user-attachments/assets/f6d1de7b-a823-4d3a-a3c8-ae589ed3a14d)

![Screenshot 2024-11-27 161219](https://github.com/user-attachments/assets/7eb3e8bd-7305-45d9-be18-97cf65385164)

![Screenshot 2024-11-27 161353](https://github.com/user-attachments/assets/5af44e67-ab1c-416d-93ac-2b11fa0a89f2)


## Active Directory User Management via PowerShell

![image](https://github.com/user-attachments/assets/ca9268ec-1bdb-4c10-86f9-1fdc5402dc95)

![image](https://github.com/user-attachments/assets/4a934c8c-5b92-4d90-b57f-3861129e7522)

![image](https://github.com/user-attachments/assets/b840554c-746c-4e69-bc1b-9f03ea698cbc)

- Used PowerShell scripts to create and manage **1,000+ users** in AD
- Provisioned and assigned user accounts to Organizational Units (OUs)
- Configured user policies and group memberships through AD

## Summary
- **Client10 VM (Windows 10 Employee Workstation)** uses the **VMWare Network (Corporate Network)** and connects to the **DC (Active Directory)** as its **default gateway**. 
- **DHCP and RAS/NAT** ensure network functionality and internet access for internal users.
- **PowerShell automation** efficiently manages large-scale user provisioning in AD.

This project replicates a real-world enterprise environment with centralized user management and controlled network access.

