# 🖥️ Virtual Machine Configuration – AD Lab Infrastructure

This document outlines the specifications and roles of the two VirtualBox-based machines used in the Active Directory lab: a Windows Server 2022 Domain Controller and a Windows 11 Education client. Each VM is tuned for network experimentation and skill-building in AD DS, DHCP, and NAT routing scenarios.

---

## 🧱 VM Roles & Purpose

| VM Name      | OS                                 | Role                                                   |
|--------------|-------------------------------------|--------------------------------------------------------|
| `DC01`        | Windows Server 2022 (Desktop Experience) | AD DS, DNS, DHCP, NAT Routing                         |
| `WIN11-EDU`   | Windows 11 Education (Version 24H2) | DHCP Client, Domain Join, Internet Access             |

Both VMs connect via a VirtualBox **Internal Network** named `LabNet`. The Server VM also includes a second **NAT adapter** for internet access and RRAS-based routing to serve the client.

---

## ⚙️ `DC01` – Server VM Specifications

| Setting           | Value                                   |
|-------------------|------------------------------------------|
| **RAM**           | 12,644 MB                                |
| **CPU**           | 8 vCPUs                                  |
| **Disk Size**     | 50 GB VDI                                |
| **Video Memory**  | 128 MB                                   |
| **Graphics Controller** | VMSVGA                             |
| **NIC 1**         | Intel PRO/1000 MT Desktop – `intnet`     |
| **NIC 2**         | Intel PRO/1000 MT Desktop – NAT          |
| **USB Controller**| xHCI                                     |
| **Guest Additions**| ISO mounted                            |
| **Boot Mode**     | EFI (GUI enabled)                        |

> GUI installation was manually selected during setup due to VirtualBox's default behavior installing Server Core in unattended mode.

---

## 💻 `WIN11-EDU` – Client VM Specifications

| Setting           | Value                                   |
|-------------------|------------------------------------------|
| **RAM**           | 4096 MB                                  |
| **CPU**           | 2 vCPUs                                  |
| **Disk Size**     | 80 GB VDI                                |
| **Video Memory**  | 128 MB                                   |
| **Graphics Controller** | VBoxSVGA                          |
| **NIC 1**         | Intel PRO/1000 MT Desktop – `intnet`     |
| **USB Controller**| xHCI                                     |
| **Guest Additions**| ISO mounted                            |
| **Boot Mode**     | EFI                                       |
| **Secure Boot**   | Enabled                                   |
| **TPM Version**   | v2.0                                      |

> Configuration supports domain joining, group policy testing, DHCP lease reception, and internet routing validation.

---

## 🌐 Network Summary

- **Internal Network** (`LabNet`) used for domain communication and DHCP delivery.
- **DC01** provides IPs to client via DHCP (`192.168.1.100–200`) and routes internet traffic via NAT adapter.
- **Client VM** successfully joined domain and accessed external sites through server routing.

---

This setup reflects hands-on knowledge in role installation, system provisioning, and network simulation—built for lab use and IT career development.

