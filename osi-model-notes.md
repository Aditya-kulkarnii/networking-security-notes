# OSI Model — My Notes

## What is the OSI Model?
OSI stands for Open Systems Interconnection. It is a framework that 
breaks down how data travels from one device to another across a network 
into 7 separate layers. Each layer has a specific job, and together they 
describe the complete journey of data from a physical cable all the way 
up to the application a user is interacting with.

## The 7 Layers (Top to Bottom)
- **Layer 7 — Application** — the one which user interacts with (HTTP, DNS, FTP)
- **Layer 6 — Presentation** — data formatting and encryption (SSL/TLS)
- **Layer 5 — Session** — manages sessions between devices (NetBIOS, RPC)
- **Layer 4 — Transport** — reliable data delivery, ports (TCP, UDP)
- **Layer 3 — Network** — IP addressing and routing (IP, ICMP)
- **Layer 2 — Data Link** — MAC addresses, switches (Ethernet, ARP)
- **Layer 1 — Physical** — actual cables, hardware, radio signals

## Why the OSI Model Matters for Security
Every cyberattack happens at a specific layer of the OSI model.
Understanding which layer an attack targets tells you exactly what 
tool or defense is needed to stop it.

For example:
- A **SYN flood attack** targets Layer 4 (Transport) — defense is a stateful firewall
- **ARP spoofing** targets Layer 2 (Data Link) — defense is Dynamic ARP Inspection
- **DNS poisoning** targets Layer 7 (Application) — defense is DNSSEC
- **IP spoofing** targets Layer 3 (Network) — defense is packet filtering and ACLs

A firewall that only works at Layer 3 and 4 cannot stop a Layer 7 attack.
This is exactly why Next-Generation Firewalls (NGFW) like **Palo Alto** operate 
all the way up to Layer 7 — they can see inside application traffic and block 
threats that basic firewalls completely miss.

## Key Takeaway
The OSI model is not just theory. It is the map that tells you 
WHERE in the network an attack is happening and WHAT kind of 
defense belongs there. Every security tool — firewall, IDS, WAF, 
VPN — maps directly to one or more layers of this model.

## What I Did
- Studied all 7 OSI layers and their security relevance
- Learned which attacks happen at which layer
- Understood why NGFWs are more powerful than basic firewalls
- Created this GitHub repository to document my cybersecurity learning journey

---
*Day 1 — Started my cybersecurity learning journey*
*Role: Technical Associate @ Intime Solutions, Bangalore*
