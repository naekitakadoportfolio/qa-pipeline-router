<p align="center"><img src="assets/banner.svg" alt="QA Pipeline Router" width="100%"></p>

<p align="center">
<img src="https://img.shields.io/badge/stack-Apps_Script_·_Sheets_·_REST_API-14384E?style=flat-square">
<img src="https://img.shields.io/badge/data-fictional-89CDE7?style=flat-square">
<a href="https://sider.ai/agents/web-creator/share/695ea81100a621619985fdfb"><img src="https://img.shields.io/badge/Portfolio-Nae_Kitakado-1D4C93?style=flat-square"></a>
</p>

<p align="center"><a href="https://naekitakadoportfolio.github.io/qa-pipeline-router/"><img src="https://img.shields.io/badge/%E2%96%B6%20Try%20the%20live%20demo-14384E?style=for-the-badge" alt="Live demo"></a></p>

# QA Pipeline Router

A multi-page app for a staged QA pipeline that validates, enriches, reviews and hands off creative cards. Bad data is parked, a circuit breaker protects the downstream API, and shadow parity drives a cutover checklist.

> **Portfolio rebuild.** A from-scratch recreation of a production system I designed and run (DataQA pipeline). It uses **fictional data**, with no client names, code or branding.

## ✨ Features
- **Overview:** stage throughput bars, parity, circuit-breaker state and recent activity
- **Submit card:** form with validation rules (https asset link, 1–180s duration, platform, title); invalid cards are parked with reasons
- **Pipeline board:** Kanban by stage; drag cards forward (no skipping stages) or click ▶ Next
- **Parked cards:** fix fields inline and resubmit
- **Circuit breaker:** simulate a downstream outage, adjust the failure threshold, run a health check, retry held hand-offs
- **Parity & cutover:** legacy vs new routing comparison and a readiness checklist that gates the **Execute cutover** button
- **Logs:** a full pipeline log
- Light/dark theme, responsive layout, state saved in your browser, and one-click **Reset demo data**

## 🧭 Try it
1. *Submit card* with Platform left blank → parked
2. *Parked cards* → choose a platform → **Fix & resubmit**
3. *Circuit breaker* → simulate an outage → move cards to Hand off on the board until the breaker opens
4. Run a **health check** after restoring the API
5. *Parity & cutover* → tick the checklist → **Execute cutover**

Open the **[live demo](https://naekitakadoportfolio.github.io/qa-pipeline-router/)**.

## 🏗 Production architecture
| Layer | Production | This demo |
|---|---|---|
| Stages | Validate / Enrich / Route / Hand off handler files | `advance()` |
| Validation | Validation.gs rules | `validate()` |
| Parking | ParkedSweep.gs + owner alerts | Parked column + log |
| Resilience | CircuitBreaker.gs | `callApi()` + `S.cb` |
| Cutover | ShadowLog.gs parity + single-writer rule | Parity report + checklist |

## 📁 Project structure
```
qa-pipeline-router/
├── index.html        # built app (open this)
├── src/
│   ├── app.js        # state, views, business logic
│   └── app.json      # app config: nav, theme, storage key
├── assets/banner.svg
├── README.md
└── LICENSE
```

## 🚀 Run locally
No install needed. Open `index.html`, or:
```bash
python3 -m http.server 8000   # http://localhost:8000
```

## 🧩 Implementation notes
- `advance()` re-validates on every move, so fixed cards flow on automatically
- `callApi()` counts consecutive failures and opens the circuit at the threshold
- Parity auto-checks once there are 30+ samples at ≥ 98%
- Board drag-and-drop blocks skipping stages

## 🗺 Roadmap
- SLA timers per stage
- Bulk resubmit for parked cards
- Export of the parity diff report

---
<p align="center"><sub>Built by <b>Nae Kitakado</b>, AI Automation Consultant · <a href="https://www.linkedin.com/in/nae-k-203194265">LinkedIn</a> · <a href="https://sider.ai/agents/web-creator/share/695ea81100a621619985fdfb">Portfolio</a> · open to retainer &amp; part-time consulting</sub></p>
