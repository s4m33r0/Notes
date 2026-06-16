# I. Understanding Network Architecture

- **Definition:** Network architecture refers to the design choices regarding which devices to use (switches, routers, access points), how they are interconnected, and their physical location within a building or company.
- **Design Factors:** The chosen architecture dictates the types of cables needed, the length of those cables, the specific path data travels between hosts and servers, and the level of available **redundancy**.
- **Redundancy:** This concept involves creating alternative paths for data to reach its destination if a primary path fails due to a disconnected cable or hardware failure. Higher redundancy means more alternative paths are available.
- **Sourcing:** Architects must decide if they will build the entire network using their own cabling and devices or if they will contract third-party providers for wide-area services.

# II. Campus and Enterprise LAN Architectures

Large and mid-sized companies typically implement tiered architectures within their buildings to manage data flow and device connectivity.

## Three-Tier Architecture

Historically, this was the first major design methodology for LANs, dividing the network into three distinct layers, each with specific responsibilities.

- **Access Layer:** This is the lowest tier where hosts (laptops, PCs, servers, tablets) physically connect to the network.
    - **Common Devices:** Network-based switches and wireless access points.
    - **Responsibilities:** Providing network access and implementing **authentication** to ensure unauthorized devices cannot connect.
- **Distribution Layer:** This middle tier consists of routers or multilayer switches.
    - **Responsibilities:** It is in charge of routing data between different network segments (e.g., from HR to Marketing).
    - **Security:** It implements security features to control which departments can communicate with one another (e.g., allowing HR to talk to Marketing but blocking them from Payroll).
- **Core Layer:** This is the top tier, designed to be a super-fast layer that moves data between major sections of the network, such as between two separate buildings.
    - **Responsibilities:** It focuses on extremely fast switching without the delays caused by data inspection or complex routing.
    - **Design Goal:** Any process that might slow down data, such as security inspection, should happen at the distribution layer so the core layer remains unencumbered.

![[Tier - 3.png]]

## Two-Tier (Collapsed Core) Architecture

Modern networking devices have gained enough functionality that the core and distribution layers can often be merged.

- **Structure:** In this model, the distribution and core layers are handled by a single tier of devices.
- **Common LAN Characteristics:** Both tiered models aim to accommodate diverse connection types (Ethernet, Wi-Fi, Bluetooth) while keeping user connections streamlined and easy to use.

![[Tier - 2.png]]

# III. Data Center Architecture: Spine-Leaf

While campus networks focus on host connectivity, **data centers** house mission-critical file servers and require a more resilient architecture known as **spine-leaf**.

- **Spine Switches:** These represent the top layer of the data center network. They are extremely expensive, high-performance devices built with multiple power supplies for maximum resiliency.
- **Leaf Switches:** These represent the bottom layer and connect directly to the servers.
- **The Fabric:** The term "fabric" refers to the highly redundant interconnection of spine and leaf switches.
- **Connectivity:** Every leaf switch has a physical connection to every spine switch.
- **Traffic Pattern:** This architecture is optimized for **East-West traffic**, which describes data moving horizontally between servers within the data center, rather than North-South traffic moving in and out of the network.

![[Spine Leaf.png]]

# IV. Wide Area Network (WAN) Architectures

WANs are used to connect offices across cities, states, or countries, and they generally fall into three categories.

- **Point-to-Point:** This is a direct connection between two specific points (e.g., Boston and New York). Data placed on one end can only go to the other end. Adding a third location (e.g., Raleigh) requires additional physical interfaces and cables on the routers.

![[PTP.png]]

- **Broadcast-Based (e.g., Metro Ethernet):** Sites connect to a shared medium, often a **fiber optic ring** carrying laser light.
    - **ISP Role:** The Internet Service Provider (ISP) owns the ring and the switches placed in customer buildings.
    - **Data Handling:** While every ISP switch on the ring physically sees the broadcasted data, the ISP switches are configured to block data from entering a customer's private switch unless it is addressed to them.

![[Broadcasr.png]]

- **Non-Broadcast Multi-Access (NBMA):** This allows a single physical connection to reach multiple remote locations through a provider's "cloud".
    - **Addressing:** Data is assigned a specific address (e.g., 101 or 301). The WAN provider uses this address to ensure the data only pops out at the intended destination site.
    - **Efficiency:** Unlike point-to-point, you do not need a separate physical cable for every remote site you wish to reach.

![[nbma.webp]]

# V. Small Office/Home Office (SOHO)

SOHO architectures are designed for smaller, simpler environments like a home or a small branch office.

- **Hardware:** These typically require minimal equipment, such as a single router or switch.
- **Security:** There is often less need for complex authentication because the owner controls all devices in the space.
- **Management Challenges:** It is difficult for corporate headquarters to manage these networks or enforce security policies because the remote hardware is often not under the direct control of the central network administrator.

# VI. On-Premises vs. Cloud-Based

These terms describe where a company's resources are physically located and who is responsible for them.

- **On-Premises:** All devices (servers, routers, switches) are located within the company's building. The company is responsible for the physical space, electricity, air conditioning, cabling, and software maintenance.
- **Cloud-Based:** Resources like servers are rented from a provider (e.g., Amazon AWS) and accessed via the internet.
    - **Provider Responsibility:** The cloud provider handles hardware repairs, patching, cooling, and cabling.
    - **Benefit:** This removes the physical maintenance burden from the company and allows multiple offices to access a single central set of resources easily