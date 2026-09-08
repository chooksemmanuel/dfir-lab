\# Evidence Acquisition Log



\## E001 - Controlled Removable USB



\*\*Case ID:\*\* DFIR-CASE-001



\*\*Evidence ID:\*\* E001



\*\*Source:\*\* Controlled removable USB used during the Day 07 scenario



\*\*Approximate Source Capacity:\*\* 250 MB



\*\*Acquisition Date:\*\* 2026-09-08



\*\*Acquisition Start:\*\* 2026-09-08 16:21:36 -04:00



\*\*Acquisition End:\*\* 2026-09-08 16:22:10 -04:00



\*\*Acquisition Tool:\*\* Exterro FTK Imager



\*\*Tool Version:\*\* 8.3.0.27



\*\*Acquisition Type:\*\* Physical drive



\*\*Image Format:\*\* RAW/DD



\*\*Image Filename:\*\* `E001\_USB.001`



\*\*Image Size:\*\* 262,144,000 bytes



\*\*Sector Count:\*\* 512,000



\*\*Bytes Per Sector:\*\* 512



\## Integrity



\*\*MD5:\*\*



`c7709f9be892b0425aeeba16695126f1`



\*\*SHA-1:\*\*



`69aa367eb381adac60eb7eeb12f168498747aae8`



\*\*SHA-256:\*\*



`B966EEFB6AE74A2280F82688F95A797B7036872A2967326A7657B23E3CD9C7F3`



\## Verification



FTK Imager verification completed successfully.



\- MD5 computed hash matched the report hash.

\- SHA-1 computed hash matched the report hash.

\- No bad blocks were reported.



An independent SHA-256 hash was also calculated using PowerShell after acquisition.



\## Handling



The physical USB was disconnected and set aside after acquisition.



The acquired image and associated hash records are stored outside the public Git repository.



\## Limitation



A hardware write blocker was not available for this educational acquisition.



The USB was connected directly to the Windows forensic host.



No intentional browsing, deletion, or modification of the source media was performed before imaging.



This limitation will be considered during later interpretation of the evidence.

