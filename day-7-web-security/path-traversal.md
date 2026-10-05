# Path Traversal Lab

## Lab
File path traversal, simple case

## Normal Request
GET /image?filename=68.jpg

## Test
The `filename` parameter was changed to:

../../../etc/passwd

## Result
The application accepted the path traversal input and the PortSwigger lab reported Solved.

## Vulnerable Behavior
The application used a user-controlled filename to access a file without properly preventing directory traversal sequences.

## Impact
An attacker could potentially access files outside the intended application directory.

## Prevention
Validate and restrict file paths on the server. Use allowlists for permitted files and resolve paths safely before accessing them. Avoid directly using user-controlled input as a filesystem path.
