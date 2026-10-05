# Day 8 Linux Privilege Escalation Foundations

## Scope
Authorized training environment: GitHub Codespaces Linux container.

## Manual Enumeration

### Identity
- `whoami`: codespace
- `id`: UID/GID 1000, user `codespace`
- Groups included several development/container-related groups.

### Operating System
- Ubuntu 24.04.5 LTS
- Kernel: Linux 6.8.0-1064-azure

### Sudo Permissions
`sudo -l` showed:

`(root) NOPASSWD: ALL`

This is a significant privilege-escalation area because the `codespace` user is permitted to execute commands as root without entering a password.

### Processes
`ps aux` showed container, SSH, Docker/containerd and VS Code/Codespaces-related processes.

### Listening Services
`ss -tuln` showed multiple listening TCP services, including ports 2000 and 2222 and several localhost services.

### SUID Files
SUID enumeration identified standard privileged binaries including:
- `/usr/bin/passwd`
- `/usr/bin/chsh`
- `/usr/bin/mount`
- `/usr/bin/su`
- `/usr/bin/sudo`

No custom suspicious SUID binary was identified during this check.

### Cron
`/etc/cron.d` contained `e2scrub_all`, owned by root and not writable by the `codespace` user.

### System Timers
`systemctl list-timers --all` could not enumerate timers because systemd is not running in the Codespaces container.

## Three Potential Escalation Areas

1. **Sudo configuration:** `(root) NOPASSWD: ALL` is a direct privilege-escalation risk.
2. **SUID binaries:** privileged executables should be reviewed for unsafe configuration or vulnerable versions.
3. **Listening services:** locally and externally listening services should be identified and checked for unnecessary exposure or misconfiguration.

## Validation
The sudo configuration was identified as the strongest potential escalation path. The environment did not display a `root` result when `sudo whoami` was run, so no additional successful escalation claim is made.

## Mock Finding

### Finding
Overly permissive sudo configuration.

### Impact
A user with access to the `codespace` account may be able to execute privileged commands as root, potentially bypassing normal privilege boundaries.

### Remediation
Restrict sudo permissions to only the commands required for the user's role. Avoid broad `NOPASSWD: ALL` rules and apply least privilege.

## Why Least Privilege Reduces Security Risk

Least privilege means giving users, processes and services only the permissions they need to perform their intended tasks. This reduces the damage that can occur when an account, application or process is compromised. If a low-privileged account is compromised, an attacker has fewer opportunities to access sensitive files, change system settings or execute privileged commands.

Excessive permissions also increase the chance that a simple configuration mistake becomes a serious security issue. For example, allowing a normal user to run arbitrary commands as root removes an important security boundary. Restricting sudo access to specific administrative commands limits what can be done even if the account is compromised.

Least privilege should also apply to services and scheduled tasks. A service that does not need administrator privileges should not run as root, and scheduled jobs should not execute files that ordinary users can modify. Regular reviews of permissions, groups, sudo rules and service accounts help keep privileges aligned with actual requirements.

In practice, least privilege does not prevent every vulnerability, but it limits the blast radius when something goes wrong. It is therefore an important defensive control alongside secure configuration, patching, authentication and monitoring.
