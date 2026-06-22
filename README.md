# WhatsApp Desktop Forensics

A PowerShell-based forensic toolkit for discovering, validating, and recovering WhatsApp Desktop artifacts from Windows systems, logical images, mounted E01 evidence files, and virtual machine disk images.

## Overview

WhatsApp Desktop investigations often require analysts to manually locate artifacts, identify session data, validate DPAPI material, recover databases, and verify decrypted output.

This project aims to automate that workflow and provide a repeatable process for artifact discovery, validation, and analysis.

## Motivation

This project was created after encountering multiple WhatsApp Desktop investigations that required significant manual effort to:

- Locate WhatsApp Desktop artifacts
- Identify session information
- Validate DPAPI-related files
- Verify recovered databases
- Determine whether database decryption was successful

The goal is to reduce repetitive analyst effort and provide a repeatable workflow for future examinations.

## Features

### Current Features

- WhatsApp Desktop artifact discovery
- Session identification
- Database inventory
- SQLite database validation
- Artifact reporting

### Planned Features

- DPAPI recovery validation
- WhatsApp database decryption workflow
- Chat reconstruction
- HTML reporting
- Mounted E01 support
- VDI/VMDK/VHDX support
- Timeline generation

## Supported Evidence Sources

| Source | Status |
|----------|----------|
| Live Windows System | ✅ |
| Extracted Artifact Folder | ✅ |
| Logical Image | ✅ |
| Mounted E01 | 🚧 Planned |
| VHD/VHDX | 🚧 Planned |
| VDI | 🚧 Planned |
| VMDK | 🚧 Planned |

## Supported WhatsApp Artifacts

The tool currently targets:

```text
LocalState\
sessions\
IndexedDB\
LevelDB\
session.db
genericStorage.db
contacts.db
```

Additional support is planned for:

```text
Microsoft\Protect
Microsoft\Credentials
Microsoft\Vault
```

## Example Usage

### Analyze an Extracted Artifact Folder

```powershell
.\WhatsAppDesktop-Forensics.ps1 `
    -Source "D:\Evidence\WhatsAppDesktop" `
    -Output ".\Case001"
```

### Analyze a Mounted Drive

```powershell
.\WhatsAppDesktop-Forensics.ps1 `
    -Source "E:\" `
    -Output ".\Case001"
```

## Example Output

```text
Case001\
├── Artifacts.csv
├── Sessions.csv
├── Findings.json
├── Report.html
└── Logs\
```

## Development Status

This project is currently under active development and is intended for:

- Digital Forensics
- Incident Response
- Research
- Educational Purposes

## Test Environment

Current testing has been performed against:

- Windows 10
- Windows 11
- WhatsApp Desktop (Microsoft Store Version)
- Logical Forensic Images
- VirtualBox Virtual Machines
- Mounted Evidence

## Roadmap

- [ ] Automatic WhatsApp artifact discovery
- [ ] Session validation
- [ ] DPAPI validation
- [ ] Database decryption verification
- [ ] Chat reconstruction
- [ ] Timeline generation
- [ ] HTML reporting
- [ ] Multi-user support
- [ ] Mounted E01 support
- [ ] Virtual disk support (VDI/VMDK/VHDX)

## Disclaimer

This tool is intended for authorized forensic examinations, incident response, digital investigations, and research purposes only.

Users are responsible for ensuring they have proper authorization to access and analyze any evidence processed by this tool.

## License

MIT License