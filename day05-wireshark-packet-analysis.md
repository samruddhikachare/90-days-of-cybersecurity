# Day 5 — Network Traffic Analysis with Wireshark

## Objective
Capture and analyze network traffic using Wireshark to understand ICMP communication and DNS resolution.

## Environment
- Operating System: Kali Linux
- Virtualization: VirtualBox
- Packet Analyzer: Wireshark 4.6.6
- Network Interface: `eth0`

## Lab 1: Starting a Packet Capture

Opened Wireshark and selected the `eth0` interface to capture live network traffic.

**Learning:** Wireshark captures packets and displays information such as source, destination, protocol, packet length, and packet details.

## Lab 2: Capturing ICMP Traffic

Generated network traffic using:

```bash
ping -c 4 1.1.1.1
```

Applied the Wireshark display filter:

```text
icmp
```

### Observations
- Kali's source IP: `10.0.2.15`
- Destination IP: `1.1.1.1`
- Protocol: ICMP
- Captured Echo Requests and Echo Replies

### ICMP Types
- Type 8: Echo Request
- Type 0: Echo Reply

**Learning:** ICMP is used by tools such as `ping` to test network reachability.

## Lab 3: Capturing DNS Traffic

Generated a DNS lookup using:

```bash
nslookup example.com
```

Applied the Wireshark display filter:

```text
dns
```

### Observations
- DNS query and response packets were visible.
- The configured DNS resolver was `10.158.244.69`.
- The response reported one question and two answer records.
- The displayed A records returned these IPv4 addresses:
  - `104.20.23.154`
  - `172.66.147.243`

### DNS Concepts Learned
- DNS resolves domain names into records containing network information.
- An A record maps a domain name to an IPv4 address.
- DNS queries and responses can be inspected using Wireshark.
- UDP port 53 is commonly used for DNS traffic.

## Important Wireshark Filters

| Filter | Purpose |
|---|---|
| `icmp` | Display ICMP packets |
| `dns` | Display DNS packets |
| `ip.addr == 1.1.1.1` | Display IPv4 packets where the source or destination matches `1.1.1.1` |

## Cybersecurity Relevance

Packet analysis helps cybersecurity professionals:
- Troubleshoot network communication.
- Investigate DNS activity.
- Understand source and destination addresses.
- Recognize expected request-and-response patterns.
- Build a foundation for investigating suspicious network traffic.

## Key Takeaway

Today, I learned how to capture live traffic and inspect ICMP and DNS packets using Wireshark. I connected networking concepts with real packet-level observations.

## Next Steps
Continue practising Wireshark display filters and learn how to interpret packet headers and protocol fields.
