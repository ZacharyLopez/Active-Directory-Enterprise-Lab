# 🏗️ Active Directory Enterprise Home Lab

## Overview

This project demonstrates the deployment of a **Windows Server 2022 Active Directory domain environment** with integrated **DNS, DHCP, and NAT routing**, along with **PowerShell-based bulk user provisioning** and a **Windows 10 domain-joined client**.

The goal of this lab was to simulate a real small-enterprise on-prem identity and network infrastructure, providing hands-on experience with core Windows Server administration and domain services.

---

## 🧰 Technologies Used

- Windows Server 2022 Standard  
- Windows 10 Enterprise  
- Active Directory Domain Services (AD DS)  
- DNS Server (AD-integrated)  
- DHCP Server  
- Routing and Remote Access Service (RRAS / NAT)  
- PowerShell  
- Virtualization Platform (VirtualBox / Hyper-V)

---

## 📐 Network Design

**Domain:** `mydomain.com`  
**Domain Controller IP:** `172.16.0.1`  
**DHCP Scope:** `172.16.0.100 – 172.16.0.200`  
**Subnet Mask:** `255.255.255.0`  
**Default Gateway:** `172.16.0.1`  
**DNS Server:** `172.16.0.1`  

**Routing:**  
RRAS NAT configured to allow internal domain clients outbound network access.

**DNS Note:**  
DNS was automatically installed and configured during Active Directory domain promotion. DHCP scope options were configured to assign the Domain Controller as the DNS server for clients.

---

## ⚙️ Deployment Steps

### 1. Configure Static IP for Domain Controller
Assigned a static IP to the internal network interface to ensure stable Active Directory and DNS operations.

[![Static IP](screenshots/01-static-ip-internal.png)](screenshots/01-static-ip-internal.png)

---

### 2. Install Active Directory Domain Services
Installed the Active Directory Domain Services role on Windows Server 2022.

[![Install AD DS](screenshots/02-install-ad-ds.png)](screenshots/02-install-ad-ds.png)

---

### 3. Promote Server to Domain Controller
Created a new forest and established the domain `mydomain.com`.

[![Promote DC](screenshots/03-promote-domain-controller.png)](screenshots/03-promote-domain-controller.png)

---

### 4. Create Administrative OU and Admin Account
Created an administrative OU and dedicated domain administrator account.

[![Create Admin](screenshots/04-create-admin-account.png)](screenshots/04-create-admin-account.png)

---

### 5. Assign Domain Admin Permissions
Added the admin account to the Domain Admins security group.

[![Assign Domain Admin](screenshots/05-assign-domain-admin.png)](screenshots/05-assign-domain-admin.png)

---

### 6. Install Routing and Remote Access Services (RRAS)
Installed RRAS to enable NAT routing for the internal domain network.

[![Install RRAS](screenshots/06-install-rras-role.png)](screenshots/06-install-rras-role.png)

---

### 7. Configure NAT Routing
Configured NAT to allow internal domain clients to access external networks.

[![Configure NAT](screenshots/07-configure-nat.png)](screenshots/07-configure-nat.png)

[![Configure NAT 2](screenshots/08-configure-nat-2.png)](screenshots/08-configure-nat-2.png)

---

### 8. Install DHCP Server Role
Installed the DHCP Server role on the Domain Controller.

[![Install DHCP](screenshots/09-install-dhcp-role.png)](screenshots/09-install-dhcp-role.png)

---

### 9. Configure DHCP Scope
Created a DHCP scope to dynamically assign IP addresses to domain clients.

[![DHCP Scope](screenshots/10-configure-dhcp-scope.png)](screenshots/10-configure-dhcp-scope.png)

---

### 10. Configure DHCP Default Gateway
Configured the Domain Controller as the default gateway for DHCP clients.

[![DHCP Gateway](screenshots/11-configure-dhcp-gateway.png)](screenshots/11-configure-dhcp-gateway.png)

---

### 11. Verify DHCP Scope Options
Verified DHCP scope configuration including DNS server and default gateway assignment for domain clients.

[![Verify DHCP Options](screenshots/12-verify-dhcp-options.png)](screenshots/12-verify-dhcp-options.png)

---

### 12. Bulk User Provisioning with PowerShell
Automated provisioning of 1000 Active Directory user accounts using PowerShell.

[![Create Users](screenshots/13-powershell-create-users.png)](screenshots/13-powershell-create-users.png)

[![Create Users 2](screenshots/14-powershell-create-users-2.png)](screenshots/14-powershell-create-users-2.png)

---

### 13. Verify Users in Active Directory
Confirmed newly created users appeared in Active Directory.

[![Users in AD](screenshots/15-users-in-active-directory.png)](screenshots/15-users-in-active-directory.png)

---

### 14. Deploy Windows 10 Client
Installed a Windows 10 virtual machine to simulate a domain workstation.

[![Windows 10 Setup](screenshots/16-windows10-client-setup.png)](screenshots/16-windows10-client-setup.png)

---

### 15. Verify Client DHCP Assignment
Confirmed the client received an IP address from the DHCP server.

[![Client DHCP](screenshots/17-client-received-dhcp.png)](screenshots/17-client-received-dhcp.png)

---

### 16. Join Client to Domain
Joined the Windows 10 client to the `mydomain.com` domain.

[![Join Domain](screenshots/18-join-client-to-domain.png)](screenshots/18-join-client-to-domain.png)

---

### 17. Confirm Client in Active Directory
Verified the domain-joined computer object appeared in Active Directory.

[![Client in AD](screenshots/19-client-visible-in-ad.png)](screenshots/19-client-visible-in-ad.png)

---

## ✅ Final Outcome

- Fully operational Windows Server 2022 domain  
- Active Directory Domain Services deployed  
- DNS and DHCP integrated  
- NAT routing providing outbound connectivity  
- 1000 domain users provisioned via PowerShell  
- Windows 10 client successfully joined to domain  

This environment mirrors a real-world small enterprise Windows infrastructure.

---

## 🎯 Skills Demonstrated

- Windows Server 2022 Administration  
- Active Directory Domain Deployment  
- DNS and DHCP Configuration  
- RRAS / NAT Routing  
- PowerShell Automation  
- Bulk User Provisioning  
- Domain Client Management  
- Enterprise Network Integration  

---

## 📜 Script Attribution

Bulk Active Directory user creation script sourced from:  
**(Replace this line with your actual GitHub script source link)**

Used for educational lab deployment.

---

## 🚀 Future Enhancements

- Group Policy deployment  
- File server with NTFS permissions  
- Password policy enforcement  
- OU-based access delegation  
- Event log monitoring  
