# I. Introduction to Power over Ethernet (PoE)

- **Definition:** PoE is a technology that allows a single Ethernet cable to deliver both data and electrical power to a connected device.
- **The Core Problem:** Most network host devices (laptops, printers, IP phones, cameras) require power. Finding a nearby AC outlet for every device is often impractical or impossible due to placement.
- **The Solution:** PoE eliminates the separate AC connector and power cord, using the existing network cabling to drive the device.
- **Target Devices:** While laptops and PCs can use it, it is especially critical for **Internet of Things (IoT)** devices such as IP cameras, thermostats, and IP phones.

# II. Benefits of PoE Technology

- **Time and Cost Savings:** Organizations run fewer cables through walls and ceilings. It also removes the cost of purchasing individual AC adapters for every device.
- **Flexibility:** A device can be placed anywhere an Ethernet cable can reach, regardless of whether a wall outlet is nearby.
- **Safety:** The delivery is "intelligent," designed to protect equipment from overloading, underpowering, or incorrect installation.
- **Reliability through Standardization:** Unlike AC wall jacks which vary by country, PoE uses universal **RJ45** jacks and standard Ethernet cables worldwide, providing a consistent and safe power source.
- **Scalability:** A single 48-port PoE switch can replace 48 individual wall jacks and power bricks, providing a condensed power source that can reach 100 meters in any direction.

![[POE vs No POE.png]]

# III. Hardware Roles: PSE and PD

Every PoE setup categorizes devices into one of two roles defined by international standards:

- **Power Sourcing Equipment (PSE):** The device that "pushes" the power down the wire. This is typically a network switch.
- **Powered Device (PD):** The device at the other end of the cable receiving the power, such as a wireless access point, IP phone, or IP camera.
- **Power Injectors:** These are used when a network switch does not support PoE. They plug into a wall outlet and have two ports: one to receive data from the switch and one to "inject" power into the cable leading to the PD.

# IV. PoE Standards and Power Capacity

As technology has evolved, standards have increased the amount of power that can be delivered:

- **802.3af:** The original standard, providing up to **15.4 watts** per port.
- **802.3at:** A mid-tier standard.
- **802.3bt (UPOE+):** The latest standard (standardized in mid-2018). Cisco’s proprietary implementation of this can deliver up to **90–95 watts** per device.
- **Power Budget:** This refers to the total maximum power a PSE (switch) can deliver across all its ports combined (e.g., a 540-watt budget).
- **Power Dissipation:** Not all power leaving the switch reaches the device; some is lost as heat or electrical resistance within the cabling.

# V. Physical Delivery and Cabling

- **UTP Cabling:** Standard Ethernet cables (Unshielded Twisted Pair) contain **eight wires** twisted into **four pairs**.
- **Wire Utilization:**
    - **Older Standards (802.3af/at):** Utilized two pairs for data and two separate pairs for power.
    - **Modern Standards (802.3bt/UPOE):** Use all **eight wires** (all four pairs) to carry both data and power simultaneously.

# VI. Detection and Negotiation Process

To prevent damaging non-PoE devices like laptops, the PSE follows an intelligent detection process:

1. **Detection Pulse:** When a device is plugged in, the PSE sends a tiny, safe pulse of electricity to check for **resistance**.
2. **Resistor Recognition:** A PD has special resistors that loop power back in a specific, standardized ratio. If the PSE detects this specific ratio, it knows it is safe to send power.
3. **Non-PoE Protection:** If a standard laptop is connected, the pulse is reflected back in full (no resistance), signaling the switch to stay in data-only mode.
4. **Bootstrapping:** Once a PD is identified, the PSE sends just enough power to allow the device to enter a "barebones" booting state.
5. **Software Negotiation:** Once the device has enough power to communicate, it uses protocols like **CDP** (Cisco) or **LLDP** (non-Cisco) to negotiate its exact power range and preferences.

# VII. Monitoring PoE on Cisco Devices

Administrators can use specific Cisco IOS commands to verify power status:

- **show cdp (Cisco Discovery Protocol) neighbor detail**: Shows the "power drawn" (maximum required) and "power request levels." For example, an IP phone might prefer 10.25 watts but can operate at 6.3 watts by reducing its screen brightness.
- **show power inline**: Displays a module's total power budget, how much is used/remaining, and a port-by-port breakdown of wattage and device types.

![[CDP Command.png]]

![[Power iniline cmd.png]]

