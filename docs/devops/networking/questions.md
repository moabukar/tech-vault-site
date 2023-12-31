# Networking Questions

<details>
<summary>What is HTTP?</summary>

The Hypertext Transfer Protocol (HTTP) is the foundation of the World Wide Web, and is used to load webpages using hypertext links. HTTP is an application layer protocol designed to transfer information between networked devices and runs on top of other layers of the network protocol stack. A typical flow over HTTP involves a client machine making a request to a server, which then sends a response message.<br><br>

HTTPS is an extension of the Hypertext Transfer Protocol. The S in HTTPS stands for “secure.” When a website is encrypted with TLS (or SSL), it uses Hypertext Transfer Protocol Secure (HTTPS).<br><br>

Basically, it’s HTTP with encryption. It is used to secure communication over a computer network and is widely used on the Internet. HTTPS encrypts and decrypts user page requests and the pages returned by the web server.<br><br>

</details>
<br>

<details>
<summary>Difference between HTTP and HTTPS?</summary>

The most significant difference between the two protocols is that HTTPS is encrypted and secured using digital certificates, while HTML is not. When you visit a website using HTTPS, your connection to that site is encrypted. Any information you send or receive on that site is also encrypted.<br><br>

Another difference between the protocols is that HTTPS uses port 443, while HTML uses port 80. Port 443 is the standard port for secured Hypertext Transfer Protocol (HTTPS). Port 80 is the default port for unsecured Hypertext Transfer Protocol.<br><br>

</details>
<br>

<details>
<summary>How does a typical HTTP request look like?</summary>

An HTTP request is the way Internet communications platforms such as web browsers ask for the information they need to load a website.<br><br>

Each HTTP request made across the Internet carries with it a series of encoded data that carries different types of information. A typical HTTP request contains:<br><br>

1) HTTP version type<br><br>
2) a URL<br><br>
3) an HTTP method<br><br>
4) HTTP request headers<br><br>
5) Optional HTTP body<br><br>

</details>
<br>

<details>
<summary>What is an HTTP method?</summary>

An HTTP method, sometimes referred to as an HTTP verb, indicates the action that the HTTP request expects from the queried server. For example, two of the most common HTTP methods are ‘GET’ and ‘POST’; a ‘GET’ request expects information back in return (usually in the form of a website), while a ‘POST’ request typically indicates that the client is submitting information to the web server (such as form information, e.g. a submitted username and password).

</details>
<br>

<details>
<summary>What are HTTP request headers?</summary>

HTTP headers contain text information stored in key-value pairs, and they are included in every HTTP request. These headers communicate core information, such as what browser the client is using and what data is being requested.

</details>
<br>

<details>
<summary>What is in an HTTP request body?</summary>

The body of a request is the part that contains the ‘body’ of information the request is transferring. The body of an HTTP request contains any information being submitted to the web server, such as a username and password, or any other data entered into a form.

</details>
<br>

<details>
<summary>What is in an HTTP response?</summary>

An HTTP response is what web clients (often browsers) receive from an Internet server in answer to an HTTP request. These responses communicate valuable information based on what was asked for in the HTTP request.<br><br>

A typical HTTP response contains:<br><br>

1) An HTTP status code<br><br>
2) HTTP response headers<br><br>
3) Optional HTTP body<br><br>

</details>
<br>

<details>
<summary>What’s an HTTP status code?</summary>

HTTP status codes are 3-digit codes most often used to indicate whether an HTTP request has been successfully completed. Status codes are broken into the following 5 blocks:<br><br>

- 1xx Informational<br><br>
- 2xx Success<br><br>
- 3xx Redirection<br><br>
- 4xx Client Error<br><br>
- 5xx Server Error<br><br>

The “xx” refers to different numbers between 00 and 99.<br><br>

Status codes starting with the number ‘2’ indicate a success. For example, after a client requests a webpage, the most commonly seen responses have a status code of ‘200 OK’, indicating that the request was properly completed.<br><br>

