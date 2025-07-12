# 🔧 Windows 11 Client Hardening – Privacy & Usability Tweaks

This document outlines system-level refinements applied to the `WIN11-EDU` virtual machine after joining the `Arcus.local` domain. Inspired by best practices from [Linus Tech Tips – How to Setup Windows Properly](https://www.youtube.com/watch?v=MBCiMK4AmEI), these edits reduce cloud-based background activity, enhance privacy, and reflect personalized interface choices that support focused, streamlined usage in a lab setting.

---

## 🧠 Registry Changes

> Location: `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Search`

| Key Name                    | Value | Purpose                                      |
|-----------------------------|--------|----------------------------------------------|
| `BingSearchEnabled`         | `0`    | Disable Bing web search integration          |
| `AllowSearchToUseLocation` | `0`    | Prevent location-based search suggestions    |
| `CortanaConsent`           | `0`    | Disable Cortana and related cloud queries    |

> These changes improve local-only search behavior, reduce telemetry, and remove voice assistant overhead.

> In addition to core security enhancements, registry-level hardening was applied to remove web-linked clutter from Start menu searches. This improves local application launching speed and creates a focused interface environment across both lab VMs and personal endpoints. The intent reflects an operational mindset prioritizing clarity, privacy, and user efficiency.

---

## 🧭 UI Customization

| Setting        | Value   | Purpose                               |
|----------------|---------|---------------------------------------|
| Start Button Position | Left-aligned | Matches legacy Windows placement for improved muscle memory and ease of use |

Applied via:  
**Settings → Personalization → Taskbar → Taskbar Behaviors → Taskbar Alignment → Left**

> This simple tweak enhances consistency across systems and reduces visual noise—especially useful when switching between domain-joined systems and personal devices.

---

## 🎯 Resulting Experience

- Search feels faster and more local  
- Interface remains familiar and distraction-free  
- Client VM behaves more predictably for GPO and policy testing

---

## 🔭 Next Steps

- Document GPO equivalents to enforce these preferences domain-wide  
- Explore Taskbar item visibility controls for deeper UI customization  
- Create PowerShell scripts to automate registry edits and Start alignment during deployment

---

> “A system isn’t truly yours until it behaves the way you think—not the way it was shipped.”
