# DFIR-CASE-001 - Case Closure

## Case

**Case ID:** DFIR-CASE-001  
**Title:** Windows Endpoint Forensics Lab: Investigating Suspicious User Activity  
**Endpoint:** LAB-WIN11-01  
**Environment:** Controlled laboratory  
**Status:** Closed - Investigation completed  

---

## Purpose

DFIR-CASE-001 was created as a controlled digital-forensics project covering the complete investigative lifecycle from laboratory preparation and activity generation through evidence acquisition, preservation, analysis, correlation and reporting.

No real victim systems, malware, stolen information or unauthorized infrastructure were used.

---

## Evidence Examined

### E001

Forensic image of controlled removable media.

Primary use:

- removable-media examination
- archive verification
- cross-source correlation

### E002

Post-reboot volatile-memory image of LAB-WIN11-01.

Primary use:

- Windows memory-analysis practice
- process examination
- process-tree analysis
- command-line examination
- available network-state examination

### E003

Preserved VMware endpoint state.

Primary use:

- filesystem examination
- browser artifacts
- file staging
- archive creation
- removable-media artifacts
- deletion evidence
- timeline reconstruction

---

## Principal Findings

The evidence supports a sequence involving:

1. browser research;
2. ProjectAtlas document activity;
3. selected files copied into a staging directory;
4. creation of project_archive.zip;
5. removable-media activity;
6. recovery of an identical archive from removable-media evidence;
7. subsequent deletion of ProjectAtlas files.

The project_archive.zip files recovered independently from E001 and E003 were both 810 bytes and produced the same SHA-256 value:

`1AB794E40D39B8DF9970A30ACE90E597B7EB68F9A539E5E82FB2BBC3F8199CD4`

This establishes that the recovered archives were byte-for-byte identical.

---

## Investigative Boundaries

The investigation does not infer malicious intent from the observed activity.

Browser searches were treated as evidence of searches, not evidence of motive.

USB attachment evidence was not used to invent an exact transfer timestamp.

PowerShell activity recovered from E002 was interpreted in the context of documented administrative and acquisition activity.

An empty Volatility netscan result was recorded as a plugin result rather than proof that the endpoint had never communicated over a network.

Evidence that differed from the planned scenario was retained rather than altered to make the investigation appear cleaner.

---

## Limitations

- E001 was acquired without a hardware write blocker.
- E002 was acquired after an earlier endpoint reboot and does not preserve the original volatile state from the controlled Day 05-Day 07 activity.
- E003 required a derived BitLocker/decryption workflow before filesystem analysis could proceed.
- The active laboratory VM was inadvertently modified during post-acquisition processing; the preserved and previously verified E003 evidence copy remained unchanged.
- A discrepancy exists between recovered deletion metadata and the originally documented execution method for one file.

---

## Final Assessment

DFIR-CASE-001 successfully demonstrated a complete controlled Windows forensic workflow involving evidence acquisition, integrity verification, filesystem analysis, removable-media analysis, memory forensics, deleted-file analysis, cross-source correlation and timeline reconstruction.

The final investigative narrative is restricted to conclusions supported by the recovered evidence.

---

## Disposition

Investigation complete.

Preserved evidence remains stored outside the public GitHub repository.

Derived analysis material remains separated from original evidence.

The public repository contains documentation, methodology, investigative findings and reporting material rather than raw forensic evidence.

**Case Status: CLOSED**