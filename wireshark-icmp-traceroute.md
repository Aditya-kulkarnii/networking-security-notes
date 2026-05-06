# Wireshark — ICMP and Traceroute Capture Session

## Setup
- OS: Kali Linux (VirtualBox VM)
- Interface: WiFi
- Focus: ICMP traffic and TTL behavior

---

## ICMP — Internet Control Message Protocol

ICMP is used by network devices to send error messages
and operational information. It operates at Layer 3.
Ping uses ICMP to test connectivity between devices.

---

## Ping Capture

### What I Did
Ran `ping google.com` in terminal while Wireshark
was capturing with the `icmp` filter applied.

### What I Saw
Wireshark immediately showed two types of packets
appearing in pairs for every ping sent:

**ICMP Echo Request (Type 8)**
My machine asking: "Are you there, Google?"
Source: my IP → Destination: Google's IP

**ICMP Echo Reply (Type 0)**
Google responding: "Yes, I am here."
Source: Google's IP → Destination: my IP

Every ping produced exactly one request and
one reply — visible as a matching pair in Wireshark.

### Filters Used
| Filter | What it showed |
|--------|---------------|
| `icmp` | All ICMP traffic |
| `icmp.type == 8` | Only Echo Requests (pings out) |
| `icmp.type == 0` | Only Echo Replies (responses back) |

---

## TTL — Time to Live

TTL is a value in every IP packet that limits how
many router hops the packet can travel before
being discarded.

Every router that forwards a packet decreases
the TTL by 1. When TTL reaches 0 the router
drops the packet and sends an ICMP "Time Exceeded"
message back to the sender.

**Why it exists:** prevents packets from circulating
forever on the internet if a routing loop occurs.

**Security relevance:** TTL values reveal network
topology. By analyzing TTL you can estimate how
many hops away a device is and sometimes identify
what OS it is running (different OS use different
default TTL values).

---

## Traceroute Capture

### What I Did
Ran `traceroute google.com` while Wireshark captured.

### What Traceroute Does
Traceroute sends packets with deliberately low TTL
values — starting at TTL=1, then TTL=2, TTL=3 and
so on — forcing each router along the path to send
back a "Time Exceeded" ICMP message.

By collecting these messages traceroute builds a
complete map of every router hop between your
machine and the destination.

### What I Saw in Wireshark
Packets being sent with increasing TTL values.
Each router along the path responding with
ICMP Time Exceeded messages as the TTL hit zero
at their hop.

The full path from my machine to Google's servers
mapped out hop by hop — each router's IP visible.

---

## Security Insight

Traceroute is used legitimately for network
troubleshooting. But attackers also use it during
reconnaissance to map network topology — identifying
routers, firewalls, and the structure of a target
network before launching an attack.

This is why some organizations block ICMP at their
perimeter firewall — to prevent external traceroutes
from revealing internal network structure.

---
*learning journey*

*Role: Technical Associate @ Intime Solutions, Bangalore*
