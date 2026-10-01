## HTTP Request Documentation

### Request 1
- Request URL: https://0a75087047788f080ddf33c00f80075.web-security-academy.net/
- Request Method: GET
- Status Code: 200 OK
- Content-Type: text/html; charset=utf-8
- Content-Encoding: gzip
- X-Frame-Options: SAMEORIGIN
- Path: /
- Scheme: HTTPS
- Parameters: None observed
- Cookies: None observed in the displayed request details

The request retrieved the main HTML page of the authorized PortSwigger training lab.


## HTTP Request Documentation

### Request 1

- Request URL: https://0a75087047788f080ddf33c00f80075.web-security-academy.net/
- Request Method: GET
- Status Code: 200 OK
- Content-Type: text/html; charset=utf-8
- Content-Encoding: gzip
- X-Frame-Options: SAMEORIGIN
- Path: /
- Scheme: HTTPS
- Parameters: None observed
- Cookie: A session cookie was present in the request headers.

The request retrieved the main HTML page of the authorized PortSwigger training lab.

The lab repeatedly generated the same main document request during this exercise. I inspected its request and response headers, including the HTTP method, status code, content type, security header, and session cookie.

### Observation

The request showed that the application uses HTTPS and returns a successful 200 OK response. The response also included the X-Frame-Options header with a value of SAMEORIGIN. A session cookie was present in the request headers.

## Burp Suite Community

I used Burp Suite Community Edition to inspect HTTP traffic from the authorized PortSwigger Web Security Academy training lab.

Burp Proxy successfully intercepted a GET request to the lab.

I then opened the request in Burp Repeater and modified one harmless, non-sensitive value by adding the query parameter `test=day5`.

Original request:

GET /

Modified request:

GET /?test=day5

The modification was performed only within the authorized PortSwigger training environment.

