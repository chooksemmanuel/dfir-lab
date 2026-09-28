# DFIR-CASE-001 - Investigative Findings

## Scope

This document records findings supported by the forensic evidence examined during DFIR-CASE-001.

The reconstruction is based primarily on:

- E001 - removable-media image
- E002 - post-reboot volatile-memory image
- E003 - preserved Windows endpoint state
- Autopsy filesystem and artifact analysis
- FTK Imager examination
- Volatility 3 memory analysis
- SHA-256 cross-source comparisons

The purpose is to reconstruct observable activity without treating the original scenario plan as an answer key.

---

## F-01 - Pre-Activity Browser Research

Autopsy recovered Microsoft Edge history showing activity on 2026-09-05 including:

- a visit to `example.com`
- a visit to the Wikipedia page for Digital Forensics
- a search for `how to compress files using powershell`
- a search for `windows copy files to usb drive`

The searches occurred before the later file-staging, archive, and removable-media activity observed elsewhere in the evidence.

### Assessment

The browser artifacts establish that these searches occurred.

Their temporal relationship to the later archive and USB activity makes them relevant to the reconstruction, but the searches alone do not establish user intent.

**Confidence:** High that the activity occurred; Moderate regarding its relationship to later actions.

---

## F-02 - ProjectAtlas Files Were Staged

The E003 filesystem contained a `Staging` directory under the lab user's Documents folder.

Recovered staging contents included:

- `client_contacts.csv`
- `project_notes.txt`
- `quarterly_summary.txt`

The files retained their earlier content-modification timestamps while receiving later creation timestamps in the staging directory on 2026-09-06.

`meeting_notes.txt` was not present in the staging set.

### Assessment

The filesystem evidence supports deliberate selection and duplication of three ProjectAtlas files into a separate staging location.

**Confidence:** High.

---

## F-03 - project_archive.zip Was Created From the Staged Material

E003 contained:

`C:\Users\labuser\Documents\project_archive.zip`

The archive was 810 bytes.

Autopsy showed three files inside the archive:

- `client_contacts.csv`
- `project_notes.txt`
- `quarterly_summary.txt`

The archive was created on 2026-09-06 at approximately 22:54 EDT.

### Assessment

The archive contents correspond with the three files observed in the Staging directory.

This supports a sequence of:

Project files -> Staging -> ZIP archive

**Confidence:** High.

---

## F-04 - Removable Media Was Connected and the Same Archive Appeared on E001

Windows artifacts recovered from E003 recorded a removable device identified as:

- Device model: GEMBIRD DM8261 Flashdisc
- Date/time observed: 2026-09-07 11:59:49 EDT

Separately, E001 contained `project_archive.zip`.

The archive exported from E003 and the archive recovered from E001 were both:

- Size: 810 bytes
- SHA-256:
  `1AB794E40D39B8DF9970A30ACE90E597B7EB68F9A539E5E82FB2BBC3F8199CD4`

### Assessment

The matching cryptographic hashes demonstrate that the archive recovered from the endpoint and the archive present on the removable-media evidence are byte-for-byte identical.

Combined with the USB attachment evidence and surrounding timestamps, the evidence strongly supports movement of the archive between the endpoint environment and the removable media.

**Confidence:** High.

---

## F-05 - ProjectAtlas Files Were Subsequently Deleted

Autopsy identified deletion-related filesystem artifacts for:

- `meeting_notes.txt`
- `quarterly_summary.txt`

The Recycle Bin Analyzer reported:

- `meeting_notes.txt` - 2026-09-07 13:05:35 EDT
- `quarterly_summary.txt` - 2026-09-07 13:14:07 EDT

Both files were also visible as unallocated entries within the ProjectAtlas directory during filesystem examination.

### Assessment

The evidence supports deletion of both files after the earlier staging/archive activity.

The recovered Recycle Bin metadata for `quarterly_summary.txt` does not perfectly align with the originally recorded execution method for that file. This discrepancy is retained rather than rewritten to force the evidence to match the intended scenario.

**Confidence:** High that deletion occurred; deletion mechanism for `quarterly_summary.txt` should be described cautiously.

---

## F-06 - Volatile Memory Provides Post-Reboot Context Only

E002 was successfully parsed using Volatility 3 Framework 2.28.2.

Analysis included:

- `windows.info`
- `windows.pslist`
- `windows.pstree`
- `windows.cmdline`
- `windows.netscan`

Recovered activity included Windows system processes, Explorer, VMware Tools, Windows Terminal and PowerShell.

PowerShell activity observed in the memory image was consistent with documented administrative/acquisition activity and was not independently classified as suspicious.

`windows.netscan` returned no connection records from the captured image.

### Limitation

E002 was acquired after the endpoint had previously been rebooted.

It therefore does not preserve the volatile state that existed during the original Day 05-Day 07 scenario.

It must not be used to claim which processes or network connections existed during those earlier events.

**Confidence:** High regarding the analysed post-reboot memory state.

---

## Overall Reconstruction

The combined evidence supports the following sequence:

Browser research
-> ProjectAtlas file activity
-> selected files copied into Staging
-> ZIP archive created
-> removable media attached
-> identical archive observed on removable-media evidence
-> ProjectAtlas files subsequently deleted

This reconstruction is based on correlations between independent forensic artifacts rather than on the scenario plan alone.

No malicious intent is inferred from the artifacts. The case demonstrates forensic reconstruction of controlled suspicious-user activity within a lab environment.