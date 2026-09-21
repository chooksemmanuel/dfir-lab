\# Chain of Custody - E003



\## Case Information



\*\*Case ID:\*\* DFIR-CASE-001



\*\*Evidence ID:\*\* E003



\*\*Evidence Description:\*\* Verified preservation set of powered-off LAB-WIN11-01 VMware virtual machine



\*\*Source:\*\* LAB-WIN11-01 VMware source directory



\*\*Preserved By:\*\* Emmanuel Ihejiamaizu



\*\*Date:\*\* 2026-09-17



\*\*Source File Count:\*\* 20



\*\*Source Size:\*\* 44,436,161,087 bytes



\*\*Destination Device:\*\* Kingston XS1000 external SSD



\*\*Destination Path:\*\* `F:\\DFIR-Lab-Evidence\\DFIR-CASE-001\\E003-VM\\original`



\## Preservation Method



The powered-off VMware source set was copied in full using Robocopy.



No snapshot was restored, deleted, renamed, or consolidated.



The existing base disk, snapshot/delta disk, VM configuration, supporting files, logs, and observed lock directory were preserved.



\## Integrity



Source and destination files were independently hashed using SHA-256.



Each file was compared using:



\- relative path

\- byte length

\- SHA-256



All 20 files matched.



\*\*Verification Status:\*\* PASSED



\## Handling Log



| Date/Time | Action | Notes |

|---|---|---|

| 2026-09-17 12:35:18.594 -04:00 | Preservation checkpoint recorded | LAB-WIN11-01 confirmed powered off |

| 2026-09-17 | Source SHA-256 manifest generated | 20 files / 44,436,161,087 bytes |

| 2026-09-17 12:43:01 | Preservation copy started | Robocopy to Kingston XS1000 |

| 2026-09-17 12:45:45 | Preservation copy completed | 20 files copied; zero failures |

| 2026-09-17 | Destination SHA-256 manifest generated | Independent verification |

| 2026-09-17 | Source and destination manifests compared | All file paths, lengths and SHA-256 values matched |



\*\*Canonical Manifest SHA-256:\*\* `8768404A2653EA7490D6368D77AB72D3127596D5A2FB495B5B254E7EB14DE595`

| E003 | LAB-WIN11-01 VMware endpoint | Preserved and hash-verified | Analysis environment prepared |