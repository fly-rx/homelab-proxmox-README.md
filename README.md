# homelab-proxmox-README.md
# Home Lab: Proxmox, Active Directory & Network Services

A self-hosted IT lab I built to practice the work of a help desk / sysadmin role: virtualization, Windows domain management, DNS, remote access, and ticketing.

## Hardware
- **Pantheon**: Lenovo ThinkCentre M920q (mini-PC) running Proxmox VE 9.2
- Raspberry Pi Zero 2 W (Pi-hole, Kali Linux, Tailscale experiments)
- TP-Link Deco mesh network

## What's running

| Service | Type | Purpose |
|---|---|---|
| Windows Server 2022 (DC01) | VM | Domain controller for `ro-lad.local`: AD DS, DNS, users/groups |
| Pi-hole | LXC | Network-wide DNS filtering and ad blocking |
| Tailscale | Host | Secure remote access to the lab |
| osTicket | LXC | Help desk ticketing, LDAP-integrated with Active Directory (in progress) |

## Active Directory
- Built domain `ro-lad.local` on Windows Server 2022
- Created an OU structure: **IT, HR, Sales**
- Managed users and groups, DNS records

## Problems I solved
- **Proxmox web UI unreachable:** traced it to a subnet mismatch on the host and corrected the network config.
- **Pi-hole DNS single point of failure:** added a secondary upstream resolver so DNS keeps working if Pi-hole goes down.
- **Pi-hole dnsmasq query warnings:** tuned the query limit.
- **Network slowdown:** found a wirelessly connected Pi-hole was hurting performance and moved to a better setup.
- **Disk space errors on Pi Zero 2 W:** troubleshot a failed Xfce install on Kali.

## Skills demonstrated
Proxmox / virtualization · Windows Server 2022 · Active Directory · DNS · LXC containers · Linux (Debian, Arch, Kali) · SSH · static IP addressing · Tailscale · troubleshooting

## Screenshots
<!-- Add 2-4 screenshots: Proxmox dashboard, AD Users & Computers showing the OUs, Pi-hole dashboard -->

## Roadmap
- [ ] Finish osTicket + LDAP integration
- [ ] Upgrade Pantheon to 16 GB RAM
- [ ] Add network diagram

## Contact
Rodney Acosta · rodneyx1222@gmail.com
