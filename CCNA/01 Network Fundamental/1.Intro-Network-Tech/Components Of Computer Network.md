
## I. What is a Computer Network?

- **Definition:** At its core, a network consists of two or more devices that need to share information and are connected by a common medium.
- **The Evolution of Networking:**
    - **Sneakernet:** Before modern networking, users shared data by copying it to floppy disks and physically walking it to another computer.
    - **Original Wired Networks:** Early networks used a single shared cable. Because it was a shared medium, only one person could talk at a time to avoid collisions (where multiple devices transmit simultaneously). This was not scalable for many users.
    - **Modern Wired Networks:** Bridges (now called switches) were introduced to give each device its own dedicated cable, allowing simultaneous communication and intelligent data forwarding.
- **Why Networks are Necessary:** They allow for the efficient exchange of data without physical movement, enabling the sharing of files, programs, and shared resources like network-based printers.

## II. Core Networking Vocabulary and Concepts

- **Nodes vs. Hosts:**
    - **Node:** Any device connected to a network, including infrastructure like routers, switches, and access points.
    - **Host:** A specific type of node that either creates or is the ultimate destination for data (e.g., laptops, smartphones, servers). Network infrastructure devices are generally not considered hosts because they merely transport data.
- **Local vs. Remote Resources:**
    - **Local Resources:** Data or hardware accessible without a network connection (e.g., a local hard drive, keyboard, or DVD ROM).
    - **Remote Resources:** Data or hardware that requires a network connection to access (e.g., Facebook, files on a server, or a network printer).
- **LAN vs. WAN:**
    - **Local Area Network (LAN):** A network confined to a small geographic area like a single building. The network administrator has complete control over the cables and equipment.
    - **Wide Area Network (WAN):** Used to connect networks over vast distances (e.g., between different states). Because it is impossible for a private entity to lay cables across such distances, companies rent WAN services from providers like AT&T or Comcast.
- **The Internet:** An interconnection of billions of networks globally, previously referred to as the "World Wide Web".
- **Internet Service Provider (ISP):** Companies (e.g., Time Warner, AT&T, Sprint) that provide the connection to the global internet for a monthly fee.

## III. Clients and Servers

- **Clients:** Devices like smartphones and laptops used to request data from remote systems.
- **Servers:** High-powered computers designed to store data and handle requests from many clients simultaneously. They have faster CPUs and much larger memory than standard clients.
- **Data Center:** A secure, centralized location where stacks of servers are stored to protect and manage a company's data.
- **Peer-to-Peer Networking:** A less common setup where clients exchange data directly with each other (e.g., music sharing) without a centralized server.

## IV. Network Hardware Components

- **Network Interface Card (NIC):** The physical component in a device that allows it to connect to the network.
    - **Wired NICs:** Often use an RJ45 (Registered Jack 45) connector for Ethernet cables.
    - **Coaxial NICs:** Used for cable modems, featuring a thick wire and SMA (Sub-Miniature version A) connectors.
    - **Wireless NICs:** Contain a transceiver (transmitter and receiver) and an antenna, which is often built into the device's case.
- **Modem**: Device used to modulate and demodulate aka digital to analog and analog to digital.
- **Ethernet Cables:** Unlike coaxial cables, these contain several small wires twisted together in pairs.
- **Switches:** Devices that connect multiple hosts in a wired network via "ports." They range from small 8-port home switches to high-end enterprise switches like the Cisco Nexus 9508, which can cost hundreds of thousands of dollars.
- **Routers:** Devices that connect different network segments (e.g., marketing, engineering). They can handle various cable types through removable modul  es and have the intelligence to prioritize traffic and optimize paths.

## V. Network Security: Firewalls and IPS

- **Firewalls:** Devices that segment networks (e.g., inside vs. outside) and control data flow based on rules.
    - **Traditional Firewalls:** Make forwarding or blocking decisions based primarily on source and destination addresses.
    - **Next-Generation Firewalls (NGFW):** Offer advanced features like Deep Packet Inspection (DPI), Application Awareness (e.g., blocking gaming while allowing web browsing), and the ability to receive real-time threat updates from outside services like Cisco.
- **Intrusion Prevention System (IPS):** Deeply inspects data to spot and kill malicious attacks. While once separate boxes, IPS capabilities are now commonly built into NGFWs like the Cisco ASA 5500-X or the Firepower 9000.

## VI. Wireless Networking (Wi-Fi)

- **Access Point (AP):** A device that picks up radio frequencies from wireless clients and puts that data onto the wired network.
- **Association:** The process where a Wi-Fi client sends a frame to an AP to request a connection to a specific network.
- **AP Management Models:**
    - **Autonomous (Standalone):** Each AP is configured individually via its own web page. This is not scalable for large companies.
    - **Wireless Controller:** A centralized box used to manage and program groups of APs simultaneously, including handling client authentication.
    - **Cloud-Based Management:** A subscription service (e.g., Meraki) where the controller is reachable via the internet rather than being a physical appliance on-site.

## VII. Cisco DNA Center

- **Definition:** A centralized management dashboard (appliance) for the entire network, including routers, switches, and APs.
- **Intent-Based Networking:** The ability to dynamically adjust and optimize the network based on current business needs or application requirements rather than just the physical layout.
- **Key Capabilities:**
    - **Design:** Creating topology maps and diagrams.
    - **Golden Images:** Identifying and deploying a standardized, tested version of software across all devices.
    - **Centralized Updates:** The ability to push software updates to access points, routers, and switches from a single location.
    - **Single Pane of Glass:** Providing a comprehensive view and control of the entire network architecture through one GUI.

## Key Terms

- **Appliance:** A physical hardware device designed for a specific task (e.g., a wireless controller).
- **Collision:** An error that occurs when two devices on a shared medium attempt to talk at the same time.
- **DNA Center:** Digital Network Architecture Center; Cisco's centralized network management platform.
- **Golden Image:** A standardized, bug-free software version selected for organization-wide deployment.
- **Host:** A node that originates or terminates data on a network.
- **LAN:** Local Area Network; a network confined to a small geographic area.
- **NIC:** Network Interface Card; the hardware required to connect a device to a network.
- **RJ45:** The standard connector type for Ethernet cables.
- **Transceiver:** A component capable of both transmitting and receiving information.
- **WAN:** Wide Area Network; a network spanning vast distances, typically using leased infrastructure.