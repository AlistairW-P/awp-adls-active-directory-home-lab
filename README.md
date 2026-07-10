# awp-adds-active-directory-home-lab
Began 7/06/2026, Completed TBA

## Overview/Goals
The goal was to simulate a real Active Directory environment similar to real-world situations, such as help desks.
- Create various users, OU's (Organisational Units) and security groups
- Connect the server to a client and have security groups and limits affect the client
- Get hands-on experience with basic troubleshooting of networking and domain connectivity

---

## Lab Environment

**Virtualisation**
-VMware Workstation
-Host-only networking (VMnet1)

**Servers and Clients**
- **DC01** - Windows Server 2019
  - Role: Domain Controller, DNS
  - Domain: 'corp.local'
  - IP Address: 192.168.93.10

- **CLIENT01** - Windows 10 Pro for Workstations
  - Role: Client, modelling an employee's environment
  - IP Address: 192.168.93.129

---

## Architecture
The lab consists of a single AD DS domain with one DC and one client on the same host-only subnet.

---

## What I implemented

### 1. Active Directory Domain Services and DNS

- **Configured a Windows 10 installation** both on the client-side and the server-side.
- **Installed AD DS** on a Windows Server 2019.
- **Promoted the server to a Domain Controller** for the 'corp.local' domain.
- **Configured AD-integrated DNS** so the DC handles name resolution for 'corp.local'.
- Set the Windows 10 client's **DNS server** to the DC's IP. 

*CLIENT01Domain.png*: Displays CLIENT01 connected to DC01's 'corp.local' domain.

### 2. Organisational Units (OUs)

Created a simple OU structure to mirror a smaller company:

- 'corp.local'
  - 'Departments'
      - 'HR'
      - 'IT Support'

This structure allows targeted application of policies and simplified management of users and computers.
*corp.localOUs.png*: Displays the structure of 'corp.local'

### 3. Users and Security Groups

- Created user accounts for HR and IT Support Staff.
- Created security groups such as:
    - 'HR Managers'
    - 'IT-HelpDesk'
- Assigned users to appropriate groups to model **role-based access control (RBAC)**

### 4. Group Policy Objects (GPOs)

- Created GPOs linked to specific OUs (e.g. 'HR').
- Implemented settings such as:
    - Interactive logon message / logon banner
    - Basic security options

### 5. Domain join and validation
- Joined CLIENT01 to the 'corp.local' domain.
- Moved CLIENT01 into the appropriate OU to ensure correct policy targeting.
- Verified
    - Domain logon works
    - GPOs apply correctly
    - DNS resolves domain resources
*SecurityGroupBanner.png*: An example of a banner; this one specifically shown only for devices in the 'HR' security group.

---

## Networking and Troubleshooting

During the lab, my main issue was as follows:
- **Host-only network mismatch between the DC and client:**
  - The original plan was to connect CLIENT01 to DC01 through a **Host-Only** connection on the network adaptor, .
  - Through troubleshooting, I realised this didn't connect the two devices, as I was unable to ping either device from the other, and vice versa.
  - The first attempt at fixing was that Network Adaptor 1 could be interfering, so I quickly disabled both adaptors on both devices.
  - Further troubleshooting led back to the Network Adaptors, but by changing from 'Host-Only' to 'Custom', specifically selecting **VMnet1**, both devices were able to connect.
Tools used to fix:
  - **ping:** to make sure both devices could communicate.
  - **ipconfig:** to clarify both devices' IP addresses and subnets.
  - **nslookup:** for DNS testing.

---

## Skills Demonstrated 

- Active Directory Domain Services (AD DS) admin
- DNS config and troubleshooting
- Organisational Unit (OU) design
- User and Group management (RBAC)
- Group Policy creation and targeting
- Windows Server 2019 admin
- VMware Workstation networking (Host-only, NAT, Bridged)
- Basic Windows networking and troubleshooting

---

## Future Improvements?

- Add a second Domain Controller (DC02) for redundancy.
- Implement more clients to test more security groups.
- Integrate a SIEM to collect Windows event logs from the DC(s) and client(s).
- Add file server and share permissions to further practice RBAC.


