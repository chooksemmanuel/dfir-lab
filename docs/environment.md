# Lab Environment

## Host System

**Operating System:** Windows 11 Pro, 64-bit

**Processor:** Intel Core i7-8650U @ 1.90 GHz

**CPU Resources:** 4 physical cores / 8 logical processors

**RAM:** 15.9 GB

**Host Storage Capacity:** Approximately 476 GB

**Free Storage at Initial Assessment:** Approximately 18 GB

## Virtualisation

The host currently has the following virtualisation platforms installed:

- VMware Workstation 17.6.3
- Oracle VirtualBox 7.1.10

Windows reports that a hypervisor is present.

The initial WMI processor check reported firmware virtualisation as disabled. This requires additional verification before the evidence VM is provisioned.

## Lab Architecture Decision

The initial lab will use a single Windows evidence VM rather than multiple concurrent virtual machines.

Forensic analysis will primarily be performed from the Windows host after evidence acquisition.

### Planned Evidence VM

**Hypervisor:** VMware Workstation

**Guest Operating System:** Windows 11

**Virtual CPUs:** 2

**RAM:** 4 GB initially

**Virtual Disk:** 64 GB, dynamically allocated

**Status:** Not yet created.

## Storage Constraint

The host had approximately 18 GB of free storage during the initial Day 1 assessment.

This is insufficient for safe creation of the evidence VM, forensic disk images, memory captures, working copies, snapshots, and forensic-tool output.

VM provisioning and evidence acquisition will not begin until additional storage capacity is available.

**Target available storage before VM provisioning:** At least 100-120 GB, with 150 GB or more preferred.

## Design Rationale

The host has sufficient CPU and memory resources for a modest single-VM laboratory.

A single evidence VM reduces unnecessary resource contention and keeps the first investigation focused.

The project will remain investigation-led rather than attempting to maximise the number of virtual machines or forensic tools used.

## Status

Host environment assessed.

Lab architecture selected provisionally.

Storage remediation and virtualisation verification are required before VM provisioning.