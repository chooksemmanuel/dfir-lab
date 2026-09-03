# DFIR Lab

A controlled digital-forensics laboratory built to practise evidence acquisition, forensic analysis, timeline reconstruction, investigative reasoning, and forensic reporting.

## Current Investigation

### Case 01: Windows Endpoint Forensics

**Investigation:** Suspicious User Activity on a Windows Endpoint

The case will use a controlled Windows environment containing synthetic user activity.

The system will eventually be examined using disk, memory, operating-system, and potentially network evidence.

## Primary Investigation Question

> What occurred on the Windows endpoint, when did it occur, and what forensic evidence supports the reconstruction?

## Planned Areas of Analysis

- Disk forensics
- Memory forensics
- Windows artefacts
- Browser activity
- File activity
- Removable-storage activity
- Process activity
- Command-line activity
- Timeline reconstruction
- Network evidence where appropriate

## Potential Tools

- Autopsy
- FTK Imager
- Volatility 3
- Wireshark

The project is **investigation-led rather than tool-led**. Tools will be used where they contribute to answering a forensic question.

## Initial Lab Architecture

The first version of the lab will use:

- Windows 11 host
- VMware Workstation
- One controlled Windows evidence VM
- Host-based forensic analysis

A second forensic-analysis VM is deliberately excluded from the initial design to keep the environment small and focused.

## Current Status

### Day 1

Completed:

- Created the repository.
- Defined Case 01.
- Defined the primary investigation question and supporting questions.
- Established safety boundaries.
- Established initial evidence-handling principles.
- Created investigation documentation and timeline structures.
- Assessed the host environment.
- Selected the initial lab architecture.
- Identified available storage as a prerequisite that must be resolved before VM provisioning.

No forensic evidence has yet been generated, acquired, or analysed.

## Repository Structure

```text
dfir-lab/
│
├── README.md
├── docs/
│   ├── environment.md
│   └── lab-scope.md
│
├── templates/
│   └── chain-of-custody.md
│
└── case-01-windows-endpoint/
    ├── case-brief.md
    ├── scenario-overview.md
    ├── evidence-expectations.md
    ├── ground-truth-commitment.md
    ├── evidence-manifest.md
    ├── investigation-notes.md
    ├── timeline.csv
    ├── report/
    └── screenshots/

### Day 2

Completed:

- Resolved the initial storage constraint sufficiently for lab provisioning.
- Designed the controlled Case 01 scenario.
- Separated public investigation information from private ground truth.
- Created an evidence-expectation matrix.
- Created a SHA-256 integrity commitment for the private scenario plan.

No forensic evidence has yet been generated or analysed.

### Day 3

Completed:

- Created the local heavy-asset storage structure.
- Recorded and hashed the Windows installation media.
- Provisioned LAB-WIN11-01 in VMware Workstation.
- Configured 2 vCPU, 4 GB RAM, a 64 GB virtual disk, NAT networking, UEFI/Secure Boot, and vTPM.
- Attached the Windows installation media.
- Kept the VM powered off pending clean operating-system installation.

No forensic evidence has yet been generated or analysed.