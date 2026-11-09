# Day 08 – DNS Traffic Analysis with Wireshark

## Objective
To understand DNS resolution and analyze DNS queries and responses using Wireshark.

## Environment
- OS: Kali Linux
- Tool: Wireshark 4.6.6
- Interface: eth0
- DNS Server: 10.11.207.137

## 1. DNS Query Analysis

### Command
```bash
nslookup example.com
```

### Wireshark Filter
```text
dns
```

### Observations
- DNS query captured successfully.
- Query Name: example.com
- Query Type: A
- Questions: 1
- Answers: 0
- Transaction ID: 0x1d74

## 2. DNS Response Analysis

### Observations
- Standard DNS query response captured.
- Status: No error
- Answer RRs: 1
- Response time: Approximately 70.386 ms
- IPv6 address observed in AAAA response:
  2606:4700:83b5:72db:f242:4b5f:ef6b:ff98
- TTL observed: 16 seconds

## 3. A and AAAA Record Comparison

### A Record
```bash
nslookup -type=A example.com
```

Observed IPv4 addresses:
- 104.20.23.154
- 172.66.147.243

### AAAA Record
```bash
nslookup -type=AAAA example.com
```

Observed IPv6 address:
- 2606:4700:83b5:72db:f2a7:4b5f:ef6b:ff98

## 4. Important DNS Wireshark Filters

| Filter | Purpose |
|---|---|
| dns | All DNS packets |
| dns.flags.response == 0 | DNS queries |
| dns.flags.response == 1 | DNS responses |
| dns.qry.type == 1 | A queries |
| dns.qry.type == 28 | AAAA queries |
| dns.qry.name == "example.com" | Domain-specific queries |
| udp.port == 53 | UDP port 53 traffic |

## 5. Key Learnings
- DNS translates domain names into IP addresses.
- A records provide IPv4 addresses.
- AAAA records provide IPv6 addresses.
- DNS queries and responses can be inspected in Wireshark.
- DNS commonly uses UDP port 53.
- TTL indicates how long a DNS record may be cached.
- DNS transaction IDs help correlate queries and responses.

## Conclusion
Successfully captured and analyzed DNS queries and responses using Wireshark. Practiced A and AAAA record resolution and understood how DNS translates domain names into IP addresses.

Day 8/90 – Completed
