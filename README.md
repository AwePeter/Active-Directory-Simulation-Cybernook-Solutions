32﻿
# Active Directory Simulation – Cybernook Solutions

This project is the deployment of a Windows Server Domain Controller (Active Directory) for a company called **Cybernook Solutions**. It includes domain setup, client configuration, OU design, group policies, and access control in an enterprise environment.

---

## Company Structure

**Cybernook Solutions** is a small IT services firm with the following structure:

- 1 x Windows Server (AD Domain Controller)
- 1 x Windows 10 Client PC (HR Department)
- 1 x Windows 7 Client PC (IT Department)

---

## Project Objectives

- Configure an AD Domain Controller on Windows Server
- Join client PCs to the domain
- Create Organizational Units (OUs)
- Implement basic Group Policies for access control
- Simulate a centralized IT environment

---

## Network Design

```
Internet
   ↓
Router (Gateway: 10.0.5.1)
   ↓
Switch
 ┌──────┬─────────────┬──────────────┐
 │      │             │              │
Server  PC1 (Win 10)   PC2 (Win 7)
```

| Device        | IP Address      | Role                       |
|---------------|----------------|-----------------------------|
| Windows Server| 10.0.5.8       | AD Domain Controller (DC)   |
| Windows 10 PC | DHCP           | Client (HR)                 |
| Windows 7 PC  | DHCP           | Client (IT)                 |

---

## Domain Configuration

- **Domain Name**: `cybernook.local`
- **Server Name**: `CYBERNOOK`
- **Static IP**: `10.0.5.8`
- **AD Roles Installed**: AD DS, DNS (DHCP)

---

## Organizational Units (OUs)

Created using **Active Directory Users and Computers**:

```
Cybernook.local
├── OU: HR Department
│   └── Users: Kerry.HR
    └── Users: Pete.HR

├── OU: IT Department
│   └── Users: Stone.IT
```

---

## Group Policy (GPO)

Created and linked using **Group Policy Management Console (gpmc.msc)**:

- **GPO Name**: `DisableRemovableDrives`
- **Linked to**: OU: IT Department
- **Policy Configured**:
  - `Computer Configuration` > `Administrative Templates` > `System` > `Removable Storage Access`
  - Set **"All Removable Storage classes: Deny all access"** to **Enabled**

Result: USB and external drives are disabled for all users in the **Accounts OU**.

- **GPO Name**: `DisableRemovableDrives`
- **Linked to**: OU: HR Department
- **Policy Configured**:
  - `Computer Configuration` > `Administrative Templates` > `System` > `Removable Storage Access`
  - Set **"Remove and Prevent all access to shutdown, Restart and Hibalate Commands"** to **Enabled**

Result: Commands disabled for all users in the **HR and IT OU**.


---

## Screenshots

- AD Domain Structure
- GPO Editor Screenshot
- PC joined to domain
- Result of denied USB access

---

## Key Takeaways

- Gained practical experience with Windows Server roles and domain setup
- Implemented centralized access control using Group Policy
- Learned how to structure users and departments with OUs
- Applied IAM concepts in a real-world simulated environment

---

## Author

**Awe Olorunniyi Peter**  
Cybersecurity Analyst  

