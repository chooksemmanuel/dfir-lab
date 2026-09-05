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