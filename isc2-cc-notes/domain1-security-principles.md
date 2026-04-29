# ISC2 CC — Domain 1: Security Principles

**Domain weight in exam:** 26% (highest weighted domain)
**My competence score:** 100%
**Status:** ✅ Complete

---

## Pre-Assessment Result
Scored 97% on the pre-assessment before starting Domain 1.

---

## Core Concepts Covered

### 1. The CIA Triad
The three fundamental principles that every security decision
is built around:

- **Confidentiality** — ensuring information is only accessible
  to those who are authorized to see it.
  Example: Encryption protects confidentiality.

- **Integrity** — ensuring information is accurate and has not
  been tampered with.
  Example: Hashing verifies file integrity (SHA-256).

- **Availability** — ensuring systems and data are accessible
  when legitimate users need them.
  Example: Redundancy and backups protect availability.

Every security control, policy, and tool maps back to protecting
one or more of these three properties.

---

### 2. Authentication vs Authorization vs Accountability

- **Authentication** — proving who you are (username + password, MFA)
- **Authorization** — what you are allowed to do once identified (permissions)
- **Accountability** — tracking what you did (audit logs)

All three must work together. Authentication without authorization
means anyone logged in can do anything. Authorization without
accountability means no record of who did what.

---

### 3. Non-Repudiation
The inability to deny having performed an action.
Digital signatures provide non-repudiation — they prove a specific
person signed or sent something and cannot deny it later.
Critical in legal and financial security contexts.

---

### 4. Privacy vs Security
- **Security** — protecting organizational assets and data
- **Privacy** — protecting individuals' personal data and rights

They overlap but are not the same. A company can be secure
(no breach) but still violate privacy (misusing customer data).
Both must be addressed separately in enterprise security programs.

---

### 5. Risk Concepts
- **Threat** — anything that could cause harm (attacker, natural disaster)
- **Vulnerability** — a weakness that could be exploited
- **Risk** — the likelihood and impact of a threat exploiting a vulnerability
- **Control** — a measure put in place to reduce risk

Risk = Threat × Vulnerability × Impact

Understanding risk is the foundation of all security decision-making.
You cannot protect everything — you prioritize based on risk.

---

### 6. Security Governance
- Policies — high-level rules (what must be done)
- Standards — specific mandatory requirements (how it must be done)
- Procedures — step-by-step instructions (the exact steps)
- Guidelines — recommended but not mandatory advice

A security program needs all four layers to be effective.

---

## Key Takeaway from Domain 1
Security is not just about technology. It is about people,
processes, and technology working together — guided by clear
principles (CIA), defined roles (authentication/authorization),
and structured governance (policies, standards, procedures).

Every technical control, every firewall rule,
every VPN policy — exists to protect Confidentiality, Integrity,
or Availability of something that matters to the organization.

---
*ISC2 CC — Domain 1 of 5 Complete*
*isc2-cc-notes folder — networking-security-notes repo*
*Role: Technical Associate @ Intime Solutions, Bangalore*
