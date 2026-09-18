# Enterprise Linux Infrastructure Lab

## Overview

I set up an isolated Linux server in VMware Workstation Pro to get hands-on practice with core Linux sysadmin skills: the command line, networking, user/permissions, and deploying a web service.

The lab is a single Ubuntu Server node on the same isolated lab network I used for my [Active Directory home lab](https://github.com/brentos123/Active-Directory-Home-Lab), configured and managed entirely from the terminal.

## Lab Setup

- **Hypervisor:** VMware Workstation Pro
- **OS:** Ubuntu Linux 20.04 LTS
- **Hostname:** `Corp-Linux-Web01`
- **Specs:** 2 vCPU / 2 GB vRAM / 20 GB disk
- **Network:** `VMnet1 (Host-only)` — same isolated lab subnet as my AD lab, no internet access

---

## Phase 1: VM Provisioning

Deployed a fresh Ubuntu Server 20.04 VM, bound to the isolated `VMnet1` host-only network so it couldn't reach the internet or my real LAN.

### Verification
![Phase 1 verification screenshot](https://github.com/user-attachments/assets/a11311f8-b270-494d-860a-e5628b252d41)

**Next:** configure networking from the shell and set a static IP.

---

## Phase 2: Static IP Configuration

### Issue: wrong network, dynamic IP

Running `ip a` after boot showed the VM had picked up a dynamic IP (`192.168.93.130`) from VMware's default NAT network — not the isolated lab subnet I wanted it on.

**Root cause:** the VM's network adapter was still set to VMware's default NAT mode instead of the host-only `VMnet1` switch I'd built for the lab.

**Fix:**
1. Changed the VM's network adapter setting to `VMnet1 (Host-only)`.
2. Flushed the existing address: `sudo ip addr flush dev ens33`
3. Assigned a static IP on the correct subnet: `192.168.100.30/24`

### Verification
![Phase 2 verification screenshot](https://github.com/user-attachments/assets/0e0c102a-d9c1-4e27-b265-7666f55f8c0e)

---

## Phase 3: Web Server Deployment

Installed and enabled Apache2 as a systemd-managed service.

```bash
sudo apt install apache2
sudo systemctl start apache2
sudo systemctl enable apache2   # persists across reboots
```

### Verification
![Phase 3 verification screenshot](https://github.com/user-attachments/assets/45ad4138-94bb-4ba5-ba5a-10c28f976f8e)

---

## Skills Demonstrated

- **Linux administration:** command-line navigation, `sudo` privilege escalation, package management
- **Networking:** diagnosing and fixing a misconfigured network adapter, static IP assignment via the CLI
- **Service management:** installing, starting, and enabling a systemd service for persistence across reboots
