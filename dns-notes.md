# DNS — Domain Name System — My Notes

## What is DNS?
DNS (Domain Name System) is the internet's address book.
It translates human-readable domain names like `google.com`
into IP addresses like `142.250.190.46` that computers use
to communicate with each other.

Without DNS, you would have to memorize the IP address of
every website you want to visit. DNS makes the internet usable.

---

## How DNS Resolution Works — Step by Step

### Step 1 — You type a domain
You type `google.com` in your browser and press Enter.

### Step 2 — Browser and OS check their cache
Before making any network request, your browser checks if it
already knows the IP address for `google.com` from a previous
visit. If found in cache — it skips all the steps below and
goes straight to loading the page. This is why revisiting
sites feels faster.

### Step 3 — Asks the DNS Resolver
If not in cache, your OS sends a query to a DNS Resolver
(usually provided by your ISP or a public one like 8.8.8.8
which is Google's resolver). The resolver is the middleman
that does all the heavy lifting.

### Step 4 — Resolver queries the chain
If the resolver does not have the answer cached, it asks:

- **Root Server** — knows where all Top Level Domain (TLD)
  servers are. Does not know google.com's IP but knows who
  manages `.com` domains.

- **TLD Server** — manages `.com`, `.org`, `.in` etc.
  Knows which authoritative server handles `google.com`
  specifically.

- **Authoritative Name Server** — Google's own DNS server.
  This is the final authority. It has the actual IP address
  for `google.com` and returns it.

### Step 5 — IP address returned
The resolver receives the IP address, caches it for future
use, and returns it to your browser.

### Step 6 — Browser loads the website
With the IP address now known, your browser:
- Establishes a TCP connection
- Performs TLS handshake (for HTTPS)
- Sends an HTTP GET request
- Server sends back HTML, CSS, JavaScript
- Browser renders the page

---

## DNS Record Types

| Record | Purpose | Example |
|--------|---------|---------|
| A | Maps domain to IPv4 address | google.com → 142.250.x.x |
| AAAA | Maps domain to IPv6 address | google.com → 2607:f8b0::x |
| MX | Mail server for the domain | gmail.com mail server |
| CNAME | Alias — points to another domain | www → google.com |
| TXT | Text records — used for SPF, DKIM | Email verification |
| NS | Name server records | Who is authoritative |

---

## DNS Security Attacks

### DNS Cache Poisoning
An attacker corrupts a DNS resolver's cache with a fake
mapping. Users type `bank.com` but get sent to the
attacker's fake site. They see the real domain name in
their browser but are actually on a malicious server.

**Defense:** DNSSEC — adds cryptographic signatures to DNS
records so resolvers can verify the response is genuine
and has not been tampered with.

### DNS Tunneling
Attackers encode data inside DNS queries and responses to
secretly communicate with command-and-control servers or
exfiltrate stolen data. Since most firewalls allow DNS
traffic (port 53) without deep inspection, this slips
through basic defenses.

**Defense:** Palo Alto's DNS Security subscription detects
abnormally long or frequent DNS queries that indicate
tunneling. NGFW with App-ID can identify DNS tunneling
traffic specifically.

### Typosquatting
Attackers register domains like `gooogle.com` or
`paypa1.com` to catch users who mistype URLs.

**Defense:** URL filtering and user awareness training.

---

## Key Takeaway
DNS is silent infrastructure that every internet connection
depends on. Because it was designed decades ago with no
built-in security, it is one of the most abused protocols
in cybersecurity. Understanding how DNS works is essential
for understanding how attacks like phishing, C2
communication, and data exfiltration actually function.

---
*learning journey*

*Role: Technical Associate @ Intime Solutions, Bangalore*
