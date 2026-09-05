# Windows Server Active Directory Home Lab

A hands-on IT Infrastructure and Windows Server administration lab built to simulate a small enterprise environment using Windows Server, Active Directory, DNS, DHCP, Group Policy, File Services, and Windows 11 Pro.

The project was built from scratch in a virtualized environment using VirtualBox, with a Windows client connected to the Active Directory domain.

# 📌 Project Overview
This project was created to develop practical skills in:


* Windows Server Administration
* Active Directory Domain Services (AD DS)
* Domain Controller Management
* DNS Administration
* DHCP Configuration
* User and Group Management
* Organizational Units (OUs)
* Group Policy (GPO)
* File Server and Shared Folders
* NTFS and Share Permissions
* Least Privilege
* Windows Domain Join
* Software Deployment
* Network Troubleshooting
* IT Support Troubleshooting
* Backup and Recovery Fundamentals

The main objective was not only to configure the environment, but also to troubleshoot problems that occurred during implementation and understand how the different infrastructure services interact.

# 🏗️ Lab Architecture

```┌─────────────────────────┐ │ Windows Server │ │ DC01 │ │ │ │ Active Directory │ │ DNS │ │ DHCP │ │ Group Policy │ │ File Services │ └────────────┬────────────┘ 
```

### Core Environment


| Component | Configuration |
| :--- | :--- |
| Server OS | Windows Server 2022 |
| Client OS | Windows 11 Pro |
| Virtualization	| Oracle VirtualBox |
| Active Directory Domain	| lab.local |
| Domain Controller	| DC01 |
| Server IP	| 192.168.20.10 |
| Client IP	| 192.168.20.100 |
| DNS | Windows Server / Domain Controller |
| DHCP | Windows Server DHCP |
| Authentication | Active Directory |
| Network | VirtualBox + Ethernet connectivity |
	
IP addresses shown above are from the lab environment and are used for documentation purposes only.

# 🔧 Technologies & Tools

  * Windows Server 2022
  * Windows 11 Pro

  ### Infrastructure Services
  * Active Directory Domain Services (AD DS)
  * DNS
  * DHCP
  * Group Policy
  * Windows File Services
 
  ### Networking
  * TCP/IP
  * IP Addressing
  * DHCP
  * DNS
  * NAT
  * Internal Network
  * Host-Only Networking
  * Bridged Networking
  * Ethernet
 
  ### Virtualization
  * Oracle VirtualBox
 
  ### Troubleshooting Tools
  * ipconfig
  * ping
  * nslookup
  * gpupdate
  * nltest
  * Windows Event Viewer
  * Server Manager
  * DNS Manager
  * DHCP Manager
  * Active Directory Users and Computers
 
# 🖥️ Windows Server Configuration

The lab started by installing and configuring Windows Server as the central infrastructure server.

The server was configured as a Domain Controller and became the main authentication and network services server for the lab.

  ### Implemented
  * Installed Windows Server
  * Configured server networking
  * Installed Active Directory Domain Services
  * Promoted the server to a Domain Controller
  * Created the lab.local domain
  * Configured DNS
  * Configured DHCP
  * Verified domain services
  * Created and managed domain objects

# 👤 Active Directory

The lab.local Active Directory environment was structured to simulate a basic organizational environment.

### Implemented
* Created Active Directory domain
* Created Organizational Units
* Created user accounts
* Created security groups
* Added users to groups
* Tested domain authentication
* Tested standard domain-user login
  
### Example Structure
```

lab.local │ ├── Builtin ├── Computers ├── Domain Controllers ├── Users ├── ForeignSecurityPrincipals ├── Managed Service Accounts │ └── IT │ └── IT-Users
```
A dedicated IT-Support security group was also created and used for access management.

# 🔐 Group Policy

Group Policy was used to simulate centralized Windows administration.

### Configured / Tested

* Password Policy
* Account Lockout Policy
* User and computer policy management
* Group Policy application
* gpupdate /force
* Domain policy troubleshooting

The lab also included testing situations where Group Policy could not communicate correctly with the Domain Controller.

# 🔑 Password & Account Security
The environment was used to practice common Active Directory account-management tasks.

### Practiced
* Password policy configuration
* Password reset
* Account lockout
* Unlocking accounts
* Testing failed login scenarios
* Standard User vs Administrator
* Least Privilege principles

The goal was to understand how an IT Support technician would handle common user-account incidents in a domain environment.

# 📁 File Server & Permissions

A file-sharing environment was configured to practice Windows access control.

### Implemented
* Created shared folders
* Configured NTFS permissions
* Configured Share permissions
* Tested user access
* Tested restricted access
* Applied least-privilege principles

### Permission Model

**User → Security Group → Share Permissions → NTFS Permissions → Effective Access**

This provided practical experience with the difference between Share Permissions and NTFS Permissions.

# 📦 Software Deployment
Software deployment through Group Policy was also practiced.

A Windows Installer package (.msi) was deployed using:
```
Group Policy ↓ Computer Configuration ↓ Software Settings ↓ Software Installation ↓ Assigned MSI Package
```
The deployment was tested on the domain client after restarting the computer.

# 🌐 DNS Configuration & Troubleshooting

DNS was an important component of the lab because Active Directory relies heavily on DNS for domain services and locating the Domain Controller.

### Practiced
* DNS zone verification
* lab.local Forward Lookup Zone
* Domain name resolution
* Domain Controller name resolution
* nslookup
* DNS troubleshooting

Example:

nslookup DC01.lab.local

The client successfully resolved the Domain Controller through DNS.

# 📡 DHCP Configuration & Troubleshooting

