# awp-adls-active-directory-home-lab
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

## What I implements

### 1. Active Directory Domain Services and DNS

- **Configured a Windows 10 installation** both on the client-side and the server-side.
- **Installed AD DS** on a Windows Server 2019.
- **Promoted the server to a Domain Controller** for the 'corp.local' domain.
- **Configured AD-integrated DNS** so the DC handles name resolution for 'corp.local'.
- Set the Windows 10 client's **DNS server** to the DC's IP. 

CLIENT01Domain.png: Displays CLIENT01 connected to DC01's 'corp.local' domain.


