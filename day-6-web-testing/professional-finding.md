# Professional Security Finding

## Title
Unprotected Administrative Functionality

## Affected Asset
Authorized PortSwigger Web Security Academy training application.

## Description
The application exposed administrative functionality without enforcing the expected authorization controls. An unauthorized user could reach the administrative functionality through a discoverable application path.

## Evidence
The administrative path was identified through the application's robots.txt file. Accessing the disclosed path exposed the administrative functionality within the authorized training environment.

## Reproduction
1. Open the authorized PortSwigger training application.
2. Request `/robots.txt`.
3. Review the paths listed in the response.
4. Identify the administrative path disclosed by the application.
5. Navigate to the disclosed administrative path.
6. Observe that the administrative functionality is accessible.

## Impact
If the same weakness existed in a real application, an unauthorized user could potentially access administrative functionality and perform actions intended only for authorized administrators.

## Remediation
Restrict administrative endpoints using server-side authorization checks. Do not rely on obscurity or robots.txt restrictions to protect sensitive functionality. Verify that every administrative action checks whether the current user has the required privileges.

## References
- PortSwigger Web Security Academy - Access Control
- OWASP Web Security Testing Guide
