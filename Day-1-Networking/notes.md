## Question 2: Identify the Active Network Interface and IP

**Command used:**
`ip addr`

**Active network interface:** `eth0`
**IP address:** `10.0.4.205`

The `eth0` interface is the active network interface because it is shown as UP and has an IPv4 address assigned to it. The IPv4 address is `10.0.4.205`. The `lo` interface with `127.0.0.1` is the loopback interface and is used for communication within the local system.



## Question 3: Default Route and Gateway

**Command used:**
`ip route`

**Default route:** `default via 10.0.0.1`
**Default gateway:** `10.0.0.1`
**Network interface:** `eth0`

The default gateway is the device that the computer sends traffic to when the destination is not on the local network. In this environment, the default gateway is `10.0.0.1`, and traffic is sent through the `eth0` interface.

## Question 4: Listening Ports

**Command used:**
`ss -tuln`

### Entry 1
- Protocol: TCP
- Local address: 127.0.0.1
- Port: 41749
- State: LISTEN

The service is listening for TCP connections on port 41749. The 127.0.0.1 address means it is only accessible from the local machine.

### Entry 2
- Protocol: TCP
- Local address: 0.0.0.0
- Port: 2000
- State: LISTEN

The service is listening for TCP connections on port 2000. The 0.0.0.0 address means it is listening on all available IPv4 network interfaces.

### Entry 3
- Protocol: TCP
- Local address: 127.0.0.1
- Port: 13005
- State: LISTEN

The service is listening for TCP connections on port 13005. The 127.0.0.1 address means it is only accessible from the local machine.

## Question 5: DNS Lookup

**Command used:**
`nslookup example.com`

**DNS server:**
`127.0.0.53`

**IP address returned:**
`104.20.23.154`

**Another IPv4 address returned:**
`172.66.147.243`


DNS translates domain names such as `example.com` into IP addresses that computers can use to locate the destination on a network.


## Question 6: HTTP Headers

**Command used:**
`curl -I https://example.com`

**HTTP Status:**
`HTTP/2 200`

The 200 status indicates that the request was successful.

### Header 1: Content-Type
`content-type: text/html; charset=utf-8`

This indicates that the response contains HTML content and uses UTF-8 character encoding.

### Header 2: Server
`server: cloudflare`

This identifies the server or service handling the request. In this response, it identifies Cloudflare.

### Header 3: Last-Modified
`last-modified: Mon, 28 Sep 2026 16:19:23 GMT`

This indicates when the resource was last modified according to the server.


## Question 7: TCP vs UDP

TCP creates a connection between two devices before data is sent and focuses on making sure the data arrives reliably and in the correct order. UDP does not establish the same type of connection and has less overhead.

For example, TCP can be used when downloading a file because the complete and correct data is important. UDP can be useful for applications where speed is more important and some lost packets can be tolerated.


## Question 8: Why Networking Knowledge Matters in Penetration Testing

Networking knowledge is important in penetration testing because a tester needs to understand how devices communicate before looking for security weaknesses. Knowing about IP addresses helps identify hosts, while understanding ports makes it easier to identify the services running on those hosts. Protocols such as TCP and UDP also help a tester understand how information is being transferred.

DNS is another important part because it connects domain names to IP addresses. Understanding HTTP and HTTPS is especially useful when testing web applications because it helps the tester understand requests, responses and the information being exchanged between a client and a server.

Routing and firewalls are also important because a service may be running on a system but still be inaccessible because network traffic is being filtered. This means that seeing an open or closed port needs to be understood in the context of the network.

Overall, networking knowledge gives a penetration tester a clear picture of the systems and services they are assessing. It helps them interpret scan results correctly instead of simply running tools and accepting whatever output they produce.