# QUIC vs TCP: Advantages and Disadvantages

## Introduction to TCP

**Transmission Control Protocol (TCP)** is one of the core protocols of the Internet Protocol Suite. It originated in the initial network implementation in which it complemented the Internet Protocol (IP). Therefore, the entire suite is commonly referred to as TCP/IP. TCP provides reliable, ordered, and error-checked delivery of a stream of bytes between applications running on hosts communicating via an IP network. Major internet applications such as the World Wide Web, email, remote administration, and file transfer rely on TCP.

## Introduction to QUIC

**Quick UDP Internet Connections (QUIC)** is a modern transport protocol developed by Google and standardized by the IETF. QUIC is designed to improve performance compared to TCP, particularly in terms of reducing latency and enhancing security. QUIC operates over the User Datagram Protocol (UDP) and incorporates features such as multiplexing, improved congestion control, and connection migration. It is also the foundation for HTTP/3, the latest version of the Hypertext Transfer Protocol.

## Advantages of QUIC over TCP

1. **Reduced Latency**:
   - **Faster Handshake**: QUIC reduces connection establishment latency by combining the transport and cryptographic handshakes. A new QUIC connection can be established in a single round-trip time (RTT), and often zero RTT if the client has previously connected to the server.
   - **No Head-of-Line Blocking**: QUIC operates over UDP and uses multiple streams within a single connection, allowing independent transmission and retransmission of data streams. In TCP, packet loss in a single stream can block the entire connection (head-of-line blocking).

2. **Improved Multiplexing**:
   - **Stream Independence**: QUIC supports multiple streams within a single connection, and each stream can be delivered independently. This prevents one stream's loss from impacting others, enhancing the performance of applications that need concurrent data streams.

3. **Integrated Security**:
   - **Built-In Encryption**: QUIC integrates TLS 1.3 encryption directly into its protocol, ensuring that all data transmitted is secure by default. This eliminates the need for a separate security layer as in TCP (TCP+TLS).

4. **Better Congestion Control and Error Recovery**:
   - **Optimized Congestion Control**: QUIC allows more flexible and advanced congestion control mechanisms compared to TCP, which can lead to better performance under varying network conditions.
   - **Efficient Error Correction**: QUIC's ability to retransmit only the lost packets in a stream without affecting others can lead to more efficient and faster recovery from packet loss.

5. **Connection Migration**:
   - **Seamless Mobility**: QUIC supports connection migration, meaning a QUIC connection can survive changes in the client's IP address (e.g., moving from Wi-Fi to mobile data) without requiring a new connection. This is particularly beneficial for mobile users.

6. **Modern Protocol Design**:
   - **Extensibility**: QUIC is designed with extensibility in mind, making it easier to introduce new features and improvements compared to TCP, which has a more rigid structure.

7. **Improved Performance**:
   - **Optimized for Web Traffic**: QUIC is specifically optimized for web traffic, providing performance enhancements for HTTP/3, which is built on top of QUIC. This results in faster page loads and better user experiences for web applications.

## Disadvantages of QUIC

1. **Complexity**:
   - **Protocol Complexity**: QUIC is a more complex protocol than TCP, requiring significant changes to existing network stacks and software implementations. This complexity can lead to longer development and debugging times.
2. **UDP-Based**:
   - **Firewall and NAT Traversal**: Since QUIC is based on UDP, it can face issues with firewalls and Network Address Translation (NAT) devices that are optimized for TCP traffic. Some network devices might block or limit UDP traffic, potentially causing connectivity problems.
   - **UDP Packet Loss**: Unlike TCP, which has built-in congestion control and reliability mechanisms, UDP is a simpler protocol without these features. Although QUIC implements its own mechanisms, it may still encounter issues in networks that heavily drop or limit UDP packets.
3. **Resource Consumption**:
   - **Processing Overhead**: The integration of encryption and multiple streams within a single connection can increase CPU and memory usage compared to traditional TCP connections, potentially leading to higher resource consumption on servers and clients.
4. **Deployment and Adoption**:
   - **Limited Support**: While support for QUIC is growing, it is not yet as widely adopted or supported as TCP. This can limit its use in some environments and applications.
   - **Interoperability Issues**: New protocols like QUIC may face interoperability issues with existing network infrastructure, software, and hardware that are not yet fully compatible.
5. **Maturity**:
   - **Protocol Maturity**: QUIC is a relatively new protocol compared to TCP, which has been extensively tested and optimized over decades. There may still be undiscovered issues or inefficiencies in QUIC that need to be addressed as it matures.
6. **Debugging and Monitoring**:
   - **Limited Tooling**: Existing network debugging and monitoring tools are primarily designed for TCP. While new tools are being developed for QUIC, there is still a lack of comprehensive tooling for analyzing and troubleshooting QUIC traffic.
   - **Encrypted Traffic**: The encryption of QUIC traffic can make it more difficult to inspect and debug network issues, as the payload is not easily accessible for analysis.
7. **Standardization and Evolution**:
   - **Ongoing Changes**: As QUIC is still evolving, its specification and implementation may change, leading to potential compatibility issues between different versions or implementations of the protocol.

---

## Conclusion

An in-depth aritcle can be found at [HTTP/3 From A To Z: Core Concepts](https://www.smashingmagazine.com/2021/08/http3-core-concepts-part1/). In my opinion, this article entails the advantages of QUIC/UDP over TCP.  The former has faster set-up, built-in encryption, flexibility for extensions, better congestion control, connection migration and suffer no Head-of-LIne Blocking.  However, it also runs into problems because its buildt upon UDP.  Many devices that place strict limitations on UDP will cause compatiliby and speed problems when dealing with QUIC/UDP packets. Furthermore, its so-called advacnements do not make a really big difference in terms of loading speed and connectiviy for most users, especially when it comes to HTTP connections, as many of its features have counterparts in TCP, which has been invested and developed for decades. These are fully explained in [HTTP/3: Performance Improvements (Part 2)](https://www.smashingmagazine.com/2021/08/http3-performance-improvements-part2/).  However, persoanlly, I would say it is still worth looking into and investing OUIC/UDP as it offers built-in security, reducing the vulnerability of tele-communication. Also, its nature of being a user-sapce protocol gives rise to incorporating  powerful extensions and mroe advanced algorithms to improve its efficiency and reliability, which is something TCP cannot keep its pace up with as it sits in kernel space. All in all, OUIC has a main advantage: it lets you have a say on what feature you would like to add on top of its base implementation without waiting for updates on the protocl by developers working on kernel-space Protocls like TCP.