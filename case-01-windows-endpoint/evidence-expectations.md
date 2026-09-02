# Evidence Expectations

This document records hypotheses about artefacts that may result from the controlled scenario.

These are **expected artefacts, not forensic findings**.

Actual findings will be documented only after evidence acquisition and analysis.

| Planned Activity | Potential Artefacts | Investigative Value |
|---|---|---|
| User logon | Windows event logs, profile artefacts, session metadata | Establish user/session activity |
| Browser use | Browser history, cache, downloads, cookies | Reconstruct browsing and download activity |
| File creation/modification | NTFS metadata, timestamps, Recent Files, LNK files, Jump Lists | Reconstruct document activity |
| PowerShell use | PowerShell history, command-line artefacts, process data | Identify commands and user actions |
| File copying | NTFS metadata, USN Journal, directory metadata | Reconstruct file movement |
| Staging directory creation | Filesystem metadata, directory timestamps | Identify potential collection/staging activity |
| Archive creation | Archive file metadata, PowerShell history, filesystem artefacts | Identify compression/staging behaviour |
| Removable-media use | Registry artefacts, USB device history, MountedDevices, related LNK artefacts | Determine whether external storage was used |
| File deletion | Recycle Bin, NTFS metadata, USN Journal, recoverable file content | Investigate deleted files |
| Running applications | Memory-resident processes, command lines, process relationships | Reconstruct active system state |
| Network activity | Browser artefacts, DNS/network artefacts, optional packet capture | Correlate local activity with network communications |

## Important

The presence or absence of any artefact above is not assumed.

The investigation must determine what evidence actually exists.