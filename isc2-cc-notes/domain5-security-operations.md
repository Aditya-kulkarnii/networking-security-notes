# ISC2 CC — Domain 5: Security Operations

**Domain weight in exam:** 18%
**My competence score:** 100%
**Status:** ✅ Complete

---

## Data Security

**Data at rest** — stored data (hard drives, databases)
Protected by: encryption, access controls

**Data in transit** — data moving across a network
Protected by: TLS, VPNs, encrypted protocols

**Data in use** — data being actively processed
Hardest to protect — must control who can access
running systems and active memory

---

## Encryption Basics

**Symmetric encryption** — same key used to encrypt
and decrypt. Fast. Problem: how do you share the key
securely? Example: AES

**Asymmetric encryption** — two keys: public key
encrypts, private key decrypts. Slower but solves
the key sharing problem. Example: RSA

**Hashing** — one-way function, converts data to
a fixed-length string. Cannot be reversed.
Used to verify integrity — if the hash changes,
the data was tampered with. Example: SHA-256

---

## Logging and Monitoring

Logs record everything that happens on a system —
logins, file access, configuration changes, errors.

Security monitoring means watching those logs in
real time for suspicious patterns — failed logins,
unusual access times, large data transfers.

Without logging there is no accountability.
Without monitoring there is no detection.
Logs without monitoring = security camera footage
that nobody ever watches.

---

## Configuration Management

Keeping systems in a known, secure, approved state.

**Baseline configuration** — the approved standard
setup for a system. Any deviation is flagged.

**Patch management** — keeping systems updated
to fix known vulnerabilities. Unpatched systems
are one of the most common causes of breaches.

---

## Best Practice Concepts

**Least privilege** — give users only the minimum
access needed for their job. Already covered in
Domain 3 but applies to operations too.

**Separation of duties** — no single person should
have complete control over a critical process.
Example: the person who requests a payment should
not also be the person who approves it.

**Need to know** — even if a user has the right
clearance level, they should only access information
they specifically need for their current task.

---

## Key Takeaway
Security operations is about maintaining security
day to day — not just setting it up once. Logging,
monitoring, patching, configuration management —
these are ongoing activities, not one-time tasks.
The most secure system in the world becomes
vulnerable the moment it stops being maintained.

---

## ALL 5 DOMAINS COMPLETE

| Domain | Weight | Score |
|---|---|---|
| Domain 1 — Security Principles | 26% | 100% |
| Domain 2 — BC, DR, IR | 10% | 100% |
| Domain 3 — Access Controls | 22% | 100% |
| Domain 4 — Network Security | 24% | 100% |
| Domain 5 — Security Operations | 18% | 100% |
| **Total** | **100%** | **100%** |

---
*ISC2 CC — All 5 Domains Complete*
*isc2-cc-notes folder — networking-security-notes repo*
*Role: Technical Associate @ Intime Solutions, Bangalore*
