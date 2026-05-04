# ISC2 CC — Domain 3: Access Controls Concepts

**Domain weight in exam:** 22%
**My competence score:** 100%
**Status:** ✅ Complete

---

## What is Access Control?
Access control is the process of granting or denying
specific requests to obtain and use information and
related information processing services.

Simply: who is allowed to access what, and what are
they allowed to do with it?

Every login screen, every file permission, every
firewall rule — all of these are access controls.

---

## The Four Steps of Access Control

**Identification** — claiming an identity
Example: typing your username

**Authentication** — proving that identity
Example: entering your password, using MFA

**Authorization** — what you are allowed to do
Example: you can read this file but not delete it

**Accountability** — tracking what you did
Example: audit logs recording every action

All four must work together. Missing any one of them
creates a security gap.

---

## Types of Access Control

### MAC — Mandatory Access Control
Access is controlled by the system or administrator.
Users cannot change permissions themselves — even
on files they created.

The system assigns security labels (like Top Secret,
Secret, Confidential) to both users and resources.
Access is only granted when the user's label matches
or exceeds the resource's label.

Used in: military and government systems where
data classification is strict and non-negotiable.

Example: A user with "Secret" clearance cannot
access "Top Secret" files — even if they are the
file creator. The system enforces this, not the user.

### DAC — Discretionary Access Control
The owner of a file or resource decides who can
access it and what they can do.

Used in: most everyday operating systems like
Windows and Linux. When you share a folder and
choose who can read or edit it — that is DAC.

Weakness: if the owner makes a mistake (shares
with wrong person, sets wrong permissions) —
the system allows it. Human error is the biggest
risk in DAC environments.

### RBAC — Role-Based Access Control
Access is given based on a user's role in the
organization — not their individual identity.

Example roles: Admin, Manager, Employee, Auditor
Each role has a defined set of permissions.
Users inherit permissions from their role.

Used in: almost every enterprise system today.
When someone joins a company they are assigned
a role — they automatically get the right access.
When they leave — remove the role, access is gone.

Advantage: much easier to manage at scale.
You manage roles, not individual users.

---

## Principle of Least Privilege

Give every user, system, and process only the
minimum access needed to perform their specific
job — nothing more.

### Why It Matters
If an attacker compromises an account with
excessive privileges — they inherit all of those
privileges. A compromised admin account is
catastrophic. A compromised limited account
is contained.

Least privilege limits the blast radius of any
security incident.

### In Practice
- A developer needs access to the development
  server — not the production database
- A receptionist needs access to the calendar
  system — not financial records
- A monitoring script needs read access to logs
  — not write access to system files

Every extra permission granted beyond what is
needed is an unnecessary risk.

---

## Physical vs Logical Access Controls

**Physical controls** — prevent unauthorized physical
access to facilities, hardware, and infrastructure.
Examples: security guards, key cards, biometrics,
CCTV cameras, locked server rooms, mantraps

**Logical controls** — prevent unauthorized access
to systems, networks, and data through software.
Examples: passwords, MFA, firewalls, encryption,
access control lists, role-based permissions

Both are required. The strongest logical controls
in the world mean nothing if an attacker can
walk into your server room.

---

## Key Takeaway
Access control is the foundation of every security
architecture. Every decision about who can access
what system, what data, what building — is an access
control decision. Understanding MAC, DAC, and RBAC
helps you design the right access model for the
right environment. And least privilege applied
consistently is one of the most powerful single
controls an organization can implement.

---
*ISC2 CC — Domain 3 of 5 Complete*
*isc2-cc-notes folder — networking-security-notes repo*
*Role: Technical Associate @ Intime Solutions, Bangalore*
