# Senior-Project
# Automated Network Fault Detection and Notification System

A hospital-aware network monitoring system that detects faults, prioritizes them based on clinical context, and sends automated alerts to IT personnel in real time.

**Author:** Natasha Leah Adhiambo | ID: SNATLE2311  
**Supervisor:** Mr. Mwatati Jefferson

---

## Overview

Unlike generic monitoring tools (Nagios, Zabbix), this system uses a **dual-layer severity model** that factors in hospital department criticality — not just raw network metrics. A fault in the ICU is treated as more urgent than a worse fault in an admin office, because patient safety demands it.

---

## Key Features

### 🏥 Hospital-Aware Priority Engine
Scores every fault on two dimensions — network severity and department criticality — so IT always responds to the most life-critical issue first.

| Department | Priority |
|---|---|
| ICU / Operating Theatre | CRITICAL |
| Emergency Department | HIGH |
| Wards | MEDIUM-HIGH |
| Lab / Pharmacy / Radiology | MEDIUM |
| Administration | LOW |

### ⏱ Fault Escalation Engine
No fault can be silently ignored. Unresolved faults auto-escalate over time:

| Time Unresolved | Action |
|---|---|
| 0–10 min | Stays at original priority |
| 10–20 min | Escalates one level, reminder sent |
| 20–30 min | Escalates again, urgent alert sent |
| 30+ min | Escalates to CRITICAL, all IT staff notified |

### 📟 Structured Device Naming
Devices follow the format `[DEPT]-[TYPE][NUMBER]` (e.g. `ICU-A01`, `LAB-B01`) so IT personnel instantly know the location and device type from the alert alone.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Backend | Python 3.13, Flask |
| Frontend | React.js |
| Database | MySQL |
| Alerting | Python smtplib (email) |
| Version Control | Git |

---

## Simulation

Since live hospital network access is unavailable during development, a Python simulation script generates realistic fault events and feeds them into the system via the Flask API — identical to how real monitoring agents would. The detection, prioritization, alerting, and logging are all fully functional.

---

## Project Roadmap

- [x] Development environment setup
- [ ] MySQL database schema design
- [ ] Flask backend & REST API
- [ ] Python monitoring & simulation scripts
- [ ] React.js admin dashboard
- [ ] Hospital-Aware Priority Engine integration
- [ ] Email alerting via smtplib
- [ ] Testing & demonstration preparation
