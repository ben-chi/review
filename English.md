### What is the network?

The computer network is a system of peripherals(routers,switches) or computers interconnected with each other and has a standard communication channel established between them to exchange different types of information and data.

### 什么是网络？

计算机网络是外围设备或计算机相互连接的系统，它们之间建立了标准的通信通道，用于交换不同类型的信息和数据。



### TCP/IP Model

from top to bottom

Application

* It contains all the higher-level protocols(http(Browse the web),rpc)

Transport

* the relationship of one-to-many
* concept:port
* the port-to-port communication (the application-to-application communication)

Network

* It delivers the IP packets where they are supposed to be delivered.
* the end-to-end communication, walk through the whole network, from one device to another, regardless of wind or rain, and finally, get to the destination, it all thanks to the Network layer

DataLink

* Mac address, which is globally unique for every PC, helps us to locate where the next-step machine is

* such as classic Ethernet must be used to meet the needs of the connectionless internet layer.

Physical



### What are the HTTP and the HTTPS protocol?

HTTP is the abbreviation of HyperText Transfer Protocol which defines the set of rules and standards on how the information can be transmitted on the World Wide Web (WWW).  It helps the web browsers and web servers for communication. It is a ‘stateless protocol’ where each intercation is independent with respect to the previous command. HTTP is an application layer protocol built upon the TCP. It uses port 80 by default.



HTTPS is the HyperText Transfer Protocol Secure or Secure HTTP. It is an advanced and secured version of HTTP. On top of HTTP, SSL/TLS protocol is used to provide security. It enables secure transactions by **encrypting** the communication and also helps identify network servers securely. It uses port 443 by default.



Asymmetric encryption: get and check the public key of web server and generate a random number to create a symmetric encryption which known only by each other

Symmetric encryption:follow-up communicate 

### 17、什么是 HTTP 和 HTTPS 协议？

HTTP 是超文本传输协议，它定义了有关如何在万维网 (WWW) 上传输信息的规则和标准。它有助于网络浏览器和网络服务器进行通信。这是一个“无状态协议”，其中每个命令相对于前一个命令是独立的。HTTP 是建立在 TCP 之上的应用层协议。它默认使用端口 80。

HTTPS 是超文本传输协议安全或安全 HTTP。它是 HTTP 的高级和安全版本。在 HTTP 之上，SSL/TLS 协议用于提供安全性。它通过加密通信来实现安全交易，还有助于安全地识别网络服务器。它默认使用端口 443。



### What is the DNS?

NS is the Domain Name System. It is considered as the devices/services directory of the Internet. It is a decentralized and hierarchical naming system for devices/services connected to the Internet. **It translates the domain names to their corresponding IPs**. It uses port 53 by default.

* Root domain name server
* Top level domain name server
* Authoritative domain name server
* local domain name server

### 19.什么是 DNS？

DNS 是域名系统。它被认为是 Internet 的设备/服务目录。它是连接到 Internet 的设备/服务的分散和分层命名系统。它将域名转换为相应的 IP。它默认使用端口 53。



### What is the use of a router and how is it different from a gateway?

gateway is quiet an abstract concept, it used for connecting **two or more network segments**.  It can be a router or a server,etc.

router is a concrete product.

The router is a networking device used for connecting **two or more network segments**. It directs the traffic in the network. It transfers information and data like web pages, emails, images, videos, etc. from source to destination in the form of packets. It operates at the network layer. The gateways are also used to route and regulate the network traffic but, they can also send data between two dissimilar networks while a router can only send data to similar networks.

### 20. 路由器有什么用，与网关有什么不同？

路由器是用于连接两个或多个网段的网络设备。它引导网络中的流量。它以数据包的形式将信息和数据（如网页、电子邮件、图像、视频等）从源传输到目的地。它在网络层运行。网关还用于路由和调节网络流量，但它们也可以在两个不同的网络之间发送数据，而路由器只能将数据发送到相似的网络。



