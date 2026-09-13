\# Case 01 - Current Status



\## Case



\*\*Case ID:\*\* DFIR-CASE-001



\*\*Case Title:\*\* Investigating Suspicious User Activity on a Windows Endpoint



\*\*Endpoint:\*\* LAB-WIN11-01



\*\*Current Phase:\*\* Evidence acquisition



\*\*Status Date:\*\* 2026-09-13



\## Investigation Question



What occurred on the Windows endpoint, when did it occur, and what forensic evidence supports the reconstruction?



\## Evidence Status



| Evidence ID | Evidence Source | Status | Analysis Status |

|---|---|---|---|

| E001 | Controlled removable USB | Acquired and hash-verified | Not analysed |

| E002 | Post-reboot volatile memory from LAB-WIN11-01 | Acquired and hash-verified | Not analysed |

| E003 | LAB-WIN11-01 endpoint disk | Pending acquisition | Not analysed |



\## E001



Evidence Item E001 is a complete forensic image of the controlled removable USB used during the Day 07 scenario.



The source device was acquired using FTK Imager.



The resulting image was verified during acquisition and an independent SHA-256 hash was calculated.



No forensic analysis of E001 has yet been performed.



\## E002



Evidence Item E002 is a post-reboot live-memory image acquired from LAB-WIN11-01 using WinPmem.



The image was hashed inside the evidence VM before transfer and again after preservation on the forensic host.



The SHA-256 values matched.



E002 does not preserve the volatile-memory state that existed during the original Day 05-Day 07 scenario because the endpoint had previously been shut down.



No forensic analysis of E002 has yet been performed.



\## E003



Evidence Item E003 will represent the final forensic acquisition of the LAB-WIN11-01 endpoint disk.



E003 has not yet been acquired.



The next acquisition step will begin only after disk layout, storage requirements, preservation method, and available host capacity have been reviewed.



\## Analysis Status



Forensic analysis has not yet begun.



The current priority is to complete evidence preservation before examining acquired evidence.



No investigative conclusion has been made from E001 or E002.



The public forensic timeline remains unpopulated.



\## Current Evidence Handling Position



\- Raw forensic evidence remains outside the public Git repository.

\- Acquisition hashes and documentation are maintained separately from raw evidence.

\- Original evidence images will not be treated as disposable working files.

\- Acquisition limitations and execution deviations remain documented.

\- Planned activity is not represented as completed activity.



\## Next Step



Prepare the E003 endpoint-disk acquisition.



This will include:



1\. Identifying the relevant VMware virtual-disk files.

2\. Measuring their actual storage requirements.

3\. Checking remaining forensic-host storage.

4\. Selecting the safest acquisition and preservation approach.

5\. Documenting the E003 acquisition plan before imaging begins.



\## Current Case Position



The investigation has completed the controlled scenario-generation phase and has entered the evidence-preservation phase.



Two evidence items have been acquired.



One primary evidence source remains to be preserved before forensic analysis begins.

