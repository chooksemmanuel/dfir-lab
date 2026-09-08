\# DFIR-CASE-001 Acquisition Plan



\## Objective



Acquire forensic evidence from the controlled Case 01 environment while preserving evidence integrity and documenting acquisition actions.



\## Planned Evidence Sources



\### E001 - Controlled Removable USB



Physical removable storage used during the Day 07 scenario.



\*\*Planned acquisition format:\*\* RAW/DD image



\### E002 - Volatile Memory



Live memory from `LAB-WIN11-01`.



Memory acquisition will occur while the endpoint is running and before final disk acquisition.



\### E003 - Windows Endpoint Disk



Forensic image of the `LAB-WIN11-01` system disk.



Disk acquisition will occur after volatile-memory acquisition.



\## Acquisition Order



For the Windows endpoint:



1\. Capture volatile memory while the system is live.

2\. Preserve acquisition metadata and hashes.

3\. Shut down the endpoint using the documented acquisition procedure.

4\. Acquire the system disk.

5\. Analyse working copies rather than altering original acquired evidence.



The removable USB is independent of the endpoint's volatile state and may be acquired separately.



\## Integrity



Acquired evidence will be hashed and documented.



Raw forensic evidence will remain outside the public Git repository.



The repository will contain only safe documentation, hashes, methodology, findings, and sanitised screenshots.



\## Limitations



This is an educational laboratory rather than a production forensic environment.



A hardware write blocker is not currently available for removable-media acquisition.



This limitation will be documented rather than concealed.

