# CITAP - Cyber Incident Ticketing & Analysis Platform

> A collaborative, open-source portfolio project bridging **Cybersecurity Engineering** and **Business Systems Analysis**.

![Status](https://img.shields.io/badge/Status-In%20Development-orange)
![Stack](https://img.shields.io/badge/Stack-Laravel%20%7C%20React%20%7C%20Inertia.js-blue)
![Database](https://img.shields.io/badge/Database-SQLite-lightgrey)

---

## What Is CITAP?

Small businesses and growing IT teams often lack the tools to manage security threats systematically. Enterprise-grade platforms are expensive and complex. **CITAP** is a lightweight, functional alternative. It is a web-based incident ticketing system built specifically for security operations workflows.

It lets non-technical staff report security issues, gives analysts a structured investigation workspace, and gives managers real-time visibility into the organisation's threat landscape.

This is a **proof-of-concept portfolio project**, and not a commercial product. Its purpose is to demonstrate how cross-functional collaboration between a cybersecurity engineer and a business systems analyst produces a real, working application from structured requirements.

---

## Key Features

| Feature | Description |
|---|---|
| **Incident Intake Form** | Any staff member can submit a security issue via a guided form. Auto-maps to MITRE ATT&CK on save. |
| **Executive Dashboard** | Real-time metrics: active incidents, unassigned queue, critical outages, category breakdown chart. |
| **Ticket Lifecycle Engine** | Strict state-machine: New → Open → Under Investigation → Resolved → Closed. |
| **VirusTotal Threat Intelligence** | Paste an IP, domain, or file hash. After that, CITAP queries VirusTotal and auto-escalates if malicious signals are detected. |
| **CSV Export** | One-click export of all incident data for management reporting. |

---

## Tech Stack

```
React (SPA Frontend)  ←→  Inertia.js Bridge  ←→  Laravel (Backend Engine)
                                                  ↓                ↓
                                             SQLite DB     VirusTotal API
```

- **Backend:** Laravel (PHP)
- **Frontend:** React + Tailwind CSS
- **Bridge:** Inertia.js (no decoupled API needed)
- **Database:** SQLite
- **External API:** VirusTotal Community (free tier)

---

## Security Framework Integrations

**MITRE ATT&CK Mapping** - Incidents are automatically tagged with a MITRE technique when submitted:

| Category | MITRE Technique | ID |
|---|---|---|
| Authentication Security | Brute Force | T1110 |
| Malware Infection | User Execution | T1204 |
| Network Anomalies | Active Scanning | T1595 |
| Email Security | Phishing | T1566 |
| Data Security | Automated Exfiltration | T1020 |

**SLA Matrix** - Severity levels carry enforced response windows:

| Severity | Target Window | Badge |
|---|---|---|
| Low | 5 Business Days | Gray |
| Medium | 48 Hours | Blue |
| High | 12 Hours | Orange |
| Critical | 4 Hours | Animated Red |

---

## Cross-Functional Collaboration Model

This project has been intentionally designed to showcase how business analysis and security engineering work together.

### 🔐 Security & Engineering - Azwad
- Designed and implemented the full-stack database schema (SQLite via Laravel Eloquent)
- Built the VirusTotal API integration and auto-escalation rules engine
- Translated the MITRE ATT&CK framework into application logic
- Developed the ticket state-machine lifecycle enforcement

### 📋 Business Systems Analysis - Shuaib
- Authored functional user stories and acceptance criteria (Gherkin format) for all five features
- Defined the incident lifecycle state-machine and enforced transition rules
- Established the SLA governance matrix based on severity and threat vectors
- Designed the BPMN process flows for incident intake, triage, and resolution
- Produced the Requirements Traceability Matrix (BR → User Story → Feature → Test Case)
- Authored project documentation and maintained the `/docs` BA artefacts folder

---

## Project Structure

```
CITAP/
├── app/
│   ├── Http/Controllers/TicketController.php
│   └── Models/
├── database/
│   ├── migrations/
│   └── seeders/TicketSeeder.php
├── resources/
│   └── js/Pages/
│       ├── Dashboard.jsx
│       ├── Tickets/Index.jsx
│       ├── Tickets/Create.jsx
│       └── Tickets/Show.jsx
├── docs/                          ← Shuaib's BA artefacts
│   ├── user-stories.md
│   ├── process-flows/
│   └── requirements-traceability-matrix.xlsx
└── README.md
```

---

## Getting Started (Local Setup)

> Requires PHP 8.2+, Composer, Node.js 18+

```bash
# 1. Clone the repo
git clone https://github.com/AzwadBhuiyan/cyber-incident-ticketing-platform.git
cd cyber-incident-ticketing-platform

# 2. Install dependencies
composer install
npm install

# 3. Set up environment
cp .env.example .env
php artisan key:generate

# 4. Configure .env - set your VirusTotal API key
VIRUSTOTAL_API_KEY=your_key_here
DB_CONNECTION=sqlite

# 5. Run migrations and seed demo data
php artisan migrate --seed

# 6. Start the dev server
php artisan serve
npm run dev
```

Open `http://localhost:8000` - demo data is pre-loaded. Use the role-switcher in the navbar to view the app as Employee, Analyst, or Manager.

---

## Predefined Demo Users

| Name | Role | Purpose |
|---|---|---|
| Azwad (SOC Analyst) | Analyst | Investigate and triage incidents |
| Shuaib (Business Manager) | Admin | Dashboard oversight and reporting |
| Demo Employee | Employee | Submit new incident reports |

---

## BA Documentation (`/docs`)

The `/docs` folder contains all business analysis artefacts produced during the project:

- `user-stories.md` - Formal user stories with Gherkin acceptance criteria
- `process-flows/` - BPMN diagrams and activity flows for the ticket lifecycle
- `requirements-traceability-matrix.xlsx` - BR → Feature → Test Case mapping
- `sla-decision-matrix.xlsx` - Severity escalation and SLA governance rules

---

## Roadmap

- [x] Project specification and BA artefacts
- [ ] Database migrations and seeder
- [ ] TicketController (CRUD + VirusTotal integration)
- [ ] React views (Dashboard, Index, Create, Show)
- [ ] CSV Export
- [ ] Final QA and GitHub polish

---

## Why We Built This

> "CITAP is not trying to replace enterprise SIEM tools. It's a demonstration that good business analysis, which includes clear requirements, defined workflows, and traceability, turns a security concept into a working, maintainable application."

---

## Licence

MIT - open source, free to use and adapt.
