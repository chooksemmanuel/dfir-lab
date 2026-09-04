## Virtual Machine Configuration

**Hypervisor:** VMware Workstation

**Virtual CPUs:** 2

**RAM:** 4 GB

**Virtual Disk:** 64 GB

**Network:** NAT

**Firmware:** UEFI

**Secure Boot:** Enabled

**Virtual TPM:** Present

**Shared Folders:** Disabled

**Host/Guest Clipboard and Drag-and-Drop:** Disabled

## Accounts

A dedicated local administrative account is used for lab configuration.

The controlled investigation user is:

**labuser**

The `labuser` account is a standard local user and is not a member of the local Administrators group.

No personal Microsoft, school, work, browser-sync, or OneDrive account is connected to the endpoint.

## Time Configuration

**Timezone:** Eastern Standard Time

## Baseline Software

At the time of baseline creation, the endpoint contains:

- Windows 11
- VMware Tools
- Default Windows applications and components
- Standard Windows updates

No forensic investigation tools are installed inside the evidence endpoint.

## Scenario Activity

No controlled suspicious-user scenario activity has been intentionally generated.

The detailed Case 01 ground-truth scenario remains private.

## Baseline Purpose

This state represents the known pre-scenario condition of the evidence endpoint.

A VMware snapshot was created from the powered-off VM so the environment can be returned to this state if the scenario must be repeated.

## Snapshot

**Snapshot Name:** `BASELINE-CLEAN-2026-09-04`

**VM State:** Powered off

## Host Storage After Baseline Creation

Approximately **103.3 GB** of free space remained on the host system after Windows installation, updates, VM configuration, and baseline snapshot creation.

Storage usage will continue to be monitored before forensic acquisition.

## Status

Clean baseline established.

Scenario execution has not begun.