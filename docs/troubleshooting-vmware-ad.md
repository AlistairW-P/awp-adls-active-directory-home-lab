# Troubleshooting VMware + Active Directory

## Common issues

### 1. Different Subnets

Symptom:
- Client IP: '192.168.93.x'
- DC IP: '192.168.100.x'
- Ping failes, domain join fails.

Fix:
- Change network adaptors inside VMwar to make sure both devices are using the **same VMware network** (e.g. VMnet1, as I used).
- Assign IPs in the same subnet.
TIP: Follow the subnet cheat sheet (/32 = 255.255.255.255 = 1 user, /31 = 255.255.255.253 = 2 users, etc.)

## 2. Wrong DNS Servevr

Symptom:
- Error: "An AD DC for the domain 'corp.local' could not be contacted".

Fix:
- Set client DNS to the **DC's IP**.
Verify with:
    ''' cmd
    nslookup corp.local