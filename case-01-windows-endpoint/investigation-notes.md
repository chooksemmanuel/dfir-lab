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

---

### Day 20 - E003 Analysis Environment Preparation

#### Actions Completed

- Created a complete working copy of the preserved E003 VMware evidence set.
- Generated SHA-256 values for the working copy.
- Compared the working copy against the preserved E003 manifest.
- Confirmed all 20 files matched by relative path, exact byte length, and SHA-256.
- Created an Autopsy analysis case for E003.
- Initially attempted to ingest the active VMware snapshot/delta VMDK directly.
- Autopsy returned an error indicating that it could not determine the filesystem type.
- Did not modify the preserved E003 evidence or VMware snapshot chain.
- Generated a consolidated derived analysis VMDK from the verified E003 working copy using VMware Virtual Disk Manager.
- Calculated a SHA-256 hash for the derived VMDK.
- Created a clean Autopsy case and successfully added the derived VMDK as the analysis data source.

#### Analysis Tool

**Autopsy Version:** 4.20.0

**Analysis Case:** `DFIR-CASE-001-E003-Analysis`

**Case Number:** `DFIR-CASE-001`

#### Working Copy Verification

**Preserved File Count:** 20

**Working File Count:** 20

**Verification Result:** PASSED

No differences were identified between the preserved E003 set and its working copy using relative path, byte length, and SHA-256.

#### Direct Snapshot Ingest Attempt

The active VMware snapshot/delta disk:

`LAB-WIN11-01-000001.vmdk`

was initially supplied to Autopsy from the verified working copy.

Autopsy reported:

`Cannot determine file system type`

The direct snapshot ingest was therefore discontinued.

The base or snapshot evidence files were not modified in response to this error.

#### Derived Analysis Disk

A consolidated VMDK was generated from the verified working VMware snapshot chain using VMware Virtual Disk Manager.

**Derived Filename:**

`LAB-WIN11-01-FLATTENED.vmdk`

**Size:**

36,425,564,160 bytes

**SHA-256:**

`F7421DD1F2FDB75D2DE69B333ED4096EE2753053BF6B23DAC03045C4428061DA`

The derived VMDK is an analysis artefact and is not treated as a replacement for preserved Evidence Item E003.

#### Autopsy Ingest

The derived VMDK was successfully accepted by Autopsy 4.20.0.

Selected ingest modules included:

- Recent Activity
- File Type Identification
- Extension Mismatch Detector
- Embedded File Extractor
- Encryption Detection
- Interesting Files Identifier

#### Findings

No endpoint-forensic finding was concluded on Day 20.

The purpose of the day was to establish a verified and reproducible analysis environment for E003.

#### Next Step

Begin filesystem and user-activity analysis of E003, focusing on:

- `ProjectAtlas`
- `Staging`
- `project_archive.zip`
- deleted-file artefacts
- Recycle Bin artefacts
- user-profile activity
- persistent evidence of removable-media interaction


---

### Day 21 - E003 Filesystem Access and BitLocker Identification

#### Actions Completed

- Opened the E003 derived analysis disk in Autopsy 4.20.0.
- Identified the primary Windows partition as `vol6`.
- Observed that the expected Windows filesystem contents, including `Users`, were not available for normal browsing.
- Reviewed the Autopsy Encryption Detection result.
- Confirmed that Autopsy identified BitLocker encryption on `vol6`.
- Performed a post-acquisition check on LAB-WIN11-01 to understand the BitLocker state.
- No changes were made to preserved Evidence Item E003.

#### Autopsy Observation

Autopsy reported:

`Bitlocker encryption detected`

for the Windows partition represented by `vol6`.

#### BitLocker State Observed on the Running Endpoint

The post-acquisition endpoint check reported:

- BitLocker Version: 2.0
- Conversion Status: Used Space Only Encrypted
- Percentage Encrypted: 100%
- Encryption Method: XTS-AES 128
- Protection Status: Protection Off
- Lock Status: Unlocked
- Key Protectors: None Found

No recovery password or other BitLocker protector was identified.

#### Evidence Handling Note

LAB-WIN11-01 was powered on after E003 had already been preserved and integrity-verified.

The resulting activity is therefore considered post-acquisition activity and does not alter the preserved E003 evidence set.

The preserved E003 copy remains the authoritative evidence source for subsequent analysis.

#### Finding

