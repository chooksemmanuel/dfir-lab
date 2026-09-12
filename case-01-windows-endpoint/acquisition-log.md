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


---

## E002 - Volatile Memory Acquisition

**Case ID:** DFIR-CASE-001

**Evidence ID:** E002

**Endpoint:** LAB-WIN11-01

**Evidence Type:** Post-reboot volatile memory

**Acquisition Date:** 2026-09-12

**Acquisition Tool:** WinPmem

**Acquisition Executable:** `go-winpmem_amd64_1.0-rc2_signed.exe`

**Acquisition Tool SHA-256:**

`86691BB4AF2C17DD9EC4834C04A99AD51E04F780A07D1B05BC382A5D1892E0C4`

**Guest Acquisition Path:**

`C:\Forensics\E002\LAB-WIN11-01_E002.raw`

**Preserved Host Filename:**

`LAB-WIN-01_E002.raw`

**Preserved Host Location:**

Stored in controlled local evidence storage outside the public Git repository.

**Image Size:** 5,368,709,120 bytes

**WinPmem Reported Acquisition Duration:** 3m39.4113131s

**Image CreationTime:** 2026-09-12 10:45:00

**Image LastWriteTime:** 2026-09-12 10:48:40

**Acquisition Completion Checkpoint:** 2026-09-12 10:49:01.367 -04:00

**Precise Acquisition Start Time:** Not separately recorded.

## Integrity

**SHA-256:**

`E4E36E18891706E3C933F8290155716914025DFA38EE5B738B4956E77C4B8C44`

The SHA-256 was calculated first against the acquired image inside the evidence VM and again against the preserved host copy.

The two values matched exactly.

## Acquisition-Induced Activity

WinPmem reported that its acquisition service stopped after imaging and that its temporary driver was removed from:

`C:\Users\labadmin\AppData\Local\Temp\3763700613.sys`

The WinPmem executable and the guest-side memory image were intentionally left on the endpoint after acquisition so that subsequent disk acquisition may preserve evidence of the acquisition process itself.

## Transfer Handling

The acquired memory image was transferred from the evidence VM to dedicated host evidence storage using a temporary VMware shared folder.

The preserved host copy was named `LAB-WIN-01_E002.raw`, while the guest acquisition filename was `LAB-WIN11-01_E002.raw`.

The filename difference does not indicate a content difference. Matching SHA-256 values confirmed that the guest image and preserved host copy were identical.

An initial guest-side verification of the VMware shared-folder destination returned a path-not-found result even though the transfer had completed successfully. The host-side evidence directory was checked directly and confirmed that the complete image was present.

## Important Limitation

The endpoint had previously been shut down after the controlled scenario activity conducted during earlier days of the case.

Therefore, E002 does not preserve the volatile-memory state that existed during the original Day 05-Day 07 scenario.

E002 represents a post-reboot live-memory acquisition of the same endpoint immediately before final disk acquisition.

No forensic analysis of E002 has yet been performed.