If the response starts with a ‘4’ or a ‘5’ that means there was an error and the webpage will not be displayed. A status code that begins with a ‘4’ indicates a client-side error (it is very common to encounter a ‘404 NOT FOUND’ status code when making a typo in a URL). A status code beginning in ‘5’ means something went wrong on the server side. Status codes can also begin with a ‘1’ or a ‘3’, which indicate an informational response and a redirect, respectively.

</details>
<br>

<details>
<summary>What are HTTP response headers?</summary>

Much like an HTTP request, an HTTP response comes with headers that convey important information such as the language and format of the data being sent in the response body.

</details>
<br>

<details>
<summary>What is in an HTTP response body?</summary>

Successful HTTP responses to ‘GET’ requests generally have a body which contains the requested information. In most web requests, this is HTML data that a web browser will translate into a webpage.

</details>
<br>

<details>
<summary>TCP vs UDP</summary>

Protocols are rules that govern how data is formatted and sent over a network. TCP and UDP are two different methods for doing the same job: transferring data via the internet. They enable servers and devices to communicate so you can send emails, watch Youtube, play games, and browse web pages.<br><br>

The main difference between TCP (transmission control protocol) and UDP (user datagram protocol) is that TCP is a connection-based protocol and UDP is connectionless. While TCP is more reliable, it transfers data more slowly. UDP is less reliable but works more quickly. This makes each protocol suited to different types of data transfers.<br><br>

</details>
<br>

<details>
<summary>What is DNS?</summary>

The process of DNS resolution involves converting a hostname (such as www.google.com) into a computer-friendly IP address (such as 192.168.1.1). An IP address is given to each device on the Internet, and that address is necessary to find the appropriate Internet device - like a street address is used to find a particular home. When a user wants to load a webpage, a translation must occur between what a user types into their web browser (example.com) and the machine-friendly address necessary to locate the example.com webpage.

</details>
<br>

<details>
<summary>How does DNS work?</summary>


DNS (Domain Name System) works by translating human-friendly domain names (like www.example.com) into IP addresses (like 192.168.1.1) that computers use to identify each other on the internet. Here's a simplified step-by-step process:<br><br>

