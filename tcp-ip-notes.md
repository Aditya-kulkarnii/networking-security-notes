# TCP/IP and 3-Way Handshake — My Notes

## What is TCP/IP?

TCP/IP is the foundation of all data transmission over the internet.
It is actually two protocols working together:

- **IP (Internet Protocol)** — gives every device a unique identity
  (IP address) on the network. This identity is what makes it possible
  to send a packet from a source device to a specific destination device
  anywhere in the world. Without IP, there is no addressing — packets
  would have nowhere to go.

- **TCP (Transmission Control Protocol)** — controls HOW that data
  travels. It breaks data into packets, ensures every packet arrives,
  confirms delivery, and re-sends anything that gets lost. TCP is why
  you can download a file and it arrives complete — not corrupted or
  missing pieces.

Together: IP handles the addressing (WHERE to send),
TCP handles the reliability (HOW it gets there safely).

---

## The TCP 3-Way Handshake

Before any data is sent, TCP establishes a connection using a
3-step process called the 3-way handshake.

### Step 1 — SYN (Client → Server)
The client sends a SYN (synchronize) packet to the server.
Message meaning: "I want to connect to you."

### Step 2 — SYN-ACK (Server → Client)
The server responds with a SYN-ACK (synchronize-acknowledge) packet.
Message meaning: "I received your request. I am ready. Please confirm."

### Step 3 — ACK (Client → Server)
The client sends a final ACK (acknowledge) packet back to the server.
Message meaning: "Confirmed. Connection is now open."

Only after all 3 steps are complete does actual data transfer begin.

---

## Why This Matters for Security

### SYN Flood Attack
An attacker abuses the handshake by sending thousands of SYN packets
to a server — but never sending the final ACK.

The server allocates memory for each half-open connection, waiting
for an ACK that never comes. Eventually the server's connection table
fills up completely and it can no longer accept connections from
legitimate users. This is a Denial of Service (DoS) attack.

**Defense:** SYN Cookies — the server does not allocate memory until
the final ACK arrives. Fake connections cost it nothing.

### TCP vs UDP
- TCP — reliable, connection-oriented, slower (used for web, email, file transfer)
- UDP — faster, no handshake, no guarantee of delivery (used for video, DNS, gaming)
- Attackers often prefer UDP for flooding attacks because it has no
  connection overhead — they can send massive volumes with no setup cost.

---

## What I Practiced
- Studied the full TCP/IP protocol stack
- Understood how IP addressing enables packet routing
- Traced the complete 3-way handshake step by step
- Learned how the SYN flood attack exploits the handshake mechanism
- Understood the difference between TCP and UDP and their security implications

---
*learning journey series*


*Role: Technical Associate @ Intime Solutions, Bangalore*