### 21. What is the TCP protocol?

TCP or TCP/IP is the Transmission Control Protocol/Internet Protocol. It is a set of rules that decides how a computer connects to the Internet and how to transmit the data over the network. It creates a virtual network when more than one computer is connected to the network and uses the three ways handshake model to establish the connection which makes it more reliable.

three/four-way handshake

build/release connection

stipulate :规定

character:Byte stream\connection-oriented\reliable

Retransmission mechanism：重传机制 

disturb：干扰

sliding window：滑动窗口

congestion control：拥塞控制

flow control：流量控制 pile up

### 21. 什么是TCP协议？

TCP 或 TCP/IP 是传输控制协议/Internet 协议。它是一组规则，用于决定计算机如何连接到 Internet 以及如何通过网络传输数据。它在多台计算机连接到网络时创建一个虚拟网络，并使用三种方式握手模型建立连接，使其更加可靠。



### 22. What is the UDP protocol?

UDP is the User Datagram Protocol and is based on **Datagrams**. Mainly, it is used for multicasting and broadcasting. Its functionality is almost the same as TCP/IP Protocol except for the three ways of handshaking and error checking. It uses a simple transmission without any hand-shaking which makes it less reliable.

Correctness

Validity

as a sender, dont care about whether the receiver receive the datagram, it will not resend  the datagram at all

as a receive,the data received maybe not so integral,unreliable but convenient and efficient if correctness is not strictly required

### 22. 什么是 UDP 协议？

UDP 是用户数据报协议，基于数据报。主要用于组播和广播。除了握手和错误检查三种方式外，它的功能几乎与 TCP/IP 协议相同。它使用简单的传输，没有任何握手，这使得它不太可靠。



### 23. Compare between TCP and UDP

- TCP is Connection-Oriented Protocol, while UDP is Connectionless Protocol.
- TCP is More Reliable, while UDP is Less Reliable.
- TCP transmission is slower than UDP transmission.
- TCP's Packets order can be preserved or can be rearranged, while UDP's Packets order is not fixed and packets are independent of each other.
- TCP Uses three ways handshake model for connection, while UDP uses No handshake for establishing the connection.
- TCP packets are heavy-weight, while UDP packets are light-weight.
- TCP Offers error checking mechanism, while UDP offers No error checking mechanism.
- Protocols like HTTP, FTP, Telnet, SMTP, HTTPS, etc use TCP at the transport layer, while Protocols like DNS, RIP, SNMP, RTP, BOOTP, TFTP, NIP, etc use UDP at the transport layer.

### 23. TCP 和 UDP 的比较

| TCP/IP                                                | UDP                                                          |
| :---------------------------------------------------- | :----------------------------------------------------------- |
| 面向连接的协议                                        | 无连接协议                                                   |
| 更可靠                                                | 不太可靠                                                     |
| 传输速度较慢                                          | 更快的传输                                                   |
| 数据包顺序可以保留或重新排列                          | 数据包顺序不固定，数据包相互独立                             |
| 使用三种方式握手模型进行连接                          | 无需握手即可建立连接                                         |
| TCP 数据包是重量级的                                  | UDP数据包是轻量级的                                          |
| 提供错误检查机制                                      | 没有错误检查机制                                             |
| HTTP、FTP、Telnet、SMTP、HTTPS 等协议在传输层使用 TCP | DNS、RIP、SNMP、RTP、BOOTP、TFTP、NIP 等协议在传输层使用 UDP |



### 25. What do you mean by the DHCP Protocol?

DHCP is the Dynamic Host Configuration Protocol.

It is an application layer protocol used to auto-configure devices on IP networks enabling them to use the TCP and UDP-based protocols. The DHCP servers auto-assign the IPs and other network configurations to the devices individually which enables them to communicate over the IP network. It helps to get the subnet mask, IP address and helps to resolve the DNS. It uses port 67 by default.

