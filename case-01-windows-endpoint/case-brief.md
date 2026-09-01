# Case 01 - Windows Endpoint Forensics

## Case Title

Investigating Suspicious User Activity on a Windows Endpoint

## Case Type

Controlled digital-forensics training investigation.

## Background

A Windows endpoint is suspected of containing evidence of unusual user activity.

This project will create a controlled Windows environment, generate known and safe activity within that environment, acquire forensic evidence from the system, and investigate the resulting evidence using digital-forensics methods.

All activity will be intentionally generated for this lab using synthetic files and non-malicious actions.

No real victim, organisation, compromised machine, stolen credentials, or unauthorised system is involved.

## Primary Investigation Question

**What occurred on the Windows endpoint, when did it occur, and what forensic evidence supports the reconstruction?**

## Investigation Questions

1. What user activity can be reconstructed from the available evidence?

2. What files were created, downloaded, modified, moved, archived, executed, or deleted?

3. Is there evidence of command-line or PowerShell activity?

4. Is there evidence that removable storage was connected or used?

5. What processes were active during the period of interest?

6. What relevant browser activity can be identified?

7. Can a reliable sequence of events be reconstructed?

8. Do multiple forensic artefacts corroborate the same events?

9. Is there evidence consistent with staging or movement of synthetic data?

10. What conclusions are supported by the evidence?

11. What conclusions cannot be made from the available evidence?

## Potential Evidence Sources

Potential evidence sources may include:

- Windows disk image
- Windows memory image
- Windows event and artefact data
- Browser artefacts
- Filesystem metadata
- Removable-device artefacts
- Process information
- Command-line artefacts
- Optional network packet captures

## Potential Tools

Tools may include:

- Autopsy
- FTK Imager
- Volatility 3
- Wireshark

The final toolset will depend on what is appropriate for the evidence and investigative questions.

## Current Status

Case defined.

No forensic evidence has yet been generated, acquired, or analysed.