# 📝 AD Promotion & Domain Join Log

This document records key moments from the setup and deployment of Active Directory Domain Services in the `windows-server-ad-lab` environment. It includes observations, setbacks, and milestone accomplishments—particularly the first successful domain join of a Windows 11 client using administrator credentials.

---

## 🛠️ Domain Controller Promotion

**Date:** July 2025  
**Server VM:** `DC01` (Windows Server 2022 Standard, Desktop Experience)

### Promotion Steps:
- Installed **Active Directory Domain Services (AD DS)** role via Server Manager.
- Selected “New Forest” setup and designated domain: `Arcus.local`.
- DNS delegation warning appeared during setup (normal for first DC).
- Domain Controller promotion completed successfully; server rebooted into domain mode.
- Verified AD DS presence in Server Manager and functionality of DNS role.

---

## 🔗 Windows 11 Domain Join

**Client VM:** `WIN11-EDU` (Windows 11 Education, 24H2)

### Preconditions:
- Confirmed client received IP lease via DHCP: `192.168.1.101`
- Verified DNS assignment from DHCP matched domain controller: `192.168.1.1`
- Pinged domain controller IP and FQDN: `Arcus.local` – successful resolution
- Routed internet access through NAT-enabled RRAS service on `DC01`

### Join Procedure:
- Accessed System → "Domain or workgroup" link
- Selected "Join a Domain" and entered: `Arcus.local`
- Supplied domain admin credentials: `Arcus\Administrator`
- Received “Welcome to the domain” confirmation
- Restarted client VM

### Result:
✅ Successfully logged into `WIN11-EDU` using domain credentials  
🧑‍💻 Username: `Arcus\Administrator`  
🌐 Verified domain membership and network access

---

## 🎯 Notes & Observations

- VirtualBox’s internal network (`intnet`) allowed isolated AD traffic without internet interference
- DHCP scope delivery and DNS resolution were vital to smooth domain join
- Initial login triggered domain profile creation and security context negotiation
- RRAS NAT routing ensured full internet access post-domain join

---

## 🧭 Next Steps

- Create new domain users within Active Directory
- Build Organizational Units (OUs) for lab simulations
- Apply basic Group Policy Objects (GPOs) to test environmental control
- Monitor event logs and Active Directory Users and Computers (ADUC) for replication or auth behavior

---

> “Joining the domain wasn’t just a checkbox—it was a handshake between machines, a moment where identity, trust, and infrastructure aligned.”  
> — Lab Notes, July 2025
