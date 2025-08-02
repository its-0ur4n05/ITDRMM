# ITDR Maturity Model Toolkit

A practical framework to help organizations assess and improve their **Identity Threat Detection and Response (ITDR)** capabilities, especially in hybrid and on-prem environments (e.g., IDC).

If you have any questions or are interested in collaborating, feel free to contact me at: its0ur4n05@gmail.com

## Why ITDR?

In recent years, identity has become the most targeted attack vector in enterprise environments. Whether it's through credential stuffing, abusing privileged accounts, or lateral movement using legitimate identities, attackers are increasingly bypassing traditional perimeter defenses and endpoint detection by simply “logging in, not breaking in.”

### The Evolution of Identity Threats

- **Credential Theft Becomes Pervasive**: Phishing, malware, and data breaches have led to an explosion in stolen credentials available on the dark web.
- **Abuse of Legitimate Access**: Attackers are increasingly leveraging valid credentials and legitimate tools (e.g., RDP, PowerShell) to avoid detection.
- **Cloud + On-Prem Complexity**: Hybrid environments mean identities span across Active Directory, Azure AD, Okta, cloud IAM roles, and more — creating fragmented visibility.
- **Rise of Supply Chain and Insider Threats**: These threats often manifest through legitimate credentials misused from inside or via third-party access.

### Limitations of Traditional Security

- **IAM ≠ Threat Detection**: Identity and Access Management systems (IAM, PAM) focus on provisioning and controlling access, not detecting misuse.
- **UEBA Misalignment**: Traditional User & Entity Behavior Analytics systems often suffer from high false positives and poor explainability, especially in dynamic hybrid environments.
- **Endpoint-Only EDR Blind Spots**: Many attacks that abuse identity leave minimal traces on the endpoint and are instead visible only through identity systems and logs.

### What is ITDR?

Identity Threat Detection and Response (ITDR) refers to a class of security capabilities and practices focused on:
- Monitoring identity infrastructure (e.g., AD, Azure AD, Okta) for signs of compromise
- Detecting abnormal or risky identity behaviors (e.g., unusual privilege escalation, impossible travel)
- Responding to identity-based threats with tailored mechanisms (e.g., token revocation, password reset, account disable)

ITDR acts as the last line of defense when attackers have bypassed MFA or gained initial access through social engineering or supply chain compromise.

## Growing Demand for ITDR

- **Compliance Pressure**: Regulatory frameworks such as NIS2, DORA, and ISO 27001 now emphasize identity-centric risk management and detection.
- **Zero Trust Push**: Organizations moving to Zero Trust architectures must continuously verify identity trustworthiness, detect abuse, and respond quickly.
- **SOC Integration**: Mature SOC teams are looking to extend EDR/XDR visibility into the identity layer, closing the gap between access control and threat response.
- **Hybrid & Legacy Environments**: Many organizations still operate critical infrastructure in on-prem (IDC) setups, where existing ITDR solutions lack coverage or compatibility.

---

## About This Tool

The current ITDR Maturity Model was created by 0ur4n05 in Jul 2025.
This repository provides a structured checklist and maturity model to help organizations self-assess their ITDR readiness and capabilities. It is designed to be:
- **Technology-agnostic**
- **Practical** for security teams, auditors, and architects
- **Applicable to hybrid, on-prem, and cloud environments**

---

## Maturity Levels

| Level | Description                         |
|-------|-------------------------------------|
| **Reactive**    |  Basic visibility & passive detection |
| **Baseline**    |  Defined coverage & manual response processes |
| **Active**    |  Real-time detection & integrated response |
| **Adaptive**    |  Fully automated, intelligent, risk-based ITDR

### Maturity Radar Chart

