# Active Directory Domain Controller Lab

## Objective
This lab demonstrates the setup and configuration of a Windows Server 2022 Domain Controller using Active Directory Domain Services (AD DS). The project includes configuring network settings, assigning a static IP address, and promoting the server to a domain controller.

---

## Tools & Requirements
- Windows Server 2022 Virtual Machine
- VirtualBox
- VirtualBox Extension Pack

---

# Lab Objectives
- Rename the server
- Configure isolated network settings
- Assign a static IP address
- Install Active Directory Domain Services
- Promote the server to a Domain Controller

---

# Renaming the Server

## Steps
1. Open **Windows Server**
2. Launch **Server Manager**
3. Navigate to:
```text
Local Server
```
4. Select the computer name
5. Rename the server to:
```text
DC01
```
6. Restart the server

---

## Screenshot — Renaming Server

<p align="center">
 <img width="1920" height="1080" alt="Screenshot 2026-05-09 214349" src="https://github.com/user-attachments/assets/0f72fe24-8562-40dc-a5f6-893bf8870868" />
<img width="1920" height="1080" alt="Screenshot 2026-05-09 220542" src="https://github.com/user-attachments/assets/98f0a1b9-3c03-4405-86f8-4d26e5739a0e" />

</p>

---

# Configuring Network Settings

## VirtualBox Network Configuration

### Adapter 1
- Attached To:
```text
Host-Only Adapter
```

### Adapter 2
- Enable Network Adapter
- Attached To:
```text
NAT
```

---

## Screenshot — VirtualBox Network Settings

<p align="center">
  <img width="1920" height="1080" alt="Screenshot 2026-05-09 220542" src="https://github.com/user-attachments/assets/06f70997-100a-4e3d-b550-cffa3e65565f" />
<img width="1920" height="1080" alt="Screenshot 2026-05-10 183718" src="https://github.com/user-attachments/assets/87d8b189-23d0-4242-a586-968cf8758bea" />
</p>

---
## Why Configure Networking This Way?

### NAT
Network Address Translation (NAT) allows the virtual machine to access external networks while remaining isolated from the main network.

### Host-Only Adapter
Creates a private internal network between the host computer and the virtual machines without exposing them directly to the internet.

> This prevents the lab environment from interfering with the home network.

---

# Assigning a Static IP Address

## Why Use a Static IP?

A Domain Controller requires a permanent IP address because devices on the network constantly communicate with it for authentication and directory services.

Dynamic IP addresses can change, which may cause communication issues between systems and the domain controller.

---

## DHCP Range Information

### DHCP Range
```text
Lower Address Bound: 192.168.56.101
Upper Address Bound: 192.168.56.254
```

### Example Static IP
```text
192.168.56.99
```

> The static IP should be outside the DHCP range to avoid address conflicts.

---

## Screenshot — Assigning a Static IP Address

<p align="center">
 <img width="1920" height="1080" alt="Screenshot 2026-05-10 185940" src="https://github.com/user-attachments/assets/e87c6799-a936-4e23-a669-c62fbbf3f9cd" />
</p>

---

# Configuring Static IP in Windows Server

## Steps
1. Open:
```text
View Network Settings
```

2. Right-click:
```text
Ethernet > Properties
```

3. Open:
```text
Internet Protocol Version 4 (TCP/IPv4)
```

4. Configure:
- IP Address
- Subnet Mask
- Preferred DNS Server

---

## Screenshot — IPv4 Configuration

<p align="center">
 <img width="1920" height="1080" alt="Screenshot 2026-05-10 190512" src="https://github.com/user-attachments/assets/527b6998-e658-430a-8196-0811a8ae6eb1" />
<img width="1920" height="1080" alt="Screenshot 2026-05-10 190813" src="https://github.com/user-attachments/assets/830ded90-acaa-4361-a66e-068684c69e26" />
<img width="1920" height="1080" alt="Screenshot 2026-05-10 191351" src="https://github.com/user-attachments/assets/de2f8a8c-a7a8-4b51-975e-b0acf2359753" />
</p>

