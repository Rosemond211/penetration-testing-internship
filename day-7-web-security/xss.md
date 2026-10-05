# XSS Lab

## Lab
Reflected XSS into HTML context with nothing encoded

## Test
Search input:

<script>alert(1)</script>

## Result
The JavaScript payload executed through the search functionality and the PortSwigger lab reported Solved.

## Vulnerable Behavior
The search input was reflected into the HTML response without being safely encoded.

## Impact
An attacker could execute JavaScript in another user's browser in the context of the vulnerable application.

## Prevention
Encode untrusted output according to its HTML context. Validate input where appropriate and use a strong Content Security Policy as an additional defense.
