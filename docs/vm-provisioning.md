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

Windows 11 installation completed.

The endpoint hostname is `LAB-WIN11-01`.

VMware Tools and standard Windows updates have been installed.

A dedicated standard scenario account, `labuser`, has been created.

The `labuser` account is not a member of the local Administrators group.

The Windows installation media has been disconnected from automatic startup.

A clean powered-off baseline snapshot has been created:

`BASELINE-CLEAN-2026-09-04`

Controlled scenario activity has not yet begun.