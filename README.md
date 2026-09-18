# Enterprise Linux Core Infrastructure & Web Service Deployment Lab

## Project Overview
The objective of this project is to provision, secure, and configure an isolated Linux enterprise server node utilizing VMware Workstation Pro. This lab demonstrates hands-on technical proficiency with Linux systems administration, bash command-line operations (CLI), user/permission mapping, network configuration, and automated web service deployment.

---

## Phase 1: Local Hypervisor Provisioning & Linux Initialization

To simulate a standardized corporate engineering environment, a dedicated Linux virtual machine framework was deployed into an isolated internal testing lane.

### 1. System Infrastructure Specifications
- **Hypervisor Platform:** VMware Workstation Pro
- **Operating System:** Ubuntu Linux 20.04 LTS (64-bit Core)
- **Planned Hostname:** Corp-Linux-Web01
- **vCPU Allocation:** 2 Cores
- **vRAM Allocation:** 2 GB (2048 MB)
- **Storage Target:** 20 GB Virtual Disk (Single file format)
- **Hypervisor Network Interconnect:** Hard-bound to custom virtual switch layer **`VMnet1 (Host-only)`** for closed network isolation.
