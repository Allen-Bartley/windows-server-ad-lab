# 🧪 Windows Server AD Lab – Virtualized Infrastructure for Learning DNS, DHCP, and NAT Routing

> *"Built by hand, broken by design, fixed by experience."*

This project documents the creation of a virtualized Active Directory lab using Windows Server 2022 and Windows 11 Education (24H2), configured inside VirtualBox for practical learning, troubleshooting, and IT infrastructure development. The lab is designed to simulate real-world scenarios such as domain joining, DHCP provisioning, NAT routing, and role-based Windows Server administration.

---

## 🧱 Environment Summary

| Component | Role | OS |
|-----------|------|----|
| `DC01` | Domain Controller / DHCP / NAT Router | Windows Server 2022 Standard (Desktop Experience) |
| `WIN11-EDU` | Client Workstation | Windows 11 Education (Version 24H2) |

Both virtual machines communicate over a VirtualBox **Internal Network** named `LabNet`, with the server also connected to the internet via a second **NAT adapter** and configured to route traffic for the client VM using **RRAS**.

---

## 🛠️ Setup Phases

### Phase 1: Server GUI Correction
- VirtualBox’s unattended install defaulted to **Server Core**, preventing GUI access.
- GUI installed successfully after disabling unattended mode and manually selecting **Desktop Experience** during setup.

### Phase 2: AD DS Deployment
- Server promoted to a **Domain Controller** using `192.168.1.1` as its static IP.
- DNS delegation warning correctly skipped (first DC in forest).

### Phase 3: DHCP Configuration
- Scope created: `192.168.1.100–192.168.1.200`
- Router address assigned as `192.168.1.1`
- DHCP validated with `ipconfig /release` and `ipconfig /renew` from the client

### Phase 4: RRAS NAT Routing
- Initial attempt using NPAS role failed due to missing tools and dependencies
- Reinstalled using full **Remote Access** role with **Routing** services selected
- Enabled NAT on the server’s internal NIC, allowing the Windows 11 client to access the internet

---

## ⚙️ VM Specifications

See [`VirtualMachines.md`](VirtualMachines.md) for full hardware allocation and adapter configuration.

> This lab environment reflects enterprise principles using home virtualization—relevant for entry-level IT support, network administration, and certification prep.

---

## ✅ Lab Capabilities

- Active Directory domain joining and DNS resolution
- DHCP lease management and scope configuration
- NAT routing simulation for internal clients
- Foundation for group policy experimentation and WSUS expansion

---

## 📸 Screenshots & Diagrams

Located in the `assets/screenshots/` folder. Topology image and installation logs to be added as the lab expands.

---

## 📚 Related Repositories

- [`residential-network-architecture`](https://github.com/Allen-Bartley/residential-network-architecture) – Physical home network layout with ISP, fiber backbone, and endpoint strategy
- [`hardware-drive-cloning`](https://github.com/Allen-Bartley/hardware-drive-cloning) – Disk prep and recovery workflows used before and after VM configuration

---

> Maintainer: Allen Bartley  
> Repository Created: July 2025  
> Status: Functional – Under Iterative Expansion
