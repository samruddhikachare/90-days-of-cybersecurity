# Day 6 — TCP Traffic Analysis with Wireshark

## Objective

Understand TCP communication, connection establishment, TCP flags, and connection termination using Wireshark.

## Environment

- OS: Kali Linux
- Tool: Wireshark 4.6.6
- Interface: eth0
- Traffic: HTTPS connection to example.com

## Lab 1: Capture TCP Traffic

Generated HTTPS traffic using:

```bash
curl -I https://example.com
```

Applied the Wireshark display filter:

```text
tcp
```

### Observations

- Client IP: `10.0.2.15`
- Server IP observed: `172.66.147.243`
- Client port observed: `33302`
- Server port: `443`
- TLSv1.3 traffic was visible after connection establishment.

## Lab 2: TCP Three-Way Handshake

Observed the following packets:

1. SYN — Client requests a connection.
2. SYN-ACK — Server acknowledges and responds.
3. ACK — Client acknowledges the server response.

### TCP Flags

| Flag | Meaning                           |
| ---- | --------------------------------- |
| SYN  | Initiates a TCP connection        |
| ACK  | Acknowledges received information |
| FIN  | Graceful connection termination   |
| RST  | Abrupt connection reset           |

## Lab 3: TCP Connection Termination

Used the display filter:

```text
tcp.flags.fin == 1
```

Observed FIN packets associated with connection closure.

Used the display filter:

```text
tcp.flags.reset == 1
```

No RST packets appeared in the capture. This was normal because the observed connection did not necessarily require an abrupt reset.

## Important Wireshark Filters

| Filter                 | Purpose                                |
| ---------------------- | -------------------------------------- |
| `tcp`                  | Display TCP traffic                    |
| `tcp.flags.syn == 1`   | Display packets with SYN set           |
| `tcp.flags.ack == 1`   | Display packets with ACK set           |
| `tcp.flags.fin == 1`   | Display packets with FIN set           |
| `tcp.flags.reset == 1` | Display packets with RST set           |
| `tcp.port == 443`      | Display TCP traffic involving port 443 |

## Key Takeaways

- TCP provides reliable and ordered communication.
- The TCP three-way handshake establishes connections.
- TCP flags help identify connection establishment and termination.
- HTTPS commonly uses TCP port 443.
- TLS encrypts application communication.
- Wireshark helps inspect real network packets.

##
