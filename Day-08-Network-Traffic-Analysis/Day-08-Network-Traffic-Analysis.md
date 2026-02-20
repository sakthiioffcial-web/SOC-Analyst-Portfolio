# Day 8 Portfolio — Network Traffic & Ping Behavior

## Objective

Understand outbound and inbound network traffic, and identify normal vs unreachable responses using ICMP (ping).

---

## Environment

* Kali Linux (VMware)
* Terminal, tcpdump

---

## Step 1 — Observing Normal Ping

### Command Used

```bash
ping -c 5 8.8.8.8
```

### Purpose

To observe normal outbound traffic and ICMP responses.

### Observation

* ICMP echo requests sent from local machine
* ICMP echo replies received from destination
* Traffic successfully reached the destination

---

## Step 2 — No Reply Scenario

### Command Used

* Disconnect network cable / ping offline host

### Purpose

To observe what happens when the destination does not respond.

### Observation

* Echo requests sent
* No replies received
* Could be cable unplugged, host down, or firewall silently dropping

---

## Step 3 — Local Unreachable Scenario

### Command Used

* Ping blocked by local gateway/firewall

### Purpose

To simulate a local block and observe ICMP unreachable response.

### Observation

* Echo requests sent
* Local gateway (192.168.127.1) replied: `Destination unreachable`
* Traffic never left local network
---

## Step 4 — Remote Unreachable Scenario

### Command Used

* Ping destination configured to reject requests

### Purpose

To simulate remote block and observe ICMP unreachable response.

### Observation

* Echo requests sent
* Destination host replied: `Destination unreachable`
* Traffic reached remote host
* Remote side rejected the communication

---

## Key Learning Points

* Source IP, destination IP, protocol, and direction are fundamental to network analysis
* No reply, local unreachable, and remote unreachable are distinguishable by **sender IP** of the ICMP response
* ICMP provides clear evidence of network behavior even if traffic is blocked or refused
* Observation and structured reasoning are the foundation for SOC traffic analysis

---

## Skills Developed

* Understanding packet flow (source → destination)
* Using ping and tcpdump for network observation
* Identifying different network failure scenarios
* Basic logical reasoning for SOC analysis

---

## Conclusion

Practiced observing network traffic under different scenarios. Learned to distinguish between normal replies, local blocks, and remote rejections, laying the foundation for network threat detection.
