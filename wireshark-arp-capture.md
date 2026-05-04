# Wireshark — ARP Packet Capture Session

## Setup
- OS: Kali Linux (VirtualBox VM)
- Interface: WiFi
- Focus: ARP traffic analysis

---

## Filters Used and What I Saw

### Filter: `arp`
Showed all ARP traffic on the network — both requests
and replies combined. Immediately visible that ARP
traffic happens constantly in the background, even
when I am not actively doing anything.

Each packet showed:
- Source MAC address (who is asking or replying)
- Destination MAC address (broadcast FF:FF:FF:FF:FF:FF
  for requests, specific MAC for replies)
- The IP address being queried or claimed

### Filter: `arp.opcode == 1`
Showed only ARP requests — devices broadcasting
"Who has this IP address? Tell me your MAC."

These are always sent to the broadcast address
FF:FF:FF:FF:FF:FF meaning every device on the
LAN receives every ARP request.

### Filter: `arp.opcode == 2`
Showed only ARP replies — devices responding
"I have that IP address. My MAC is XX:XX:XX:XX:XX:XX"

Unlike requests, replies are unicast — sent directly
to the device that asked, not broadcast to everyone.

---

## Terminal Commands

### `arp -a`
Displayed my machine's current ARP cache — every
IP to MAC address mapping stored from recent
network activity.

Showed entries like:
- Gateway IP → Gateway MAC address
- Other devices on the LAN → their MAC addresses

This is exactly the cache that gets poisoned during
an ARP spoofing attack. The attacker's goal is to
replace the legitimate gateway MAC with their own
MAC in this table.

### `ip neigh show`
Alternative command showing the same ARP cache
with additional state information — whether each
entry is REACHABLE, STALE, or FAILED.

REACHABLE = recently confirmed valid
STALE = not recently confirmed, may be outdated
FAILED = could not be reached

---

## Security Insight

Watching ARP in Wireshark made the ARP spoofing
attack completely clear. Because:

1. ARP requests go to EVERYONE on the LAN
   (broadcast) — the attacker receives them too

2. ARP has no authentication — any device can
   send any ARP reply claiming any IP

3. Devices update their cache automatically
   without verifying the reply is genuine

An attacker just needs to send ARP replies faster
than the legitimate device. No special tools needed
beyond basic network access.

The defense (DAI) works at the switch level —
before fake ARP replies ever reach their target.

---

## Filters to Practice Next
| Filter | Purpose |
|--------|---------|
| `arp.duplicate-address-detected` | Spot potential ARP spoofing |
| `arp.src.hw_mac == XX:XX:XX:XX:XX:XX` | Track specific MAC |
| `arp and eth.addr == ff:ff:ff:ff:ff:ff` | Only broadcast ARPs |

---
*learning journey*

*Role: Technical Associate @ Intime Solutions, Bangalore*
