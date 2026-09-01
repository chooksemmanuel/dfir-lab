# DFIR Lab Scope and Rules

## Purpose

This lab exists for controlled digital-forensics learning, experimentation, documentation, and portfolio development.

## Scope

The first investigation focuses on forensic analysis of a controlled Windows endpoint.

Potential areas of analysis include:

- Disk forensics
- Memory forensics
- Filesystem analysis
- Browser artefacts
- Windows artefacts
- Removable-storage artefacts
- Process analysis
- Timeline analysis
- Network analysis
- Forensic reporting

## Safety Boundaries

The lab will not intentionally use:

- Real malware
- Ransomware
- Stolen credentials
- Personal or confidential victim data
- Unauthorised systems
- Third-party targets

All user documents and activity generated for the case will be synthetic.

Any suspicious-looking behaviour will be intentionally created inside the controlled lab environment.

## Evidence Handling Principles

The project will attempt to follow these principles:

1. Preserve original evidence where practical.
2. Analyse working copies instead of altering original evidence.
3. Calculate and record cryptographic hashes.
4. Record evidence provenance.
5. Document tools and versions.
6. Maintain investigation notes.
7. Distinguish observations from interpretations.
8. Record uncertainty and limitations.
9. Avoid conclusions that are not supported by evidence.
10. Keep raw forensic evidence outside the public GitHub repository.

## Documentation Rule

The repository will describe what was actually completed.

Planned functionality will not be represented as completed functionality.