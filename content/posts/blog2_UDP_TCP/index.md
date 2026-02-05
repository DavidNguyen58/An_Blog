---
date: '2026-02-05T18:26:36Z'
draft: false
title: 'TCP vs UDP'
tags: ["Networking", "Network Protocols"]
ShowToc: true
TocOpen: false 
---
UDP and TCP two main protocols in the Transport Layer of the OSI and TCP/IP models. Both protocols help applications to communicate with each other, however, they are different mainly in terms of speed, reliability and use cases. We will explore the basic ideas behind each protocol and their use cases.

## User Datagram Protocol

The User Datagram Protocol (UDP) is an efficient communication protocol which allows fast transmission of data packet at the cost of reliability. The protocol works by sending packets directly to the target computer without setting up the connection. It's worth to note that the UDP protocol does not guarantee packet delivery, and the ordering of the packets.

UDP packets are referred as datagrams.
## Transmission Control Protocol

The Transmission Control Protocol requires two computers establishing a connection before sending packets to each other. This process is called a "handshake". After the connection has been established, the two computers can communicate with each other by sending packets. TCP will handle resending lost packets or rearranging packets which received out of order.

The 3-way handshaking process
- Step 1: (SYN) The sender will send a segment SYN to inform the receiver about the incoming connection and with what sequence number
- Step 2: (SYN + ACK) The receiver once received the message from sender will respond with a packet containing SYN + ACK flags. The ACK is the acknowledge flag, telling to the sender that it has received the SYN packet. The SYN indicates the starting sequence number that it wants to start with.
- Step 3: (ACK) The sender acknowledge and response to the receiver. The reliable connection is then established. 

SYN (Synchronise Sequence Number) tells what the sequence number should the data start with, which will ensure correct data transmission and packets reordering if needed. 

For example, 
- The sender starting sequence is `#1000`
- The receiver starting sequence is `#5000`
- Once both sides know about SYN, then data can flow safely in both directions.
- If neither two does not specify the starting sequence, then packets can not be reordered and transmitted correctly. 

{{< figure align=center
    src="https://www.cloudflare.com/img/learning/ddos/glossary/user-datagram-protocol-udp/tcp-vs-udp.svg"
    alt="TCP vs UDP communication"
    caption="Figure: TCP vs UDP communication overview (Cloudflare)."
>}}

## Use cases

UDP
- Real-time traffic where low latency matters more than perfect delivery (voice, video, gaming)
    - For instance, it's generally prefer to have a slightly blurry video than high-resolution video but heavily delayed
- Lightweight request/response (DNS lookups)

TCP
- Reliable, ordered delivery for complete data transfer (file transfer, web browsing)
- Interactive sessions that need in-order text (SSH, chat/messaging)

## References

- https://www.cloudflare.com/en-gb/learning/ddos/glossary/user-datagram-protocol-udp/
- https://www.geeksforgeeks.org/computer-networks/tcp-3-way-handshake-process/
