# Windows-EventID-Book

## Event Log Categories

1. SECURITY (Security.evtx)
2. SYSMON (Sysmon Operational Log)
3. SYSTEM (System.evtx)
4. APPLICATION (Application.evtx)
5. FIREWALL (Windows Defender Firewall Logs)
6. POWERSHELL
7. KERBEROS / AUTHENTICATION (AD DS Logs)
8. REMOTE DESKTOP SERVICES (RDP Logs)
9. FILE SHARE / SMB ACTIVITY
10. REGISTRY AUDITING
11. TASK SCHEDULER
12. WINDOWS DEFENDER / ANTIVIRUS
13. EVENT LOG SERVICE (AUDIT SYSTEM)

---

## 1. SECURITY (Security.evtx)

| Event ID | Name                              | Description                                    | Threat Hunting Value                                         |
| -------- | --------------------------------- | ---------------------------------------------- | ------------------------------------------------------------ |
| 4624     | Successful Logon                  | A user successfully logged into the system     | Detect lateral movement, unusual logins, brute-force success |
| 4625     | Failed Logon                      | A logon attempt failed                         | Brute force, password spraying, credential stuffing          |
| 4634     | Logoff                            | User session ended                             | Session tracking, unusual session duration                   |
| 4648     | Logon with Explicit Credentials   | A process used different credentials to log in | Pass-the-hash, lateral movement detection                    |
| 4672     | Special Privileges Assigned       | Admin-level privileges granted at logon        | Privilege escalation detection                               |
| 4688     | Process Creation                  | A new process was created                      | Malware execution, LOLBins detection                         |
| 4689     | Process Exit                      | A process terminated                           | Execution flow tracking                                      |
| 4697     | Service Installed                 | A new service was installed                    | Persistence via services                                     |
| 4719     | Audit Policy Changed              | Audit policy was modified                      | Defense evasion (log disabling)                              |
| 4720     | User Account Created              | A new user account was created                 | Unauthorized account creation                                |
| 4722     | User Account Enabled              | Disabled account was enabled                   | Account takeover, insider threat                             |
| 4723     | Password Change Attempt           | User attempted password change                 | Credential abuse detection                                   |
| 4724     | Password Reset Attempt            | Password reset performed                       | Privilege abuse or account takeover                          |
| 4725     | User Account Disabled             | Account was disabled                           | Attack cleanup or insider activity                           |
| 4726     | User Account Deleted              | Account removed from system                    | Persistence removal or sabotage                              |
| 4732     | Added to Local Group              | User added to privileged group                 | Privilege escalation                                         |
| 4738     | User Account Modified             | Account properties changed                     | Persistence or privilege manipulation                        |
| 4740     | Account Locked Out                | Account locked due to failed attempts          | Brute-force detection                                        |
| 4768     | Kerberos TGT Requested            | Ticket Granting Ticket requested               | Authentication analysis, lateral movement                    |
| 4769     | Kerberos Service Ticket Requested | Service ticket requested                       | Lateral movement, access tracking                            |
| 4776     | NTLM Authentication               | NTLM authentication attempt                    | Legacy auth abuse, pass-the-hash                             |
| 1102     | Audit Log Cleared                 | Security logs were cleared                     | Log tampering / defense evasion                              |

---

## 2. SYSMON (Sysmon Operational Log)

| Event ID | Name                         | Description                          | Threat Hunting Value                                    |
| -------- | ---------------------------- | ------------------------------------ | ------------------------------------------------------- |
| 1        | Process Creation             | A new process was created            | Detect malware execution, LOLBins, command-line attacks |
| 2        | File Creation Time Changed   | File timestamp modified              | Timestomping (evasion technique)                        |
| 3        | Network Connection           | Process initiated network connection | C2 traffic, data exfiltration, suspicious IPs           |
| 4        | Sysmon Service State Change  | Sysmon service started/stopped       | Detection evasion (sensor disable attempts)             |
| 5        | Process Terminated           | A process ended                      | Track execution lifecycle                               |
| 6        | Driver Loaded                | Kernel driver loaded                 | Rootkits, malicious drivers                             |
| 7        | Image Loaded (DLL)           | DLL loaded into process              | DLL injection, sideloading attacks                      |
| 8        | CreateRemoteThread           | Thread created in another process    | Process injection (classic malware behavior)            |
| 9        | Raw Access Read              | Direct disk read access              | Credential dumping, LSASS access                        |
| 10       | Process Access               | One process accessed another         | Credential theft, LSASS injection                       |
| 11       | File Created                 | File created on system               | Malware dropper activity                                |
| 12       | Registry Key Created/Deleted | Registry structure modified          | Persistence mechanisms                                  |
| 13       | Registry Value Set           | Registry value modified              | Startup persistence, malware config                     |
| 14       | Registry Key/Value Renamed   | Registry object renamed              | Evasion and persistence hiding                          |
| 15       | File Stream Created          | Alternate Data Stream (ADS) created  | Hidden payloads in NTFS ADS                             |
| 17       | Pipe Created                 | Named pipe created                   | C2 communication, lateral movement                      |
| 18       | Pipe Connected               | Named pipe accessed                  | Inter-process or lateral communication                  |
| 19       | WMI Event Filter             | WMI persistence created              | Advanced persistence technique                          |
| 20       | WMI Consumer                 | WMI event consumer created           | Execution persistence via WMI                           |
| 21       | WMI Binding                  | WMI filter-consumer binding          | Full WMI persistence chain                              |
| 22       | DNS Query                    | DNS request made by process          | Domain-based C2 detection, DGA malware                  |

---
