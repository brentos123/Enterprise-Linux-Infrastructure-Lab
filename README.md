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

### 2. Visual Verification
<img width="1919" height="1013" alt="image" src="https://github.com/user-attachments/assets/a11311f8-b270-494d-860a-e5628b252d41" />


### 3. Next Milestone
- Access the native Bash shell interface platform, configure explicit interface IP addresses, and begin system software initialization loops.

---

## Phase 2: Command-Line Interface (CLI) Networking & Static IP Provisioning

To integrate the Linux node into the existing corporate network block, system configuration variables were applied directly via the Bash shell terminal layer.

### 1. Troubleshooting Case Study: Hypervisor Network Mismatch & Dynamic IP Leases
- **Issue Encountered:** Running the initial network audit tool (`ip a`) revealed a random, dynamic IP address block (`192.168.93.130`) matching default hypervisor NAT/DHCP scopes rather than the isolated testing lane specifications.
- **Root Cause Analysis:** The underlying virtual machine network configuration defaulted to standard broad NAT properties upon compilation, splitting network communication routing paths away from the target core subnet layer.
- **Remediation Action:** Intervened at the hypervisor level to map the hardware network adapter strictly to the **`VMnet1 (Host-only)`** switch segment. Flushed the active random address stacks (`sudo ip addr flush dev ens33`), and systematically injected an explicit static signature address matching project design criteria.

### 2. Network Specifications
- **Target Interface Identifier:** Local adapter instance (`ens33`)
- **Assigned Static IP Parameters:** `192.168.100.30/24` (Bound directly to the private lab subnet layer)

### 3. Visual Verification
<img width="1919" height="1028" alt="image" src="https://github.com/user-attachments/assets/0e0c102a-d9c1-4e27-b265-7666f55f8c0e" />


---

## Phase 3: Enterprise Service Provisioning & Web Server Deployment

The Linux node infrastructure layout has concluded with the successful deployment of a public-facing system web application daemon.

### 1. Service Deployment Parameters
- **Application Engine:** Apache2 HTTP Server (Open-Source Web Daemon)
- **Service Controller Tooling:** Systemd Initialization Daemon (`systemctl`)
- **System Constraints Applied:** Initialized the baseline runtime module (`sudo systemctl start apache2`) and committed a boot-persistence parameter configuration (`sudo systemctl enable apache2`) to guarantee software availability upon system power cycles.

### 2. Visual Verification
<img width="1919" height="1030" alt="image" src="https://github.com/user-attachments/assets/45ad4138-94bb-4ba5-ba5a-10c28f976f8e" />


## Project Conclusion & Core Competencies Demonstrated
This lab validates practical cross-platform competencies critical for systems administration and helpdesk engineer support roles:
- **Systems Administration CLI:** Advanced command navigation across the Bash Shell environment and administrative privilege escalations using `sudo`.
- **Infrastructure Troubleshooting:** Rectified automated hypervisor network adapter bindings, mapping fixed interface signatures via terminal input code arrays.
- **Service Lifecycle Management:** Package execution, service status auditing, and system boot profile modifications.