1. User enters a domain name in a web browser.<br><br>
2. The computer first checks its local DNS cache to see if it already knows the corresponding IP address.<br><br>
3. If not found, the computer sends a DNS query to a DNS resolver (usually provided by your internet service provider or a public DNS service like Google's 8.8.8.8).<br><br>
4. The DNS resolver searches its cache for the IP address. If not found, it starts a recursive process:<br><br>
  a. The resolver queries root DNS servers to find the authoritative DNS server for the top-level domain (like .com).<br><br>
  b. The resolver then queries the top-level domain's authoritative DNS server to find the authoritative server for the specific domain (like example.com).<br><br>
  c. Finally, the resolver queries the domain's authoritative server for the IP address of the requested domain (www.example.com).<br><br>
1. The authoritative DNS server responds with the IP address, and the resolver caches this information for future use.<br><br>
2. The resolver returns the IP address to the user's computer.<br><br>
3. The computer can now establish a connection with the web server at the provided IP address, allowing the user to access the website associated with the domain name.<br><br>

- In essence, DNS acts as the internet's phone book, translating user-friendly domain names into the numerical addresses computers need to communicate.

</details>
<br>

<details>
<summary>What is TLS?</summary>

TLS (Transport Layer Security) is a cryptographic protocol that provides secure communication over a computer network, such as the internet. It ensures data privacy and integrity by encrypting the data transmitted between two systems, typically a web browser and a web server. TLS is commonly used to secure online transactions, like credit card payments and sensitive data transfers, by establishing a secure, encrypted connection between the client and server. This encryption helps protect against eavesdropping and data tampering during transmission.

</details>
<br>

<details>
<summary>What are CIDR ranges?</summary>

CIDR (Classless Inter-Domain Routing) ranges are a way to represent and allocate IP addresses and subnets in a more flexible manner than traditional subnetting using classes (Class A, B, C, etc.). In CIDR notation, an IP address is followed by a slash ("/") and a number, which indicates the number of bits in the network portion of the address. Here's a simple example:<br><br>

IP Address: 192.168.1.0<br><br>
CIDR Notation: 192.168.1.0/24<br><br>
In this example, "/24" means that the first 24 bits of the IP address are used to identify the network, leaving 8 bits for host addresses. This allows for finer control over IP address allocation and subnetting compared to the older class-based system (e.g., Class A, B, C).<br><br>

CIDR notation is widely used in networking to specify IP address ranges, making it easier to manage and allocate IP addresses efficiently.

</details>
<br>

<details>
<summary>What is ingress and egress traffic?</summary>

In networking and security, "ingress" and "egress" refer to the movement of data or traffic into and out of a network, system, or device:<br><br>

**Ingress Traffic:** This is incoming traffic that enters a network or system. Ingress traffic typically originates from external sources, such as the internet, and flows into a network through a gateway, router, or firewall. Monitoring and controlling ingress traffic is important for security purposes to prevent unauthorized access or attacks.<br><br>

**Egress Traffic:** Egress traffic, on the other hand, is outgoing traffic that exits a network or system and goes towards external destinations. Egress traffic might include data leaving a corporate network to access a website, send emails, or communicate with cloud services. Managing egress traffic is essential for monitoring data leaving a network and enforcing policies related to data transmission.<br><br>

In summary, ingress traffic comes into a network, while egress traffic goes out of it. Network administrators often use firewall rules and security measures to control and secure both ingress and egress traffic to protect the network from threats and ensure proper data flow.

</details>
<br>

<details>
<summary>What is a switch vs a hub?</summary>

A switch and a hub are both networking devices used to connect multiple devices in a local area network (LAN), but they operate in fundamentally different ways:<br><br>

**Switch:**<br><br>

A switch operates at the data link layer (Layer 2) of the OSI model.<br><br>

It is an intelligent device that examines the MAC (Media Access Control) addresses of data packets to determine where to forward them.
Switches create a dedicated, point-to-point connection between the sender and recipient, improving network efficiency by reducing collisions.
They can filter and forward traffic only to the specific device that needs it, enhancing network security and performance.
Switches are common in modern networks due to their efficiency and ability to handle high traffic loads.

**Hub:**<br><br>

A hub operates at the physical layer (Layer 1) of the OSI model.<br><br>

It is a basic and passive device that simply broadcasts incoming data packets to all connected devices without any intelligence.<br><br>

Hubs do not examine MAC addresses or make decisions about where to send data; they indiscriminately send data to all connected devices.<br><br>

This broadcasting approach can lead to network congestion and collisions, especially in larger networks.<br><br>

Hubs are considered outdated and inefficient for modern networks, and they are rarely used today.
In summary, switches are more advanced and efficient networking devices that intelligently forward data packets to the appropriate recipient, while hubs are basic and outdated devices that broadcast data to all connected devices, leading to less efficient network communication. Switches are the preferred choice for building modern, high-performance LANs.

</details>
<br>

<details>
<summary>What is a switch vs a router?</summary>

**Switch:**<br><br>

A switch operates at the data link layer (Layer 2) of the OSI model.<br><br>

It is used to connect devices within a local area network (LAN).<br><br>

Switches make forwarding decisions based on MAC (Media Access Control) addresses and create efficient, dedicated connections between devices within the same LAN.<br><br>

They are primarily used for local traffic management and do not have a role in routing traffic between different networks.<br><br>

**Router:**<br><br>

A router operates at the network layer (Layer 3) of the OSI model.<br><br>

It connects different networks together and directs traffic between them.<br><br>

Routers use IP addresses to make routing decisions, determining the most appropriate path for data packets to reach their destination, whether that destination is within the same local network or in a different network (e.g., the internet).<br><br>

Routers are essential for interconnecting multiple LANs and facilitating communication between devices on different networks.<br><br>

In summary, switches are used for local network traffic management within a single LAN, while routers are used to connect and route traffic between different networks, including routing traffic between LANs and the broader internet. Both devices play critical roles in network communication and connectivity.

</details>
<br>

<details>
<summary>What is HTTPS vs Websockets?</summary>

HTTPS and WebSockets are both protocols used for web communication, but they serve different purposes and operate in distinct ways:<br><br>

**HTTPS (HyperText Transfer Protocol Secure):**<br><br>

- HTTPS is an extension of the HTTP protocol used for secure communication over the internet.<br><br>
It encrypts the data transmitted between a web browser and a web server, providing data confidentiality and integrity.<br><br>
- HTTPS uses SSL/TLS (Secure Sockets Layer/Transport Layer Security) to establish a secure, encrypted connection between the client and server.<br><br>
- It is commonly used for secure web browsing, online transactions, and protecting sensitive data, such as login credentials and personal information.<br><br>
- HTTPS is a request-response protocol, meaning that the client sends a request to the server, and the server responds with the requested data.<br><br>

**WebSockets:**<br><br>
- WebSockets is a protocol that provides full-duplex communication channels over a single TCP connection.
Unlike HTTP(S), which is request-response-based and stateless, WebSockets allow for two-way, real-time communication between a client (e.g., a web browser) and a server.
- WebSockets are often used in applications that require real-time updates, such as chat applications, online gaming, collaborative tools, and live data feeds.
- They are more efficient for scenarios where continuous communication is needed, as they eliminate the need for repeatedly establishing new connections.
- WebSockets allow data to be pushed from the server to the client and vice versa without the overhead of frequent HTTP requests.

In summary, HTTPS is a protocol for securing web communication, while WebSockets provide a framework for real-time, bidirectional communication over a single, long-lived connection. They are used for different purposes but can complement each other in web applications, where secure and real-time communication is required.

</details>
<br>

<details>
<summary>Explain how a 3 way handshake works?</summary>

A three-way handshake is a method used in a TCP/IP network to create a connection between a host and a client. It’s called a three-way handshake because it is a three-step method in which the client and server exchanges packets. The three steps are as follows: The client sends a SYN(Synchronize) packet to the server check if the server is up or has open ports. The server sends SYN-ACK packet to the client if it has open ports. The client acknowledges this and sends an ACK(Acknowledgment) packet back to the server.

</details>
<br>

<details>
<summary>Stateless vs Stateful firewalls?</summary>

Stateless and stateful firewalls are two types of network security devices that filter and control incoming and outgoing network traffic, but they do so in different ways:

**Stateless Firewall:**

- Stateless firewalls filter traffic based solely on the source and destination IP addresses, as well as port numbers.
They do not maintain any information about the state of ongoing network connections.
- Stateless firewalls are simpler and faster but lack the ability to make decisions based on the context or state of a connection.
- Each packet is evaluated in isolation, without considering whether it's part of an established connection or whether it's a legitimate response to an outbound request.
- Stateless firewalls are often used in basic network security setups and are suitable for scenarios where a basic level of security is sufficient.

**Stateful Firewall:**

- Stateful firewalls, also known as dynamic packet filtering firewalls, maintain a table of the state of active network connections.
- They keep track of the state of TCP and UDP sessions, including the state of each connection (e.g., established, related, new) and their associated ports.
- Stateful firewalls make decisions based on the context of network traffic, allowing them to permit or deny packets based on whether they are part of a legitimate, established connection.
- This context-awareness makes stateful firewalls more effective at protecting against various types of attacks, such as port scanning and certain forms of packet-level attacks.
- They are commonly used in enterprise networks and provide a higher level of security compared to stateless firewalls.

In summary, stateless firewalls filter traffic based solely on basic information like IP addresses and port numbers, while stateful firewalls maintain information about the state of active connections and make decisions based on the context of the traffic. Stateful firewalls are generally more advanced and provide better security for modern network environments.

</details>
<br>

<details>
<summary>What are VPCs?</summary>

VPC stands for Virtual Private Cloud. It is a fundamental component of cloud computing infrastructure, particularly in services like Amazon Web Services (AWS) and Microsoft Azure.

**VPC (Virtual Private Cloud):**

- A VPC is a logically isolated section of a cloud provider's network where you can launch and manage your virtual resources like virtual machines (VMs), databases, and storage.
- It allows you to create your own private network within the cloud, complete with private IP addresses, subnets, route tables, and security groups.
- VPCs provide control over network configurations, security, and communication between resources, making it possible to build secure and scalable cloud-based applications.
- You can also connect your VPC to your on-premises data centers or other VPCs, creating a hybrid or multi-cloud network.
- VPCs are essential for ensuring network isolation, security, and resource organization in cloud environments.

</details>
<br>

<details>
<summary>What is subnetting?</summary>

Subnetting is the process of dividing a larger IP network into smaller, more manageable subnetworks, or "subnets." This practice is commonly used in networking to:

- Improve Network Efficiency: Subnetting allows you to create smaller segments within a larger network. This can help reduce broadcast traffic and improve overall network performance by isolating traffic to specific subnets.

- Enhance Security: By dividing a network into subnets, you can implement access control lists (ACLs) and firewall rules more effectively. This helps control and secure traffic between different parts of the network.

- IP Address Management: Subnetting aids in efficient IP address allocation. Each subnet can have its own range of IP addresses, making it easier to manage and allocate IP addresses within an organization.

- Isolation and Segmentation: Subnets can isolate different types of devices or services from each other. For example, you can place servers in one subnet and user devices in another to improve security and management.

Subnetting involves dividing an IP address range into smaller, contiguous blocks, each with its own network address and a range of host addresses. This is typically done by modifying the subnet mask associated with the IP address range. The subnet mask designates which portion of the IP address is the network part and which part is the host part.

For example, if you have the IP address range 192.168.0.0/24 (where "/24" indicates a subnet mask of 255.255.255.0), you can subnet it into smaller subnets like 192.168.0.0/25 and 192.168.0.128/25, each with half of the original IP address range's available host addresses.

</details>
<br>

<details>
<summary>What is DHCP?</summary>


DHCP stands for Dynamic Host Configuration Protocol. It is a network protocol used to automate and simplify the process of assigning IP addresses and other network configuration settings to devices on a local network.

**DHCP (Dynamic Host Configuration Protocol):**

- DHCP is a client-server protocol commonly used in local area networks (LANs) and on the internet.
- It eliminates the need for manual IP address configuration on each device in a network.
- When a device (client) connects to a network, it sends a DHCP request to a DHCP server, typically a router or dedicated DHCP server.
- The DHCP server responds with an available IP address, subnet mask, default gateway, DNS server addresses, and other configuration parameters.
- The client then configures itself with the provided information, making it ready to communicate on the network.

</details>
<br>

#### Advanced + Scenario based questions:

<details>
<summary>When I type google.com into the browser, what actually happens? (basic version)</summary>

When you type "google.com" into your web browser's address bar and hit Enter, several steps occur behind the scenes to display the Google homepage. Here's a simple breakdown of what happens:

**DNS Resolution:**

- Your web browser first checks its local cache to see if it already knows the IP address associated with "google.com." If it does, it skips the next steps.
- If not found in the cache, your browser sends a DNS (Domain Name System) resolution request to a DNS resolver. This is usually provided by your internet service provider (ISP) or a public DNS service like Google's 8.8.8.8.
- The DNS resolver checks its cache to see if it has the IP address for "google.com." If not, it initiates the DNS resolution process.

**DNS Resolution Process:**

- The DNS resolver queries root DNS servers to find the authoritative DNS server for the top-level domain (TLD), which is "com" in this case.
- The root DNS server responds with the IP address of the authoritative DNS server for the "com" TLD.
- The resolver then queries the authoritative DNS server for the "com" TLD to find the authoritative DNS server for "google.com."
- The authoritative DNS server for "google.com" responds with the IP address associated with "google.com."

**IP Address Retrieval:**

- The DNS resolver returns the IP address of "google.com" to your web browser.

**HTTP Request:**

- Your browser initiates an HTTP (Hypertext Transfer Protocol) request to the IP address it received for "google.com."
- The request includes additional information like the specific web page you're trying to access (e.g., "/", which typically represents the homepage).

**Server Processing:**

- Google's web server, located at the provided IP address, receives the HTTP request.
- The server processes the request and generates an appropriate response.

**Response Transmission:**

- The web server sends back an HTTP response, which includes the HTML, CSS, JavaScript, and other resources needed to render the Google homepage.

**Rendering the Web Page:**

Your browser receives the HTTP response and begins rendering the Google homepage on your screen.
It may also make additional requests for images, stylesheets, and scripts referenced in the HTML to fully load and display the page.

**Page Display:**

Once all resources are loaded, your web browser displays the Google homepage on your screen, and you can interact with it.
In summary, when you type "google.com" into your browser, a complex series of steps involving DNS resolution, HTTP requests, and server responses occurs to retrieve and display the webpage you requested. This process ensures that you can access websites using human-readable domain names while the internet works behind the scenes using IP addresses to route and deliver content.

</details>
<br>

<details>
<summary>I can't reach a website, how can I troubleshoot? (use deep Linux + networking knowledge)</summary>

**Check Network Connectivity:**

- Ensure your Linux machine has a working internet connection. Try pinging a reliable website or an IP address (e.g., `ping google.com` or `ping 8.8.8.8` for Google's DNS).

**DNS Resolution:**

- Verify that DNS resolution is working correctly. Try to resolve the website's IP address using `nslookup` or `dig` (e.g., `nslookup website.com` or `dig website.com`).
- Check your DNS server configuration in /etc/resolv.conf. Ensure it points to a valid DNS server (e.g., `nameserver 8.8.8.8` for Google's DNS).

**Check Hosts File:**

- Make sure the website is not blocked by entries in the `/etc/hosts` file. Check for any entries that may be redirecting the website.

**Firewall Rules:**

- Check if a firewall is blocking outgoing or incoming traffic. Use the `iptables` or firewall-cmd command to inspect firewall rules.

**Web Proxy:**

- If you are behind a proxy server, ensure that proxy settings are correctly configured in your environment, including `HTTP_PROXY` and `HTTPS_PROXY` environment variables.

**Browser Issues:**

- Try accessing the website from a different web browser or an incognito/private browsing window to rule out browser-related problems.

**SSL/TLS Issues:**

- If you are getting SSL/TLS-related errors, ensure your system has up-to-date CA certificates installed. You can also check for SSL/TLS issues using the openssl command (e.g., `openssl s_client -connect website.com:443`).

**Check DNS Cache:**

- If you've made changes to DNS configurations, clear your DNS cache using `systemctl restart systemd-resolved` (on systems using systemd-resolved) or `sudo /etc/init.d/nscd restart` (on systems using nscd).

**Trace Route (Traceroute):**

- Use the traceroute or tracepath command to trace the network path to the website (e.g., `traceroute website.com` or `tracepath website.com`).

**Check System Logs:**

- Inspect system logs in `/var/log` (e.g., `/var/log/syslog`, `/var/log/messages`, `/var/log/auth.log`) for any network-related errors or issues.

**Check DNS Server Status:**

- Verify the availability and responsiveness of your DNS servers by pinging them or using tools like `dig`.

**Check Website Status:**

It's possible that the website itself is down. Check its status on a service like "DownDetector" or "Is It Down Right Now?".

**Packet Capture (Optional):**

- As a last resort, you can use packet capture tools like `tcpdump` or `wireshark` to capture network traffic and analyze it for issues.

</details>
<br>

<details>
<summary>Can you break down the OSI model and what does it signify?</summary>

The OSI (Open Systems Interconnection) model is a conceptual framework that standardizes and defines the functions of a telecommunication or networking system. It consists of seven distinct layers, each responsible for specific tasks in the communication process. Here's a breakdown of the OSI model and what each layer signifies:

**Physical Layer (Layer 1):**

Significance: This layer deals with the physical medium and transmission of raw binary data over a physical network.
Responsibilities: It defines the physical characteristics of the network, such as cables, connectors, electrical voltages, and transmission speeds. It also specifies how bits are represented, encoded, and transmitted over the network medium.

**Data Link Layer (Layer 2):**

Significance: This layer focuses on reliable data transfer between directly connected devices on a local network.
Responsibilities: It manages the framing of data into frames, error detection and correction, and flow control. Ethernet and Wi-Fi operate at this layer. MAC (Media Access Control) addresses are used for device identification.

**Network Layer (Layer 3):**

Significance: The network layer is responsible for routing packets across different networks to reach their destination.
Responsibilities: It handles logical addressing, routing, and packet forwarding. The Internet Protocol (IP) operates at this layer, and IP addresses are used to identify devices on different networks.

**Transport Layer (Layer 4):**

Significance: This layer ensures end-to-end communication and data reliability between devices on different networks.
Responsibilities: It manages data segmentation, flow control, error detection, and retransmission. TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are commonly used transport layer protocols.

**Session Layer (Layer 5):**

Significance: The session layer establishes, manages, and terminates communication sessions between two devices.
Responsibilities: It handles session setup, maintenance, and teardown, including synchronization, checkpointing, and recovery of data in case of interruptions.

**Presentation Layer (Layer 6):**

Significance: This layer ensures that data is presented in a readable format for the application layer.
Responsibilities: It handles data translation, encryption, compression, and character encoding to ensure that data sent by one device can be understood by another.

**Application Layer (Layer 7):**

Significance: The application layer is the top layer and represents the actual software applications that users interact with.
Responsibilities: It provides a platform-independent interface for application software to communicate with the lower layers. This layer includes protocols like HTTP, FTP, SMTP, and DNS, which enable specific application-level functions.

</details>
<br>

<details>
<summary>How does mTLS work and compare it to TLS?</summary>

mTLS (mutual Transport Layer Security) is an extension of the traditional TLS (Transport Layer Security) protocol. Both TLS and mTLS are cryptographic protocols used to secure data transmission over a network, but they differ in how they authenticate and secure the communication.

**TLS (Transport Layer Security):**

- TLS is used to establish secure, encrypted communication between a client (such as a web browser) and a server (such as a web server).
- In a typical TLS handshake, the server presents its digital certificate to prove its identity to the client.
- The client verifies the server's certificate against a trusted certificate authority (CA) to ensure it's valid.
- Once the server's identity is verified, a symmetric encryption key is exchanged, and encrypted communication begins.
- TLS is primarily used for server authentication and encryption of data in transit between a client and a server.

**mTLS (Mutual Transport Layer Security):**

- mTLS, also known as two-way TLS or client-side TLS, extends TLS by requiring both the client and the server to present digital certificates and authenticate each other.
- In an mTLS handshake, the client and server exchange certificates and verify each other's identities.
- The client verifies the server's certificate, just like in traditional TLS.
- The server, in turn, verifies the client's certificate to ensure it's valid and belongs to an authorized client.
- Once both parties are authenticated, a symmetric encryption key is exchanged, and encrypted communication begins.
- mTLS is used when both parties (client and server) need to be authenticated and data encryption is required. It's often used in scenarios like secure API communication and IoT device authentication.

In summary, TLS and mTLS are both cryptographic protocols for securing data transmission, but mTLS goes a step further by requiring mutual authentication, where both the client and server authenticate each other using digital certificates. This added layer of security is useful in scenarios where bidirectional trust is essential, such as in securing APIs, web services, or IoT device communication.

</details>
<br>

<details>
<summary>Describe the TCP/IP connection process?</summary>


The TCP/IP (Transmission Control Protocol/Internet Protocol) connection process involves several steps that occur when two devices communicate over a network. Key steps include:

**1. Initialization:**

The client initiates the connection by sending a TCP segment with the SYN (synchronize) flag set to the server.
This initiates the "three-way handshake" process.

**2. Three-Way Handshake:**

SYN (Synchronize): The client sends a TCP segment with the SYN flag set, indicating its intent to establish a connection. It also selects an initial sequence number.
SYN-ACK (Synchronize-Acknowledgment): The server responds with a TCP segment that has the SYN and ACK (acknowledge) flags set. It acknowledges the client's sequence number and selects its own initial sequence number.
ACK (Acknowledgment): The client sends an acknowledgment back to the server, acknowledging the server's sequence number. At this point, the connection is established, and both parties are synchronized.

**3. Data Transfer:**

Once the connection is established, data can be transmitted in both directions.
Data is divided into segments, each with a sequence number for tracking and reordering.

**4. Termination:**

When one party wishes to close the connection, it sends a TCP segment with the FIN (finish) flag set.
The other party acknowledges the FIN and may also send its own FIN.
This initiates a "four-way handshake" to ensure that both sides agree to close the connection gracefully.

**5. Four-Way Handshake (Connection Termination):**

FIN (Finish): One party sends a TCP segment with the FIN flag set to indicate the intent to close the connection.
ACK (Acknowledgment): The other party acknowledges the FIN.
FIN: The acknowledging party may also send its own FIN to close the connection from its side.
ACK: The initial party acknowledges the FIN from the other side, completing the termination process.

**6. Connection Closed:**

After the four-way handshake, the connection is closed, and no further data can be exchanged.

</details>
<br>

<details>
<summary>When and why would one use a TCP over UDP?</summary>

TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are two transport layer protocols used in networking, and each has its own strengths and weaknesses. The choice between TCP and UDP depends on the specific requirements of the application or service being used. Here's when and why you might choose TCP over UDP:

**Use TCP When:**

- Reliability is Critical: TCP provides a reliable and error-checked connection. It ensures that data is delivered accurately and in the correct order. This makes it suitable for applications where data integrity is crucial, such as file transfers, email, and web browsing.

- Ordered Data Delivery: If your application requires data to be delivered in the same order it was sent, TCP is the better choice. It maintains a sequencing mechanism to guarantee ordered data delivery.

- Flow Control: TCP includes flow control mechanisms to prevent overwhelming the receiver with too much data too quickly. This is essential for applications that require rate limiting, like streaming video or real-time communication apps.

- Error Recovery: TCP can detect and recover from errors that may occur during transmission. It retransmits lost or corrupted packets to ensure data reliability.

- Connection-Oriented: TCP establishes a connection before data transfer begins and releases it after the transfer is complete. This connection-oriented nature is suitable for applications that require a reliable, well-defined start and end to communication sessions.

**Use UDP When:**

- Low Latency is Critical: UDP is faster than TCP due to its minimal overhead. It's suitable for applications that prioritize low latency, such as online gaming, live streaming, and VoIP (Voice over IP).

- Loss Tolerance: UDP does not guarantee data delivery or order, so it's a good choice for applications where occasional packet loss is acceptable, such as real-time data feeds, video conferencing, and some IoT applications.

- Reduced Network Overhead: UDP has less overhead than TCP because it doesn't involve establishing connections, maintaining sequencing, or performing extensive error checking. This can be advantageous for applications with limited bandwidth or high data rates.

- Broadcast or Multicast: UDP supports broadcast and multicast communication, which allows data to be sent to multiple recipients simultaneously. This is useful for applications like online gaming and video streaming.

- Simple Implementation: UDP is easier to implement because it doesn't have the complexities of connection establishment and error recovery. This makes it a good choice for lightweight applications and protocols.

In summary, use TCP when data reliability, ordered delivery, and error recovery are critical. Choose UDP when low latency, reduced overhead, and loss tolerance are more important, and you can handle potential data loss or out-of-order delivery at the application level. The decision depends on the specific needs of your application and the trade-offs you are willing to make between reliability and performance.

</details>
<br>

<details>
<summary>Data transfer between 2 hosts is extremely slow. How can you troubleshoot?</summary>

**Check Network Connectivity:**

Verify that both hosts have a stable and functioning network connection. Ensure that cables, switches, and routers are working correctly.

**Test Other Network Services:**

Determine if the slowness is specific to data transfer or if it affects other network services as well. Try accessing websites, pinging other hosts, or testing other network applications to see if the issue is widespread or isolated.

**Check Host Resource Utilization:**

Monitor the CPU, memory, and disk utilization on both hosts. High resource usage can lead to slow data transfer. Identify any resource-intensive processes or applications that may be affecting performance.

**Review Network Configuration:**

Verify that the network configurations on both hosts are correct, including IP addresses, subnet masks, gateways, and DNS settings. Ensure there are no conflicts or misconfigurations.

**Check for Network Congestion:**

Network congestion can slow down data transfer. Monitor network traffic and identify any bottlenecks or excessive usage on the network segments between the two hosts.

**Test Connectivity to Other Hosts:**

Try transferring data between each host and other devices on the network to determine if the issue is specific to the connection between these two hosts.


</details>
<br>
