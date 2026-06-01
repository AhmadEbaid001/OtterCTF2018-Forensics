# MITRE ATT&CK Mapping — OtterCTF 2018

| ID | Tactic | Technique | Evidence |
|----|--------|-----------|---------|
| T1189 | Initial Access | Drive-by Compromise | ThePirateBay torrent download |
| T1204.002 | Execution | User Execution: Malicious File | Dropper executed 7x (UserAssist count=7) |
| T1036.005 | Defense Evasion | Masquerading | vmware-tray.exe mimics VMware utility |
| T1027 | Defense Evasion | Obfuscated Files | RAR-SFX dropper, ZoneId=3 |
| T1055 | Privilege Escalation | Process Injection | 4 RWX regions in PID 3720 (malfind) |
| T1055.002 | Privilege Escalation | Reflective DLL Loading | mscorrc.dll False/False/False (ldrmodules) |
| T1003.001 | Credential Access | LSASS Memory | Rick NTLM hash extracted and cracked |
| T1071 | Command and Control | Application Layer Protocol | TCP to 77.102.199.102:7575 |
| T1486 | Impact | Data Encrypted for Impact | AES encryption, .WINDOWS extension |
| T1547.001 | Persistence | Registry Run Keys | NOT PRESENT - confirmed absent |
