I. IPv4 Address Structure and Comparison

- **IPv4 Address (32 bits):** A binary number used to identify the source and destination of packets.
- **Network Portion:** The bits at the beginning of an address that form a common pattern for all devices on a local network.
- **Host Portion:** The remaining bits in the address that uniquely identify a specific device within a network.
- **Local Network Comparison:** Before a device transmits a packet, it compares its source address to the destination address to determine if the destination is on the same local network.
    - If the patterns match, the destination is local.
    - If the patterns differ, the packet must be forwarded to a **router**.

II. Classful Addressing

- **Early Networking (1980s):** Introduced in **RFC 791**, this method used fixed bit patterns to determine the dividing line between network and host bits.
- **Class A:** Any address where the first binary bit is **0**.
    - The network portion is the first **8 bits** (one octet).
- **Class B:** Any address beginning with the bit pattern **10**.
    - The network portion is the first **16 bits** (two octets).
- **Class C:** Any address beginning with the bit pattern **110**.
    - The network portion is the first **24 bits** (three octets).
- **Class D:** Any address beginning with the bit pattern **1110**.
    - Reserved exclusively for **multicasting** destinations.
- **Class E:** Reserved for experimental purposes.
    - This class was never implemented for general use and is rejected as an error by most modern operating systems.
- **Host Addressing:** Only addresses from Classes **A**, **B**, and **C** can be assigned to host devices like laptops, servers, or routers.

III. Classless Interdomain Routing (CIDR) and Subnet Masks

- **Scalability Issues:** Classful addressing became inefficient as the number of networks grew, leading to a shortage of available address space.
- **Subnet Mask (1985):** Introduced in **RFC 950**, it is a **32-bit** binary comparison tool used to arbitrarily define the boundary between network and host bits.
- **CIDR (1993):** **Classless Interdomain Routing** formally deprecated classful addressing, requiring every IP address to be bundled with a subnet mask.
- **Subnet Mask Logic:** A mask consists of a contiguous section of **1s** followed by contiguous **0s**.
    - The number of **1s** (reading left to right) indicates exactly how many bits in the IP address belong to the network.
    - Example: A mask with **12** ones means the first **12 bits** of the IP address are the networking bits.

IV. Route Summarization

- **Manual Summarization:** A network administrator identifies a common bit pattern among multiple networks to advertise them as a single route.
- **Auto-summarization:** A feature in many routing protocols that automatically shrinks routes back to their original **classful boundary**.
    - Example: A router learning multiple **10.x.x.x** networks will summarize them all as **10.0.0.0** because **10** is a **Class A** address.

V. IPv4 Communication Types

- **Unicast:** One-to-one communication between a single source and a single destination.
    - Uses addresses from the **Class A**, **B**, and **C** space.
- **Multicast:** One-to-many communication using **Class D** address space.
    - **Class D Range:** **224.0.0.1** to **239.255.255.255**.
    - The source address is always a **unicast** address, while the destination is a **multicast** address.
    - **NIC (Network Interface Card):** A device's network card is programmed to listen for a specific multicast destination address in addition to its unique unicast address.
- **Broadcast:** One-to-all communication where every device on a network must process the packet.
    - **General Broadcast:** Destination address **255.255.255.255**, used by protocols like **DHCP** (**Dynamic Host Configuration Protocol**) to request an IP address when joining a new network.
    - **Directed Broadcast:** A broadcast targeted at a specific network by setting all host bits to **1s**.
- **Reserved Host Bits:** In any network, the host bits cannot be all **0s** or all **1s**.
    - All **0s** identifies the network itself.
    - All **1s** is reserved for the directed broadcast address.