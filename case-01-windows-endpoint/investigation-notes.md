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