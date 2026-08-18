# Cybersecurity Career Roadmap: IT Support → IT Security

This roadmap replaces the previous `PERSONAL_ROADMAP.md`. It's built around one core idea: **your IT support job is already inside the roadmap, not outside it.** Every phase below tells you what to study *and* how to turn your day-to-day support work into evidence for a security role.

---

## 0. Why IT Support → Security is a strong path (and how to use it)

Hiring managers for junior security roles (SOC Analyst, IT Security Analyst, Security+ adjacent roles) actively want candidates who've done support, because you already understand:

- How real networks, tickets, and users actually break (most attacks start with a helpdesk-style problem: phishing, a weird login, a slow machine).
- Windows/AD administration, patching, and endpoint basics.
- How to document, triage, and escalate — which is exactly what a SOC analyst does with alerts.

**Action while you study:** keep a running list in your repo (`transition-notes.md`) of support tickets that map to security concepts — a phishing report, a locked-out account, a suspicious login, a firewall change request. These become interview stories and, later, portfolio writeups.

---

## 1. Phase-by-phase plan

### Phase 1 — Networking Fundamentals + CompTIA Network+ (Weeks 1–8)
**Goal:** Understand networking well enough that packet flow, addressing, and troubleshooting are second nature — not memorized trivia.

- Start with a baseline check (done — see the quiz above) to see what you already know from support work.
- Core topics: OSI & TCP/IP models, IPv4/IPv6 addressing, subnetting (practice until it's fast, not just correct), switching vs routing, VLANs, DNS, DHCP, NAT, common ports/protocols, cabling & wireless basics, network troubleshooting methodology.
- Study flow: 1 topic/week → notes → 20–30 min subnetting drills daily → practice questions → Wireshark lab to *see* the concept on the wire.
- Milestone: pass **CompTIA Network+ (N10-009)**.

### Phase 2 — Deep Linux (Weeks 6–12, overlaps Phase 1)
**Goal:** Be comfortable enough in Linux to administer, troubleshoot, and investigate a box without hesitating.

- Shell fundamentals: navigation, permissions (`chmod`/`chown`/umask), process management, package management.
- Services & systemd: starting/stopping/enabling services, reading unit files.
- Networking tools: `ip`, `ss`/`netstat`, `curl`, `dig`/`nslookup`, `tcpdump`, `nmap`.
- Logging: `/var/log`, `journalctl`, syslog basics — this is the bridge into SOC/log-analysis work.
- Shell scripting: automate one real thing (e.g., a log-parsing script) and put it in the repo.
- Optional but recommended here: **CompTIA Linux+** or a structured course (e.g., Linux Journey / OverTheWire Bandit) if you want a checkpoint.

### Phase 3 — Databases & Data Flow (Weeks 10–14, overlaps Phase 2)
**Goal:** Understand how data is stored, moved, and secured between systems — this underpins both cloud and appsec knowledge later.

- Core concepts: relational model, SQL basics (SELECT/JOIN/INSERT), indexes, transactions and **ACID**, normalization.
- Systems concepts: client-server request flow, replication, backups/recovery, connection strings, and where credentials/secrets typically live (a common attack surface).
- Light hands-on: stand up a local MySQL/PostgreSQL instance, write a few queries, break/restore it once so backups are real to you.

### Phase 4 — Foundational Security Certs (Months 3–7)
**Goal:** Build the security vocabulary and framework knowledge employers screen for.

1. **Google Cybersecurity Certificate** — broad, beginner-friendly, includes intro Python and SIEM (Splunk) exposure.
2. **CompTIA Security+** — the industry baseline cert; ties together networking + Linux + security concepts you already have.
- Study flow: use your Network+/Linux notes as scaffolding — most Security+ topics (firewalls, IAM, cryptography basics, risk concepts) will click faster because you already have the plumbing knowledge.

### Phase 5 — Hands-On Practice & Offensive/Defensive Certs (Months 6–14)
**Goal:** Move from "I know the theory" to "I can do the work" — this is what actually gets interviews.

- Start on **Hack The Box**: easy machines first, always write a private writeup even when you solve it, note what you'd search for next time.
- SIEM/detection practice: Splunk or Microsoft Sentinel free tiers, write a few detection queries (KQL/SPL) against sample logs.
- Certification targets: **HTB CPTS** (Certified Penetration Testing Specialist) and/or **HTB CBBH/other paths**; SL1 (if referring to a specific HTB Academy path, confirm the exact current name before scheduling, since HTB renames paths occasionally.
- Also consider **CompTIA Pentest+** or **eJPT** around here if you want a lower-cost proof point before HTB's paid certs.

### Phase 6 — Cloud Security (Months 10+, ongoing)
**Goal:** Understand cloud storage, identity, networking, and logging — nearly every modern environment is hybrid or cloud-first.

- Pick one cloud first (AWS or Azure — Azure pairs naturally if your support work is Windows/AD-heavy; AWS is more universally requested).
- Core topics: IAM (roles/policies), VPC/networking, storage (S3/Blob) and its common misconfigurations, logging (CloudTrail/Azure Monitor), shared responsibility model.
- Certs: **AWS Cloud Practitioner → AWS Security Specialty**, or **Azure Fundamentals (AZ-900) → Azure Security Engineer (AZ-500)**.
- Build one portfolio project: a small cloud environment with logging/alerting configured, documented in `projects/`.

---

## 2. Tracking system

- **Primary tracker:** GitHub Projects (kanban board tied directly to this repo — no context-switching to a separate app). Columns: `Backlog / Studying / Lab-in-Progress / Blocked / Done`.
- **Daily log:** `notes/learning-log.md` — one dated entry per study day, 5–10 minutes, format below.
- **Weekly review:** every Sunday, review the week's log entries and move Project board cards.

### `learning-log.md` entry template
```markdown
## YYYY-MM-DD
- Studied: <topic>
- Did: <what you actually did — reading, lab, quiz score>
- Understood: <the one thing that clicked>
- Still fuzzy on: <what to revisit>
- Next: <tomorrow's plan>
```

---

## 3. Repository structure

```
cyber-security-journey/
├── PERSONAL_ROADMAP.md          # this file
├── notes/
│   └── learning-log.md          # daily log
├── 01-Networking/
│   ├── notes.md
│   ├── labs/
│   │   └── lab1-subnetting.md
│   └── captures/
│       └── sample1.pcap
├── 02-Linux/
│   ├── notes.md
│   └── labs/
├── 03-Databases/
│   └── notes.md
├── 04-Security-Foundations/      # Google Cert + Security+
│   └── notes.md
├── 05-Cloud/
│   ├── aws/
│   └── azure/
├── 10-Hack-The-Box/
│   └── writeups/
│       └── box-template.md
├── projects/
│   └── (portfolio projects, e.g. cloud lab, detection rules)
└── templates/
    ├── notes-template.md
    ├── lab-writeup-template.md
    └── cert-checklist.md
```

---

## 4. Cert checklist template (reuse per certification)

- [ ] Study plan created
- [ ] Materials collected (course, book, practice tests)
- [ ] Lab environment configured
- [ ] Practice tests completed (log scores over time — you want to see upward trend, not just a pass)
- [ ] Exam scheduled
- [ ] Exam passed (date)
- [ ] Post-exam writeup added to `notes/` (what helped, what you'd do differently)

---

## 5. Immediate next actions

1. Take the networking fundamentals quiz (delivered separately) to confirm your starting point.
2. Create the folder structure above in the repo.
3. Add `notes/learning-log.md` and make today's first entry.
4. Set up the GitHub Projects board with the 6 phases as top-level tracking columns/epics.
5. Book week 1: OSI model + TCP/IP deep dive + first subnetting drill set.

---
*Update this file as milestones are hit — check off certs, add dates, and link to writeups as they land.*
