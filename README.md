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
    ├── baseline.md
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

### Day 4

Completed:

- Installed Windows 11 on `LAB-WIN11-01`.
- Configured the endpoint hostname and timezone.
- Created a separate standard scenario user, `labuser`.
- Verified that `labuser` does not have local administrator privileges.
- Installed VMware Tools and standard Windows updates.
- Avoided connecting personal cloud, Microsoft, school, work, or browser-sync accounts.
- Documented the known pre-scenario endpoint state.
- Created the powered-off snapshot `BASELINE-CLEAN-2026-09-04`.

No controlled suspicious-user activity has yet been generated or analysed.

### Day 5

Completed:

- Began controlled user activity on `LAB-WIN11-01`.
- Generated browser activity using the standard `labuser` account.
- Created and modified synthetic project documents.
- Documented unexpected file-location and filename-extension corrections as part of the real scenario history.
- Maintained a private timestamped ground-truth execution record.
- Published a SHA-256 commitment for the completed Day 05 record.

Forensic evidence has not yet been acquired or analysed.

### Day 6

Completed:

- Generated controlled PowerShell activity under `labuser`.
- Created a synthetic data-staging directory.
- Copied selected project files into the staging area.
- Created a ZIP archive from the staged files.
- Verified the archive contents.
- Maintained a private timestamped execution record.
- Published a SHA-256 commitment for the completed Day 06 record.

Forensic evidence has not yet been acquired or analysed.


### Day 7

Completed:

- Added controlled removable-media activity using a dedicated USB device.
- Copied `project_archive.zip` to the removable media and verified the copied archive using SHA-256.
- Deleted `meeting_notes.txt` through the normal Windows deletion workflow and left it in the Recycle Bin.
- Permanently removed the original `quarterly_summary.txt` from `ProjectAtlas`.
- Preserved surviving copies of `quarterly_summary.txt` in `Staging` and inside `project_archive.zip`.
- Maintained a private timestamped ground-truth execution record.
- Published a SHA-256 commitment for the completed Day 07 record.
- Preserved the final endpoint state without restoring or clearing scenario artefacts.

No forensic acquisition or forensic analysis had yet been performed at the end of Day 7.

### Day 8

Completed:

- Began the forensic acquisition phase.
- Designated the Day 07 removable USB as Evidence Item `E001`.
- Acquired a complete physical RAW/DD image of the removable media.
- Verified the image using FTK Imager.
- Independently calculated a SHA-256 hash.
- Added E001 to the evidence manifest.
- Created acquisition and chain-of-custody documentation.
- Documented acquisition limitations.

No forensic analysis has yet been performed on E001.

### Day 9

Completed:

- Prepared the volatile-memory acquisition workflow.
- Defined the planned memory image as Evidence Item `E002`.
- Documented expected storage requirements and acquisition order.
- Documented the intrusive nature and limitations of live-memory acquisition.
- Kept the evidence endpoint powered off until the acquisition workflow is ready.

No additional evidence was acquired or analysed on Day 9.

### Day 10

Completed:

- Prepared dedicated storage for Evidence Item `E002`.
- Selected and staged the volatile-memory acquisition utility.
- Calculated a SHA-256 hash of the acquisition executable.
- Updated the memory-acquisition plan.
- Kept the evidence endpoint powered off.

E002 has not yet been acquired.

### Day 11

Completed:

- Took an intentional rest day after ten consecutive days of project work.
- Kept LAB-WIN11-01 untouched.
- Performed no evidence acquisition or forensic analysis.
- Preserved the current case state for the next acquisition step.
- Prioritised recovery so the volatile-memory acquisition could be completed with proper attention.

No new evidence was acquired or analysed on Day 11.

### Day 12

Completed:

- Acquired Evidence Item `E002`, a live post-reboot memory image of LAB-WIN11-01.
- Used the previously staged and SHA-256-verified WinPmem acquisition utility.
- Preserved a 5,368,709,120-byte memory image outside the public repository.
- Calculated SHA-256 before and after transfer to the forensic host.
- Confirmed that both integrity values matched.
- Documented acquisition-induced activity and transfer-handling deviations.
- Documented that E002 does not preserve the volatile state from the earlier scenario because the endpoint had previously been shut down.
- Shut down the evidence endpoint after preservation was confirmed.

