# Volatile Memory Acquisition Plan

## Case

**Case ID:** DFIR-CASE-001

**Planned Evidence ID:** E002

**Endpoint:** LAB-WIN11-01

**Evidence Type:** Volatile memory

## Objective

Acquire a memory image from the controlled Windows endpoint before final disk acquisition.

The purpose is to preserve volatile information that would otherwise be lost when the system is powered off.

## Acquisition Principle

Volatile memory must be acquired while the endpoint is running.

The acquisition process itself will modify the live system to some degree because a memory-acquisition utility must execute on the endpoint.

This limitation will be documented.

## Planned Order

1. Confirm available storage on the forensic host.
2. Prepare a dedicated E002 evidence directory outside the public Git repository.
3. Select and document the memory-acquisition utility and exact version.
4. Power on LAB-WIN11-01 from its current post-scenario state.
5. Log in using the documented acquisition procedure.
6. Avoid unnecessary interaction with the endpoint.
7. Capture volatile memory.
8. Record acquisition start and end times.
9. Calculate and record SHA-256.
10. Preserve the original memory image outside GitHub.
11. Update the evidence manifest and chain-of-custody documentation.
12. Shut down the endpoint only after volatile acquisition is complete.
13. Proceed to endpoint disk acquisition afterward.

## Expected Size

LAB-WIN11-01 is configured with approximately 4 GB of RAM.

The resulting memory image may therefore require approximately 4 GB or more of available storage, depending on the acquisition tool and output format.

Additional free space will be reserved for hashes, logs, working copies, and later analysis.

## Evidence Handling

The original E002 memory image will remain outside the public Git repository.

A SHA-256 hash will be calculated after acquisition.

Analysis will be performed from a working copy where practical.

## Important Limitation

Live-memory acquisition is inherently intrusive.

The acquisition utility and associated operator actions may create or alter processes, memory contents, timestamps, logs, and other artefacts.

Those acquisition-related changes will be documented and considered during analysis.

### Post-Reboot Volatile-State Limitation

The endpoint was shut down after the controlled scenario activity performed during earlier days of the case.

As a result, E002 cannot preserve the volatile-memory state that existed during the original Day 05-Day 07 scenario execution.

E002 instead represents a post-reboot live-memory acquisition of the same endpoint immediately before final disk acquisition.

The memory image remains useful for practising memory acquisition and analysis of the current endpoint state, but it will not be represented as evidence of processes or other volatile state that existed before the earlier shutdown.

## Selected Acquisition Tool

**Tool:** WinPmem

**Executable:** `go-winpmem_amd64_1.0-rc2_signed.exe`

**Purpose:** Acquire physical memory from the live Windows evidence endpoint.

**Expected Output:** RAW memory image

**Tool SHA-256:** 86691BB4AF2C17DD9EC4834C04A99AD51E04F780A07D1B05BC382A5D1892E0C4 

The acquisition executable is stored outside the public Git repository.

The tool will be introduced to the endpoint only when E002 acquisition begins.

Any processes, drivers, temporary files, or other system changes caused by the acquisition utility will be treated as acquisition-induced artefacts and documented accordingly.

## Current Status

Memory-acquisition planning completed.

Dedicated E002 evidence storage has been created outside the public Git repository.

The memory-acquisition utility has been selected, staged, and hashed.

E002 has not yet been acquired.

LAB-WIN11-01 remains powered off.

## Current Status

E002 acquisition completed.

The memory image was acquired from the live post-reboot endpoint and preserved outside the public Git repository.

Guest-side and host-side SHA-256 values matched.

The evidence endpoint was subsequently shut down.

No forensic analysis of E002 has yet been performed.