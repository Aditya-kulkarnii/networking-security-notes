# ARP and DHCP — Protocols and Attacks

## ARP — Address Resolution Protocol

### What is ARP?
ARP maps IP addresses to MAC addresses within a local network.
When a device wants to communicate with another device on the
same LAN, it knows the destination IP address but needs the
MAC address to actually deliver the frame.

ARP broadcast: "Who has IP 192.168.1.1? Tell 192.168.1.50"
ARP reply: "192.168.1.1 is at MAC address AA:BB:CC:DD:EE:FF"

The requesting device stores this mapping in its ARP cache
for future use — so it does not have to ask every time.

### The Critical Weakness
ARP has zero authentication. Any device on the network
can send an ARP reply claiming any IP address belongs to
its MAC address — and other devices will believe it and
update their cache without question.

---

## ARP Spoofing Attack — How It Works

ARP spoofing is an attack where a device on the same LAN
sends fake ARP replies to both the victim and the router,
making both believe the attacker's MAC address belongs to
each other's IP address.

### Step by Step

**Step 1 — Attacker sends fake ARP reply to victim**
"Hey victim — the router's IP (192.168.1.1) is at
MY MAC address (attacker's MAC)"
Victim updates its ARP cache with the fake mapping.

**Step 2 — Attacker sends fake ARP reply to router**
"Hey router — the victim's IP (192.168.1.100) is at
MY MAC address (attacker's MAC)"
Router updates its ARP cache with the fake mapping.

**Step 3 — Traffic flows through the attacker**
Now all traffic from victim → router passes through
the attacker first. And all traffic from router →
victim passes through the attacker first.

The attacker is now a Man-in-the-Middle (MITM).
They can read, modify, or redirect every packet
without either the victim or router knowing.

### Why It Works
ARP was designed in 1982 for trusted networks.
It has no cryptographic verification. No digital
signatures. No way to confirm that an ARP reply
is genuine. Any device can claim any identity.

### Defense — Dynamic ARP Inspection (DAI)
DAI is a switch-level security feature that validates
ARP packets against a trusted DHCP snooping table.
If an ARP reply claims a MAC-IP mapping that does not
match the trusted table — the switch drops it.

DAI stops ARP spoofing at the network infrastructure
level before the fake cache entries are ever created.

---

## DHCP — Dynamic Host Configuration Protocol

### What is DHCP?
DHCP automatically assigns IP addresses and network
configuration to devices when they join a network.

When a device connects:
1. Device broadcasts: "I need an IP address" (DHCP Discover)
2. DHCP server responds: "Here, take this IP" (DHCP Offer)
3. Device accepts: "I'll take it" (DHCP Request)
4. Server confirms: "It's yours" (DHCP Acknowledge)

This is called the DORA process — Discover, Offer,
Request, Acknowledge.

### The Critical Weakness
DHCP also has no authentication. Any device can
pretend to be a DHCP server and respond to requests.

---

## DHCP Attacks

### DHCP Starvation
The attacker floods the DHCP server with thousands
of fake DHCP Discover requests using spoofed MAC
addresses — exhausting the entire pool of available
IP addresses.

Result: Legitimate devices that join the network
cannot get an IP address. Network access denied.
This is a Denial of Service attack at the IP layer.

### DHCP Spoofing
After a starvation attack exhausts the real DHCP
server, the attacker sets up a rogue DHCP server.

Now when a new device asks for an IP address,
the rogue server responds first and assigns:
- A valid IP address (so the device connects)
- The attacker's machine as the default gateway
- The attacker's machine as the DNS server

Result: All traffic and all DNS queries from the
victim now route through the attacker. Full MITM
without any ARP spoofing needed.

### Defense — DHCP Snooping
A switch feature that designates specific ports as
"trusted" (connected to the real DHCP server) and
all others as "untrusted."

DHCP Offer and Acknowledge packets coming from
untrusted ports are dropped immediately. Rogue
DHCP servers on untrusted ports cannot respond.

DHCP snooping also builds the trusted IP-MAC mapping
table that Dynamic ARP Inspection relies on.

---

## Key Takeaway
ARP and DHCP were both designed for trusted networks
with no concept of attackers on the LAN. In modern
enterprise networks, both protocols must be protected
by switch-level security features — DAI for ARP and
DHCP snooping for DHCP. These are standard
configurations on any well-secured network switch.

As a network engineer, enabling DAI and DHCP snooping
on every access switch is a baseline security requirement.

---
*learning journey*

*Role: Technical Associate @ Intime Solutions, Bangalore*
