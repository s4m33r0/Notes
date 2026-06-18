# I. History and Purpose of the Internet Protocol

- **Early Networking (1950s–1960s):** Initial data networks relied on dedicated **telephone lines**.
- **The Telephone Analogy:** Alexander Graham Bell’s original network used electrical current to carry voice by vibrating magnets to mimic vocal cord vibrations. Early data networks repurposed these exact wires and magnets to transmit information.
- **The Terminal Problem:** Early mainframe computer systems (at locations like University A, B, or C) were linked by specific dedicated wires. To send data to a different destination, a user had to physically move to a different terminal in a different room or building connected to the specific lines for that location.
- **The Need for Addressing:** Computers required a system where a single terminal could address data so it would "know" which system to go to upon leaving the terminal, rather than relying on physical wire paths.

# II. The Concept of Packet Switching

- **Paul Baron:** In the early 1960s, this American computer scientist developed "distributed adaptive message block switching," the precursor to **packet switching**.
- **Discrete Blocks:** Rather than a continuous stream of data on a dedicated wire, information is cut into "little blocks" called **packets**.
- **Addressing:** Each block contains an address identifying where it came from and where it is going.
- **Packet Switching Components:** To function, packet switching requires a decentralized network with multiple paths, data divided into discrete blocks, and delivery via **store and forward switching**.

# III. Switching Methodologies

- **Cut-through Switching:** An early method where a switch reads the destination address at the very beginning of a data stream and starts forwarding it immediately (even before receiving the full packet). This is fast but cannot detect corrupted data.
- **Store and Forward Switching:** The switch buffers and stores the entire packet in memory. It then inspects the data for corruption and discards bad frames before forwarding them. Most modern switches utilize this method.

# IV. DARPA and the Development of TCP/IP

- **Interconnecting Networks (1973):** The US Defense Advanced Research Projects Agency (**DARPA**) shifted focus to linking non-homogeneous, unconnected packet networks.
- **Military Resiliency:** The goal was to interconnect radar defense systems into a redundant network so that if one node was destroyed, missile warnings could still travel through alternative paths.
- **Standardization:** DARPA requested quotes from companies for a standardized way to handle addressing and headers.
- **TCP/IP:** This suite of protocols was the response to DARPA's request and remains the de facto standard today. While originally one program, TCP (transmission control) and IP (routing/addressing) were eventually split into standalone protocols.

# V. Internet Protocol Version 4 (IPv4) Overview

- **Usage:** IPv4 has been the predominant standard for decades. While IPv6 is gaining traction, IPv4 still runs on the vast majority of devices as of 2019.
- **OSI Model:** IPv4 resides at **Layer 3 (Network Layer)**.
- **Connectionless Protocol:** IP does not verify if a destination is alive or ready before sending data, nor does it provide acknowledgments that the data arrived.
- **Lack of Reliability:** IP has no inherent reliability or verification; it relies on upper-layer protocols (like TCP) for those features.
- **Encapsulation:** IP provides an encapsulation method—a **header** or wrapper—that allows data to be transmitted across routed networks.

# VI. IPv4 Header Fields and Functions

When data is passed from upper layers (TCP/UDP), IP adds its own unique header to create an **IP packet**.

- **Version (4 bits):** Identifies the protocol version; binary "0100" indicates **IP version 4**.
- **Header Length (IHL) (4 bits):** Tells the receiver where the IP header ends and the next header (TCP/UDP) begins.
    - It represents the number of **32-bit words** in the header.
    - A value of "5" indicates five 32-bit words, which equals 20 bytes (the size of a standard IPv4 header).
- **IP Options:** A rare, variable-size field that can make the header larger. If present, it often suggests malicious activity or someone trying to bypass security.
- **Differentiated Services (ToS) (8 bits):** Also called the "Type of Service" (toss) field, it represents the packet's relative **priority**.
    - It defaults to all zeros (lowest priority).
    - Higher numbers allow network devices with **Quality of Service (QoS)** to prioritize traffic, such as voice data from an IP phone.
- **Total Length:** The size of the entire IP packet, including the header and all data behind it.
- **Identification (ID):** A unique random number assigned to every packet created by a host. It is primarily used during the fragmentation process.
- **Time to Live (TTL) (8 bits):** Prevents packets from circling infinitely in a **routing loop**.
    - Each router (hop) the packet hits decrements this number by one.
    - If the TTL reaches zero, the router kills the packet. The maximum value is 255.
- **Protocol:** A registered number identifying the upper-layer protocol carried in the packet.
    - **UDP** is protocol 17; **TCP** is 6; **ICMP** (ping) is 1; **IGMP** (multicasting) is 2.
- **Header Checksum:** An integrity check that runs a formula on all header bits. The destination runs the same formula; if the results don't match, the packet is discarded as corrupted.
- **Source/Destination Address:** The 32-bit addresses for the sender and receiver.

# VII. Fragmentation and Reassembly

- **Maximum Transmission Unit (MTU):** The largest frame size allowed on a network. For wired Ethernet, this is typically **1518 bytes**.
- **The Fragmentation Process:** If a router receives a packet (e.g., 1500 bytes) but the outgoing interface only supports a smaller MTU (e.g., 500 bytes), the router cuts the packet into smaller **fragments**.
- **Identification:** All fragments of the same original packet share the same ID number so the receiver can recombine them.
- **Flags (More Fragments Bit):** This bit is set to "1" on all fragments except the very last one, which is set to "0".
- **Fragment Offset:** Indicates how many bytes away from the start of the original packet a fragment is.
    - An offset of **zero** identifies the beginning of the packet.
    - This allows the receiver to reorder fragments that arrive out of sequence.

---
