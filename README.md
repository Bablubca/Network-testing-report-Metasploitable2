# Network Testing Report – Metasploitable2

## Project Overview

This project demonstrates a network security assessment conducted on the Metasploitable2 vulnerable virtual machine. The objective was to identify open ports, enumerate services, discover vulnerabilities, and understand the security weaknesses present in a deliberately insecure system.

## Objectives

* Perform network reconnaissance.
* Identify open ports and running services.
* Enumerate service versions.
* Detect potential vulnerabilities.
* Document findings and security recommendations.

## Target Environment

| Component        | Details                            |
| ---------------- | ---------------------------------- |
| Attacker Machine | Kali Linux                         |
| Target Machine   | Metasploitable2                    |
| Network Type     | Host-Only / NAT                    |
| Tools Used       | Nmap, Netcat, Metasploit Framework |

## Methodology

### 1. Host Discovery

Verified connectivity between Kali Linux and Metasploitable2 using:

```bash
ping <target-ip>
```

### 2. Port Scanning

Performed TCP port scanning using Nmap:

```bash
nmap -sV -sC <target-ip>
```

### 3. Service Enumeration

Enumerated running services and versions:

```bash
nmap -A <target-ip>
```

### 4. Vulnerability Identification

Analyzed exposed services for known vulnerabilities.

## Scan Results

| Port | Service | Version              |
| ---- | ------- | -------------------- |
| 21   | FTP     | vsftpd 2.3.4         |
| 22   | SSH     | OpenSSH 4.7p1        |
| 23   | Telnet  | Linux Telnet Service |
| 25   | SMTP    | Postfix SMTP         |
| 53   | DNS     | ISC BIND             |
| 80   | HTTP    | Apache Web Server    |
| 111  | RPC     | RPCbind              |
| 139  | NetBIOS | Samba                |
| 445  | SMB     | Samba 3.0.20         |
| 3306 | MySQL   | MySQL Database       |

## Vulnerabilities Identified

### VSFTPD 2.3.4 Backdoor

* Port: 21
* Severity: Critical
* Description:
  The VSFTPD 2.3.4 service contains a backdoor vulnerability that may allow unauthorized remote access.

### Samba 3.0.20

* Port: 445
* Severity: High
* Description:
  Vulnerable to remote command execution through known Samba exploits.

### Telnet Service Enabled

* Port: 23
* Severity: Medium
* Description:
  Telnet transmits credentials in plaintext, making it insecure.

### Weak Web Services

* Port: 80
* Severity: Medium
* Description:
  Multiple vulnerable web applications may be exposed.

## Sample Nmap Output

```bash
nmap -sV -A 192.168.x.x
```

Key findings:

* Multiple outdated services detected.
* Insecure protocols enabled.
* Known vulnerable software versions present.

## Security Recommendations

1. Disable Telnet and use SSH.
2. Upgrade outdated software versions.
3. Restrict unnecessary services.
4. Apply latest security patches.
5. Implement firewall rules.
6. Conduct regular vulnerability assessments.

## Learning Outcomes

* Network reconnaissance using Nmap.
* Service enumeration techniques.
* Vulnerability identification.
* Security reporting and documentation.
* Understanding real-world attack surfaces.

## Disclaimer

This project was conducted in a controlled lab environment using Metasploitable2 for educational and ethical cybersecurity learning purposes only.

## Author

Bablu

Cybersecurity Enthusiast | Vulnerability Assessment & Penetration Testing Learner
