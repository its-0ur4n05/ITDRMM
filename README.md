@[toc]

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
| **Reactive**    |  Organizations in the Reactive stage lack structured identity governance and have minimal visibility into identity activities. Detection relies on limited logs (e.g., AD only), with responses mostly ad-hoc and manual. Identity risks are often discovered after damage has occurred. |
| **Baseline**    |  At this stage, basic identity processes like approval workflows and system onboarding begin to take shape. Detection capabilities rely on real-time rule-based alerts, and manual responses follow documented SOPs. Visibility into accounts and entitlements improves but remains static and fragmented. |
| **Active**    |  The organization achieves broader system coverage, including cloud and session data, with integrated IGA or CIEM solutions. Detection leverages behavioral analytics and identity signals such as privilege abuse or abnormal sessions. Response mechanisms are partially automated using playbooks or SOAR tools. |
| **Adaptive**    |  An adaptive ITDR program features full-context identity governance, real-time cross-domain visibility, and dynamic threat detection via ML or identity graphs. Response is risk-adaptive, fully automated, and closed-loop, minimizing human intervention. The system continuously learns and evolves based on feedback and attack patterns. |

---

## Capability Dimensions

| **Dimension / Stage**     | **Reactive**                                               | **Baseline**                                                | **Active**                                                        | **Adaptive**                                                      |
|---------------------------|-------------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------------------|--------------------------------------------------------------------|
| **Identity Governance**| No directory, siloed mgmt, manual ops                       | Approval workflows, audit trails, basic automation           | IGA/CIEM integration, privilege control, drift detection           | Contextual enforcement, adaptive provisioning, full automation     |
| **System Coverage**    | AD-only, missing logs, partial visibility                   | Key systems onboarded (AD, VPN), coverage growing            | Full infra & cloud logs, session tracing, cross-domain correlation | Unified data layer, real-time sync, end-to-end coverage            |
| **Asset Visibility**   | Incomplete account list, no session view                   | Static mapping of IDs and entitlements                       | Live identity inventory, session + privilege tracking              | Historical lineage, context-aware assets, identity graphing        |
| **Detection & Analytics** | Rule-only, delayed alerts, weak signal                    | Real-time detections, basic context rules                    | UEBA, privilege abuse detection, session patterning                | ML models, identity graph analysis, adaptive detection              |
| **Response Capability**| Manual alerts, no SOP, reactive steps                      | SOP-driven, human-in-loop response                          | Semi-automated response, playbooks, alert enrichment               | Fully automated loop, dynamic decisions, risk-based response        |

---

### Maturity Radar Chart

