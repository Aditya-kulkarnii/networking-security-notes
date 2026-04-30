# ISC2 CC — Domain 2: Business Continuity, DR and Incident Response

**Domain weight in exam:** 10%
**My competence score:** 100%
**Status:** ✅ Complete

---

## The Big Picture
This domain answers one question:
"What does an organization do when something goes wrong?"

Whether it is a cyberattack, natural disaster, power failure,
or hardware crash — every organization needs a plan to survive,
recover, and continue operating. That is what BC, DR, and IR
are all about.

---

## Business Continuity (BC)

Business Continuity is about keeping the organization
running during and after a disruptive event.

A **Business Continuity Plan (BCP)** documents:
- Which business functions are most critical
- What the minimum acceptable level of operation is
- How to maintain those functions if primary systems fail
- Who is responsible for what during a disruption

Key concept: BC is about the BUSINESS continuing to operate.
It is bigger than just IT — it covers people, processes,
locations, communications, and suppliers too.

---

## Disaster Recovery (DR)

Disaster Recovery is specifically about restoring IT systems
and data after a disruption. It is a subset of BC focused
on technology.

### Two Critical Metrics Every Security Engineer Must Know

**RTO — Recovery Time Objective**
The maximum acceptable time that a system can be down
before it causes unacceptable damage to the business.
Example: "Our payment system must be back online within
4 hours of any outage."
RTO answers: How fast must we recover?

**RPO — Recovery Point Objective**
The maximum acceptable amount of data loss measured in time.
Example: "We can afford to lose no more than 1 hour of
transaction data."
RPO answers: How much data can we afford to lose?

If RPO is 1 hour — you must back up data at least every hour.
If RTO is 4 hours — your recovery process must complete
within 4 hours.

These two numbers drive every backup and recovery decision
in an organization.

### DR Site Types
- **Hot site** — fully operational duplicate, can take over
  immediately. Most expensive.
- **Warm site** — partially set up, needs some time to
  activate. Medium cost.
- **Cold site** — just a physical space with power and
  connectivity, needs full setup. Cheapest but slowest.

---

## Incident Response (IR)

Incident Response is the structured process for detecting,
containing, and recovering from a security incident.

### The IR Lifecycle — 6 Phases

**Phase 1 — Preparation**
Before anything happens. Build the IR team, create playbooks,
set up logging and monitoring, run drills. The organizations
that respond well to incidents prepared before the incident.

**Phase 2 — Detection and Analysis**
Identify that an incident has occurred. Analyze alerts,
logs, and indicators to understand what happened, what
systems are affected, and how serious it is.

**Phase 3 — Containment**
Stop the bleeding. Isolate affected systems to prevent
the attack from spreading further. Short-term containment
(disconnect the compromised machine) and long-term
containment (patch the vulnerability, change credentials).

**Phase 4 — Eradication**
Remove the threat completely. Delete malware, close
backdoors, remove attacker accounts, patch the
vulnerability that was exploited.

**Phase 5 — Recovery**
Restore systems to normal operation. Verify they are
clean before bringing them back online. Monitor closely
for any signs of re-infection.

**Phase 6 — Lessons Learned**
After everything is resolved — what happened? Why?
What did we do well? What failed? How do we prevent
this from happening again? Document everything.

---

## Key Takeaway
BC, DR, and IR are not just theoretical frameworks.
They are the difference between an organization that
survives a cyberattack and one that shuts down because
of it. As a security engineer, understanding RTO and RPO
helps you design backup systems. Understanding the IR
lifecycle helps you respond effectively when — not if —
an incident occurs.

---
*ISC2 CC — Domain 2 of 5 Complete*
*isc2-cc-notes folder — networking-security-notes repo*
*Role: Technical Associate @ Intime Solutions, Bangalore*
