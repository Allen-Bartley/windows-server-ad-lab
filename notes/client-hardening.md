# 🔧 Windows 11 Client Hardening – Privacy & Performance Tweaks

This document outlines optional system adjustments made to the `WIN11-EDU` virtual machine after joining the Active Directory domain. Inspired by best practices and the [Linus Tech Tips "How to Setup Windows Properly"](https://www.youtube.com/watch?v=MBCiMK4AmEI) video, these tweaks reduce unnecessary background activity, enhance privacy, and clean up the user interface for a more focused lab experience.

---

## 🧠 Registry Tweaks Applied

> Location: `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Search`

| Key Name             | Value | Purpose |
|----------------------|-------|---------|
| `BingSearchEnabled`  | `0`   | Disables Bing web results from Windows Search |
| `AllowSearchToUseLocation` | `0` | Prevents search from using geolocation |
| `CortanaConsent`     | `0`   | Disables Cortana integration |

> These edits were made manually via `regedit` and reflect recommendations from timestamp [13:59](https://youtu.be/MBCiMK4AmEI?t=839) onward in the LTT guide.

---

## 🎯 Intent & Outcome

- ✅ Search behaves locally, without cloud intrusion or location tracking  
- ✅ Cortana removed from the equation for better performance and clarity  
- ✅ Alignment with AD join policies and future Group Policy controls  

This helps shape the client VM into a lean, responsive domain workstation—ideal for testing GPOs, login profiles, and lab security policies.

---

## 🔭 Next Steps

- Document GPOs that replicate or enforce these changes domain-wide  
- Compare experience between hardened client and untouched test VM  
- Explore scripting these changes via PowerShell for automation

---

> “Clean interface. Clear behavior. Controlled privacy. It’s not just hardening—it’s choosing what matters.”