Windows Server DHCP was configured to automatically provide network configuration to clients.

### Practiced
* DHCP installation
* DHCP authorization
* Scope configuration
* IP address assignment
* DHCP client testing
* DHCP renewal
* DHCP troubleshooting

One of the real troubleshooting scenarios involved clients receiving:

169.254.x.x

This APIPA address indicated that the client was not receiving a valid DHCP lease.

# 🔗 Domain Join

The Windows 10 Pro client was successfully joined to:

lab.local

The final authentication flow was:
```
Windows 11 Pro │ ▼ Network Connectivity │ ▼ DNS │ ▼ Domain Controller │ ▼ Active Directory │ ▼ Domain User Authentication
```

The client was successfully authenticated using a domain user account.

# 🧪 Troubleshooting Scenarios

One of the most valuable parts of the project was troubleshooting real problems instead of only following configuration steps.

###Issues Encountered
* Virtual machines stopping unexpectedly
* Host resource / VM execution problems
* DHCP clients receiving 169.254.x.x APIPA addresses
* DHCP renewal failures
* Ping failures between network interfaces
* Firewall blocking ICMP traffic
* Connectivity problems between physical and virtual network environments
* Domain Join authentication errors
* Domain Controller connectivity problems
* Group Policy communication failures

These issues were investigated using tools such as:

ipconfig
ping
nslookup
nltest
gpupdate /force

along with Windows administrative tools and network adapter configuration.

# 🔎 Domain Connectivity Verification

The final environment was tested using:

nltest /dsgetdc:lab.local

and:

nltest /sc_verify:lab.local

These tests were used to verify that the client could locate the Domain Controller and that the domain secure channel was functioning correctly.

DNS resolution was also tested using:

nslookup DC01.lab.local

# 💾 Backup & Recovery Fundamentals

The project also included basic backup and recovery concepts to understand how Windows infrastructure should be protected against configuration or system failures.

The focus was on understanding:

* Backup concepts
* Recovery planning
* System availability
* Importance of infrastructure documentation
* Recovery considerations for Windows Server environments

# 🧠 Key Lessons Learned

This project strengthened my understanding of how enterprise IT infrastructure components work together.

### 1. DNS is critical for Active Directory

Active Directory is highly dependent on DNS for locating domain services and Domain Controllers.

### 2. DHCP problems can look like network problems

An incorrectly configured DHCP environment can result in APIPA addresses and loss of connectivity.

### 3. Troubleshooting should be systematic

Instead of changing random settings, I learned to isolate the problem by checking:

IP Configuration
      ↓
Network Connectivity
      ↓
DNS Resolution
      ↓
Domain Controller Connectivity
      ↓
Authentication
      ↓
Group Policy

### 4. Permissions should follow Least Privilege

Users should receive only the access required to perform their responsibilities.

### 5. Understanding the cause is more important than simply fixing the error

The project helped me develop a troubleshooting mindset based on eliminating possible causes one by one.

# 📸 Screenshots

Screenshots documenting the lab configuration are organized into the following categories:

- **Active Directory** — Users, Groups, OUs, and domain configuration
- **DNS** — DNS zones and name resolution
- **DHCP** — DHCP configuration and IP address assignment
- **Group Policy** — GPO configuration and policy testing
- **File Server** — Shared folders and permissions
- **Troubleshooting** — Network, DNS, DHCP, domain connectivity, and troubleshooting tests

These screenshots demonstrate the actual configuration and successful testing of the environment.

# 📂 Project Structure

The repository is organized into the following sections:

- `README.md` — Main project documentation
- `docs/` — Project documentation and network diagram
- `docs/network-diagram.png` — Lab network architecture
- `docs/lab-overview.md` — Lab configuration overview
- `docs/troubleshooting.md` — Troubleshooting scenarios and solutions
- `screenshots/` — Screenshots documenting the lab
- `screenshots/active-directory/` — Active Directory configuration
- `screenshots/dns/` — DNS configuration
- `screenshots/dhcp/` — DHCP configuration
- `screenshots/group-policy/` — Group Policy configuration
- `screenshots/file-server/` — File Server and permissions
- `screenshots/troubleshooting/` — Troubleshooting evidence
- `.gitignore` — Files and folders excluded from Git

# 🎯 Project Goals

The main goals of this project were to:

* Build a realistic Windows infrastructure environment
* Gain hands-on Active Directory experience
* Practice Windows Server administration
* Understand DNS and DHCP dependencies
* Practice centralized administration using Group Policy
* Understand Windows permissions
* Develop practical troubleshooting skills
* Create documented infrastructure experience suitable for an IT Support / Infrastructure role

# 🚀 Future Improvements

Possible future extensions include:

* Adding additional domain clients
* Creating multiple departments and OUs
* Expanding Group Policy configurations
* Implementing more advanced file-server permissions
* Adding monitoring
* Implementing Windows Server backup scenarios
* Adding additional networking scenarios
* Practicing more advanced Active Directory administration

# 💼 Skills Demonstrated

This project demonstrates practical experience with:

* Windows Server Administration
* Active Directory
* DNS
* DHCP
* Group Policy
* User & Group Management
* Organizational Units
* File Server Administration
* NTFS Permissions
* Share Permissions
* Least Privilege
* Domain Join
* Network Troubleshooting
* IT Support Troubleshooting
* VirtualBox

# 📌 Project Status

### Completed ✅

This lab was built as a hands-on learning and portfolio project to demonstrate practical Windows infrastructure, Active Directory administration, networking, security, and troubleshooting skills.

# Author

Yasser Obaid

Computer Engineering Graduate | IT Support | Infrastructure | Networking

GitHub: Yasser-Obaid
