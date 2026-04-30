# Wireshark — DNS Packet Capture Session

## Setup
- OS: Kali Linux (VirtualBox VM)
- Interface: WiFi
- Focus: DNS traffic analysis

---

## What I Did

### Captured live DNS traffic
Started a Wireshark capture and applied the `dns` filter.
Visited multiple websites — google.com, github.com,
paloaltonetworks.com — and watched the DNS queries and
responses appear in real time for each site.

### Followed packet streams
Right-clicked on DNS packets and followed the UDP stream
to see the full conversation between my machine and the
DNS resolver — the query going out and the response
coming back with the IP address.

### Analyzed query and response structure
For each DNS packet I examined:
- The source IP (my machine) and destination IP (DNS resolver)
- Whether it was a query or a response
- The domain name being requested
- The record type being asked for (A record for IPv4)
- The IP address returned in the response

---

## Filters I Used and What They Showed

| Filter | What it showed |
|--------|---------------|
| `dns` | All DNS traffic — queries and responses |
| `dns.qry.name contains "google"` | Only DNS queries containing the word google |
| `dns.flags.response == 0` | Only outgoing queries — my machine asking |
| `dns.flags.response == 1` | Only incoming responses — DNS server answering |
| `dns.qry.type == 1` | Only A record queries — looking up IPv4 addresses |

---

## Key Observations

**1. DNS uses UDP not TCP**
All DNS queries and responses travel over UDP port 53.
UDP is used because DNS queries are small and speed
matters more than reliability. If a query fails, the
resolver simply asks again.

**2. You can read the domain names in plain text**
DNS queries are not encrypted by default. Anyone capturing
traffic on your network can see every domain you are
querying — every website you are about to visit — before
you even load the page. This is why DNS-over-HTTPS (DoH)
was created.

**3. The query-response pattern is clear**
Every DNS lookup follows the same pattern:
- Query: my machine asks "what is the IP of github.com?"
- Response: DNS server answers with the IP address
Both packets visible in Wireshark, matched by transaction ID.

**4. Filters make everything manageable**
Without filters, DNS packets get buried in TCP and other
traffic. Learning to filter precisely is as important as
knowing what to look for.

---

## Security Insight
If I can see all DNS queries in plaintext on Wireshark,
so can an attacker on the same network. This is exactly
how DNS-based attacks like poisoning and tunneling are
set up — the attacker watches DNS traffic first to
understand what the target is querying, then manipulates
or abuses those queries.

---

## Filters to Practice Next
- `dns.resp.ttl < 60` — find suspiciously short TTL records
  (could indicate fast-flux DNS used by malware)
- `dns.qry.name contains "."` and long query names
  (could indicate DNS tunneling)
- `dns and ip.addr == 8.8.8.8` — show only traffic to
  Google's DNS resolver specifically

---
*learning journey*

*Role: Technical Associate @ Inmate Solutions, Bangalore*
