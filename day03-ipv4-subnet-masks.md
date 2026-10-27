# Day 3 — IPv4 Addresses and Subnet Masks

**Challenge:** 90 Days of Cybersecurity
**Environment:** Windows + Kali Linux (VirtualBox)

## Objective

Understand IPv4 addresses, subnet masks, network addresses, and default gateways by inspecting real network configurations.

## Concepts Learned

- **IPv4 Address:** A 32-bit address written as four decimal octets separated by dots.
- **Subnet Mask:** Identifies the network portion and host portion of an IPv4 address.
- **CIDR Notation:** `/24` means the first 24 bits are the network prefix.
- **Network Address:** Identifies a subnet.
- **Default Gateway:** The next hop used to reach destinations outside the directly connected network.

## Practical Work

### 1. Windows

**Command:** `ipconfig`

**Observed configuration:**

- IPv4 address: `192.168.56.1`
- Subnet mask: `255.255.255.0`
- Default gateway: Not shown for the displayed adapter

**What I learned:** The subnet mask `255.255.255.0` corresponds to `/24`. The displayed address and mask identify the network `192.168.56.0/24`.

### 2. Kali Linux

**Commands:**

```bash
ip -br addr
ip route
```

**Observed configuration:**

- Interface: `eth0`
- IPv4 address and prefix: `10.0.2.15/24`
- Network: `10.0.2.0/24`
- Default gateway: `10.0.2.2`

**What I learned:** `ip -br addr` displays network interfaces and their assigned addresses. `ip route` displays routing information, including the default route.

### 3. Subnet Calculation Practice

**Example:** `192.168.1.25/24`

- Subnet mask: `255.255.255.0`
- Network address: `192.168.1.0`
- Host portion: `25`

## Key Takeaways

- IPv4 addresses contain 32 bits divided into four octets.
- A `/24` prefix corresponds to the subnet mask `255.255.255.0`.
- For a standard `/24` subnet, the network address ends in `.0`.
- The default gateway helps route traffic to destinations outside the local subnet.
- Windows and Kali can use different private networks in a virtualized environment.

##
