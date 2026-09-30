### Sample log
I created a 22-line sample log containing INFO, WARNING, ERROR, and FAILED LOGIN entries.

### Failed-login result

Command used:

```bash
grep -c "FAILED LOGIN" sample.log


## Targets

I created three fictional training hosts:

- web-lab: Fictional training host used for web application testing.
- linux-lab: Fictional Linux host used for practicing Linux administration and security testing.
- windows-lab: Fictional Windows host used for practicing Windows security assessment.

##Sample Log and Text Searching

I created a 22-line sample log containing INFO, WARNING, ERROR, and FAILED LOGIN entries.

### Failed-login result

There are **4 failed-login lines** in the sample log.

### ERROR result

The lines containing ERROR are:

- ERROR Database connection timeout
- ERROR Failed to connect to database
- ERROR Application service stopped unexpectedly

The filtered ERROR output was saved in `evidence/errors.txt`.

## File Permissions

I created `secret-demo.txt` and inspected its permissions before changing them.

The file permissions were changed to `600` using `chmod 600`.

The final permission setting allows the owner to read and write the file, while the group and all other users have no permissions.

The three digits in `600` represent:
- 6: owner can read and write (4 + 2)
- 0: group has no permissions
- 0: others have no permissions


##Process Identification

I used `ps aux` to view running processes.

One recognized process was:

- PID: 1
- User: codespace
- Command: /sbin/docker-init -- /bin/sh

PID 1 is the first process running in the container and is associated with the container initialization process.

## Listening Sockets

Two listening sockets identified were:
- TCP 0.0.0.0:2000: This service is listening on port 2000 on all IPv4 network interfaces.
- TCP 127.0.0.1:40689: This service is listening on port 40689 but is accessible only from the local machine.

The `LISTEN` state means the TCP socket is waiting for incoming connections.

## HTTP Headers with curl

I used `curl` to request `https://example.com` and saved the response headers as evidence.

The server returned HTTP/2 200, indicating a successful response.

The headers showed:
- Content-Type: text/html; charset=utf-8
- Server: cloudflare
- Allow: GET, HEAD
- Accept-Ranges: bytes

The response headers were saved in `evidence/example-headers.txt`.

##System Snapshot Script

I created a Bash script named `system_snapshot.sh`.

The script records:
- Current user
- Hostname
- Current date
- IP addresses
- Routing table

I made the script executable and ran it successfully.

The output was saved to `evidence/snapshot.txt`.

The snapshot showed the active network interface as `eth0` with IP address `10.0.5.217` and a default gateway of `10.0.0.1`.

## Linux Commands Reflection

Five Linux commands I find useful during penetration testing are `ip addr`, `ip route`, `ss -tuln`, `ps aux`, and `grep`.

`ip addr` is useful for identifying network interfaces and IP addresses on a system. `ip route` helps identify the routing table and default gateway, which is important for understanding how network traffic is directed.

`ss -tuln` is useful for identifying listening network ports and services. This can help a tester understand which services may be exposed on a system.

`ps aux` shows running processes, which can help identify applications and services currently running.

`grep` is useful for searching through command output and log files for specific information such as errors, warnings, or failed login attempts.

Together, these commands provide useful information about the system, network configuration, running processes, and logs without requiring complex tools.