The lack of visible Windows user files in Autopsy was attributable to BitLocker encryption on the Windows partition rather than absence of the expected filesystem.

#### Limitation

Autopsy 4.20.0 could identify the BitLocker-protected partition but did not expose the encrypted Windows filesystem for analysis in the current workflow.

#### Next Step

Create a separate disposable analysis clone derived from the verified E003 working material and obtain a decrypted analysis artefact without modifying preserved E003.

---

### Day 22 - Creation of Decrypted E003 Analysis Artefact

#### Actions Completed

- Continued preparation of E003 for filesystem analysis.
- Created a disposable decryption workflow while maintaining the preserved E003 evidence set separately.
- Initiated full BitLocker decryption of the Windows volume.
- Confirmed the Windows volume reached:
  - Conversion Status: Fully Decrypted
  - Percentage Encrypted: 0.0%
  - Encryption Method: None
- Identified that the original LAB-WIN11-01 VM had inadvertently been booted and decrypted instead of the intended disposable clone.
- Confirmed that this activity occurred after E003 had already been preserved and integrity-verified.
- Treated the modified original VM only as a post-acquisition processing source.
- Consolidated the post-acquisition decrypted VMware snapshot chain into a new derived VMDK.
- Calculated and recorded a SHA-256 hash for the derived analysis disk.
- Added the derived decrypted disk to a clean Autopsy 4.20.0 analysis case.
- Successfully exposed the Windows filesystem for analysis.

#### Workflow Deviation

The intended workflow was to decrypt a disposable clone of the E003 working copy.

During execution, the original LAB-WIN11-01 VM was inadvertently booted instead.

This was identified by comparing VMware disk modification timestamps and log activity.

Because E003 had already been preserved and independently hash-verified before this occurred, the preserved evidence item was not modified.

The original VM after this point is therefore considered a post-acquisition processing source rather than the authoritative preserved evidence.

#### Derived Analysis Artefact

**Filename:**

`LAB-WIN11-01-DECRYPTED-POSTACQ.vmdk`

**Size:**

38,913,048,576 bytes

**SHA-256:**

`1DD35A8CE98FAD6BAD7B9E5A4E9E50EC9D27FDBABDEA721F8A1C6B84FD8F7BFD`

The derived VMDK is an analysis artefact and is not represented as Evidence Item E003 itself.

#### Autopsy Result

Autopsy successfully exposed the primary Windows filesystem.

Visible root-level artefacts included:

- `$Recycle.Bin`
- `Program Files`
- `Program Files (x86)`
- `ProgramData`
- `Users`
- `Windows`

A non-critical filesystem-identification warning remained for the Microsoft Reserved partition.

#### Findings

No scenario-related endpoint finding was concluded on Day 22.

The purpose of the day was to overcome the BitLocker analysis barrier and establish a usable decrypted filesystem for subsequent examination.

#### Next Step

Begin endpoint filesystem analysis under:

`Users\labuser\Documents`

with focus on:

- `ProjectAtlas`
- `Staging`
- `project_archive.zip`
- surviving and deleted copies of scenario files
- Recycle Bin artefacts

---

### Day 23 - E003 Filesystem Activity Reconstruction

#### Actions Completed

- Examined `Users\labuser\Documents` in the decrypted E003 analysis artefact.
- Examined the `ProjectAtlas` directory.
- Examined the `Staging` directory.
- Inspected the endpoint copy of `project_archive.zip`.
- Searched E003 for:
  - `quarterly_summary.txt`
  - `meeting_notes.txt`
  - `project_archive.zip`
- Reviewed `$Recycle.Bin` directory structure.
- Distinguished allocated files from unallocated/deleted filesystem entries.

#### Documents Directory

Autopsy identified the following relevant items under:

`Users\labuser\Documents`

- `ProjectAtlas`
- `Staging`
- `project_archive.zip`

The endpoint copy of `project_archive.zip` was:

- Size: 810 bytes
- Created: `2026-09-06 22:54:02 EDT`
- Modified: `2026-09-06 22:54:03 EDT`
- Status: Allocated

#### ProjectAtlas

The directory contained allocated copies of:

- `client_contacts.csv` - 199 bytes
- `project_notes.txt` - 250 bytes

Autopsy also identified unallocated entries for:

- `meeting_notes.txt` - 168 bytes
- `quarterly_summary.txt` - 164 bytes