![Image text](https://github.com/its-0ur4n05/ITDRMM/blob/c09c7eb810489ba7be0de6958cab306a9bf2bd93/img/itdrmm_radar_chart.png)

### Level Descriptions (Detailed)

#### 🟠 Reactive
- Initial efforts to collect identity-related logs (e.g., AD logs)
- Limited visibility over key users or critical accounts
- Alerts sent via email or basic ticketing, but no structured response
- No standardized roles or responsibilities for identity incidents
- Detection mostly occurs *after* an incident or external report

#### 🟡 Baseline
- Basic inventory of accounts and identity-asset mapping exists
- Detection rules in place for common abuse patterns (e.g., login anomalies)
- Security team responds using SOPs: manual account disable, reset password, etc.
- Incidents logged and escalated based on severity
- Detection-to-response linkage starts forming but is still mostly manual

#### 🟢 Active
- Comprehensive identity inventory with privileged tracking and session logs
- Real-time detection rules with behavioral analytics or baselines
- Integration with SOAR for partial automation of response workflows
- Response actions include contextual decisions based on role or criticality
- Threat hunting for identity misuse starts to become systematic

#### 🔵 Adaptive
- Risk-based identity protection and dynamic response policies
- Detection enriched by ML/graph/LLM-based analysis
- Continuous feedback loop between detection, investigation, and policy tuning
- Automated remediation with minimal human intervention (e.g., auto-MFA challenges, just-in-time access revocation)
- Unified visibility across hybrid/cloud/on-prem identity infrastructure

---

## Capability Dimensions

| **Dimension / Stage**     | **Reactive**                                               | **Baseline**                                                | **Active**                                                        | **Adaptive**                                                      |
|---------------------------|-------------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------------|--------------------------------------------------------------------|
| **1. Identity Governance**| No directory, siloed mgmt, manual ops                       | Approval workflows, audit trails, basic automation           | IGA/CIEM integration, privilege control, drift detection           | Contextual enforcement, adaptive provisioning, full automation     |
| **2. System Coverage**    | AD-only, missing logs, partial visibility                   | Key systems onboarded (AD, VPN), coverage growing            | Full infra & cloud logs, session tracing, cross-domain correlation | Unified data layer, real-time sync, end-to-end coverage            |
| **3. Asset Visibility**   | Incomplete account list, no session view                   | Static mapping of IDs and entitlements                       | Live identity inventory, session + privilege tracking              | Historical lineage, context-aware assets, identity graphing        |
| **4. Detection & Analytics** | Rule-only, delayed alerts, weak signal                    | Real-time detections, basic context rules                    | UEBA, privilege abuse detection, session patterning                | ML models, identity graph analysis, adaptive detection              |
| **5. Response Capability**| Manual alerts, no SOP, reactive steps                      | SOP-driven, human-in-loop response                          | Semi-automated response, playbooks, alert enrichment               | Fully automated loop, dynamic decisions, risk-based response        |


---

## Evaluation Checklist

Create a checklist (e.g., YAML or JSON) to self-assess each dimension:

```yaml
identity_visibility:
  - [ ] Do you maintain an up-to-date inventory of all identities (human + machine)?
  - [ ] Are privileged accounts clearly identified and tracked?
  - [ ] Are service accounts and their owners documented?
  - [ ] Can you trace which identities access which systems (identity-to-asset mapping)?

detection_coverage:
  - [ ] Are identity-related logs (e.g., AD, PAM, VPN, Jump server) being collected?
  - [ ] Are there rules to detect lateral movement and privilege escalation?
  - [ ] Do you have baselines for normal user behavior (e.g., login times, locations)?
  - [ ] Are high-risk activities (e.g., password dump, multiple failed logins) being monitored?

response_mechanism:
  - [ ] Is there a documented SOP for responding to identity-related incidents?
  - [ ] Can you manually disable, lock, or reset accounts based on alerts?
  - [ ] Are identity alerts routed via a ticketing system or SOAR playbook?
  - [ ] Is there a review/escalation process when privileged accounts are involved?

automation_intelligence:
  - [ ] Do you apply risk scoring to users based on behavior or context?
  - [ ] Are responses automated in part (e.g., auto-disable, MFA challenges)?
  - [ ] Can your detection model adapt over time based on new inputs or feedback?
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

## ITDR Capability Metrics

To evaluate and track ITDR program effectiveness over time, organizations should define and monitor a set of measurable indicators across the four capability dimensions. These metrics help distinguish maturity not just by implementation, but by **operational impact** and **quality**.

Here are the metrics with examples for reference.

### Identity Visibility Metrics

| Metric | Description | Target (Active+) |
|--------|-------------|------------------|
| **Identity Inventory Coverage** | % of total identities accounted for in inventory (incl. human, machine, service accounts) | ≥ 95% |
| **Privileged Account Coverage** | % of privileged identities with owner, usage audit, and least-privilege status verified | ≥ 90% |
| **Asset Mapping Accuracy** | % of identities mapped to assets/systems they access | ≥ 90% |

### Detection Coverage Metrics

| Metric | Description | Target (Active+) |
|--------|-------------|------------------|
| **Log Source Coverage** | % of relevant identity-related log sources onboarded (e.g., AD, VPN, IAM, PAM) | ≥ 90% |
| **Rule Effectiveness** | % of identity detection rules triggered that result in true positives | ≥ 70% |
| **Behavioral Baseline Completeness** | % of users with baseline behavioral profiles established | ≥ 85% |

### Response Mechanism Metrics

| Metric | Description | Target (Active+) |
|--------|-------------|------------------|
| **Mean Time to Contain (MTTC)** | Average time from alert to account containment (disable/lock/reset) | < 10 mins |
| **Response SOP Coverage** | % of identity alerts that are covered by SOP or playbook | ≥ 90% |
| **Privileged Incident Escalation** | % of privileged identity incidents escalated within SLA | ≥ 95% |

### Automation & Intelligence Metrics

| Metric | Description | Target (Adaptive) |
|--------|-------------|------------------|
| **Automated Response Ratio** | % of identity alerts with partially or fully automated responses | ≥ 70% |
| **Risk Score Accuracy** | Correlation between user risk score and actual incident severity (manual review) | ≥ 80% |
| **Detection Adaptiveness** | % of detection models updated with new IOCs, TTPs, or feedback monthly | ≥ 90% |

---

> **Author**: 0ur4n05
> 
> **Last Updated**: Aug 2025
