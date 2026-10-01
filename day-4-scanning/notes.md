# Day 4 - Nmap Scanning & Service Discovery

## Target

127.0.0.1

## Authorization / Scope

The target is the local Codespace environment used for this training exercise. Testing is limited to this authorized local environment. No external systems are being scanned.

## Start Time

2026-10-01

## Objective

The objective is to use Nmap to identify open TCP ports and the services running on the authorized local training environment.

## Task 2: Nmap Scanning

### Basic Scan

Command used:

```bash
nmap 127.0.0.1


```markdown
## Service Analysis
### Port 2000/tcp

**What I know:**
- The port is open.
- The service is SSH.
- The detected version is OpenSSH 8.9p1 Ubuntu 3ubuntu0.17.
- The operating system was identified as Linux.

**What I still need to know:**
- What SSH configuration is being used.
- Which authentication methods are enabled.
- Whether the service has any relevant security weaknesses.

**Next safe enumeration step:**
- Review the SSH service configuration and authorized authentication methods within the local training environment.

### Port 2222/tcp

**What I know:**
- The port is open.
- The service is SSH.
- The detected version is OpenSSH 9.6p1 Ubuntu 3ubuntu13.19.
- The operating system was identified as Linux.

**What I still need to know:**
- What SSH configuration is being used.
- Which authentication methods are enabled.
- Whether the service has any relevant security weaknesses.

**Next safe enumeration step:**
- Review the SSH service configuration and authorized authentication methods within the local training environment.


##Why an Open Port Is Not Automatically a Vulnerability

An open port is not automatically a vulnerability because a port simply indicates that a service is listening and available for network communication. Many legitimate applications and system services require open ports to function correctly. Therefore, discovering an open port is only an observation about the target's attack surface and is not proof that the service is insecure.

During a penetration test, the tester needs to identify the service running on the open port and gather more information about it. Service and version detection can help determine what software is being used and which version is installed. However, even identifying a specific software version does not automatically prove that the system is vulnerable.

Other factors must also be considered, including the service configuration, authentication requirements, exposed functionality, security controls and whether a relevant weakness actually exists. A service may be running on an open port but still be properly configured and secured.

For example, an SSH service listening on TCP port 22 or another port is not automatically a vulnerability. The tester would need to understand how the SSH service is configured, what authentication methods are enabled and whether there are relevant security weaknesses.

Nmap is therefore useful for discovering the attack surface and identifying services, but its output should not automatically be treated as a vulnerability report. The results should be investigated further and supported by evidence before a security finding is reported.

The main lesson is that an open port is a starting point for enumeration, not a confirmed vulnerability.