The unallocated status supports that these files no longer existed as normal allocated files in their original ProjectAtlas location at the time represented by E003.

The unallocated entries displayed later filesystem metadata timestamps, but these are not yet being treated as definitive deletion times pending Recycle Bin correlation.

#### Staging

The `Staging` directory contained allocated copies of:

- `client_contacts.csv` - 199 bytes
- `project_notes.txt` - 250 bytes
- `quarterly_summary.txt` - 164 bytes

The staging copies retained earlier content-modification times while showing later creation times associated with their placement in the Staging directory.

This supports the existence of separate staged copies rather than modification of the original ProjectAtlas files in place.

#### Archive Contents

Autopsy parsed `project_archive.zip` and identified:

- `client_contacts.csv` - 199 bytes
- `project_notes.txt` - 250 bytes
- `quarterly_summary.txt` - 164 bytes

These contents are consistent with the archive previously observed independently in E001.

#### Filename Search Results

Searches identified multiple filesystem artefacts associated with `quarterly_summary.txt`, including:

- an allocated copy associated with the Staging workflow
- an unallocated 164-byte entry associated with the earlier ProjectAtlas state
- shortcut-related artefacts

Searches for `meeting_notes.txt` identified:

- an unallocated 168-byte file entry
- shortcut-related artefacts

Searches for `project_archive.zip` identified the allocated 810-byte endpoint archive and associated filesystem slack.

#### Recycle Bin

Windows Recycle Bin structures and multiple SID-specific directories were present.

No `$I` / `$R` pair has yet been conclusively attributed to `meeting_notes.txt`.

Recycle Bin attribution is therefore deferred until the metadata records are decoded directly.

#### Findings

E003 supports the following sequence at the filesystem level:

1. Project-related files existed within `ProjectAtlas`.
2. Selected files existed separately within `Staging`.
3. `project_archive.zip` was created and contained three staged project files.
4. `meeting_notes.txt` and `quarterly_summary.txt` were no longer allocated in their original ProjectAtlas location.
5. A separate allocated copy of `quarterly_summary.txt` survived in Staging.

These findings are derived from the endpoint evidence rather than the private scenario ground truth.

#### Next Step

Decode the Windows Recycle Bin records, attribute deleted items to their original paths, and begin constructing the evidence-supported forensic timeline.

---

### Day 24 - Recycle Bin Attribution and Forensic Timeline

#### Actions Completed

- Reviewed parsed Windows Recycle Bin artifacts in Autopsy.
- Correlated Recycle Bin records with previously identified unallocated ProjectAtlas files.
- Confirmed original paths and deletion timestamps for two scenario files.
- Began populating the forensic timeline using evidence-derived timestamps rather than private ground truth.

#### Recycle Bin Findings

Autopsy identified two parsed Recycle Bin records.

**meeting_notes.txt**

Original path:

`C:\Users\labuser\Documents\ProjectAtlas\meeting_notes.txt`

Deletion time:

`2026-09-07 13:05:35 EDT`

The record correlates with the previously observed 168-byte unallocated `meeting_notes.txt` entry in ProjectAtlas.

**quarterly_summary.txt**

Original path:

`C:\Users\labuser\Documents\ProjectAtlas\quarterly_summary.txt`

Deletion time:

`2026-09-07 13:14:07 EDT`

The record correlates with the previously observed 164-byte unallocated ProjectAtlas entry.

A separate allocated copy of `quarterly_summary.txt` remains present in the Staging directory.

#### Timeline Development

The forensic timeline was populated with evidence-supported events covering:

- creation of staged file copies
- creation and modification of `project_archive.zip`
- Recycle Bin deletion of `meeting_notes.txt`
- Recycle Bin deletion of `quarterly_summary.txt`

Later access timestamps associated with acquisition, analysis, and post-acquisition processing were excluded from the original scenario timeline.

#### Findings

E003 now supports a chronological sequence in which selected project files were copied into a staging directory, an archive was subsequently created, and two files were later deleted from their original ProjectAtlas location.

Recycle Bin metadata provides direct evidence of the original file paths and deletion timestamps.

The surviving Staging copy of `quarterly_summary.txt` demonstrates that deletion of the original ProjectAtlas copy did not remove every copy of the file from the endpoint.

#### Next Step

Correlate removable-media artifacts and browser/command activity with the filesystem timeline and E001 USB evidence.