![Image text](https://github.com/its-0ur4n05/ITDRMM/blob/7d108b9742c36446da89279c06ad77ef9328568a/img/itdrmm_radar_chart.png)

---

### Level Descriptions (Detailed)

#### 🟠 Reactive Stage
- **Identity Governance:** No centralized identity directory. Accounts and permissions are siloed, with manual provisioning and no consistent cleanup or review.
- **System Coverage:** Only core identity logs (e.g., AD) are connected. Critical systems like VPN, SaaS, and cloud services are not integrated.
- **Identity Asset Visibility:** User listings are incomplete. No insight into entitlements, active sessions, or access relationships.
- **Detection & Analytics:** Very limited logs. Detection is reactive and lacks correlation or context.
- **Response Capability:** Manual observations or emails trigger actions. No formal response process or tooling.

#### 🟡 Baseline Stage
- **Identity Governance:** Approval workflows are in place. Basic access reviews and audits are conducted with some automation for lifecycle management.
- **System Coverage:** Major identity systems (e.g., AD, VPN, bastion hosts) are connected. Some key business systems are integrated.
- **Identity Asset Visibility:** A static inventory of identities and privileges exists. Mappings are manually or semi-automatically maintained.
- **Detection & Analytics:** Real-time rule-based alerts are available, such as detections for abnormal login times or locations.
- **Response Capability:** Standard operating procedures (SOPs) are in place for incidents. Responses are manual but consistent.

#### 🟢 Active Stage
- **Identity Governance:** IGA/CIEM solutions are in use. Privilege assignments are dynamically enforced. Unauthorized changes are automatically flagged.
- **System Coverage:** Broad log coverage including on-prem, SaaS, cloud services, and more. Identity data is correlated across sources.
- **Identity Asset Visibility:** Full dynamic visibility into identities, entitlements, sessions, and ownership relationships.
- **Detection & Analytics:** Behavioral analytics (UEBA) are in place to detect lateral movement, privilege escalation, and impersonation attempts.
- **Response Capability:** Responses are semi-automated via SOAR or playbooks. Some steps (e.g., alert enrichment or account lockout) are automated.

#### 🔵 Adaptive
- **Identity Governance:** Fully automated governance with context-aware adjustments. Risk-based policies and feedback loops from detections guide enforcement.
- **System Coverage:** Continuous and scalable system integration. Real-time analytics provide unified, cross-domain insights into identity behavior.
- **Identity Asset Visibility:** Identity activity is tracked over time for forensics and policy enforcement. Visibility is real-time and historical.
- **Detection & Analytics:** Self-learning detection using ML and identity graphs. Capable of adapting to new threats dynamically.
- **Response Capability:** Fully automated and adaptive response. Closed-loop detection-response cycles minimize human intervention.

---

## Evaluation Checklist

Create a checklist (e.g., YAML or JSON) to self-assess each dimension:

```yaml
identity_governance:
  - [ ] Is there a centralized identity source (e.g., directory, IGA platform) managing all identities?
  - [ ] Are identity lifecycle events (provisioning, deprovisioning, transfers) automated or workflow-driven?
  - [ ] Are there regular access reviews and certification processes?
  - [ ] Is there governance over privilege escalation and role assignment?
  - [ ] Are identity policies dynamically enforced (e.g., based on risk or context)?

system_coverage:
  - [ ] Are all critical systems (e.g., AD, VPN, cloud, SaaS, PAM, bastion) integrated with identity monitoring?
  - [ ] Is log data from both on-premises and cloud platforms being collected and normalized?
  - [ ] Can identity activity be correlated across different systems or domains?
  - [ ] Is integration regularly updated to reflect changes in infrastructure or new systems?

identity_asset_visibility:
  - [ ] Is there an up-to-date inventory of all identities, including service and machine accounts?
  - [ ] Are entitlements, privileges, and roles mapped to each identity?
  - [ ] Can you view active login sessions and their associated assets?
  - [ ] Is there visibility into identity relationships (e.g., ownership, group memberships, delegated access)?
  - [ ] Can historical identity activity be reconstructed for investigation?

detection_and_analytics:
  - [ ] Are identity-related logs (e.g., AD, PAM, VPN, SaaS) actively monitored?
  - [ ] Are there detection rules or UEBA models for common threats (e.g., lateral movement, impersonation)?
  - [ ] Are anomalies in login behavior, permission use, and session context detected?
  - [ ] Is detection enriched with context like user risk level, privilege type, or historical behavior?
  - [ ] Are detection models self-learning or adjusted based on feedback?

response_capability:
  - [ ] Is there an SOP for identity-related security incidents?
  - [ ] Are alerts for identity threats routed to appropriate teams (e.g., via ticket or SOAR)?
  - [ ] Can responders take immediate actions (e.g., disable account, rotate keys) in response to alerts?
  - [ ] Is incident response partially or fully automated for high-risk identity events?
  - [ ] Is there a closed-loop feedback mechanism from response outcomes to improve detection?

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

Here are the metrics with examples **- For reference only**.

### Identity Visibility Metrics

| Metric | Description | Target (Active+) |
|--------|-------------|------------------|
| **Identity Inventory Coverage** | % of total identities accounted for in inventory (incl. human, machine, service accounts) | ≥ 95% |
| **Privileged Account Accuracy** | % of privileged identities with clear ownership, classification, and usage logs | ≥ 90% |
| **Identity-to-Asset Mapping** | % of identities mapped to the systems or applications they access | ≥ 90% |
| **Session Visibility Rate** | % of active sessions traceable to individual identities | ≥ 85% |

### Detection Coverage Metrics

| Metric | Description | Target (Active+) |
|--------|-------------|------------------|
| **Log Source Coverage** | % of relevant identity-related log sources onboarded (e.g., AD, VPN, IAM, PAM) | ≥ 90% |
| **Detection Rule Effectiveness** | 	% of identity detection alerts that result in true positives | ≥ 99% |
| **Behavioral Baseline Coverage** | % of identities with behavior profiles (login, access patterns, locations) | ≥ 85% |
| **Anomaly Detection Precision** | % of anomalies correctly flagged by rule or ML-based methods | ≥ 80% |

### Response Mechanism Metrics

| Metric | Description | Target (Active+) |
|--------|-------------|------------------|
| **Mean Time to Contain (MTTC)** | Average time from alert to account containment (disable/lock/reset) | < 10 mins |
| **Response SOP Coverage** | % of identity alerts that are covered by SOP or playbook | ≥ 90% |
| **Privileged Incident Escalation** | % of privileged identity incidents escalated within SLA | ≥ 95% |
| **Response Automation Rate** | % of responses initiated via automation (e.g., via SOAR or script) | ≥ 70% |

### Identity Governance Metrics

| Metric | Description | Target (Adaptive) |
|--------|-------------|------------------|
| **Joiner/Mover/Leaver Process Coverage** | % of identity lifecycle events governed by automated workflows | ≥ 90% |
| **Access Review Completion Rate** | % of periodic entitlement reviews completed on time | ≥ 95% |
| **Policy Enforcement Accuracy** | % of access violations detected and remediated within SLA | ≥ 90% |
| **Orphan Account Ratio** | % of accounts without active owner or recent activity | < 1% |

### System Coverage Metrics

| Metric | Description | Target (Adaptive) |
|--------|-------------|------------------|
| **System Log Source Coverage** | % of key identity-linked systems with telemetry/logs integrated | ≥ 90% |
| **Shadow System Detection Rate** | % of unauthorized or unmanaged systems identified and flagged | ≥ 85% |
| **Session Recording Coverage** | % of high-risk systems with session logging or recording enabled | ≥ 80% |
| **Jump/Proxy System Coverage** | % of bastions/jump servers monitored for identity activity | ≥ 90% |

---

> **Author**: 0ur4n05
> 
> **Last Updated**: Aug 2025
