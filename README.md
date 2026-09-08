## NETWORKWALKS-EMMANUEL-B083-WK1-PM1-CYBERSECURITY-LAB-SETUP
Week 1 Project Kali Linux Lab Setup
## 📌 Project Overview
This first project focuses on setting up a virtual machine for cybersecurity laboratory using VirtualBox and Kali Linux.

The purpose of using VirtualBox for the lab is to create a controlled environment where cybersecurity activities can be performed safely and repeatedly.

On the VirtualBox environment lab we can configure a private virtual network so that we can add other machines to be used as targets for authorized security testing.

## 🎯 Objectives
The main objectives of this project are to:

1. Install and configure VirtualBox.
2. Install Kali Linux as a virtual machine.
3. Create a private NAT Network for the lab.
4. Configure network connectivity for Kali Linux VM.
5. Assign manually IP address to the Kali Linux VM.
6. Verify network connectivity and DNS resolution using ping command.
7. Take a clean VM snapshot for recovery.
8. Document the complete setup process.
9. Prepare the environment for future projects.

## 🛡️ Purpose of the Lab
The lab provides an isolated and controlled environment for learning purposes and authorized security testing.

It can be used for activities such as:

Network reconnaissance
Port scanning
Vulnerability assessment
Packet analysis
Web security testing
Exploitation practice
Security-tool experimentation

⚠️ Important: This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.

## 🏗️ Lab Architecture
<img width="2800" height="1315" alt="image" src="https://github.com/user-attachments/assets/1563d72e-9632-4ef3-bb75-b5a562e893f7" />

Additional target machines can be added to the same virtual network in future projects.

## ⚙️ Lab Configuration

| 🧩 Component | ⚙️ Configuration |
|---|---|
| 🖥️ Host OS | Windows 10 |
| 🧠 Host RAM | 16 GB |
| ⚡ Processor | Intel Core i5 |
| 🧰 Hypervisor | VirtualBox 7.2.16 r174877 |
| 🐉 Security OS | Kali Linux 2026.2 |
| 🧠 Kali RAM | 2048 MB |
| 🌐 Virtual Network | NAT Network |
| 📡 Network Address | `10.0.0.0/24` |
| 🐧 Kali IP Address | `10.0.0.4/24` |
| 🚪 Default Gateway | `10.0.0.1` |
| 🌍 DNS Server | `8.8.8.8` |
| 🔮 Future VM Range | `10.0.0.5 – 10.0.0.99` |

## 🛠️ Lab Setup Procedure

### Step 1 — Install 7-Zip

7-Zip was installed to extract and manage compressed files used during the lab setup.

### Step 2 — Install VirtualBox

Oracle VirtualBox was installed as the hypervisor for creating and managing the CyberLab virtual machines.

### Step 3 — Create the NAT Network

A dedicated NAT Network was created in VirtualBox to provide connectivity between the virtual machines while maintaining Internet access.

#### NAT Network Configuration

| 🧩 Setting | ⚙️ Configuration |
|---|---|
| 🌐 Network Name | `NatNetwork` |
| 📡 IPv4 Prefix | `10.0.0.0/24` |
| 🔄 DHCP | Enabled |
| 🌍 IPv6 | Disabled |

The `10.0.0.0/24` network was selected as the private network range for the CyberLab environment.

<img width="1515" height="826" alt="image" src="https://github.com/user-attachments/assets/b6e5a0a5-66ca-4aa2-a146-f9d19584db86" />
A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

# Step 4. Import Kali Linux
The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

Adapter 1
Attached to: NAT Network
Network:     NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop

The VM was allocated 2048 MB RAM

<img width="1545" height="1043" alt="image" src="https://github.com/user-attachments/assets/456afed4-1d87-4915-af83-9f1d43de7dcb" />

A shared folder was also configured for transferring required files between the host operating system and the Kali VM.

# Step 5. Configure the Kali Linux Network
The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

IP Address: 10.0.0.4
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 8.8.8.8

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

<img width="1546" height="1049" alt="image" src="https://github.com/user-attachments/assets/8ca93a9f-10b3-4528-85ec-71f1828020c8" />

Step 6. Create a Clean VM Snapshot
After completing the initial configuration, a VirtualBox snapshot was created.

Example snapshot name:

Kali Linux Instalation
Description: Configured IP Addresses and Internet is working properly.

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

## 🔎 Lab Verification

| Status | Test | Command | Expected Result |
|---|---|---|---|
| ✅ | Check IP Address | `ip addr` | Correct Kali IP address is displayed |
| ✅ | Test Gateway | `ping -c 4 10.0.0.1` | Successful replies |
| ✅ | Test Internet Connectivity | `ping -c 4 8.8.8.8` | Successful replies |
| ✅ | Test DNS Resolution | `nslookup networkwalks.com` | Domain resolves successfully |
| ✅ | Verify Nmap | `nmap --version` | Nmap version is displayed |
| ✅ | Verify Snapshot | Restore snapshot and run baseline tests | Baseline configuration is restored |

## 🐞 Problems Encountered & Solutions

No major problems were encountered during this lab.

However, a Kali NetworkManager IPv4 timeout issue may be resolved with:

bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0

## 💡 Lesson Learned
The most important concepts I learned include:

# 1. NAT vs NAT Network
A standard NAT configuration and a NAT Network serve different purposes.
A NAT a VM can only access the Internet, but Kali normally cannot directly ping Windows, because each VM is behind its own isolated NAT.
A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine cybersecurity laboratory.

# 2. Virtual Machine Networking
I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

# 3. Static IP Configuration
I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

# 4. VM Snapshots
I learned that a clean snapshot should be created before performing any risky or experimental activities.

This provides a known-good recovery point for future cybersecurity exercises.

# 5. Documentation
I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

## 🔐 Security & Ethical Use
This laboratory is intended strictly for education purposes only.

## 🔗 Tools & Resources
7-Zip: https://7-zip.org/download.html
VirtualBox: https://virtualbox.org/wiki/Downloads
Kali Linux: https://kali.org/get-kali

## 👤 Author

This CyberLab was created and documented by **Adelino Sulude**
for hands-on cybersecurity practice.

**LinkedIn:** [Adelino Sulude](https://www.linkedin.com/in/adelino-sulude/)

## 🙏 Credits

The training and lab concepts were learned from:

- **Waqas Karim** — Cybersecurity Professional, CCIE
  - Instructor of the cybersecurity training used as a learning reference.
  - **LinkedIn:** [Waqas Karim](https://www.linkedin.com/in/waqaskarim/)

All lab configurations, testing, documentation, and practical experimentation
were performed by me in my own virtual lab environment.

## 📌 Project Information
Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub
