\# E003 Endpoint Disk Acquisition Plan



\## Case



\*\*Case ID:\*\* DFIR-CASE-001



\*\*Planned Evidence ID:\*\* E003



\*\*Endpoint:\*\* LAB-WIN11-01



\*\*Evidence Type:\*\* Endpoint virtual disk



\*\*Status:\*\* Pre-acquisition planning



\*\*Preflight Date:\*\* 2026-09-14



\## Objective



Preserve the current disk state of LAB-WIN11-01 after completion of the controlled scenario and volatile-memory acquisition.



No forensic disk analysis will begin before E003 has been acquired and integrity-verified.



\## VMware Configuration



VM configuration file:



`C:\\Users\\DELL\\Documents\\DFIR-Lab-Assets\\VMs\\LAB-WIN11-01.vmx`



The VM is currently powered off.



One VMware snapshot exists:



`BASELINE-CLEAN-2026-09-04`



The snapshot will not be restored, deleted, renamed, or consolidated before acquisition.



\## Current Virtual Disk Chain



Base virtual disk:



`LAB-WIN11-01.vmdk`



Observed host size:



18.68 GB



Current snapshot/delta disk:



`LAB-WIN11-01-000001.vmdk`



Observed host size:



22.70 GB



The VM configuration currently references:



`LAB-WIN11-01-000001.vmdk`



Therefore, the current endpoint state depends on the VMware snapshot chain and must not be represented by the delta VMDK alone.



\## Storage Preflight



Observed VM-folder size:



41.38 GB



Observed host C: free space:



65.0 GB



The endpoint was originally configured with a 64 GB virtual disk.



A RAW/DD acquisition could therefore approach the logical disk capacity and would leave insufficient safe free space on the current host.



A final acquisition format and destination will be selected only after adequate evidence-storage capacity has been confirmed.



\## Preservation Rules



\- Keep LAB-WIN11-01 powered off before disk acquisition.

\- Do not restore the clean baseline.

\- Do not delete or consolidate the existing snapshot.

\- Do not rename or independently manipulate components of the VMware disk chain.

\- Do not analyse the original VM disk files directly.

\- Preserve acquired evidence outside the public Git repository.

\- Calculate and record cryptographic hashes for the acquired evidence.

\- Document the exact acquisition tool, version, format, timestamps, destination, and any deviations.



\## Planned Next Step



Confirm sufficient destination storage and select the acquisition method for E003.



The acquisition method must preserve the current endpoint state represented by the complete VMware disk chain.



No E003 acquisition was performed during this preflight.