### 25. DHCP 协议是什么意思？

DHCP 是动态主机配置协议。

它是一种应用层协议，用于自动配置 IP 网络上的设备，使它们能够使用基于 TCP 和 UDP 的协议。DHCP 服务器会自动将 IP 和其他网络配置单独分配给设备，从而使它们能够通过 IP 网络进行通信。它有助于获取子网掩码、IP 地址并有助于解析 DNS。它默认使用端口 67。

only when you have an IP address can you communicate with others

geektime 

* 45 courses of mysql
* source code resolution of Redis

### 26. What is the ARP protocol?

ARP is Address Resolution Protocol. It is a network-level protocol used to convert the logical address i.e. IP address to the device's physical address i.e. MAC address. It can also be used to get the MAC address of devices when they are trying to communicate over the local network.

### 26.什么是ARP协议？

ARP是地址解析协议。它是一种网络级协议，用于将逻辑地址（即 IP 地址）转换为设备的物理地址（即 MAC 地址）。当设备尝试通过本地网络进行通信时，它还可用于获取设备的 MAC 地址。



### 35. What happens when you enter google.com in the web browser?

Below are the steps that are being followed:

- Check the browser cache first if the content is fresh and present in cache display the same.
- If not, the browser checks if the IP of the URL is present in the cache (browser and OS) if not then request the OS to do a DNS lookup using UDP to get the corresponding IP address of the URL from the DNS server to establish a new TCP connection.
- A new TCP connection is set between the browser and the server using three-way handshaking.
- An HTTP request is sent to the server using the TCP connection.
- The web servers running on the Servers handle the incoming HTTP request and send the HTTP response.
- The browser process the HTTP response sent by the server and may close the TCP connection or reuse the same for future requests.
- If the response data is cacheable then browsers cache the same.
- Browser decodes the response and renders the content.

### 35. 当您在网络浏览器中输入 google.com 时会发生什么？

以下是正在遵循的步骤：

- 首先检查浏览器缓存，如果内容是新的并且存在于缓存中，那么直接显示。
- 如果没有，浏览器检查 URL 的 IP 是否存在于缓存（浏览器和操作系统）中，如果没有，则请求操作系统使用 UDP 进行 DNS 查找，以从 DNS 服务器获取 URL 的相应 IP 地址以建立一个新的 TCP 连接。
- 使用三次握手在浏览器和服务器之间设置新的 TCP 连接。
- 使用 TCP 连接将 HTTP 请求发送到服务器。
- 服务器上运行的 Web 服务器处理传入的 HTTP 请求并发送 HTTP 响应。
- 浏览器处理服务器发送的 HTTP 响应，并可能关闭 TCP 连接或在未来的请求中重用。
- 如果响应数据是可缓存的，那么浏览器会缓存相同的数据。
- 浏览器解码响应并呈现内容。









## 数据结构

optimize

time complexity

space complexity

data structure and algorithm,cooperate with each other,expect to optimize time complexity and space complexity



My name is benchi. I spend both of my undergraduate and postgraduate time in NanJing University, major in mathematics, and I'm going to get my master's degree next year, and I've being studying CS courses by myself for two years, such as computer network, operating system, data structure, etc. and in this year ,from February to August, I worked in ByteDance as a back-end development trainee. My most familiar development language is GO, and I

Research direction : Interval analysis

It comes from a quite simple problem. the total number of floating point number is finite, 64 bit can represent 2 to the power of 64 numbers, but the number of real number is infinite, so when we cast the real number into the floating point number, there must exists an error, which is called by rounding error, this error is ignorable at the begining, but with the accumulation of the calculation, this error can be accumulated to the level that cannot be ignored. And Interval analysis is 

one of the solution for this problem. We can represent the real number by an interval of floating point number and replace real number calculation by interval calculation and finally we get an interval and the real solution is promised to be contained in this interval.and most important work of the interval analysis is to shorten the length of final answer.