# HTB Starting Point — Fawn

![Status](https://img.shields.io/badge/Status-PWNED-brightgreen?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-Hack%20The%20Box-green?style=for-the-badge)
![Difficulty](https://img.shields.io/badge/Difficulty-Tier%200-blue?style=for-the-badge)
![OS](https://img.shields.io/badge/OS-UNIX-lightgrey?style=for-the-badge)

## Machine Information

| Detail | Information |
|---|---|
| Platform | Hack The Box |
| Machine | Fawn |
| Difficulty | Tier 0 |
| Operating System | UNIX |
| Main Service | FTP |
| Port | 21/TCP |
| FTP Server | vsftpd 3.0.3 |
| Status | Pwned |

## Objective

Explore an FTP service, identify anonymous access, and retrieve an accessible file from the server.

## Tools Used

- Kali Linux
- Nmap
- FTP client

## Enumeration

Command:

```bash
nmap -sC -sV TARGET_IP
```

Findings:

- Port 21/TCP was open.
- FTP service: vsftpd 3.0.3.
- Anonymous FTP login was allowed.
- FTP control and data connections were unencrypted.
- The server reported a UNIX system type.

## FTP Access

Connect to the FTP server:

```bash
ftp TARGET_IP
```

Username:

```text
anonymous
```

The server returned:

```text
230 Login successful.
```

This confirmed successful anonymous authentication.

## FTP Commands Practiced

| Command | Purpose |
|---|---|
| `ftp -?` | Display FTP client help |
| `ls` | List files |
| `dir` | List files and directories |
| `get filename` | Download a file |
| `exit` | Close FTP session |

## Key Findings

- Anonymous authentication was enabled.
- Files were accessible without a registered account.
- FTP transmitted data without encryption.

## SOC Analyst Perspective

Security monitoring should focus on:

- Unexpected FTP connections.
- Anonymous FTP authentication.
- Unusual file downloads.
- Access to exposed or sensitive files.

## Security Recommendations

- Disable anonymous FTP access unless explicitly required.
- Use SFTP or another secure file transfer solution.
- Restrict FTP access through firewall rules.
- Monitor authentication events and file transfers.

## Completion Proof

![Fawn Pwned Screenshot](./images/fawn-pwned.png)

## Lessons Learned

- Identified FTP on TCP port 21.
- Performed service enumeration using Nmap.
- Practiced anonymous FTP authentication.
- Listed and downloaded files using FTP commands.
- Identified the security risks of unencrypted FTP.

