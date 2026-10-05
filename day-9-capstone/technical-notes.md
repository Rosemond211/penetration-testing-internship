# Day 9 Technical Notes

## Scope
Target: OWASP Juice Shop running locally in GitHub Codespaces.

Target URL:
http://127.0.0.1:3000

Restrictions:
- Testing was limited to the locally running Juice Shop container.
- No external or unauthorized systems were tested.
- No real credentials or sensitive company information were used.

## Reconnaissance and Enumeration

### Application Availability
The Juice Shop application responded successfully on port 3000.

### Product API
The product search API responded to:

GET /rest/products/search?q=apple

The response returned product information in JSON format.

### FTP Directory
Request:

GET /ftp

Result:
The application returned a directory listing containing multiple files.

One exposed file was:

/ftp/acquisitions.md

The file contained confidential acquisition-related information.

### Administrative Configuration Endpoint
Request:

GET /rest/admin/application-configuration

Result:
HTTP 200 OK without authentication.

The response contained extensive application configuration and data.

### HTTP Security Headers
The application response included:

Access-Control-Allow-Origin: *

This represents a permissive CORS configuration and was recorded as a security observation.

### SQL Injection Test
A basic SQL injection test against the product search endpoint did not provide sufficient evidence of SQL injection and was therefore rejected as a finding.

### Login Injection Test
A login injection test did not produce useful evidence and was not reported as a finding.

## Findings
1. Sensitive files exposed through the FTP directory.
2. Unauthenticated administrative application configuration endpoint.
3. Permissive CORS configuration security observation.

## Testing Principle
Findings were only recorded when there was observable evidence. Unsuccessful tests were documented rather than reported as vulnerabilities.
