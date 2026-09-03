# Evidence VM Provisioning

## Virtual Machine

**VM Name:** LAB-WIN11-01

**Purpose:** Controlled Windows evidence endpoint for DFIR-CASE-001

**Hypervisor:** VMware Workstation 17.6.3

**Guest OS:** Windows 11 x64

## Planned Hardware

| Component | Configuration |
|---|---|
| Virtual CPUs | 2 |
| Memory | 4 GB |
| Virtual Disk | 64 GB dynamically allocated |
| Networking | NAT |
| Firmware | UEFI |
| Secure Boot | Enabled |
| Virtual TPM | Enabled |
| Shared Folders | Disabled |

## Installation Media

**Source:** Official Microsoft Windows 11 download

**ISO Filename:** Win11_25H2_English_x64_v2

**SHA-256:** 768984706B909479417B2368438909440F2967FF05C6A9195ED2667254E465E3 

## Storage

VM files are stored outside the public Git repository.

Local VM location:

`Documents/DFIR-Lab-Assets/VMs/LAB-WIN11-01`

Raw VM files, ISO files, forensic evidence and working copies are not committed to GitHub.

## Current Status

Initial VM hardware provisioning completed.

Windows 11 installation media is attached.

The VM remains powered off.

Operating system installation has not yet begun.