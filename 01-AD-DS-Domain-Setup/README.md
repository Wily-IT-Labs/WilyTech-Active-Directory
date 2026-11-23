# Lab 01 — Active Directory Domain Services Deployment & Verification

## Project Overview

This lab demonstrates the deployment and validation of Active Directory Domain Services (AD DS) in a virtualized Windows Server 2022 environment for a fictional company, WilyTech.

The objective is to establish a functional domain infrastructure, validate DNS and domain controller discovery, and verify critical Active Directory services.

## Lab Environment

| Component | Configuration |
|---|---|
| Hypervisor | VMware Workstation |
| Domain Controller | DC01 |
| Server OS | Windows Server 2022 |
| Client OS | Windows 11 Pro |
| Domain | ad.wilytech.test |
| Domain Controller IP | 192.168.72.10 |
| Client Computer | PC01 |
| Network | VMware NAT |

## Implementation and Verification

1. Configured the Windows Server environment and promoted DC01 to a domain controller.
2. Installed and configured Active Directory Domain Services and DNS.
3. Joined the Windows 11 client PC01 to the domain.
4. Verified Active Directory DNS zones and domain controller discovery.
5. Validated LDAP SRV records using `nslookup`.
6. Performed DNS health checks using `dcdiag /test:DNS /v`.
7. Verified NTDS, DNS, Netlogon, and KDC service status.
8. Confirmed all five FSMO roles were assigned to DC01.
9. Verified the SYSVOL and NETLOGON network shares.

## PowerShell and Administrative Commands

```powershell
Get-DnsServerZone
nltest /dsgetdc:ad.wilytech.test
nslookup -type=SRV _ldap._tcp.dc._msdcs.ad.wilytech.test
dcdiag /test:DNS /v
Get-Service NTDS,DNS,Netlogon,KDC
netdom query fsmo
net share
```

## Results

- Domain controller discovery completed successfully.
- LDAP SRV records resolved to DC01.
- DNS diagnostic tests passed.
- All four essential Active Directory services were running.
- All five FSMO roles were assigned to DC01.
- SYSVOL and NETLOGON shares were available.

## Skills Demonstrated

- Windows Server 2022 administration
- Active Directory Domain Services
- DNS configuration and troubleshooting
- Domain controller validation
- PowerShell administration
- Infrastructure health verification

## Evidence

Screenshots documenting the configuration and verification steps are stored in the `screenshots` directory.

## Conclusion

The WilyTech Active Directory environment was successfully deployed and its core domain services were validated. This lab establishes the foundation for subsequent identity, access management, Group Policy, and automation exercises.