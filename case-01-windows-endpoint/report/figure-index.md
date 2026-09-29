# DFIR-CASE-001 - Figure Index

## Figure 1 - Clean Windows forensic laboratory
Suggested visual:
LAB-WIN11-01 VMware configuration / baseline environment.

Purpose:
Establishes the investigated endpoint and controlled laboratory.

---

## Figure 2 - E001 acquisition verification
Suggested visual:
FTK Imager verification showing matching hashes and no bad blocks.

Purpose:
Demonstrates forensic acquisition and integrity verification.

---

## Figure 3 - E003 evidence preservation
Suggested visual:
PowerShell output showing preserved/working manifest verification.

Purpose:
Demonstrates separation and verification of endpoint evidence.

---

## Figure 4 - Browser research artifacts
Suggested visual:
Autopsy Web History / Web Search showing:
- how to compress files using powershell
- windows copy files to usb drive

Purpose:
Places browser research before later filesystem activity.

---

## Figure 5 - ProjectAtlas filesystem state
Suggested visual:
Autopsy ProjectAtlas directory showing:
- client_contacts.csv
- project_notes.txt
- meeting_notes.txt [unallocated]
- quarterly_summary.txt [unallocated]

Purpose:
Shows surviving and deleted project artifacts together.

---

## Figure 6 - Staging directory
Suggested visual:
Autopsy Staging directory containing:
- client_contacts.csv
- project_notes.txt
- quarterly_summary.txt

Purpose:
Supports selected-file staging.

---

## Figure 7 - Archive contents
Suggested visual:
Autopsy or FTK view of project_archive.zip containing the three staged files.

Purpose:
Connects Staging contents with the archive.

---

## Figure 8 - USB attachment artifact
Suggested visual:
Autopsy USB Device Attached entry for GEMBIRD DM8261 Flashdisc.

Purpose:
Supports removable-media activity.

---

## Figure 9 - Cross-source archive verification
Suggested visual:
PowerShell hash output comparing E001 and E003 project_archive.zip.

Purpose:
Shows matching 810-byte files and identical SHA-256 values.

---

## Figure 10 - Recycle Bin findings
Suggested visual:
Autopsy Recycle Bin Analyzer showing meeting_notes.txt and quarterly_summary.txt with deletion timestamps.

Purpose:
Supports subsequent file deletion.

---

## Figure 11 - Memory image identification
Suggested visual:
Volatility windows.info output.

Purpose:
Demonstrates successful parsing of E002.

---

## Figure 12 - Memory process triage
Suggested visual:
Volatility process / PowerShell triage output.

Purpose:
Shows post-reboot process evidence and acquisition-related context.

---

## Figure 13 - Reconstructed investigation timeline
Suggested visual:
Final timeline chart generated from timeline.csv.

Purpose:
Provides a visual summary of the reconstructed sequence.