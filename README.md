# ITDR Maturity Model Toolkit

A practical framework to help organizations assess and improve their **Identity Threat Detection and Response (ITDR)** capabilities, especially in hybrid and on-prem environments (e.g., IDC).

## Overview
This maturity model helps teams benchmark their ITDR readiness across **five maturity levels** and **four capability dimensions**. It's designed to be:

- Technology-agnostic
- Usable for cloud, hybrid, and on-prem (IDC) environments
- Practical for SOCs, blue teams, and security architects

---

## Maturity Levels

| Level | Description                         |
|-------|-------------------------------------|
| L0    | **Nonexistent** - No ITDR capability |
| L1    | **Reactive** - Basic visibility & passive detection |
| L2    | **Baseline** - Defined coverage & manual response processes |
| L3    | **Active** - Real-time detection & integrated response |
| L4    | **Adaptive** - Fully automated, intelligent, risk-based ITDR

---

## Capability Dimensions

| Dimension            | L0 - Nonexistent | L1 - Reactive | L2 - Baseline | L3 - Active | L4 - Adaptive |
|----------------------|------------------|---------------|---------------|-------------|---------------|
| **Identity Visibility** | No inventory; accounts mixed | Partial account listing | Identity-asset mapping established | Full inventory incl. privileges & sessions | Dynamic, contextual identity risk profiling |
| **Detection Coverage** | No logs collected | Some logs (e.g. AD) ingested | Baseline behavior rules defined | Real-time detection + behavior analytics | Cross-domain anomaly detection, LLM/graph-powered |
| **Response Mechanism** | No process | Email alerts, ad-hoc reactions | SOP-based manual responses (lockout/reset) | Semi-automated via SOAR/playbooks | Closed-loop auto-response with risk-adaptive policy |
| **Automation & Intelligence** | None | None | Scripted/manual triggers | Risk scoring & policy-based automation | ML/graph analysis, self-learning detection engine |

---

## Evaluation Checklist

Create a checklist (e.g., YAML or JSON) to self-assess each dimension:

```yaml
identity_visibility:
  - [ ] Do you maintain an up-to-date inventory of all identities (human + machine)?
  - [ ] Are privileged accounts clearly identified and tracked?

detection_coverage:
  - [ ] Are identity-related logs collected from AD, PAM, SSO, Jump servers, etc.?
  - [ ] Are there rules to detect lateral movement and abnormal logins?

response_mechanism:
  - [ ] Is there a documented SOP for responding to suspicious identity activity?
  - [ ] Can your SOC manually disable or reset accounts on detection?
  - [ ] Is there partial automation (e.g., ticket + disable)?

automation_intelligence:
  - [ ] Is risk scoring applied to accounts?
  - [ ] Are detection rules adaptive based on feedback or context?
  - [ ] Are LLM or graph-based techniques used for detection?
```

---

## How to Use This

- Start by mapping your current state to each dimension and level.
- Identify the lowest dimension to determine your **overall maturity floor**.
- Plan improvements dimension-by-dimension using this toolkit as a roadmap.

You can extend this repository with:
- JSON/YAML-based self-assessment form
- Python script to generate a spider chart of maturity
- Integration checklist with IAM / PAM / SIEM / SOAR

---

> **Author**: 0ur4n05
> **Last Updated**: July 2025
