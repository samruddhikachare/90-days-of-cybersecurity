# Day 4 — How Data Travels Across a Network

## Objective

Understand how data reaches a destination using routing, gateways, connectivity tests, traceroute, and DNS.

## Practical Environment

- Operating system: Kali Linux
- Virtualization: VirtualBox
- Network interface: `eth0`
- Kali private IP: `10.0.2.15`
- Default gateway: `10.0.2.2`

## Commands Practised

### 1. Inspect the routing table

```bash
ip route
```

Observed the default route through `10.0.2.2` and the directly connected network `10.0.2.0/24`.

### 2. Test the gateway

```bash
ping -c 4 10.0.2.2
```

Result: 4 packets received, 0% packet loss.

### 3. Test external IP connectivity

```bash
ping -c 4 1.1.1.1
```

Result: 4 packets received, 0% packet loss. Average response time was approximately 50.4 ms during this test.

### 4. Investigate network hops

```bash
traceroute 1.1.1.1
```

The first hop was the VirtualBox gateway. Later UDP probes timed out.

### 5. Compare ICMP traceroute

```bash
traceroute -I -m 12 -w 2 1.1.1.1
```

The destination responded in the first reported hop. This does not mean the real network path contains only one router; intermediate devices may not return traceroute responses.

### 6. Perform DNS lookups

```bash
nslookup google.com
```

Observed the configured DNS resolver and multiple IPv4 and IPv6 addresses for the domain.

### 7. Query Google Public DNS

```bash
nslookup google.com 8.8.8.8
```

The output identified `8.8.8.8` as the DNS server and returned address records for `google.com`.

## Key Concepts Learned

- Routing tables and default gateways
- Private IP addresses and VirtualBox NAT
- Connectivity testing using ping
- Traceroute, TTL, and hop responses
- DNS resolution and public DNS resolvers
- IPv4 versus IPv6
- Why traceroute timeouts do not always indicate network failure

## Cybersecurity Connection

Networking knowledge helps with troubleshooting, understanding packet paths, analyzing DNS activity, and investigating suspicious connections.

## Reflection

Today I practised networking commands in Kali Linux and compared their actual outputs. I learned that successful connectivity tests, DNS resolution, and traceroute results each provide different information about a network.

##
