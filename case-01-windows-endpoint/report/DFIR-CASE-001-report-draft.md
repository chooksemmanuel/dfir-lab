# DFIR-CASE-001
## Windows Endpoint Forensics Lab: Investigating Suspicious User Activity

**Examiner:** Emmanuel Ihejiamaizu  
**Endpoint:** LAB-WIN11-01  
**Environment:** Controlled Windows 11 forensic laboratory  
**Case Type:** Endpoint / removable-media / memory investigation  
**Status:** Final analysis and reporting phase  

---

# Executive Summary

DFIR-CASE-001 is a controlled digital-forensics investigation created to practise the complete investigative lifecycle rather than only individual forensic tools.

The lab began with the creation of a clean Windows 11 virtual endpoint. Controlled user activity was then introduced involving browser research, document handling, file staging, archive creation, removable-media activity and subsequent file deletion.

Evidence was acquired and analysed using multiple forensic approaches.

The investigation ultimately correlated evidence from:

- E001 - removable-media image
- E002 - volatile-memory image
- E003 - preserved Windows endpoint state

Analysis was performed using tools including Exterro FTK Imager, Autopsy and Volatility 3.

The recovered evidence supports a sequence in which selected ProjectAtlas files were staged, compressed into `project_archive.zip`, associated with removable-media activity, and followed by deletion of files from the original project directory.

Cryptographic comparison established that the archive recovered from the Windows endpoint and the archive recovered from the USB evidence were byte-for-byte identical.

No conclusion of malicious intent is made. The scenario was intentionally generated inside a controlled forensic laboratory.

---

# 1. Introduction

Digital-forensics investigations require more than finding individual artifacts.

A defensible investigation must preserve evidence, verify integrity, distinguish original evidence from working copies, correlate independent artifacts, document limitations and reconstruct only what the available evidence supports.

This project was designed to practise that complete workflow against a Windows endpoint.

The investigation was developed progressively over a 30-day period, beginning with laboratory preparation and controlled activity generation before moving through evidence acquisition, preservation, analysis, correlation and reporting.

---

# 2. Aim

The aim of DFIR-CASE-001 was to build and investigate a controlled Windows endpoint scenario while applying a structured digital-forensics workflow from evidence generation through final reporting.

---

# 3. Objectives

The investigation was designed to:

1. Build an isolated Windows forensic laboratory.
2. Generate realistic but controlled user activity.
3. Preserve evidence before analysis.
4. Maintain separation between original evidence and working copies.
5. Verify evidence using cryptographic hashes.
6. Examine filesystem, browser, deletion, removable-media and memory artifacts.
7. Correlate evidence from multiple independent sources.
8. Reconstruct a defensible sequence of activity.
9. Document investigative mistakes, deviations and limitations rather than concealing them.
10. Produce a professional final forensic report.

---

# 4. Laboratory Environment

The investigated endpoint was a Windows 11 virtual machine named:

`LAB-WIN11-01`

The VM was created using VMware Workstation.

Relevant configuration included:

| Component | Configuration |
|---|---|
| Operating System | Windows 11 Pro |
| Architecture | 64-bit |
| VM Platform | VMware Workstation |
| CPU | 2 vCPU |
| RAM | 4 GB |
| Virtual Disk | 64 GB |
| Network | NAT |
| Firmware | UEFI |
| Secure Boot | Enabled |
| Virtual TPM | Enabled |

Two primary user contexts were used:

- `labadmin` - administrative/setup and acquisition activity
- `labuser` - controlled scenario activity

The lab contained synthetic data only.

---

# 5. Scenario Overview

The controlled scenario generated several categories of activity.

The scenario included:

Browser research
→ creation and handling of ProjectAtlas documents
→ selected files copied into a staging directory
→ archive creation
→ removable-media interaction
→ subsequent file deletion

The scenario plan itself was not used as the forensic answer key.

A separate private ground-truth record was maintained during activity generation, while the public investigative timeline remained empty until evidence analysis produced supportable findings.

---

# 6. Evidence Inventory

| Evidence ID | Evidence Type | Description | Primary Purpose |
|---|---|---|---|
| E001 | Removable-media image | Forensic image of controlled USB media | Examine transferred archive and removable-media contents |
| E002 | Volatile memory | Live-memory image of LAB-WIN11-01 | Practise Windows memory analysis |
| E003 | Endpoint state | Preserved VMware endpoint files | Filesystem and endpoint-artifact investigation |

