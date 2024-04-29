# 13.1 Student Guide: Networking With Command Line
 
### Overview

Today's lesson introduces networking basics and command-line functions that perform networking tasks.

### Class Objectives

By the end of the lesson, you will be able to:

- Understand basic networking terms and concepts.

- Be familiar with the command-line interface and essential networking commands.

- Diagnose common network issues using command-line tools.

### Slideshow

The lesson slides are available on Google Drive here: [13.1 Slides](https://docs.google.com/presentation/d/1BUxFFqHD-x6fSVf9c7r6cVR9DEbHnZVDN9nzz4Xn6jA/edit#slide=id.g2c265dbf074_0_1014)

### Lab Environment

Today will not require a lab environment. Instead, you will work with Git Bash to do command-line functions. Git Bash is a minimalist application that requires very little hardware requirements.

[Git Bash Installation Link](https://gitforwindows.org/)

[Git Bash for Mac](https://git-scm.com/download/mac)

### 01. Networking With Command Line

In today's supplemental lesson we will learn about networking and using the command line to query, test, and validate various networking functions. Today will start with a review of networking basics, then go into the command-line functions. 

### 02. IP Addresses

As the basis to networking, we must first understand what an Internet Protocol (IP) address is. An IP address is a unique identifier assigned to each device connected to a network that uses the Internet Protocol for communication. Its primary function is to allow devices to locate and communicate with each other on a network. IP addresses have gone through a few renditions, but currently IP version 4 (IPv4) is the most used. 

**IPv4** consists of four numbers separated by dots (e.g., 192.168.1.1). 

- Due to the exponential growth of the internet, IPv4 addresses are running out, leading to the development of IPv6.

**IPv6** uses a 128-bit address space, allowing for a virtually limitless number of devices. An IPv6 address is represented as eight groups of four hexadecimal digits (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334). 

There's also type types of IPv4 addresses: private and public.

- **Public** IP addresses are used on the internet and must be unique across the entire internet.

- **Private** IP addresses are used within private networks and do not need to be unique outside their network. Ranges like 192.168.x.x, 10.x.x.x, and 172.16.x.x to 172.31.x.x are reserved for private use.

### 03. DHCP

IP addresses are assigned two different ways: statically and dynamically.

A **static** IP address is manually assigned to a device and remains constant until it is manually changed. Static IP addresses are typically used for devices that need to maintain the same IP address for extended periods, such as servers, printers, and other network equipment where consistent addressing is necessary for easy access and communication.

- The IP address does not change, which is essential for DNS servers, network printers, and permanent network connections.

- It makes it easier to diagnose network issues because it is consistent.

- Since it requires manual configuration and management, it can be time-consuming in large networks.

**Dynamic** IP addresses are assigned automatically by a DHCP server and can change over time. Most devices on home and corporate networks use dynamic IP addressing due to its ease of management and flexibility.

- Automatic assignment reduces the need for manual configuration, making it easier to add new devices to the network.

- The IP address can change, which can be inconvenient for network services that require a constant IP address.

In most cases, a dynamic IP address is used, especially for laptops and workstations. This dynamic IP address is typically assigned through the **Dynamic Host Configuration Protocol (DHCP)**. DHCP is a network management protocol used on IP networks. Its primary function is to dynamically assign IP addresses to devices on a network, allowing them to communicate with other IP networks. DHCP automates and centralizes the management of IP address allocation, reducing the need for a network administrator to manually assign IP addresses to each device.

#### How DHCP Works

1. When a device connects to a network (for example, when you turn on your computer or connect your phone to Wi-Fi), it broadcasts a DHCPDISCOVER message to the network.
2. A DHCP server on the network responds to the discovery request with a DHCPOFFER message, which offers an IP address to the device.
3. The device responds to the offer with a DHCPREQUEST message, requesting the offered IP address.
4. The DHCP server sends a DHCPACK message, confirming the IP address assignment. The device can now use the assigned IP address to communicate on the network.

### 04. DNS

Domain Name System (DNS) is an integral component of the internet's infrastructure, acting as the directory that facilitates the translation of human-friendly domain names into IP addresses that computers use to identify each other on the network. Without DNS, you would have to remember the numerical IP addresses of every web server you want to access, which would be impractical. 

DNS operates on a distributed database model, meaning that no single server contains the entire DNS database. Instead, the data is spread across many servers worldwide, structured in a hierarchical manner. When you attempt to visit a website by typing its domain name (e.g., www.example.com), a series of DNS queries and responses occur:

- DNS resolver: The process begins with a DNS resolver, usually provided by your internet service provider (ISP). The resolver acts as the intermediary between your device and the DNS servers that contain the address records.

- Root nameservers: The resolver first queries one of the root nameservers. The internet has 13 root nameservers, labeled A through M, that are operated by various organizations around the globe. These servers don't know the IP addresses for domain names but can direct the query to the appropriate Top-Level Domain (TLD) server.

- TLD nameservers: The TLD nameservers manage the domains under a specific top-level domain, such as .com, .net, and .org. The TLD server directs the resolver to the nameservers responsible for the specific domain being queried.

- Authoritative nameservers: These are the servers that hold the actual IP address records for the domain. If the authoritative nameserver has the IP address for the requested domain, it returns this information to the DNS resolver.

- Caching: To reduce the number of queries in the future, DNS resolvers cache the IP addresses of the domains they resolve for a certain period, known as the Time to Live (TTL). Cached data allows subsequent requests to the same domain to be answered more quickly.

- Final response: The DNS resolver, now having the IP address for the domain, sends it back to your device, enabling your browser to connect to the website's server using this IP address.

DNS is crucial for the usability and functionality of the internet, making it possible for users to access websites using memorable domain names instead of numerical IP addresses. It supports the dynamic nature of the internet, where IP addresses can change due to changes in hosting and infrastructure, without affecting the domain name through which users access services and information.

### 05. Activity: nslookup

In this activity, you will use `nslookup` to find the IP addresses of various websites.

Use the following file:

- [Activity File: nslookup](Activities/nslookup/Unsolved/README.md)

### 06. ping

`ping` is a widely used network administration command-line tool that tests the reachability of a host on an IP network. It measures the **round-trip time (RTT)** for messages sent from the originating host to a destination computer and echoes back. 

- `ping` operates by sending Internet Control Message Protocol (ICMP) echo request packets to the target host and waits for ICMP echo reply packets. From these transactions, `ping` computes the RTT and packet loss to evaluate the network connection quality.

- ICMP echo request and reply: ICMP is a part of the internet protocol suite, used by network devices to send error messages and operational information indicating success or failure when communicating with another IP address. For `ping`, it uses two types: echo request and echo reply.

#### Demo

The basic syntax for `ping` is simple. For example, to ping Google's public DNS server, you would use:

`ping 8.8.8.8`

Or you can ping domain names:

`ping www.google.com`

#### Common Options and Parameters

- -c <count>: Specifies the number of echo requests to send. For example, `ping -c 4 www.google.com` will send four requests.
- -t <ttl>: Sets the TTL for packets. The TTL decrements by one for each hop the packet makes; when it hits zero, the packet is discarded. This can be useful for tracing route issues.
- -s <size>: Specifies the size of the payload data in the echo request in bytes. The default is 56, which translates into 64 ICMP data bytes when the 8 bytes of ICMP header data are added.
- -i <interval>: Specifies the interval between sending each packet in seconds. The default is one second.

`ping` is often used for troubleshooting. It is primarily used to check if a host is reachable across an IP network, which is fundamental for troubleshooting network connectivity issues. By analyzing the RTT and packet loss, `ping` helps assess the quality of a network link. System administrators also use `ping` to monitor the availability of servers, routers, and other networked devices.

### 07. Ports

A **port** is a virtual point where network connections start and end. Ports are software-based and allow computers to simultaneously support multiple communication sessions with devices on a network or the internet. Each port is associated with a specific process or service and is identified by a number ranging from 0 to 65535, divided into different ranges with specific uses.

Ports are broadly classified into three ranges:

- **Well-known ports** (0&ndash;1023): These ports are reserved for specific, commonly used services and are controlled and assigned by the Internet Assigned Numbers Authority (IANA). For example, HTTP (the protocol for transferring web pages) uses port 80 and HTTPS (secure version of HTTP) uses port 443.

- **Registered ports** (1024&ndash;49151): These ports are not as strictly controlled as well-known ports but are still registered for specific services to avoid conflicts. For instance, the PostgreSQL database server commonly uses port 5432.

- **Dynamic or private ports** (49152&ndash;65535): These ports are usually not assigned to any specific service and can be used for temporary purposes, such as when a client establishes a connection to a server. The client will use a dynamic port number for the duration of the session.

When a computer sends a request over the network, it includes its IP address and a port number. The combination of an IP address and port number is known as a socket, and it provides a unique identifier for the service within the network. This way, the receiving device knows which application or service the message is intended for. For example, if a computer sends a request to a web server, it uses the server's IP address and the well-known port number for HTTP (80) to direct the request to the web server application.

Some well-known protocols and their default ports are:

- HTTP (HyperText Transfer Protocol): Port 80
- HTTPS (HTTP Secure): Port 443
- FTP (File Transfer Protocol): Ports 20 (data transfer) and 21 (control)
- SSH (Secure Shell): Port 22
- SMTP (Simple Mail Transfer Protocol): Port 25 (for email sending)
- DNS (Domain Name System): Port 53

Imagine a large apartment building as the internet, where the building's address represents the IP address. This building has many apartments, each with a unique apartment number. In this analogy, each apartment number functions like a port.

Just as the building's address directs you to the building, the IP address gets your data to the right server on the internet. Once at the building, you need to know the apartment number (port) to deliver your message to the exact destination within the building (server). For instance, if you're delivering a letter (data packet) intended for someone who lives in Apartment 80 (port 80), that tells you the letter is meant for the resident (service) who handles HTTP traffic, typically a web server.

### 08. Traceroute

Traceroute (`tracert`) is a diagnostic tool that displays the route (path) and measures the transit delays of packets across an IP network. Traceroute is used to identify the path taken by packets from a source to a destination by sending out a sequence of ICMP echo requests or UDP packets to the target. 

It works through a few steps:

- Traceroute sends a series of packets with increasing TTL values, starting from 1. The first set of packets has a TTL of 1, ensuring it is discarded by the first router in the path, which then sends back an ICMP "Time Exceeded" message. The next set of packets has a TTL of 2, reaching the second router. This process continues until a set of packets reaches the destination, which responds with an ICMP "Echo Reply" message instead of "Time Exceeded."

- By incrementing the TTL for each set of packets and recording where the "Time Exceeded" messages come from, traceroute builds a list of routers that the packets traverse on their way to the destination.

- Traceroute measures the RTT for each set of packets to reach each router and return a response. This provides data on the latency between the source and each hop along the route.

Traceroute is used often by network engineers for diagnostics.

- It's helpful for identifying where packets are being delayed or dropped in the network and pinpointing routers or links that are experiencing congestion, configuration issues, or failures.

- By revealing the path packets take to reach their destination, traceroute helps network administrators and engineers understand how their traffic is being routed through the internet or a Wide Area Network (WAN). This can be crucial for optimizing network performance or diagnosing routing issues.

- The transit delay measurements provided by traceroute can be used to analyze the performance of network segments over time. This can help identify trends in network congestion or assess the impact of network changes on performance.

Traceroute can also be used in security contexts to map out network topologies or identify unexpected routes that could indicate a security breach or misconfiguration.

### 09. Activity: Traceroute

In this activity, you will use traceroute to trace the packets of a connection to a website.

Use the following file:

- [Activity File: Traceroute](Activities/Traceroute/Unsolved/README.md)

### 10. cURL

Client URL (cURL) is a powerful command-line tool and library (libcurl) for transferring data using various network protocols. It supports a wide range of protocols, including HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, LDAP, LDAPS, DICT, TELNET, FILE, IMAP, SMTP, and POP3, making it incredibly versatile for many types of network communications. Think of a command-line based web browser: that is cURL. 

- cURL supports a wide variety of protocols, enabling it to interact with different types of servers.
- It supports different authentication methods, making it possible to transfer data securely.
- cURL can upload or download data, supporting operations like HTTP POST, PUT, and multipart/form-data for uploading files.
- It can route requests through proxies, which is helpful for testing and accessing resources in different network environments.
- cURL supports secure connections, allowing for encrypted data transfers using HTTPS and other secure protocols.
- Its command-line nature makes it easy to integrate into scripts and batch jobs for automating tasks.

cURL is widely used in software development and IT operations and by power users for various tasks:

- Developers use cURL to test API endpoints, view web server responses, and interact with web services without a graphical interface.
- cURL can download files from FTP servers or upload files to remote servers, supporting batch operations for multiple files.
- cURL commands can be incorporated into scripts to automate the retrieval or submission of data. This is useful for backups, monitoring, and integrating different systems.
- By inspecting web server responses, headers, and cookies, developers can use cURL to troubleshoot issues with web applications or services.

### 11. Activity: cURL

In this activity, you will use `curl` to perform various website operations.

Use the following file:

- [Activity File: cURL](Activities/curl/Unsolved/README.md)

------------

&copy; 2024 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.