---

# Verifying Static IP Address

## Steps
1. Open Command Prompt
2. Run:
```text
ipconfig
```

3. Verify the assigned IP address

---

## Screenshot — ipconfig Verification

<p align="center">
  <img width="1920" height="1080" alt="Screenshot 2026-05-10 191657" src="https://github.com/user-attachments/assets/e359c6d8-01ec-4125-afbe-ae0cb8a92a0d" />
</p>

---

# Installing Active Directory Domain Services

## Steps
1. Open **Server Manager**
2. Select:
```text
Add Roles and Features
```

3. Proceed with default settings
4. Under Server Roles select:
```text
Active Directory Domain Services
```

5. Click:
```text
Add Features
```

6. Continue with defaults and install

---

## Screenshot — AD DS Installation

<p align="center">
  <img width="1920" height="1080" alt="Screenshot 2026-05-10 192025" src="https://github.com/user-attachments/assets/4b8e4846-9ade-4371-99bb-ae1f44994244" />
<img width="1920" height="1080" alt="Screenshot 2026-05-10 192615" src="https://github.com/user-attachments/assets/5e93a2e9-7f7f-4d1b-9590-59a133c93d57" />
<img width="1920" height="1080" alt="Screenshot 2026-05-10 192735" src="https://github.com/user-attachments/assets/2e6d68e2-81ba-404e-97b5-3883726adb5f" />
<img width="1920" height="1080" alt="Screenshot 2026-05-10 192735" src="https://github.com/user-attachments/assets/5f5aaa59-dc81-4379-a8b3-ba5031d94e42" />
</p>

---

# Promoting Server to Domain Controller

## Deployment Configuration

### Select
```text
Add a new forest
```

### Root Domain Example
```text
LAB.local
```

---

## Domain Controller Options
- Create Directory Services Restore Mode (DSRM) password
- Continue with default settings
- Install and restart the server

> After installation, the virtual machine will reboot automatically.

---

## Screenshot — Domain Controller Promotion

<p align="center">
  <img width="1920" height="1080" alt="Screenshot 2026-05-10 193232" src="https://github.com/user-attachments/assets/8f87b523-e5be-4c34-a9e6-6acacaa2b994" />
<img width="1920" height="1080" alt="Screenshot 2026-05-10 193903" src="https://github.com/user-attachments/assets/c84d815b-61cb-4b76-bbbf-bbbed268489a" />
<img width="1920" height="1080" alt="Screenshot 2026-05-10 193924" src="https://github.com/user-attachments/assets/2faaba66-1b32-4565-8409-00bade04d8d2" />
<img width="1920" height="1080" alt="Screenshot 2026-05-10 193924" src="https://github.com/user-attachments/assets/a3643b57-1f58-4994-9f31-f524779bf56f" />

</p>

---

# Completed Domain Controller Setup

After restarting:
- The login screen should display:
```text
LAB\Administrator
```

- Active Directory administrative tools should now be available.

---

## Screenshot — Completed Domain Controller

<p align="center">
<img width="1920" height="1032" alt="Screenshot 2026-05-10 194815" src="https://github.com/user-attachments/assets/f1e39ec6-c431-4bf6-b698-9f8777b03b25" />
<img width="1920" height="1080" alt="Screenshot 2026-05-10 194559" src="https://github.com/user-attachments/assets/474ffbb4-6f83-4b4d-b3b5-95a2b8d69716" />

</p>

---

# Skills Practiced
- Windows Server administration
- Active Directory setup
- Domain Controller deployment
- Network configuration
- Static IP assignment
- VirtualBox networking
- Basic troubleshooting

---

# What I Learned
This lab provided hands-on experience configuring a Windows Server Domain Controller, managing isolated virtual networks, assigning static IP addresses, and deploying Active Directory services in a virtualized environment.