Original forensic evidence and large working files were stored outside the public GitHub repository.

---

# 7. Evidence Acquisition and Preservation

## 7.1 E001 - USB Evidence

E001 was acquired using Exterro FTK Imager 8.3.0.27.

The removable media was imaged using RAW/DD format.

The resulting image size was:

`262,144,000 bytes`

FTK verification reported matching MD5 and SHA-1 values and no bad blocks.

An independent SHA-256 hash was also calculated:

`B966EEFB6AE74A2280F82688F95A797B7036872A2967326A7657B23E3CD9C7F3`

A hardware write blocker was not available. This limitation was documented during acquisition.

---

## 7.2 E002 - Volatile Memory

E002 was acquired from the running Windows endpoint.

The preserved image size was:

`5,368,709,120 bytes`

SHA-256:

`E4E36E18891706E3C933F8290155716914025DFA38EE5B738B4956E77C4B8C44`

The preserved image and working copy were independently hashed and verified as identical.

E002 has an important limitation.

The endpoint had previously been rebooted after the original controlled scenario activity. E002 therefore represents post-reboot volatile state and does not preserve the original memory state from the Day 05-Day 07 activity.

---

## 7.3 E003 - Endpoint Evidence

The VMware endpoint state was preserved separately from the active laboratory environment.

The preserved E003 set contained 20 files totalling approximately 41.38 GB.

A source manifest containing individual SHA-256 hashes was generated before preservation.

After copying the evidence to external storage, a destination manifest was independently generated.

Comparison of:

- relative paths
- file lengths
- SHA-256 hashes

returned no differences.

The preserved E003 copy therefore passed integrity verification.

---

# 8. Analysis Methodology

Analysis was conducted against working or derived copies rather than intentionally modifying preserved evidence.

The principal tools included:

| Tool | Purpose |
|---|---|
| FTK Imager 8.3.0.27 | Evidence acquisition and USB examination |
| Autopsy 4.20.0 | Filesystem and artifact analysis |
| Volatility 3 Framework 2.28.2 | Windows memory analysis |
| PowerShell | Hashing, validation, manifests and controlled evidence handling |
| VMware Workstation | Controlled endpoint environment |

E003 initially presented an additional challenge because the Windows partition was BitLocker protected.

A derived analysis workflow was therefore used to obtain a readable Windows filesystem for examination.

During this process, the original active laboratory VM was inadvertently modified instead of the intended disposable clone.

This did not alter the previously preserved E003 evidence set.

The deviation was documented, and the modified VM was subsequently treated only as a post-acquisition processing source.

---

# 9. Investigative Findings

## 9.1 Browser Activity

Microsoft Edge artifacts recovered by Autopsy showed browser activity including:

- `example.com`
- Wikipedia - Digital Forensics
- `how to compress files using powershell`
- `windows copy files to usb drive`

The searches occurred before later staging, archive and removable-media activity.

The browser evidence establishes that the searches occurred.

It does not independently establish intent.

---

## 9.2 ProjectAtlas

The ProjectAtlas directory contained evidence associated with:

- `client_contacts.csv`
- `project_notes.txt`
- `meeting_notes.txt`
- `quarterly_summary.txt`

Analysis later showed `meeting_notes.txt` and `quarterly_summary.txt` as unallocated/deleted entries.

---

## 9.3 File Staging

A `Staging` directory was identified under the lab user's Documents directory.

It contained:

- `client_contacts.csv`
- `project_notes.txt`
- `quarterly_summary.txt`

`meeting_notes.txt` was not present in the staging set.

The evidence supports deliberate selection and duplication of three project files.

---

## 9.4 Archive Creation

The endpoint contained:

`C:\Users\labuser\Documents\project_archive.zip`

Size:

`810 bytes`

The archive contained:

- `client_contacts.csv`
- `project_notes.txt`
- `quarterly_summary.txt`

The archive contents correspond with the files identified in the Staging directory.

---

## 9.5 Removable-Media Activity

Endpoint artifacts identified removable-media activity associated with:

`GEMBIRD DM8261 Flashdisc`

The removable-media image E001 also contained `project_archive.zip`.

