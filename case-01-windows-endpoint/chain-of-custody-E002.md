\# Chain of Custody - E002



\## Case Information



\*\*Case ID:\*\* DFIR-CASE-001



\*\*Evidence ID:\*\* E002



\*\*Evidence Description:\*\* Post-reboot volatile-memory acquisition from LAB-WIN11-01



\*\*Evidence Source:\*\* Live Windows evidence endpoint



\*\*Acquired By:\*\* Emmanuel Ihejiamaizu



\*\*Acquisition Date:\*\* 2026-09-12



\*\*Acquisition Method:\*\* Live physical-memory acquisition



\*\*Tool Used:\*\* WinPmem



\*\*Acquisition Executable:\*\* `go-winpmem\_amd64\_1.0-rc2\_signed.exe`



\*\*Tool SHA-256:\*\* `86691BB4AF2C17DD9EC4834C04A99AD51E04F780A07D1B05BC382A5D1892E0C4`



\*\*Guest Image Filename:\*\* `LAB-WIN11-01\_E002.raw`



\*\*Preserved Host Filename:\*\* `LAB-WIN-01\_E002.raw`



\*\*Image Size:\*\* 5,368,709,120 bytes



\*\*Evidence SHA-256:\*\* `E4E36E18891706E3C933F8290155716914025DFA38EE5B738B4956E77C4B8C44`



\*\*Evidence Storage:\*\* Controlled local evidence storage outside the public Git repository



\---



\## Evidence Handling Log



| Date/Time | Action | Location | Notes |

|---|---|---|---|

| 2026-09-12 10:45:00 | Memory image file created | LAB-WIN11-01 | Timestamp taken from image CreationTime; exact acquisition start was not separately recorded |

| 2026-09-12 10:48:40 | Image final-write timestamp recorded | LAB-WIN11-01 | Guest image size 5,368,709,120 bytes |

| 2026-09-12 10:49:01.367 -04:00 | Acquisition completion checkpoint recorded | LAB-WIN11-01 | WinPmem reported completion after 3m39.4113131s |

| 2026-09-12 | Guest SHA-256 calculated | LAB-WIN11-01 | Integrity value recorded before transfer |

| 2026-09-12 | Memory image transferred to forensic host | VMware shared folder | Host copy saved as `LAB-WIN-01\_E002.raw` |

| 2026-09-12 | Host SHA-256 calculated | Forensic host | Hash matched guest-side value exactly |

| 2026-09-12 | SHA-256 record saved | Forensic host | `E002-SHA256.txt` stored outside GitHub |

| 2026-09-12 | Evidence endpoint shut down | LAB-WIN11-01 | Guest acquisition image and WinPmem artefacts intentionally retained for later disk acquisition |

