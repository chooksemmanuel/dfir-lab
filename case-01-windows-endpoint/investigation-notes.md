# Investigation Notes

## Case

Case 01 - Windows Endpoint Forensics

---

## Investigation Log

### Day 1 - Project Definition

#### Actions Completed

- Created the DFIR lab repository.
- Created the initial project structure.
- Defined Case 01.
- Defined the primary investigation question.
- Defined investigation sub-questions.
- Established lab safety boundaries.
- Established initial evidence-handling principles.
- Created the documentation structure.
- Profiled the host operating system, CPU, memory, storage, and available virtualisation platforms.
- Selected a single-evidence-VM architecture based on available host resources.
- Selected VMware Workstation as the planned hypervisor.
- Identified insufficient available storage as a blocker to VM provisioning.
- Deferred VM creation until sufficient storage capacity is available.
- Verified hardware virtualisation as enabled through Windows Task Manager.
- Confirmed that Windows detects an active hypervisor.

#### Evidence Examined

None.

#### Findings

None.

#### Interpretation

No forensic conclusions can currently be made because forensic evidence has not yet been generated or acquired.

#### Next Step

Resolve the available-storage constraint before provisioning the Windows evidence VM.

After sufficient storage is available, verify VMware guest startup and design the controlled investigation scenario before evidence generation begins.


---

### Day 2 - Scenario Design and Ground-Truth Separation

#### Actions Completed

- Confirmed that approximately 140 GB of host storage is now available.
- Updated the lab environment documentation.
- Designed the controlled Case 01 user-activity scenario.
- Created a private ground-truth scenario plan.
- Added the private ground-truth directory to `.gitignore`.
- Created a public scenario overview that excludes the answer to the investigation.
- Created an evidence-expectation matrix linking planned activity to potential forensic artefacts.
- Calculated a SHA-256 hash of the private scenario plan.
- Published the hash as a ground-truth integrity commitment.

#### Evidence Examined

None.

#### Findings

None.

#### Interpretation

The scenario has been designed, but no forensic evidence has yet been generated or analysed.

Expected artefacts documented during this phase are hypotheses only and must not be treated as findings.

#### Next Step

Provision the controlled Windows evidence VM and establish a clean baseline before scenario activity begins.

---

### Day 3 - Evidence VM Provisioning

#### Actions Completed

- Created a dedicated local storage structure for VM files, ISO files, evidence, and working copies.
- Downloaded Windows 11 installation media from Microsoft.
- Calculated and recorded the SHA-256 hash of the installation ISO.
- Created the LAB-WIN11-01 virtual machine in VMware Workstation.
- Allocated 2 virtual CPU cores and 4 GB of memory.
- Configured a 64 GB dynamically allocated virtual disk.
- Configured NAT networking.
- Configured UEFI, Secure Boot, and a virtual TPM.
- Disabled shared folders.
- Attached the Windows 11 installation ISO.

#### Evidence Examined

None.

#### Findings

None.

#### Interpretation

The evidence endpoint infrastructure has been provisioned, but no operating system or scenario activity has yet been created.

#### Next Step

Install Windows 11, configure the controlled lab account, perform basic updates, and establish a clean baseline before generating scenario activity.

---

### Day 4 - Windows Installation and Clean Baseline

#### Actions Completed

- Installed Windows 11 on `LAB-WIN11-01`.
- Configured the endpoint hostname.
- Verified the Eastern Time timezone configuration.
- Maintained a separate local administrative setup account, `labadmin`.
- Created the standard local scenario account, `labuser`.
- Verified that `labuser` is a member of the Users group and is not a member of the Administrators group.
- Installed VMware Tools.
- Installed standard Windows updates.
- Avoided connecting personal Microsoft, school, work, browser-sync, or cloud-storage accounts.
- Verified the `labuser` profile.
- Disconnected the Windows installation media from automatic startup.
- Created the clean endpoint baseline document.
- Created the powered-off VMware snapshot `BASELINE-CLEAN-2026-09-04`.
- Verified approximately 103.3 GB of host storage remained after baseline creation.

#### Evidence Examined

None.

#### Findings

None.

#### Interpretation

The Windows evidence endpoint now has a documented pre-scenario baseline.

No controlled suspicious-user scenario activity has been intentionally generated.

The powered-off baseline snapshot provides a known state to which the environment can be restored if the scenario needs to be repeated.

#### Next Step

Prepare the controlled endpoint for scenario execution.

Scenario activity will be generated using the `labuser` account while actual ground-truth timestamps and actions are recorded separately from the forensic investigation documentation.


---

### Day 5 - Controlled Scenario Execution Begins

#### Actions Completed

