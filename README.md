# OtterCTF 2018 — Ransomware Memory Forensics Investigation

> A four-phase memory forensics investigation of a Windows 7 SP1 x64
> system compromised by a torrent-delivered ransomware payload.
> Conducted as part of ITNS 414 — Cyber Forensics coursework.

---

## Team

| Name | Role |
|------|------|
| Ahmed M. Ebaid | Lead · Kill chain · MITRE ATT&CK · Prevention |
| Omar A. Hamed | Vector analyst · Browser history · Network |
| Shady M. Afifi | Malware analyst · Injection · Credentials |

---

## Case Summary

| Item | Value |
|------|-------|
| Evidence file | OtterCTF.vmem (2.0 GB — publicly available) |
| Operating system | Windows 7 SP1 x64 (NT 6.1) |
| Hostname | WIN-LO6FAF3DTFE |
| Compromised user | Rick |
| Memory capture time | 2018-08-04 19:34:22 UTC |
| Time from execution to encryption | ~75 seconds |
| MITRE techniques mapped | 9 across 7 tactics |
| Evidence screenshots | 40 |
| Report pages | 67 |

---

## Key Findings

- **Dropper:** Rick And Morty season 1 download.exe
  SHA-256: 520161bec23819a713c2b467fe72f2378dc9a2808e176bc03f54cdbcf73f4b1d
  Detection: 1 of 71 on VirusTotal

- **Ransomware:** vmware-tray.exe (PID 3720)
  Type: .NET 32-bit, AES encryption, .WINDOWS extension

- **Injection:** 4 RWX shellcode regions and reflective DLL (mscorrc.dll)
  Hidden from all 3 Windows PEB tracking lists

- **C2 connection:** 77.102.199.102:7575 via LunarMS.exe

- **Credential exposure:** NTLM hash extracted from LSASS

- **Persistence:** None confirmed — smash-and-grab design

---

## MITRE ATT&CK Mapping

See [docs/mitre_mapping.md](docs/mitre_mapping.md) for full table.

| ID | Technique |
|----|-----------|
| T1189 | Drive-by Compromise |
| T1204.002 | User Execution: Malicious File |
| T1036.005 | Masquerading |
| T1027 | Obfuscated Files |
| T1055 | Process Injection |
| T1055.002 | Reflective DLL Loading |
| T1003.001 | LSASS Credential Dumping |
| T1071 | Application Layer Protocol |
| T1486 | Data Encrypted for Impact |

---

## Tools Used

| Tool | Version | Purpose |
|------|---------|---------|
| Volatility 2 | 2.6.1 | Primary memory analysis |
| Volatility 3 | 2.27.0 | Secondary verification |
| Hashcat | 7.1.2 | NTLM hash cracking |
| SQLite | 3.46.1 | Chrome history analysis |
| GNU strings | 2.46 | Memory string extraction |
| YARA | 4.5.5 | Pattern matching |

---

## Repository Structure

- report — 67-page LaTeX technical report PDF
- presentation — Professional HTML presentation
- screenshots — 40 evidence screenshots across all phases
- phase4 — Attack timeline and MITRE ATT&CK Navigator
- output — All Volatility command outputs and extracted artifacts
- docs — IOC list and MITRE mapping documents
- logs — Investigation command history

---

## Evidence Integrity

The original memory image is not included due to its 2 GB size.
It is publicly available from the OtterCTF 2018 CTF dataset.

Hash files are provided for integrity verification:
- OtterCTF.vmem.md5
- OtterCTF.vmem.sha256

---

*ITNS 414 — Cyber Forensics · 2026*