No forensic analysis of E002 has yet been performed.


### Day 13

Completed:

- Created a formal case-status checkpoint.
- Reviewed the current state of E001, E002, and planned E003.
- Confirmed that two evidence items have been acquired and hash-verified.
- Confirmed that forensic analysis has not yet begun.
- Defined endpoint-disk acquisition as the next major step.

No new evidence was acquired or analysed on Day 13.

### Day 14

Completed:

- Performed the E003 endpoint-disk acquisition preflight.
- Identified the VMware base disk and snapshot/delta disk.
- Confirmed that the current VM state depends on an existing snapshot chain.
- Confirmed that the clean baseline snapshot remains intact.
- Reviewed current evidence-storage requirements.
- Determined that additional storage planning is required before disk acquisition.

No new evidence was acquired or analysed on Day 14.

### Day 15

Completed:

- Kept LAB-WIN11-01 powered off following the E003 acquisition preflight.
- Performed no evidence acquisition or forensic analysis.
- Preserved the existing VMware snapshot chain without modification.
- Intentionally paused technical lab work for the day before continuing with E003 preparation.

No new evidence was acquired or analysed on Day 15.


### Day 16

Completed:

- Confirmed that LAB-WIN11-01 was not running.
- Reviewed host storage before E003 preservation.
- Confirmed that current host free space is insufficient for a comfortable full preservation workflow.
- Inspected the existing VMware lock directory and confirmed no active `vmware-vmx` process was running.
- Deferred E003 preservation until separate SSD storage is available.

No evidence was acquired or analysed on Day 16.


### Day 17

Completed:

- Preserved Evidence Item E003 to dedicated external SSD storage.
- Copied the complete powered-off VMware source set, including the base disk and active snapshot/delta disk.
- Preserved 20 files totalling 44,436,161,087 bytes.
- Generated independent source and destination SHA-256 manifests.
- Verified every preserved file using relative path, exact byte length, and SHA-256.
- Confirmed zero verification differences.
- Preserved the original VMware source and E003 copy without beginning forensic analysis.

E003 is documented as a verified VMware preservation set, not as a sector-by-sector disk image.

### Day 18

Completed:

- Began forensic analysis of E001.
- Created and SHA-256-verified a working copy of the USB image.
- Opened E001 in FTK Imager.
- Identified the FAT16 filesystem and `DFIR_CASE_001` directory.
- Identified and inspected `project_archive.zip`.
- Confirmed that the archive contained three project-related files.
- Observed a possible deleted archive entry for later validation.

This was the first day of evidence analysis rather than evidence generation or acquisition.


### Day 20

Completed:

- Created and verified an E003 analysis working copy.
- Confirmed all 20 working-copy files matched preserved E003 using SHA-256.
- Created an Autopsy 4.20.0 analysis case.
- Attempted direct ingestion of the active VMware snapshot VMDK.
- Documented the resulting filesystem-detection failure.
- Created a consolidated derived VMDK from the verified working snapshot chain.
- Calculated and recorded the derived disk SHA-256.
- Successfully added the derived endpoint disk to Autopsy for analysis.

The preserved E003 evidence set remained unchanged.

No endpoint finding was concluded on Day 20.

### Day 21

Completed:

- Began filesystem analysis of E003 in Autopsy.
- Identified the primary Windows partition.
- Confirmed that the Windows volume is protected by BitLocker.
- Verified that the volume remained 100% encrypted while appearing unlocked in the running endpoint.
- Confirmed that no BitLocker key protectors were present.
- Documented the post-acquisition endpoint check separately from preserved E003.
- Defined a decrypted analysis-clone workflow as the next step.

No user-file findings were concluded because the encrypted filesystem was not yet accessible in the analysis environment.

### Day 22

Completed:

- Completed BitLocker decryption for E003 analysis preparation.
- Documented a workflow deviation in which the original VM was inadvertently decrypted after E003 had already been preserved.
- Confirmed that preserved E003 remained unchanged.
- Created a consolidated post-acquisition decrypted analysis VMDK.
- Recorded the derived disk SHA-256.
- Successfully loaded the decrypted derived disk into Autopsy.
- Confirmed that the Windows filesystem, including `Users`, `Windows`, `Program Files`, and `$Recycle.Bin`, is now accessible for analysis.

No scenario-related finding was concluded on Day 22.