# Meow – HTB Starting Point

## Machine Information

| Property | Details |
|---|---|
| Platform | Hack The Box |
| Machine | Meow |
| Difficulty | Tier 0 |
| Operating System | Linux |
| Main Service | Telnet |
| Port | 23/TCP |
| Status | Completed |

## 1. Objective

The objective of this lab was to practice basic network enumeration, identify an exposed remote access service, and understand Linux user privileges.

## 2. Tools Used

- Kali Linux
- Nmap
- Telnet

## 3. Enumeration

Started with an Nmap scan to identify open ports and running services.

**Command:**

```bash
nmap -sC -sV 10.129.121.180
```

**Findings:**

| Port | State | Service | Version |
|---|---|---|---|
| 23/TCP | Open | Telnet | Linux telnetd |

Only one open TCP port was identified in the default Nmap scan.

## 4. Service Analysis

**Telnet – Port 23**

Telnet is a remote access protocol that allows users to interact with a remote system through a command-line interface.

Security considerations:

- Telnet does not encrypt communication.
- Credentials may be transmitted in plaintext.
- Exposing Telnet to untrusted networks creates security risks.

## 5. Access and Privilege Verification

A Telnet connection was successfully established.

The lab demonstrated a serious authentication misconfiguration that allowed privileged access to the Linux system.

After access was obtained, the following commands were used to inspect the system:

**Identify the current user:**

```bash
whoami
```

**Check user and group privileges:**

```bash
id
```

**Display the current working directory:**

```bash
pwd
```

**List files, including hidden files:**

```bash
ls -la /root
```

**Read a text file:**

```bash
cat filename
```

## 6. Key Findings

- TCP port 23 was exposed.
- Telnet was running on the target.
- Authentication was improperly configured.
- Privileged root access was obtained.
- The system was running Ubuntu 20.04.2 LTS.

## 7. SOC Perspective

From a defensive security perspective, the following activities should be investigated:

- Unexpected Telnet connections.
- Remote login attempts involving privileged accounts.
- Successful root logins from unusual source addresses.
- Suspicious commands executed after authentication.
- Unexpected access to sensitive directories.

**Relevant Linux log sources:**

- `/var/log/auth.log` – Authentication and login events.
- `/var/log/syslog` – General system events.

## 8. Lessons Learned

Through this lab, I practiced:

- Basic Nmap scanning.
- Service and version identification.
- Telnet connectivity.
- Linux command-line navigation.
- User and privilege verification.
- Identifying authentication misconfigurations.
- Understanding the security risks of unencrypted remote access.

## 9. Security Recommendations

- Disable Telnet when it is not required.
- Use SSH for encrypted remote administration.
- Enforce strong authentication.
- Prevent direct remote root login.
- Monitor authentication logs.
- Investigate unusual privileged access.

---

**Lab completed – HTB Starting Point: Meow**

*Documented as part of my hands-on cybersecurity learning journey.*