- Logged into `LAB-WIN11-01` using the standard `labuser` account.
- Generated controlled browser activity.
- Created four synthetic project documents.
- Modified `project_notes.txt` after its initial creation.
- Identified and documented an unintended file-location discrepancy.
- Moved the synthetic files into the intended `ProjectAtlas` directory.
- Identified and corrected unintended duplicate file extensions.
- Maintained a separate private ground-truth execution record.
- Calculated a SHA-256 hash of the completed Day 05 ground-truth record.
- Published only the integrity commitment hash.

#### Evidence Examined

None.

#### Findings

None.

#### Interpretation

Controlled scenario activity has begun and the endpoint now contains intentionally generated user artefacts.

The unexpected file-movement and renaming actions are retained as part of the scenario history.

No forensic acquisition or analysis has yet been performed.

#### Next Step

Continue the controlled scenario with command-line activity, file staging, and archive creation while maintaining separate ground-truth documentation.

---

### Day 6 - Command-Line Activity, File Staging, and Archive Creation

#### Actions Completed

- Continued controlled scenario execution using the standard `labuser` account.
- Generated normal PowerShell command-line activity.
- Created a `Staging` directory.
- Copied three synthetic documents from `ProjectAtlas` into the staging directory.
- Intentionally excluded `meeting_notes.txt` from the staged collection.
- Created `project_archive.zip` from the staged files.
- Verified the contents of the archive without extracting it.
- Recorded execution deviations encountered during archive verification.
- Maintained a private timestamped ground-truth execution record.
- Calculated a SHA-256 hash of the completed Day 06 ground-truth record.
- Published only the integrity commitment hash.

#### Evidence Examined

None.

#### Findings

None.

#### Interpretation

The endpoint now contains intentionally generated command-line, file-copying, staging, and archive-creation artefacts.

These actions have not yet been examined through forensic acquisition or analysis.

#### Next Step

Continue the controlled scenario with removable-media activity and file deletion while preserving separate ground-truth documentation.


---

### Day 8 - First Forensic Acquisition

#### Actions Completed

- Transitioned from controlled scenario generation into evidence acquisition.
- Designated the Day 07 removable USB as Evidence Item `E001`.
- Created dedicated forensic evidence storage outside the public Git repository.
- Identified the physical USB as a 250 MB USB device.
- Acquired the complete physical device using Exterro FTK Imager 8.3.0.27.
- Created a RAW/DD image named `E001_USB.001`.
- Verified the image using FTK Imager.
- Confirmed matching MD5 and SHA-1 verification values.
- Confirmed that FTK Imager reported no bad blocks.
- Calculated an independent SHA-256 hash using PowerShell.
- Updated the evidence manifest.
- Created an acquisition log and chain-of-custody record.
- Documented the lack of a hardware write blocker as an acquisition limitation.
- Removed the source USB from further scenario use.

#### Evidence Analysis

None.

#### Findings

None.

#### Interpretation

Evidence acquisition has begun, but no forensic findings have yet been made.

E001 is now preserved as a forensic image and will be examined from a working copy rather than through continued interaction with the source removable media.

#### Next Step

Prepare for volatile-memory acquisition from `LAB-WIN11-01` before acquiring the endpoint disk.


---

### Day 9 - Volatile Memory Acquisition Preparation

#### Actions Completed

- Kept LAB-WIN11-01 powered off.
- Reviewed the planned transition from removable-media acquisition to volatile-memory acquisition.
- Created a dedicated volatile-memory acquisition plan.
- Defined E002 as the planned memory evidence item.
- Documented the expected storage requirement.
- Documented the intrusive nature of live-memory acquisition.
- Defined the acquisition order before final endpoint disk imaging.

#### Evidence Acquisition

No new evidence was acquired.

#### Evidence Analysis

None.

#### Findings

None.

#### Interpretation

Volatile-memory acquisition requires deliberate preparation because the acquisition process itself changes the running system.

The endpoint was left untouched rather than beginning the acquisition without completing the necessary preparation.

#### Next Step

Prepare dedicated storage and the selected acquisition utility, then acquire E002 from the live Windows endpoint.

---

### Day 10 - E002 Acquisition Kit Preparation

#### Actions Completed

- Prepared dedicated evidence storage for E002.
- Selected WinPmem as the planned volatile-memory acquisition utility.
- Stored the acquisition utility outside the public Git repository.
- Calculated and recorded a SHA-256 hash of the acquisition executable.
- Updated the volatile-memory acquisition plan.
- Kept LAB-WIN11-01 powered off.

#### Evidence Acquisition

No new evidence was acquired.

#### Evidence Analysis

None.

#### Next Step

Introduce the documented acquisition utility to the live endpoint and acquire E002.

---

### Day 12 - E002 Volatile Memory Acquisition

#### Actions Completed

