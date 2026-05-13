# ISC2 CC — Exam Revision Notes

## Security Principles — Key Concepts Revised

### Governance Hierarchy
- Policy — mandatory, high level rules, set by management
- Standard — mandatory, specific measurable requirements
- Procedure — step by step instructions on how to comply
- Guideline — recommended but not mandatory advice

Remember: Policies and Standards are MANDATORY.
Guidelines are NOT mandatory.

### CIA Triad — How to Apply in Exam Questions
Every scenario maps to one of these three:

- Confidentiality — preventing unauthorized access to data
  Example: encryption, access controls, MFA

- Integrity — ensuring data is accurate and not tampered with
  Example: hashing (SHA-256), digital signatures, checksums

- Availability — ensuring systems are accessible when needed
  Example: backups, redundancy, disaster recovery, uptime SLAs

Quick test for any question:
Is it about WHO can see it? → Confidentiality
Is it about WHETHER it was changed? → Integrity
Is it about WHETHER you can access it? → Availability

### Risk Terminology
- Threat — the potential danger (attacker, natural disaster)
- Vulnerability — the weakness being exploited
- Risk — the likelihood and impact of threat exploiting vulnerability
- Control — the measure put in place to reduce risk

Formula: Risk = Threat × Vulnerability × Impact

### BC DR — Key Terms
- RTO (Recovery Time Objective) — how fast must we recover?
- RPO (Recovery Point Objective) — how much data can we lose?
- Hot site — fully operational, immediate takeover, most expensive
- Warm site — partially ready, needs some activation time
- Cold site — empty space, needs full setup, cheapest

---
*ISC2 CC Exam Revision — Key concepts for exam preparation*
*Role: Technical Associate @ Intime Solutions, Bangalore*
