# SYN-Flood-DoS-Attack# SYN Flood DoS Attack Analysis

## Overview

This project documents a hands-on analysis of a SYN Flood Denial-of-Service (DoS) attack captured in a network traffic log. Using tcpdump for packet capture and Wireshark for visual analysis, I traced the attack from its first entry in the logs through to full service disruption — and documented exactly how it worked at the TCP protocol level.

---

## Objectives

- Identify the attack type from raw packet capture logs
- Trace the TCP three-way handshake breakdown in real time
- Classify the attack and explain the mechanism technically
- Recommend defensive mitigations

---

## Tools Used

| Tool | Purpose |
|------|---------|
| tcpdump | Live packet capture from the network interface |
| Wireshark | Log organisation, colour-coding, and visual traffic analysis |

---

## Key Log Findings

| Log Entries | What I Observed |
|-------------|----------------|
| #47–#51 | Legitimate users completing full handshakes — server functional |
| #52 onward | 203.0.113.0 begins sending continuous SYN packets — never completes handshake |
| #73, #77, #80, #85 | Server sends RST, ACK to real users — backlog saturated |
| #77 | First 504 Gateway Timeout error — service degraded |

---

## Recommended Mitigations

1. **Enable SYN Cookies** — prevents backlog allocation until full handshake is verified
2. **Configure Rate Limiting** — cap SYN packets per second per source IP
3. **Deploy WAF / DDoS Protection** — absorbs flood traffic upstream
4. **Reduce SYN-RECEIVED Timeout** — clears half-open connections faster
5. **Implement IP Reputation Filtering** — block known malicious IP ranges at the firewall

---

## Skills Demonstrated

- TCP/IP protocol analysis
- Packet capture log reading (tcpdump)
- Traffic visualisation (Wireshark)
- DoS attack classification
- Incident report writing
- Security control recommendations

---

*Popoola Moses · Google Cybersecurity Certificate Program*