- Powered on LAB-WIN11-01 from its current post-scenario state.
- Used the administrative lab account for acquisition activity.
- Introduced the previously staged and hashed WinPmem acquisition utility.
- Verified the acquisition utility against its known SHA-256.
- Acquired a live memory image from the endpoint.
- Preserved the resulting memory image as Evidence Item `E002`.
- Calculated SHA-256 inside the evidence VM before transfer.
- Transferred the acquired image to dedicated evidence storage on the forensic host.
- Calculated SHA-256 again against the preserved host copy.
- Confirmed that the guest and host SHA-256 values matched.
- Preserved WinPmem and the guest-side acquisition image on the endpoint for later disk acquisition.
- Shut down the endpoint after memory preservation was confirmed.
- Documented transfer-handling deviations and the post-reboot volatile-state limitation.

#### Evidence Acquired

**E002 - Post-reboot volatile memory image**

**Size:** 5,368,709,120 bytes

**SHA-256:** `E4E36E18891706E3C933F8290155716914025DFA38EE5B738B4956E77C4B8C44`

#### Evidence Analysis

None.

#### Findings

None.

#### Interpretation

E002 successfully preserves the live volatile-memory state that existed at the time of acquisition.

It does not preserve the earlier volatile state from the original Day 05-Day 07 scenario because the endpoint had previously been shut down.

No forensic conclusions have yet been drawn from the memory image.

#### Next Step

Prepare for final forensic acquisition of the LAB-WIN11-01 virtual disk before beginning evidence analysis.


---

### Day 13 - Case Status Checkpoint

#### Actions Completed

- Reviewed the current position of DFIR-CASE-001.
- Confirmed that E001 has been acquired and hash-verified.
- Confirmed that E002 has been acquired and hash-verified.
- Confirmed that E003 remains pending.
- Confirmed that forensic analysis has not yet begun.
- Created a dedicated case-status document summarising the evidence and current investigation phase.
- Defined endpoint-disk acquisition as the next major technical step.

#### Evidence Acquisition

No new evidence was acquired.

#### Evidence Analysis

None.

#### Findings

None.

#### Next Step

Perform an E003 acquisition preflight before acquiring the LAB-WIN11-01 endpoint disk.

---

### Day 14 - E003 Disk Acquisition Preflight

#### Actions Completed

- Confirmed the LAB-WIN11-01 VM remained powered off.
- Identified the VM configuration file.
- Identified the base VMDK and current snapshot/delta VMDK.
- Confirmed that one snapshot exists: `BASELINE-CLEAN-2026-09-04`.
- Confirmed that the current VM configuration references `LAB-WIN11-01-000001.vmdk`.
- Confirmed that the current endpoint state depends on the VMware snapshot chain.
- Measured the VM folder at approximately 41.38 GB.
- Measured approximately 65.0 GB of free host storage.
- Determined that additional storage planning is required before E003 acquisition.

#### Evidence Acquisition

None.

#### Evidence Analysis

None.

#### Next Step

Confirm sufficient evidence-storage capacity and select the E003 disk-acquisition method.

---

### Day 15 - Planned Case Hold

#### Actions Completed

- Maintained the current evidence-preservation state.
- Kept LAB-WIN11-01 powered off.
- Made no changes to the VMware snapshot chain.
- Performed no evidence acquisition or analysis.

#### Evidence Acquisition

None.

#### Evidence Analysis

None.

#### Findings

None.

#### Next Step

Resume E003 endpoint-disk acquisition preparation.

---

### Day 16 - E003 Storage and Lock-State Check

#### Actions Completed

- Confirmed zero running VMware virtual machines.
- Confirmed no active `vmware-vmx` process.
- Reviewed approximately 64.5 GB of free host storage.
- Reconfirmed that the VMware source set requires approximately 41 GB of storage.
- Inspected `LAB-WIN11-01.vmx.lck`.
- Observed that the lock directory had not been modified since 2026-09-08.
- Deferred E003 preservation until separate SSD storage is available.

#### Evidence Acquisition

None.

#### Evidence Analysis

None.

#### Next Step

Connect separate SSD storage and prepare E003 preservation.

---

### Day 17 - E003 VMware Endpoint Preservation

#### Actions Completed

- Connected dedicated external evidence storage.
- Confirmed LAB-WIN11-01 remained powered off.
- Confirmed no active `vmware-vmx` process.
- Preserved the complete VMware source set to separate external storage.
- Preserved the existing base disk and active snapshot/delta disk together.
- Preserved the previously observed VMware lock directory rather than deleting it.
- Generated SHA-256 manifests independently for the source and preserved copy.
- Compared all files using relative path, exact byte length, and SHA-256.
- Confirmed all 20 source files matched the preserved copies.
- Confirmed source and destination sizes were both 44,436,161,087 bytes.