The endpoint archive and USB archive were independently exported and hashed.

Both were:

`810 bytes`

and both produced the SHA-256 value:

`1AB794E40D39B8DF9970A30ACE90E597B7EB68F9A539E5E82FB2BBC3F8199CD4`

The matching cryptographic hashes establish that the two recovered archives are byte-for-byte identical.

---

## 9.6 Deleted Files

Autopsy identified Recycle Bin metadata associated with:

`meeting_notes.txt`

Deletion time:

`2026-09-07 13:05:35 EDT`

and:

`quarterly_summary.txt`

Deletion time:

`2026-09-07 13:14:07 EDT`

Both were also observed as unallocated entries during filesystem analysis.

A discrepancy exists between recovered deletion metadata for `quarterly_summary.txt` and the originally recorded execution method.

The discrepancy has been retained rather than altering the investigative narrative to force agreement with the planned scenario.

---

## 9.7 Memory Analysis

E002 was examined using Volatility 3 Framework 2.28.2.

Analysis included:

- `windows.info`
- `windows.pslist`
- `windows.pstree`
- `windows.cmdline`
- `windows.netscan`

The memory image was successfully parsed.

Observed processes included standard Windows activity, Explorer, VMware Tools, Windows Terminal and PowerShell.

PowerShell PID 5816 had a creation time of:

`2026-09-12 14:11:05 UTC`

Its presence was consistent with documented administrative/acquisition activity and was not classified as suspicious.

`windows.netscan` returned no socket or connection rows from the captured image.

This result is not interpreted as evidence that the endpoint had never used the network.

---

# 10. Timeline Reconstruction

The evidence currently supports the following high-level sequence:

Browser research
↓
ProjectAtlas activity
↓
Selected files copied to Staging
↓
project_archive.zip created
↓
Removable media attached
↓
Identical archive identified on USB evidence
↓
ProjectAtlas files deleted

The reconstruction was generated from examined forensic artifacts rather than from the private scenario plan.

---

# 11. Cross-Source Correlation

One of the strongest findings in the investigation came from comparing independent evidence sources.

`project_archive.zip` was recovered from both:

- E003 - Windows endpoint
- E001 - removable-media evidence

Both copies had the same file length and the same SHA-256 value.

This provides cryptographic evidence linking the archive observed on the endpoint with the archive recovered from the removable media.

---

# 12. Investigative Limitations

Several limitations should be considered when interpreting this case.

The USB was acquired without a hardware write blocker.

E002 was captured after the endpoint had already been rebooted and therefore does not represent the original volatile state from the controlled scenario.

The BitLocker analysis workflow required post-acquisition processing and produced derived evidence for examination.

The original active laboratory VM was unintentionally modified during this process; however, the previously preserved and hash-verified E003 evidence remained unchanged.

Some recovered metadata did not perfectly match the originally planned execution sequence.

These discrepancies were documented rather than removed.

---

# 13. Conclusion

DFIR-CASE-001 demonstrated the complete lifecycle of a controlled Windows endpoint investigation.

The investigation moved from environment preparation and synthetic scenario generation through evidence acquisition, integrity verification, filesystem analysis, removable-media examination, memory analysis, cross-source correlation and timeline reconstruction.

The strongest reconstructed sequence supports selected ProjectAtlas files being staged, compressed into an archive, associated with removable-media activity and followed by file deletion.

Cryptographic comparison established that the archive recovered from the endpoint and the archive recovered from the USB were identical.

More importantly, the project demonstrated the difference between observing an artifact and making an investigative claim.

Browser searches were not treated as proof of intent.

PowerShell activity was not automatically classified as suspicious.

An empty `netscan` result was not treated as proof that no network activity occurred.

Unexpected evidence was retained even where it differed from the intended scenario.

The final conclusions therefore remain limited to what the forensic evidence itself can support.

---

# 14. Tools Used

- VMware Workstation
- Windows 11
- Exterro FTK Imager 8.3.0.27
- Autopsy 4.20.0
- Volatility 3 Framework 2.28.2
- PowerShell
- Git
- GitHub

---

# 15. Appendices

## Appendix A - Evidence hashes

## Appendix B - Reconstructed timeline

## Appendix C - Selected forensic screenshots

## Appendix D - Acquisition and chain-of-custody documentation