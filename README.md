<p align="center"><img src="assets/banner.svg" alt="QA Pipeline Router" width="100%"></p>

<p align="center">
<img src="https://img.shields.io/badge/stack-Apps_Script_·_Sheets_·_REST_API-5B3A3A?style=flat-square">
<img src="https://img.shields.io/badge/data-fictional-FBE3EC?style=flat-square">
<a href="https://sider.ai/agents/web-creator/share/695ea81100a621619985fdfb"><img src="https://img.shields.io/badge/Portfolio-Nae_Kitakado-F4B4CD?style=flat-square"></a>
</p>

<p align="center"><a href="https://naekitakadoportfolio.github.io/qa-pipeline-router/"><img src="https://img.shields.io/badge/%E2%96%B6%20Try%20the%20live%20demo-5B3A3A?style=for-the-badge" alt="Live demo"></a></p>

# QA Pipeline Router

A multi-stage QA pipeline that validates, enriches and routes creative cards. Submit good and bad cards, take the downstream API offline and watch the circuit breaker protect the system.

> **Portfolio rebuild.** This is a from-scratch recreation of a production system I designed and run, rebuilt with **fictional data** and no client names, code or branding. The live demo runs entirely in the browser.

## The problem
Four high-volume no-code workflow steps validated and routed ad cards into QA. Together they consumed about 381k billable tasks over seven months, failed silently on bad data, and had no protection when a downstream API was down.

## Impact in production
Consolidated four workflow steps into one multi-file script. Each stage ran in shadow mode with parity checks before cutover, and the legacy step was turned off the same minute its replacement went live (single-writer rule). This drove a billing-tier downgrade.

## What it demonstrates
| Capability | How |
|---|---|
| Stage-based pipeline | Validate → Enrich → Route → Hand off handlers |
| Data validation | Required fields, ranges and URL format, with bad cards parked instead of dropped |
| Circuit breaker | Stops calling a failing API after 3 errors, resumes after a health check |
| Shadow-mode parity | Compares new vs legacy routing before cutover |
| Cutover readiness | Go/no-go metric from parity data |

## Production architecture
Config.gs · Router.gs · Validation.gs · stage handlers · RetryQueue.gs · ParkedSweep.gs · CircuitBreaker.gs · ShadowLog.gs · SlackAlerts.gs · Dashboard.html

## Try it
Open the **[live demo](https://naekitakadoportfolio.github.io/qa-pipeline-router/)** or run `index.html` locally. No install needed.

---
<p align="center"><sub>Built by <b>Nae Kitakado</b>, AI Automation Consultant · <a href="https://www.linkedin.com/in/nae-k-203194265">LinkedIn</a> · <a href="https://sider.ai/agents/web-creator/share/695ea81100a621619985fdfb">Portfolio</a> · open to retainer &amp; part-time consulting</sub></p>