#### Evidence Acquired

**E003 - Powered-off VMware endpoint preservation set**

**Files:** 20

**Total Size:** 44,436,161,087 bytes

**Integrity Verification:** Passed

#### Evidence Analysis

None.

#### Findings

None.

#### Interpretation

E003 preserves the complete VMware file set representing the current powered-off state of LAB-WIN11-01.

E003 is a verified file-level preservation set and is not being represented as a sector-by-sector forensic image of the host filesystem.

#### Next Step

Prepare a verified working copy and analysis environment while keeping the preserved E003 set untouched.

---

### Day 18 - Initial Analysis of E001 USB Evidence

#### Actions Completed

- Created a working copy of E001 for analysis.
- Verified that the original E001 image and working copy had identical SHA-256 values.
- Opened the working copy in Exterro FTK Imager 8.3.0.27.
- Identified the FAT16 filesystem.
- Located the `DFIR_CASE_001` directory.
- Identified a live `project_archive.zip` file.
- Inspected the contents of the ZIP archive.
- Observed a possible deleted directory entry associated with `project_archive.zip`.

#### Integrity Verification

**Original E001 SHA-256:**

`B966EEFB6AE74A2280F82688F95A797B7036872A2967326A7657B23E3CD9C7F3`

**Working Copy SHA-256:**

`B966EEFB6AE74A2280F82688F95A797B7036872A2967326A7657B23E3CD9C7F3`

**Result:** MATCH

#### Observed Evidence

The directory `DFIR_CASE_001` was present on the FAT16 volume.

A live archive named `project_archive.zip` was present with a size of 810 bytes.

FTK Imager parsed the archive and displayed the following files:

- `client_contacts.csv` - 199 bytes
- `project_notes.txt` - 250 bytes
- `quarterly_summary.txt` - 164 bytes

A second `project_archive.zip` entry with a deleted-file indicator was also visible.

The deletion status and significance of that entry have not yet been independently validated through filesystem metadata.

#### Findings

E001 supports the presence of a ZIP archive containing three project-related files.

At this stage, the evidence supports the existence and contents of the archive, but no conclusion is being made yet about intent or broader user activity.

#### Next Step

Continue analysis using additional evidence sources and later correlate E001 findings with endpoint artefacts from E003.

---

### Day 19 - Initial E002 Memory Analysis

#### Actions Completed

- Created a verified working copy of E002 for analysis.
- Analysed the working copy using Volatility 3.
- Successfully ran `windows.info`, `windows.pslist`, `windows.pstree`, and `windows.cmdline`.
- Reviewed the live system and process state captured in the post-reboot memory image.
- Performed a targeted search for acquisition-related and interactive processes.

#### Analysis Tool

**Tool:** Volatility 3

**Observed Framework Version:** 2.28.2

#### System Information

Volatility identified the memory image as a 64-bit Windows system.

Observed information included:

- Windows kernel family: Windows 10
- 64-bit architecture
- 2 processors
- System time: `2026-09-12 14:45:01 UTC`

#### Process Observations

The memory image contained an active interactive Windows session.

Observed process activity included:

- `explorer.exe`
- `WindowsTerminal.exe`
- `OpenConsole.exe`
- `powershell.exe`
- VMware Tools processes including `vmtoolsd.exe`
- standard Windows services and security processes

The process tree showed:

`explorer.exe -> WindowsTerminal.exe -> powershell.exe`

`powershell.exe` was observed with a creation time of:

`2026-09-12 14:11:05 UTC`

The command-line plugin identified the PowerShell executable path but did not expose the individual commands entered inside the shell.

#### Acquisition-Related Search

A targeted search was performed for:

- `winpmem`
- `powershell`
- `explorer`
- `vmtoolsd`
- `labadmin`
- `C:\Forensics`

The generated `pslist`, `pstree`, and `cmdline` outputs contained matches for PowerShell, Explorer, VMware Tools, and paths associated with the `labadmin` profile.

No `winpmem` or `C:\Forensics` match was observed in these selected plugin outputs.

This absence is not interpreted as proof that WinPmem-related data does not exist elsewhere in the memory image.

#### Findings

E002 independently establishes that an interactive administrative Windows session was active at the time represented by the post-reboot memory acquisition.

Windows Terminal and PowerShell were active during the captured state.

The memory image also supports that the endpoint was running inside VMware through the presence of VMware Tools processes.

#### Limitation

E002 represents the post-reboot state of LAB-WIN11-01 and does not preserve the volatile state from the original Day 05-Day 07 scenario.

Therefore, these memory findings will not be used as proof that the same processes existed during the earlier controlled scenario.

#### Next Step

Begin filesystem and user-activity analysis of E003 and later correlate persistent endpoint artefacts with findings from E001 and E002.