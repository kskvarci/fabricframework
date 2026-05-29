# Microsoft Fabric Security Configuration Baseline
## For Regulated Enterprise Adoption

---

## Table of Contents

- [Purpose](#purpose)
- [Sources](#sources)
- [Legend](#legend)
- [Regulatory Framework Mappings](#regulatory-framework-mappings)
- [How to Use](#how-to-use)
- [Implementation Types](#implementation-types)
- [Where This Fits: SaaS Service Enablement for Regulated Industries](#where-this-fits-saas-service-enablement-for-regulated-industries)
- [How This Relates to Compliance Frameworks, the MCSB, and Internal Policies](#how-this-relates-to-compliance-frameworks-the-mcsb-and-internal-policies)
- [1. Network Security (NS)](#1-network-security-ns)
- [2. Identity Management (IM)](#2-identity-management-im)
- [3. Privileged Access (PA)](#3-privileged-access-pa)
- [4. Data Protection (DP)](#4-data-protection-dp)
- [5. Asset Management (AM)](#5-asset-management-am)
- [6. Logging and Threat Detection (LT)](#6-logging-and-threat-detection-lt)
- [7. Incident Response (IR)](#7-incident-response-ir)
- [8. Posture and Vulnerability Management (PV)](#8-posture-and-vulnerability-management-pv)
- [9. Endpoint Security (ES)](#9-endpoint-security-es)
- [10. Backup and Recovery (BR)](#10-backup-and-recovery-br)
- [Evidence Collection](#evidence-collection)
- [Notes](#notes)

---

### Purpose
This artifact provides a complete mapping of every control in the MCSB Fabric Security Baseline to implementation guidance. Each row is sourced directly from Microsoft's publicly documented MCSB Fabric Security Baseline and/or the Fabric Tenant Settings Index. Every entry includes a link to its source documentation.

### Sources
- **MCSB Fabric Security Baseline**: https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline
- **Fabric Tenant Settings Index**: https://learn.microsoft.com/en-us/fabric/admin/tenant-settings-index
- **MCSB Overview**: https://learn.microsoft.com/en-us/security/benchmark/azure/overview

### Legend

- Rows **without** a marker = the setting/configuration is explicitly named or linked in the MCSB Fabric Security Baseline document
- Rows marked with **†** (dagger) = the setting is documented in the Tenant Settings Index but is **not** explicitly referenced in the baseline; it has been mapped to this control by inference based on the control's stated purpose

### Regulatory Framework Mappings

Each MCSB control maps to NIST SP 800-53 r4, CIS Controls v8, and PCI-DSS v3.2.1. These mappings are published by Microsoft at the MCSB control domain level.

| MCSB Control | CIS Controls v8 | NIST SP 800-53 r4 | PCI-DSS v3.2.1 | Source |
|---|---|---|---|---|
| **NS-1** | 3.12, 13.4, 4.4 | AC-4, SC-2, SC-7 | 1.1, 1.2, 1.3 | [MCSB Network Security](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-network-security#ns-1-establish-network-segmentation-boundaries) |
| **NS-2** | 3.12, 4.4 | AC-4, SC-2, SC-7 | 1.1, 1.2, 1.3 | [MCSB Network Security](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-network-security#ns-2-secure-cloud-native-services-with-network-controls) |
| **NS-3** | 4.4, 4.8, 13.10 | AC-4, SC-7, CM-7 | 1.1, 1.2, 1.3 | [MCSB Network Security](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-network-security#ns-3-deploy-firewall-at-the-edge-of-enterprise-network) |
| **NS-4** | 13.2, 13.3, 13.7, 13.8 | SC-7, SI-4 | 11.4 | [MCSB Network Security](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-network-security#ns-4-deploy-intrusion-detectionintrusion-prevention-systems-idsips) |
| **NS-5** | 13.10 | SC-5 | 6.6 | [MCSB Network Security](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-network-security#ns-5-deploy-ddos-protection) |
| **NS-6** | 13.10 | SC-7 | 6.6 | [MCSB Network Security](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-network-security#ns-6-deploy-web-application-firewall) |
| **NS-7** | 4.4, 4.8 | SC-7 | 1.1, 1.2, 1.3 | [MCSB Network Security](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-network-security#ns-7-simplify-network-security-configuration) |
| **NS-8** | 4.4, 4.8 | CM-7 | 2.2.2 | [MCSB Network Security](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-network-security#ns-8-detect-and-disable-insecure-services-and-protocols) |
| **NS-9** | 12.7 | CA-3, AC-17, AC-4 | N/A | [MCSB Network Security](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-network-security#ns-9-connect-on-premises-or-cloud-network-privately) |
| **NS-10** | 4.9 | SC-20, SC-21 | N/A | [MCSB Network Security](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-network-security#ns-10-ensure-domain-name-system-dns-security) |
| **IM-1** | 6.7, 12.5 | AC-2, AC-3, IA-2, IA-8 | 7.2, 8.3 | [MCSB Identity Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-identity-management#im-1-use-centralized-identity-and-authentication-system) |
| **IM-2** | 5.4, 6.5 | AC-2, AC-3, IA-2, IA-8, SI-4 | 8.2, 8.3 | [MCSB Identity Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-identity-management#im-2-protect-identity-and-authentication-systems) |
| **IM-3** | N/A | AC-2, AC-3, IA-4, IA-5, IA-9 | N/A | [MCSB Identity Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-identity-management#im-3-manage-application-identities-securely-and-automatically) |
| **IM-4** | N/A | SC-8 | 4.1 | [MCSB Identity Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-identity-management#im-4-authenticate-server-and-services) |
| **IM-5** | N/A | IA-4, IA-2, IA-8 | 7.2, 8.3 | [MCSB Identity Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-identity-management#im-5-use-single-sign-on-sso-for-application-access) |
| **IM-6** | 6.3, 6.4 | AC-2, AC-3, IA-2, IA-5, IA-8 | 7.2, 8.2, 8.3, 8.4 | [MCSB Identity Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-identity-management#im-6-use-strong-authentication-controls) |
| **IM-7** | 3.3, 6.4, 13.5 | AC-2, AC-3, AC-6 | 7.2 | [MCSB Identity Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-identity-management#im-7-restrict-resource-access-based-on-conditions) |
| **IM-8** | N/A | IA-5 | 3.5, 3.6, 8.2, 8.5 | [MCSB Identity Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-identity-management#im-8-restrict-the-exposure-of-credentials-and-secrets) |
| **IM-9** | N/A | AC-2, AC-3, IA-4 | N/A | [MCSB Identity Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-identity-management#im-9-secure-user-access-to-existing-applications) |
| **PA-1** | 5.4, 6.8 | AC-2, AC-6 | 7.1, 7.2, 8.1 | [MCSB Privileged Access](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-privileged-access#pa-1-separate-and-limit-highly-privilegedadministrative-users) |
| **PA-2** | N/A | AC-2 | N/A | [MCSB Privileged Access](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-privileged-access#pa-2-avoid-standing-access-for-user-accounts-and-permissions) |
| **PA-3** | N/A | AC-2, AC-5, AC-6 | 7.1, 7.2, 8.1 | [MCSB Privileged Access](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-privileged-access#pa-3-manage-lifecycle-of-identities-and-entitlements) |
| **PA-4** | N/A | AC-2, AC-6 | 7.2, 8.1 | [MCSB Privileged Access](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-privileged-access#pa-4-review-and-reconcile-user-access-regularly) |
| **PA-5** | N/A | AC-2 | N/A | [MCSB Privileged Access](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-privileged-access#pa-5-set-up-emergency-access) |
| **PA-6** | 12.8, 13.5 | AC-2, SC-2, SC-7 | N/A | [MCSB Privileged Access](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-privileged-access#pa-6-use-privileged-access-workstations) |
| **PA-7** | 3.3, 6.8 | AC-2, AC-3, AC-6 | 7.1, 7.2 | [MCSB Privileged Access](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-privileged-access#pa-7-follow-just-enough-administration-least-privilege-principle) |
| **PA-8** | N/A | AC-2, AC-3, AC-6 | N/A | [MCSB Privileged Access](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-privileged-access#pa-8-determine-access-process-for-cloud-provider-support) |
| **DP-1** | 3.2, 3.7, 3.13 | RA-2, SC-28 | A3.2 | [MCSB Data Protection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-data-protection#dp-1-discover-classify-and-label-sensitive-data) |
| **DP-2** | 3.13 | AC-4, SI-4 | A3.2 | [MCSB Data Protection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-data-protection#dp-2-monitor-anomalies-and-threats-targeting-sensitive-data) |
| **DP-3** | 3.10 | SC-8 | 3.5, 3.6, 4.1 | [MCSB Data Protection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-data-protection#dp-3-encrypt-sensitive-data-in-transit) |
| **DP-4** | 3.11 | SC-28 | 3.4, 3.5 | [MCSB Data Protection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-data-protection#dp-4-enable-data-at-rest-encryption-by-default) |
| **DP-5** | 3.11 | SC-12, SC-28 | 3.4, 3.5, 3.6 | [MCSB Data Protection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-data-protection#dp-5-use-customer-managed-key-option-in-data-at-rest-encryption-when-required) |
| **DP-6** | N/A | SC-12, SC-28 | 3.5, 3.6 | [MCSB Data Protection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-data-protection#dp-6-use-a-secure-key-management-process) |
| **DP-7** | N/A | SC-12, SC-28 | 3.5, 3.6 | [MCSB Data Protection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-data-protection#dp-7-use-a-secure-certificate-management-process) |
| **DP-8** | N/A | SC-12, SC-28 | 3.5, 3.6 | [MCSB Data Protection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-data-protection#dp-8-ensure-security-of-key-and-certificate-repository) |
| **AM-1** | 1.1, 1.5, 2.1, 2.4 | CM-8, PM-5 | 2.4 | [MCSB Asset Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-asset-management#am-1-track-asset-inventory-and-their-risks) |
| **AM-2** | 2.5, 2.6, 2.7, 4.8 | CM-8, PM-5 | 6.3 | [MCSB Asset Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-asset-management#am-2-use-only-approved-services) |
| **AM-3** | 1.1, 2.1 | CM-8, CM-7 | 2.4 | [MCSB Asset Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-asset-management#am-3-ensure-security-of-asset-lifecycle-management) |
| **AM-4** | N/A | AC-2, AC-6 | N/A | [MCSB Asset Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-asset-management#am-4-limit-access-to-asset-management) |
| **AM-5** | 2.5, 2.6, 2.7 | CM-8, CM-7 | 6.3 | [MCSB Asset Management](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-asset-management#am-5-use-only-approved-applications-in-virtual-machine) |
| **LT-1** | 8.11 | AU-3, AU-6, AU-12, SI-4 | 10.6, 10.8, A3.5 | [MCSB Logging and Threat Detection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-logging-threat-detection#lt-1-enable-threat-detection-capabilities) |
| **LT-2** | 8.11 | AU-3, AU-6, AU-12, SI-4 | 10.6, 10.8, A3.5 | [MCSB Logging and Threat Detection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-logging-threat-detection#lt-2-enable-threat-detection-for-identity-and-access-management) |
| **LT-3** | 8.2, 8.5, 8.12 | AU-3, AU-6, AU-12, SI-4 | 10.1, 10.2, 10.3 | [MCSB Logging and Threat Detection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-logging-threat-detection#lt-3-enable-logging-for-security-investigation) |
| **LT-4** | 8.2, 8.5, 8.6, 8.7, 13.6 | AU-3, AU-6, AU-12, SI-4 | 10.8 | [MCSB Logging and Threat Detection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-logging-threat-detection#lt-4-enable-network-logging-for-security-investigation) |
| **LT-5** | 8.9, 8.11, 13.1 | AU-3, AU-6, AU-12, SI-4 | N/A | [MCSB Logging and Threat Detection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-logging-threat-detection#lt-5-centralize-security-log-management-and-analysis) |
| **LT-6** | 8.10 | AU-11 | 10.7 | [MCSB Logging and Threat Detection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-logging-threat-detection#lt-6-configure-log-storage-retention) |
| **LT-7** | 8.4 | AU-8 | 10.4 | [MCSB Logging and Threat Detection](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-logging-threat-detection#lt-7-use-approved-time-synchronization-sources) |
| **IR-1** | 17.4, 17.7 | IR-4, IR-8 | 10.8 | [MCSB Incident Response](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-incident-response#ir-1-preparation---update-incident-response-plan-and-handling-process) |
| **IR-2** | 17.1, 17.3, 17.6 | IR-4, IR-8, IR-5, IR-6 | 12.10 | [MCSB Incident Response](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-incident-response#ir-2-preparation---setup-incident-notification) |
| **IR-3** | 17.9 | IR-4, IR-5, IR-7 | 10.8 | [MCSB Incident Response](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-incident-response#ir-3-detection-and-analysis---create-incidents-based-on-high-quality-alerts) |
| **IR-4** | N/A | IR-4 | 12.10 | [MCSB Incident Response](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-incident-response#ir-4-detection-and-analysis---investigate-an-incident) |
| **IR-5** | N/A | IR-4 | 12.10 | [MCSB Incident Response](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-incident-response#ir-5-detection-and-analysis---prioritize-incidents) |
| **IR-6** | N/A | IR-4, IR-5, IR-6 | 12.10 | [MCSB Incident Response](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-incident-response#ir-6-containment-eradication-and-recovery---automate-the-incident-handling) |
| **IR-7** | N/A | IR-4 | 12.10 | [MCSB Incident Response](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-incident-response#ir-7-post-incident-activity---conduct-lessons-learned-and-retain-evidence) |
| **PV-1** | 4.1, 4.2 | CM-2, CM-6 | 1.1 | [MCSB Posture and Vulnerability Mgmt](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-posture-vulnerability-management#pv-1-define-and-establish-secure-configurations) |
| **PV-2** | 4.1, 4.2 | CM-2, CM-6 | 2.2 | [MCSB Posture and Vulnerability Mgmt](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-posture-vulnerability-management#pv-2-audit-and-enforce-secure-configurations) |
| **PV-3** | 4.1 | CM-2, CM-6 | 2.2 | [MCSB Posture and Vulnerability Mgmt](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-posture-vulnerability-management#pv-3-define-and-establish-secure-configurations-for-compute-resources) |
| **PV-4** | 4.1 | CM-2, CM-6 | 2.2 | [MCSB Posture and Vulnerability Mgmt](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-posture-vulnerability-management#pv-4-audit-and-enforce-secure-configurations-for-compute-resources) |
| **PV-5** | 5.5, 7.1, 7.5, 7.6 | RA-3, RA-5 | 6.1, 6.2 | [MCSB Posture and Vulnerability Mgmt](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-posture-vulnerability-management#pv-5-perform-vulnerability-assessments) |
| **PV-6** | 7.2, 7.3, 7.4, 7.7 | RA-3, RA-5 | 6.1, 6.2 | [MCSB Posture and Vulnerability Mgmt](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-posture-vulnerability-management#pv-6-rapidly-and-automatically-remediate-vulnerabilities) |
| **PV-7** | 18.1, 18.2, 18.3 | CA-8, RA-5 | 11.3 | [MCSB Posture and Vulnerability Mgmt](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-posture-vulnerability-management#pv-7-conduct-regular-red-team-operations) |
| **BR-1** | 11.2 | CP-2, CP-4, CP-9 | N/A | [MCSB Backup and Recovery](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-backup-recovery#br-1-ensure-regular-automated-backups) |
| **BR-2** | 11.3 | CP-6, CP-9 | 3.4 | [MCSB Backup and Recovery](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-backup-recovery#br-2-protect-backup-and-recovery-data) |
| **BR-3** | 11.5 | CP-9 | N/A | [MCSB Backup and Recovery](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-backup-recovery#br-3-validate-all-backups-including-customer-managed-keys) |
| **BR-4** | 11.5 | CP-4 | N/A | [MCSB Backup and Recovery](https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-backup-recovery#br-4-mitigate-risk-of-lost-keys) |

*Source: [MCSB Control Domains](https://learn.microsoft.com/en-us/security/benchmark/azure/overview)*

### How to Use
- **MCSB Control** = control ID and name from the Fabric Security Baseline
- **Responsibility** = as stated in the baseline (Customer, Microsoft, Shared)
- **Implementation Type** = Tenant Setting | Platform Config | Process Control | Microsoft Managed
- **Configuration** = the specific setting or action referenced
- **Baseline Guidance Summary** = summarized from the baseline document
- **Source** = URL to the relevant documentation

### Implementation Types
- **Tenant Setting** — Configurable in Fabric Admin Portal
- **Platform Config** — Configured in Entra ID, Azure, Purview, or Defender
- **Process Control** — Requires organizational procedure
- **Microsoft Managed** — Handled by Microsoft; no customer configuration required

### Where This Fits: SaaS Service Enablement for Regulated Industries

Regulated enterprises (financial services, healthcare, government, etc.) typically follow a structured process before enabling a new SaaS service in production. This document serves a specific role in that lifecycle:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  PHASE 1: DEMAND & ASSESSMENT                                               │
│                                                                             │
│  1. Business Use Case Identification                                        │
│     └─ Stakeholder identifies need for analytics/data platform capability   │
│                                                                             │
│  2. Third-Party Risk Management (TPRM) / Vendor Assessment                  │
│     └─ Procurement & Risk team evaluate Microsoft as vendor                 │
│     └─ Review SOC 2, ISO 27001, FedRAMP (if applicable), DPA, SLAs         │
│                                                                             │
│  3. Service-Level Security Assessment                                       │
│     └─ Map service capabilities to internal control framework               │
│     └─ Identify shared responsibility boundaries                            │
│     └─ Input: MCSB Fabric Security Baseline, Microsoft trust documents      │
│                                                                             │
│  4. Gap Analysis & Risk Acceptance                                          │
│     └─ Identify controls that cannot be satisfied by the platform           │
│     └─ Document compensating controls or accept residual risk               │
│     └─ Obtain CISO / Risk Committee sign-off                                │
├─────────────────────────────────────────────────────────────────────────────┤
│  PHASE 2: CONFIGURATION & HARDENING                                         │
│                                                                             │
│  5. Security Configuration Baseline   ◄── THIS DOCUMENT                    │
│     └─ Defines the complete inventory of security-relevant controls         │
│     └─ Maps each control to a specific setting, platform config, or process │
│     └─ Does NOT prescribe posture (enable/disable) — that is Step 6        │
│                                                                             │
│  6. Posture Decision & Policy Authoring                                     │
│     └─ Security team decides target state for each setting                  │
│     └─ Documents justification (e.g., "Disabled — data sovereignty req")    │
│     └─ Produces: Tenant Configuration Policy / SOPsecurity standards        │
│                                                                             │
│  7. Tenant Provisioning & Baseline Deployment                               │
│     └─ Admin applies configuration per the posture decisions                │
│     └─ Automate via Fabric REST APIs / Tenant Settings API where possible   │
│     └─ API: https://learn.microsoft.com/en-us/rest/api/fabric/admin/tenants │
├─────────────────────────────────────────────────────────────────────────────┤
│  PHASE 3: OPERATE & GOVERN                                                  │
│                                                                             │
│  8. Validation & Compliance Evidence                                        │
│     └─ Capture current tenant state via API                                 │
│     └─ Compare against posture decisions (drift detection)                  │
│     └─ Produce compliance artifacts for auditors                            │
│                                                                             │
│  9. Ongoing Monitoring & Alerting                                           │
│     └─ Microsoft Defender for Cloud Apps / Unified Audit Log                │
│     └─ Alert on setting changes, anomalous access, data exfiltration        │
│                                                                             │
│  10. Periodic Reassessment                                                  │
│      └─ Re-evaluate when Microsoft adds new settings or features            │
│      └─ Re-evaluate when internal framework changes                         │
│      └─ Refresh this baseline document (see AGENT_SKILL.md for process)     │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Key distinction**: This document (Step 5) tells you *what levers exist*. It does not tell you *which way to set them*. The posture decisions (Step 6) are organization-specific and depend on risk appetite, regulatory requirements, and business needs. Separating these concerns allows the baseline to remain factual and reusable across engagements while posture decisions are tailored per customer.

**Typical roles involved at each phase:**

| Phase | Primary Owner | Supporting Roles |
|-------|--------------|-----------------|
| 1. Use Case | Business Unit / Data Team | Enterprise Architecture |
| 2. TPRM | Procurement / Third-Party Risk | Legal, InfoSec |
| 3. Security Assessment | Information Security | Cloud Architecture, Compliance |
| 4. Gap Analysis | CISO Office / Risk | InfoSec, Compliance |
| 5. Configuration Baseline | Cloud Security Architecture | Platform Engineering |
| 6. Posture Decisions | CISO / Security Governance | Compliance, Legal, Business |
| 7. Deployment | Platform / Fabric Admin | Cloud Security, DevOps |
| 8. Validation | Compliance / Audit | Platform Engineering |
| 9. Monitoring | Security Operations (SOC) | Platform Engineering |
| 10. Reassessment | Cloud Security Architecture | All of the above |

### How This Relates to Compliance Frameworks, the MCSB, and Internal Policies

Regulated organizations operate within a layered hierarchy of controls. This document sits at a specific layer in that stack. Understanding the relationships prevents confusion about what this artifact does and does not replace.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  LAYER 1: EXTERNAL REGULATIONS & INDUSTRY STANDARDS                         │
│                                                                             │
│  Examples: NIST SP 800-53, PCI-DSS, SOX/FFIEC, HIPAA, DORA, NIS2,         │
│            CIS Controls, ISO 27001/27002, FedRAMP                           │
│                                                                             │
│  What they are: Mandatory or adopted-by-policy control requirements         │
│  Who owns them: Regulators, standards bodies, industry consortia            │
│  Fabric-specific? No — they are technology-agnostic                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                              ▼ mapped into ▼                                │
├─────────────────────────────────────────────────────────────────────────────┤
│  LAYER 2: CUSTOMER'S INTERNAL SECURITY FRAMEWORK / POLICY                   │
│                                                                             │
│  Examples: "Enterprise Information Security Policy v4.2",                   │
│            "Cloud Security Standard", "Data Classification Policy"          │
│                                                                             │
│  What they are: Organization-specific interpretation of Layer 1             │
│  Who owns them: CISO office, Risk & Compliance, Security Governance         │
│  Fabric-specific? No — they apply to all technologies/services              │
│                                                                             │
│  Typical structure:                                                         │
│  • Control domains (Access Control, Data Protection, Logging, etc.)         │
│  • Requirements per domain (e.g., "All data at rest must be encrypted       │
│    with keys managed per the Key Management Standard")                      │
│  • Risk ratings and exceptions process                                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                              ▼ satisfied by ▼                               │
├─────────────────────────────────────────────────────────────────────────────┤
│  LAYER 3: MICROSOFT CLOUD SECURITY BENCHMARK (MCSB)                         │
│                                                                             │
│  What it is: Microsoft's control framework that maps Azure/M365/Fabric      │
│              capabilities back to industry standards (NIST, CIS, PCI-DSS)   │
│  Who owns it: Microsoft Product Security                                    │
│  Fabric-specific? Partially — the MCSB Fabric Security Baseline is the     │
│                   service-specific view of the MCSB for Fabric              │
│                                                                             │
│  Role in the hierarchy:                                                     │
│  • Provides a BRIDGE between customer's internal framework (Layer 2) and    │
│    the actual platform capabilities (Layer 4)                               │
│  • Pre-maps to NIST, CIS, PCI-DSS so customers don't start from scratch    │
│  • Tells you WHAT controls exist and WHO is responsible (Customer vs MSFT)  │
│  • Does NOT tell you how to configure specific settings                     │
│                                                                             │
│  Published mappings (included in this document):                             │
│  • MCSB → NIST SP 800-53 r4                                                │
│  • MCSB → CIS Controls v8                                                  │
│  • MCSB → PCI-DSS v3.2.1                                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                              ▼ implemented by ▼                             │
├─────────────────────────────────────────────────────────────────────────────┤
│  LAYER 4: THIS DOCUMENT — FABRIC SECURITY CONFIGURATION BASELINE            │
│                                                                             │
│  What it is: Complete inventory of every security-relevant setting and      │
│              configuration available in Microsoft Fabric, mapped to the     │
│              MCSB controls they satisfy                                     │
│  Who owns it: Cloud Security Architecture / Consulting                      │
│  Fabric-specific? YES — this is entirely Fabric-specific                    │
│                                                                             │
│  Role in the hierarchy:                                                     │
│  • Translates MCSB controls into ACTIONABLE Fabric configurations           │
│  • Provides the "knobs and levers" inventory for each control domain        │
│  • Includes settings explicitly referenced in the baseline AND              │
│    additional settings mapped by inference (marked with †)                  │
│  • Enables traceability: Setting → MCSB Control → NIST/CIS/PCI-DSS →      │
│    Customer's internal policy requirement                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                              ▼ drives ▼                                     │
├─────────────────────────────────────────────────────────────────────────────┤
│  LAYER 5: CUSTOMER'S POSTURE DECISIONS (NOT IN THIS DOCUMENT)               │
│                                                                             │
│  What it is: The customer's specific enable/disable/restrict decisions      │
│              for each setting, based on their risk appetite & requirements   │
│  Who owns it: CISO / Security Governance with business input                │
│  Fabric-specific? Yes                                                       │
│                                                                             │
│  Example decisions:                                                         │
│  • "Disable all external sharing" (satisfies internal DLP-04 requirement)   │
│  • "Restrict export to PDF only for Confidential-labeled content"           │
│  • "Enable private links, disable public internet access"                   │
│  • "Accept risk: allow Azure Maps cross-geo processing (low data sens.)"   │
└─────────────────────────────────────────────────────────────────────────────┘
```

**The traceability chain** (bottom-up, for audit purposes):

```
Fabric Tenant Setting (e.g., "Block Public Internet Access = Enabled")
  └─► MCSB Control: NS-2 (Secure cloud native services with network controls)
       └─► NIST SP 800-53: AC-4, SC-2, SC-7
            └─► Customer Policy: "NET-03: All SaaS services must restrict 
                 network access to corporate-approved paths"
                 └─► Regulation: PCI-DSS Req 1.3 (Prohibit direct public 
                      access between Internet and cardholder data environment)
```

**Why this layering matters:**

| Question | Answered By |
|----------|-------------|
| "What regulations require us to do this?" | Layer 1 (NIST, PCI-DSS, etc.) |
| "What does our policy say we must do?" | Layer 2 (Internal framework) |
| "Does Microsoft's platform address our requirements?" | Layer 3 (MCSB Fabric Baseline) |
| "What specific settings exist to implement a given control?" | **Layer 4 (This document)** |
| "What should each setting be set to for our organization?" | Layer 5 (Posture decisions) |

**Common customer confusion this resolves:**

1. **"We have the MCSB baseline but don't know what to do"** — They are stuck between Layer 3 and Layer 4. This document bridges that gap.

2. **"We mapped MCSB to our internal framework but still can't configure Fabric"** — They completed the Layer 2↔Layer 3 mapping but lack the Layer 3→Layer 4 translation.

3. **"We need a list of all security settings"** — They want Layer 4 without the control mapping context. This document provides both: the inventory AND the traceability upward.

4. **"How do we prove compliance to our auditors?"** — Auditors want the full chain: Policy requirement → MCSB control → specific setting → evidence of configuration. This document provides the middle links.

---

## 1. Network Security (NS)

| MCSB Control | Responsibility | Implementation Type | Configuration | Baseline Guidance Summary | Source |
|---|---|---|---|---|---|
| NS-1: Establish network segmentation boundaries | Shared | Platform Config | Create and use managed private endpoints for notebooks, lakehouses, and Spark job definitions | Use managed private endpoints to securely connect to data sources behind private endpoints | [Baseline NS-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-1-establish-network-segmentation-boundaries) / [Managed Private Endpoints](https://learn.microsoft.com/en-us/fabric/security/security-managed-private-endpoints-create) |
| NS-2: Secure cloud native services with network controls | Shared | Tenant Setting | **Tenant-level Private Link** | Connect your Fabric tenant to a private link endpoint | [Baseline NS-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-2-secure-cloud-native-services-with-network-controls) / [Private Links](https://learn.microsoft.com/en-us/fabric/security/security-private-links-overview) |
| NS-2 | Shared | Tenant Setting | **Block Public Internet Access** | Disable public internet access to the Fabric tenant | [Baseline NS-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-2-secure-cloud-native-services-with-network-controls) / [Private Links](https://learn.microsoft.com/en-us/fabric/security/security-private-links-overview) |
| NS-2 | Shared | Tenant Setting | **Configure workspace-level inbound network rules** | Configure workspace-level private link access protection | [Baseline NS-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-2-secure-cloud-native-services-with-network-controls) / [Workspace Private Links](https://learn.microsoft.com/en-us/fabric/security/security-workspace-level-private-links-overview) |
| NS-2 | Shared | Tenant Setting | **Configure workspace-level outbound network rules** | Configure outbound access protection for workspaces | [Baseline NS-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-2-secure-cloud-native-services-with-network-controls) / [Outbound Access Protection](https://learn.microsoft.com/en-us/fabric/security/workspace-outbound-access-protection-overview) |
| NS-2 | Shared | Tenant Setting | **Configure workspace-level IP firewall rules** | Configure workspace-level firewall rules | [Baseline NS-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-2-secure-cloud-native-services-with-network-controls) / [Workspace Firewall](https://learn.microsoft.com/en-us/fabric/security/security-workspace-level-firewall-overview) |
| NS-2 | Shared | Platform Config | **Entra ID Conditional Access** for inbound network traffic control | Inbound network traffic control for SaaS via Conditional Access Policies | [Baseline NS-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-2-secure-cloud-native-services-with-network-controls) / [Protect Inbound Traffic](https://learn.microsoft.com/en-us/fabric/security/protect-inbound-traffic) |
| NS-3: Deploy firewall at edge of enterprise network | Microsoft | Microsoft Managed | N/A - automatic protections built into Azure infrastructure | Microsoft Fabric has automatic protections for well-known common attack vectors | [Baseline NS-3](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-3-deploy-firewall-at-the-edge-of-enterprise-network) |
| NS-4: Deploy IDS/IPS | Shared | Platform Config | Track user activities via activity and audit logs | Fabric does not have explicit IDS/IPS; provides activity and audit logs for monitoring | [Baseline NS-4](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-4-deploy-intrusion-detectionintrusion-prevention-systems-idsips) / [Track User Activities](https://learn.microsoft.com/en-us/fabric/admin/track-user-activities) |
| NS-5: Deploy DDoS protection | Microsoft | Microsoft Managed | N/A - built-in DDoS protection | Microsoft Fabric has built-in DDoS protection managed by Microsoft | [Baseline NS-5](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-5-deploy-ddos-protection) |
| NS-6: Deploy web application firewall | Microsoft | Microsoft Managed | N/A - built-in WAF managed by Microsoft | Microsoft Fabric has built-in WAF managed by Microsoft | [Baseline NS-6](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-6-deploy-web-application-firewall) |
| NS-7: Simplify network security configuration | N/A | N/A | Not applicable | Fabric does not expose underlying network configurations | [Baseline NS-7](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-7-simplify-network-security-configuration-na) |
| NS-8: Detect and disable insecure services and protocols | N/A | N/A | Not applicable | Fabric does not expose underlying configurations | [Baseline NS-8](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-8-detect-and-disable-insecure-services-and-protocols-na) |
| NS-9: Connect on-premises or cloud network privately | Customer | Platform Config | Deploy virtual network data gateway or on-premises data gateway | Use VNet data gateway or on-premises data gateway for hybrid connectivity | [Baseline NS-9](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-9-connect-on-premises-or-cloud-network-privately) / [VNet Gateway](https://learn.microsoft.com/en-us/data-integration/vnet/data-gateway-architecture) / [On-prem Gateway](https://learn.microsoft.com/en-us/power-bi/connect-data/service-gateway-onprem) |
| NS-10: Ensure DNS security | N/A | N/A | Not applicable | Fabric does not expose DNS configurations | [Baseline NS-10](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-10-ensure-domain-name-system-dns-security-na) |

---

## 2. Identity Management (IM)

| MCSB Control | Responsibility | Implementation Type | Configuration | Baseline Guidance Summary | Source |
|---|---|---|---|---|---|
| IM-1: Use centralized identity and authentication system | Customer | Platform Config | **Microsoft Entra ID** as default identity and access management service | Standardize on Entra ID; assess Identity Secure Score; govern external identities via B2B | [Baseline IM-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-1-use-centralized-identity-and-authentication-system) / [Fabric B2B](https://learn.microsoft.com/en-us/fabric/security/security-b2b) |
| IM-1 | Customer | Tenant Setting | **Guest users can access Microsoft Fabric** | Control guest user access to Fabric (baseline references B2B) | [Baseline IM-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-1-use-centralized-identity-and-authentication-system) / [B2B Tenant Setting](https://learn.microsoft.com/en-us/fabric/enterprise/powerbi/service-admin-entra-b2b) |
| IM-1 | Customer | Tenant Setting | **Users can invite guest users to collaborate through item sharing and permissions** | Control whether users can invite guests via item sharing (baseline references B2B) | [Baseline IM-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-1-use-centralized-identity-and-authentication-system) / [B2B Invite](https://learn.microsoft.com/en-us/fabric/enterprise/powerbi/service-admin-entra-b2b#invite-guest-users) |
| IM-1 | Customer | Tenant Setting | **Guest users can browse and access Fabric content** | Control whether guests can browse and request access to content (baseline references B2B) | [Baseline IM-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-1-use-centralized-identity-and-authentication-system) / [B2B Access](https://learn.microsoft.com/en-us/fabric/enterprise/powerbi/service-admin-entra-b2b) |
| IM-1 † | Customer | Tenant Setting | **Block ResourceKey Authentication** | Block use of resource key based authentication for streaming semantic models | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-developer#block-resourcekey-authentication) |
| IM-1 † | Customer | Tenant Setting | **Allow non-Entra ID auth in Eventstream** | Control whether non-Entra authentication is allowed in Eventstream Custom Endpoint | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-integration) |
| IM-1 † | Customer | Tenant Setting | **Users can see guest users in lists of suggested people** | Control guest visibility in people pickers | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-export-sharing#users-can-see-guest-users-in-lists-of-suggested-people) |
| IM-1 † | Customer | Tenant Setting | **Microsoft Entra SSO for data gateway** | Sends user access token information (name, email) to on-premises data sources for SSO authentication | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-integration#azure-ad-single-sign-on-sso-for-gateway) |
| IM-2: Protect identity and authentication systems | Customer | Platform Config | **Entra ID security baseline and Identity Secure Score** | Secure identity system as high priority; use Entra ID security operations guide | [Baseline IM-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-2-protect-identity-and-authentication-systems) / [Entra Security Operations](https://learn.microsoft.com/en-us/entra/architecture/security-operations-introduction) |
| IM-3: Manage application identities securely | Customer | Platform Config | **Workspace Identity** (managed service principal) | Use managed identities instead of human accounts; use workspace identity for credential-free auth | [Baseline IM-3](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-3-manage-application-identities-securely-and-automatically) / [Workspace Identity](https://learn.microsoft.com/en-us/fabric/security/workspace-identity) |
| IM-3 | Customer | Tenant Setting | **Service principals can call Fabric public APIs** | Allow service principals to call Fabric APIs (baseline references SP support) | [Baseline IM-3](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-3-manage-application-identities-securely-and-automatically) / [SP APIs](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-developer#service-principals-can-call-fabric-public-apis) |
| IM-3 † | Customer | Tenant Setting | **Service principals can create workspaces, connections, and deployment pipelines** | Allow service principals to create workspaces and deployment resources | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-developer#service-principals-can-create-workspaces-connections-and-deployment-pipelines) |
| IM-4: Authenticate server and services | Customer | Microsoft Managed | **TLS 1.2+ enforcement** | Fabric enforces TLS 1.2+ on all connections; ensure data ingestion processes are secured | [Baseline IM-4](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-4-authenticate-server-and-services) / [Data in Transit](https://learn.microsoft.com/en-us/fabric/security/security-fundamentals#data-in-transit) |
| IM-5: Use SSO for application access | Customer | Platform Config | **Microsoft Entra ID SSO** | Fabric uses Entra ID for SSO across cloud and on-premises applications | [Baseline IM-5](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-5-use-single-sign-on-sso-for-application-access) / [Entra ID SSO](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on) |
| IM-6: Use strong authentication controls | Customer | Platform Config | **MFA, passwordless, block legacy auth** | Enforce strong authentication via centralized identity system | [Baseline IM-6](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-6-use-strong-authentication-controls) / [Enable MFA](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-mfa-getstarted) / [Block Legacy Auth](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-block-legacy-authentication) |
| IM-7: Restrict resource access based on conditions | Customer | Platform Config | **Entra ID Conditional Access for Fabric** | Enforce MFA, allow only Intune enrolled devices, restrict user locations and IP ranges | [Baseline IM-7](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-7-restrict-resource-access-based-on-conditions) / [Conditional Access for Fabric](https://learn.microsoft.com/en-us/fabric/security/security-conditional-access) |
| IM-8: Restrict exposure of credentials and secrets | Customer | Platform Config | **Workspace Identity + Credential Scanner** | Use workspace identity for credential-free auth; implement Credential Scanner; use Key Vault | [Baseline IM-8](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-8-restrict-the-exposure-of-credentials-and-secrets) / [Workspace Identity](https://learn.microsoft.com/en-us/fabric/security/workspace-identity) / [Purview Scan Fabric](https://learn.microsoft.com/en-us/purview/register-scan-fabric-tenant) |
| IM-8 † | Customer | Tenant Setting | **Use short-lived user-delegated SAS tokens** | Control OneLake SAS token generation | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-onelake) |
| IM-8 † | Customer | Tenant Setting | **Authenticate with OneLake user-delegated SAS tokens** | Control SAS token authentication to OneLake | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-onelake) |
| IM-8 † | Customer | Tenant Setting | **Dremio SSO** | Sends user access token (name, email) to Dremio for authentication | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-integration) |
| IM-8 † | Customer | Tenant Setting | **Snowflake SSO** | Sends user access token (name, email) to Snowflake for authentication | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/connect-data/service-connect-snowflake) |
| IM-8 † | Customer | Tenant Setting | **Redshift SSO** | Sends user access token (name, email) to Redshift for authentication | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/connect-data/service-gateway-sso-overview) |
| IM-8 † | Customer | Tenant Setting | **Google BigQuery SSO** | Sends user access token (name, email) to Google BigQuery for authentication | [Tenant Setting](https://learn.microsoft.com/en-us/power-query/connectors/google-bigquery-aad) |
| IM-8 † | Customer | Tenant Setting | **AppSource Custom Visuals SSO** | Sends Entra ID access tokens to AppSource custom visual publishers (may cross regions) | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/admin/organizational-visuals#appsource-custom-visuals-sso) |
| IM-9: Secure user access to existing applications | Customer | Platform Config | **On-premises data gateway** for secure hybrid data access | Use on-prem gateway for securely transferring data from on-premises to Fabric | [Baseline IM-9](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#im-9-secure-user-access-to-existing-applications) / [On-prem Gateway](https://learn.microsoft.com/en-us/data-integration/gateway/service-gateway-onprem) |

---

## 3. Privileged Access (PA)

| MCSB Control | Responsibility | Implementation Type | Configuration | Baseline Guidance Summary | Source |
|---|---|---|---|---|---|
| PA-1: Separate and limit highly privileged/administrative users | Customer | Tenant Setting | **Service principals can access read-only admin APIs** | Enable service principal authentication for admin APIs with task-specific permissions | [Baseline PA-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pa-1-separate-and-limit-highly-privilegedadministrative-users) / [Enable SP Admin APIs](https://learn.microsoft.com/en-us/fabric/admin/enable-service-principal-admin-apis) |
| PA-1 | Customer | Tenant Setting | **Delegate tenant settings** | Exercise caution when delegating settings to capacity and workspace admins | [Baseline PA-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pa-1-separate-and-limit-highly-privilegedadministrative-users) / [Delegate Settings](https://learn.microsoft.com/en-us/fabric/admin/delegate-settings) |
| PA-1 | Customer | Platform Config | **Privileged Identity Management (PIM)** | Use PIM for just-in-time admin access; limit standing Fabric/Global admin assignments | [Baseline PA-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pa-1-separate-and-limit-highly-privilegedadministrative-users) / [PIM](https://learn.microsoft.com/en-us/purview/privileged-access-management-configuration) |
| PA-1 † | Customer | Tenant Setting | **Service principals can access admin APIs used for updates** | Allow service principals to authenticate to write admin APIs | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/enable-service-principal-admin-apis) |
| PA-1 † | Customer | Tenant Setting | **Enhance admin APIs responses with detailed metadata** | API callers get table/column names from scan results (data exposure via admin APIs) | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-admin-api-settings#enhance-admin-apis-responses-with-detailed-metadata) |
| PA-1 † | Customer | Tenant Setting | **Enhance admin APIs responses with DAX and mashup expressions** | API callers get DAX queries and mashup expressions (logic/query exposure) | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-admin-api-settings#enhance-admin-apis-responses-with-dax-and-mashup-expressions) |
| PA-2: Avoid standing access for user accounts and permissions | N/A | N/A | Not applicable | N/A per baseline | [Baseline PA-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pa-2-avoid-standing-access-for-user-accounts-and-permissions-na) |
| PA-3: Manage lifecycle of identities and entitlements | Customer | Platform Config | **Metadata scanning + Permission model** | Use automated process to monitor and manage access permissions to tenant and items | [Baseline PA-3](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pa-3-manage-lifecycle-of-identities-and-entitlements) / [Metadata Scanning](https://learn.microsoft.com/en-us/fabric/governance/metadata-scanning-overview) / [Permission Model](https://learn.microsoft.com/en-us/fabric/security/permission-model) |
| PA-4: Review and reconcile user access regularly | Customer | Process Control | **Activity log review + access audit** | Analyze usage for all Fabric resources using activity logs, REST API, or PowerShell cmdlets | [Baseline PA-4](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pa-4-review-and-reconcile-user-access-regularly) / [Track User Activities](https://learn.microsoft.com/en-us/fabric/admin/track-user-activities) |
| PA-5: Set up emergency access | N/A | N/A | Not applicable | N/A per baseline | [Baseline PA-5](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pa-5-set-up-emergency-access-na) |
| PA-6: Use privileged access workstations | Customer | Process Control | **PAW/SAW for admin tasks** | Use secure workstations for admin tasks; enforce via Conditional Access device compliance | [Baseline PA-6](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pa-6-use-privileged-access-workstations) / [PAW Overview](https://learn.microsoft.com/en-us/security/compass/overview) / [PAW Deployment](https://learn.microsoft.com/en-us/security/privileged-access-workstations/privileged-access-deployment) |
| PA-7: Follow just enough administration (least privilege) | Customer | Process Control | **RBAC at workspace, capacity, and item level** | Follow least privilege; use fine-grained role-based access control | [Baseline PA-7](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pa-7-follow-just-enough-administration-least-privilege-principle) / [Permission Model](https://learn.microsoft.com/en-us/fabric/security/permission-model) |
| PA-7 † | Customer | Tenant Setting | **Create workspaces** | Control who can create app workspaces (restricts resource provisioning) | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/portal-workspace#create-workspaces) |
| PA-7 † | Customer | Tenant Setting | **Enable granular access control for all data connections** | Enforce strict access control; shared items disconnected if edited by users without data connection permission | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-integration) |
| PA-8: Determine access process for cloud provider support | Customer | Platform Config | **Customer Lockbox** | Establish approval process for Microsoft support access; use Lockbox to review/approve data access requests | [Baseline PA-8](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pa-8-determine-access-process-for-cloud-provider-support) / [Lockbox for Fabric](https://learn.microsoft.com/en-us/fabric/security/security-lockbox) |

---

## 4. Data Protection (DP)

| MCSB Control | Responsibility | Implementation Type | Configuration | Baseline Guidance Summary | Source |
|---|---|---|---|---|---|
| DP-1: Discover, classify, and label sensitive data | Customer | Tenant Setting | **Allow users to apply sensitivity labels for content** | Use Microsoft Purview sensitivity labels on Fabric items to protect against unauthorized access and leakage | [Baseline DP-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#dp-1-discover-classify-and-label-sensitive-data) / [Apply Sensitivity Labels](https://learn.microsoft.com/en-us/fabric/fundamentals/apply-sensitivity-labels) |
| DP-1 † | Customer | Tenant Setting | **Apply sensitivity labels from data sources to their data in Power BI** | Inherit sensitivity labels from supported data sources | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/enterprise/service-security-sensitivity-label-inheritance-from-data-sources) |
| DP-1 † | Customer | Tenant Setting | **Automatically apply sensitivity labels to downstream content** | When a label is changed or applied, also apply to eligible downstream content | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/enterprise/service-security-sensitivity-label-downstream-inheritance) |
| DP-1 † | Customer | Tenant Setting | **Restrict content with protected labels from being shared via link with everyone in your organization** | Prevent protected content from being shared via org-wide links | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-information-protection#restrict-content-with-protected-labels-from-being-shared-via-link-with-everyone-in-your-organization) |
| DP-1 † | Customer | Tenant Setting | **Users can export workspace items with applied sensitivity labels to Git repositories** | Control export of labeled items to Git | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/git-integration-admin-settings#users-can-export-workspace-items-with-applied-sensitivity-labels-to-git-repositories) |
| DP-1 † | Customer | Tenant Setting | **Allow workspace admins to override automatically applied sensitivity labels** | Allows workspace admins to change or remove labels applied automatically (weakens label enforcement) | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/enterprise/service-security-sensitivity-label-change-enforcement#relaxations-to-accommodate-automatic-labeling-scenarios) |
| DP-2: Monitor anomalies and threats targeting sensitive data | Customer | Platform Config | **Microsoft Purview Data Loss Prevention Policies** | Use DLP policies to detect upload of sensitive data and trigger automatic remediation | [Baseline DP-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#dp-2-monitor-anomalies-and-threats-targeting-sensitive-data) / [DLP Overview](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp) |
| DP-2 | Customer | Process Control | **Track user activities** | Use activity and audit logs to monitor data access patterns | [Baseline DP-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#dp-2-monitor-anomalies-and-threats-targeting-sensitive-data) / [Track Activities](https://learn.microsoft.com/en-us/power-bi/enterprise/service-admin-auditing) |
| DP-2 † | Customer | Tenant Setting | **Export to Excel** | Control export of data from visualizations to Excel | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/visuals/power-bi-visualization-export-data) |
| DP-2 † | Customer | Tenant Setting | **Export to .csv** | Control export of data to CSV files | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/paginated-reports/report-builder/export-csv-file-report-builder) |
| DP-2 † | Customer | Tenant Setting | **Download reports** | Control download of .pbix files and paginated reports | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/create-reports/service-export-to-pbix) |
| DP-2 † | Customer | Tenant Setting | **Export reports as PowerPoint presentations or PDF documents** | Control export of reports as PowerPoint/PDF | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-export-sharing#export-reports-as-powerpoint-presentations-or-pdf-documents) |
| DP-2 † | Customer | Tenant Setting | **Export reports as MHTML documents** | Control export of paginated reports as MHTML | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-export-sharing) |
| DP-2 † | Customer | Tenant Setting | **Export reports as Word documents** | Control export of paginated reports as Word | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/paginated-reports/report-builder/export-microsoft-word-report-builder) |
| DP-2 † | Customer | Tenant Setting | **Export reports as XML documents** | Control export of paginated reports as XML | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/paginated-reports/report-builder/export-xml-report-builder) |
| DP-2 † | Customer | Tenant Setting | **Export reports as image files** | Control export of reports as image files via API | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/paginated-reports/report-builder/export-image-file-report-builder) |
| DP-2 † | Customer | Tenant Setting | **Print dashboards and reports** | Control printing of dashboards and reports | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/consumer/end-user-print) |
| DP-2 † | Customer | Tenant Setting | **Publish to web** | Control public embedding of reports (no authentication required to view) | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-export-sharing#publish-to-web) |
| DP-2 † | Customer | Tenant Setting | **Allow downloads from custom visuals** | Control whether custom visuals can download data | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/admin/organizational-visuals#export-data-to-file) |
| DP-2 † | Customer | Tenant Setting | **External data sharing** | Control sharing of OneLake data with collaborators outside your organization | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/governance/external-data-sharing-overview) |
| DP-2 † | Customer | Tenant Setting | **Users can accept external data shares** | Control acceptance of external data share links | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/governance/external-data-sharing-overview) |
| DP-2 † | Customer | Tenant Setting | **Allow shareable links to grant access to everyone in your organization** | Control org-wide sharing links | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-export-sharing#allow-shareable-links-to-grant-access-to-everyone-in-your-organization) |
| DP-2 † | Customer | Tenant Setting | **Users can send email subscriptions to external users** | Control email subscriptions to users outside the organization | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-export-sharing#users-can-send-email-subscriptions-to-external-users) |
| DP-2 † | Customer | Tenant Setting | **B2B guest users can set up and be subscribed to email subscriptions** | Control guest user email subscriptions | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-export-sharing#b2b-guest-users-can-set-up-and-be-subscribed-to-email-subscriptions) |
| DP-2 † | Customer | Tenant Setting | **Users with read or write permission can download data from notebooks** | Control notebook data downloads | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-export-sharing) |
| DP-2 † | Customer | Tenant Setting | **Guest users can work with shared semantic models in their own tenants** | Allow cross-tenant dataset access for guests | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/collaborate-share/service-dataset-external-org-share-admin#allow-guest-users-to-work-with-shared-datasets-in-their-own-tenants) |
| DP-2 † | Customer | Tenant Setting | **Allow specific users to turn on external data sharing** | Control who can enable external data sharing | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/collaborate-share/service-dataset-external-org-share-admin#allow-specific-users-to-turn-on-external-data-sharing) |
| DP-2 † | Customer | Tenant Setting | **Users can access data stored in OneLake with apps external to Fabric** | Control external app access to OneLake via ADLS APIs | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/onelake/security/fabric-onelake-security#allow-apps-running-outside-of-fabric-to-access-data-via-onelake) |
| DP-2 † | Customer | Tenant Setting | **Users can sync data in OneLake with the OneLake File Explorer app** | Control OneLake File Explorer sync to local machine | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/onelake/onelake-file-explorer) |
| DP-2 † | Customer | Tenant Setting | **Users can use Copilot and other features powered by Azure OpenAI** | Control access to AI/Copilot features (data sent to AI model) | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-copilot) |
| DP-2 † | Customer | Tenant Setting | **Share Fabric data with your Microsoft 365 services** | Control data sharing with M365 services (search, Copilot) | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/admin-share-power-bi-metadata-microsoft-365-services) |
| DP-2 † | Customer | Tenant Setting | **Allow Microsoft Purview to secure AI interactions** | Allow Purview to access/process Copilot prompts and responses | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-information-protection) |
| DP-2 † | Customer | Tenant Setting | **Users can export items to Git repositories in other geographical locations** | Control cross-geo Git export (data leaves region) | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/git-integration-admin-settings#users-can-export-items-to-git-repositories-in-other-geographical-locations) |
| DP-2 † | Customer | Tenant Setting | **Allow XMLA endpoints and Analyze in Excel with on-premises semantic models** | Allows direct model access via XMLA protocol and Excel live connections (bypasses report-level controls) | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/collaborate-share/service-analyze-in-excel) |
| DP-2 † | Customer | Tenant Setting | **Semantic Model Execute Queries REST API** | Allows DAX queries against semantic models via REST API | [Tenant Setting](https://learn.microsoft.com/en-us/rest/api/power-bi/datasets/execute-queries) |
| DP-2 † | Customer | Tenant Setting | **Users can use the Power BI MCP server endpoint (preview)** | Allows external MCP clients to connect to and query Power BI artifacts | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-integration) |
| DP-2 † | Customer | Tenant Setting | **Embed content in apps** | Allows embedding Power BI content in external web applications | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/developer/embedded/embedded-analytics-power-bi) |
| DP-2 † | Customer | Tenant Setting | **Semantic models can export data to OneLake** | Allows import tables to be sent from semantic models to OneLake | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/enterprise/onelake-integration-overview) |
| DP-2 † | Customer | Tenant Setting | **Allow access to the browser's local storage** | Allows custom visuals to store information on user's browser local storage | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/admin/organizational-visuals#appsource-custom-visuals-sso) |
| DP-2 † | Customer | Tenant Setting | **Copy and paste visuals** | Allows users to copy visuals and paste as static images into external applications | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-export-sharing) |
| DP-2 † | Customer | Tenant Setting | **Enable Power BI add-in for PowerPoint** | Allows embedding Power BI data into PowerPoint presentations | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-export-sharing#enable-power-bi-add-in-for-powerpoint) |
| DP-2 † | Customer | Tenant Setting | **Per-user data in usage metrics for content creators** | Exposes display names and email addresses of users accessing content in usage metrics | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/collaborate-share/service-modern-usage-metrics#exclude-user-information-from-usage-metrics-reports) |
| DP-2 † | Customer | Tenant Setting | **Microsoft can store query text to aid in support investigations** | Query text is stored by Microsoft for support; turning off limits support capability | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/query-text-storage) |
| DP-3: Encrypt sensitive data in transit | Customer | Microsoft Managed | **TLS 1.2+ enforced** | Ensure clients and data sources can negotiate TLS v1.2 or greater | [Baseline DP-3](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#dp-3-encrypt-sensitive-data-in-transit) / [TLS Enforcement](https://learn.microsoft.com/en-us/power-bi/admin/service-admin-power-bi-security#enforcing-tls-version-usage) |
| DP-3 † | Customer | Tenant Setting | **Data sent to Azure OpenAI can be processed outside your capacity's geographic region** | Control cross-geo AI data processing (data in transit to other region) | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-copilot) |
| DP-3 † | Customer | Tenant Setting | **Data sent to Azure OpenAI can be stored outside your capacity's geographic region** | Data sent to AI features may be stored (not just processed) outside your geo/compliance boundary | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/fundamentals/copilot-fabric-overview#available-regions) |
| DP-3 † | Customer | Tenant Setting | **Enable Operations Agents (Preview)** | Data sent to operations agents processed through Azure AI Bot Service (processes in EU Data Boundary) | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-microsoft-fabric-tenant-settings) |
| DP-3 † | Customer | Tenant Setting | **Data sent to Azure Maps can be processed outside your tenant's geographic region** | Location data sent to Azure Maps may be processed outside geo/compliance boundary | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-integration) |
| DP-3 † | Customer | Tenant Setting | **Data sent to Azure Maps can be processed by Microsoft Online Services Subprocessors** | Location data may be shared with third-party subprocessors; data may be stored in US or other countries | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-integration) |
| DP-4: Enable data at rest encryption by default | Microsoft | Microsoft Managed | N/A - Microsoft encrypts all data at rest by default | Fabric encrypts all data at rest and in transit by default | [Baseline DP-4](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#dp-4-enable-data-at-rest-encryption-by-default) |
| DP-5: Use customer-managed key option | Customer | Tenant Setting | **Apply customer-managed keys** | If required for regulatory compliance, enable CMK for imported semantic models in Premium capacities | [Baseline DP-5](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#dp-5-use-customer-managed-key-option-in-data-at-rest-encryption-when-required) / [CMK in Fabric](https://learn.microsoft.com/en-us/fabric/security/workspace-customer-managed-keys) / [BYOK Power BI](https://learn.microsoft.com/en-us/power-bi/enterprise/service-encryption-byok) |
| DP-6: Use a secure key management process | Customer | Platform Config | **Azure Key Vault (HSM-backed)** | Use secure key vault for key generation, distribution, storage; rotate and revoke keys | [Baseline DP-6](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#dp-6-use-a-secure-key-management-process) / [HSM Key Import](https://learn.microsoft.com/en-us/azure/key-vault/keys/hsm-protected-keys-byok) |
| DP-7: Use a secure certificate management process | N/A | N/A | Not applicable | N/A per baseline | [Baseline DP-7](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#dp-7-use-a-secure-certificate-management-process-na) |
| DP-8: Ensure security of key and certificate repository | N/A | N/A | Not applicable | N/A per baseline | [Baseline DP-8](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#dp-8-ensure-security-of-key-and-certificate-repository-na) |

---

## 5. Asset Management (AM)

| MCSB Control | Responsibility | Implementation Type | Configuration | Baseline Guidance Summary | Source |
|---|---|---|---|---|---|
| AM-1: Track asset inventory and their risks | Shared | Platform Config | **Fabric Scanner API (metadata scanning)** | Use Scanner API to set up metadata scanning of your organization's Fabric items | [Baseline AM-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#am-1-track-asset-inventory-and-their-risks) / [Metadata Scanning](https://learn.microsoft.com/en-us/fabric/governance/metadata-scanning-run) |
| AM-2: Use only approved services | Customer | Tenant Setting | **Users can create Fabric items** | Restrict which workloads users can create and access in the tenant | [Baseline AM-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#am-2-use-only-approved-services) / [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-microsoft-fabric-tenant-settings) |
| AM-2 | Customer | Platform Config | **Azure Policy for Fabric capacity provisioning** | Use Azure Policies to control who can provision Fabric capacities | [Baseline AM-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#am-2-use-only-approved-services) / [Azure Policy](https://learn.microsoft.com/en-us/azure/governance/policy/tutorials/create-and-manage) |
| AM-2 | Customer | Tenant Setting | **Delegate tenant settings** | Use tenant, capacity, or workspace admin delegated controls | [Baseline AM-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#am-2-use-only-approved-services) / [Delegate Settings](https://learn.microsoft.com/en-us/fabric/admin/delegate-settings) |
| AM-2 † | Customer | Tenant Setting | **Allow visuals created using the Power BI SDK** | Control import of custom visuals from AppSource or file | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/admin/organizational-visuals#visuals-from-appsource-or-a-file) |
| AM-2 † | Customer | Tenant Setting | **Add and use certified visuals only (block uncertified)** | Restrict to certified custom visuals only | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/admin/organizational-visuals#certified-power-bi-visuals) |
| AM-2 † | Customer | Tenant Setting | **Interact with and share R and Python visuals** | Allows visuals with arbitrary R/Python code execution | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-r-python-visuals) |
| AM-2 † | Customer | Tenant Setting | **Web content on dashboard tiles** | Allows web content tiles on dashboards (Microsoft notes: may expose org to security risks) | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/create-reports/service-dashboard-add-widget#add-web-content) |
| AM-2 † | Customer | Tenant Setting | **Workspace admins can add and remove additional workloads (preview)** | Third-party workloads receive user data and access tokens; sensitivity labels not enforced | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-microsoft-fabric-tenant-settings) |
| AM-2 † | Customer | Tenant Setting | **Users can see and work with additional workloads not validated by Microsoft** | Allows untrusted/unvalidated third-party workloads | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/workload-development-kit/publish-workload-requirements) |
| AM-2 † | Customer | Tenant Setting | **Install template apps not listed in AppSource** | Allows installing template apps from sources not vetted by Microsoft | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-template-app) |
| AM-3: Ensure security of asset lifecycle management | Customer | Process Control | **Remove unused resources; manage lifecycle** | Establish security policies for asset lifecycle; identify and remove unneeded resources | [Baseline AM-3](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#am-3-ensure-security-of-asset-lifecycle-management) / [Get Unused Artifacts API](https://learn.microsoft.com/en-us/rest/api/power-bi/admin/groups-get-unused-artifacts-as-admin) |
| AM-3 † | Customer | Tenant Setting | **Users can synchronize workspace items with their Git repositories** | Control Git integration for workspace items (asset lifecycle via source control) | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/intro-to-git-integration) |
| AM-4: Limit access to asset management | Customer | Process Control | **Least privilege for tenant, workspace, and capacity admin roles** | Limit users with highly privileged roles; use least privilege for all management features | [Baseline AM-4](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#am-4-limit-access-to-asset-management) / [Fabric Admin](https://learn.microsoft.com/en-us/fabric/admin/microsoft-fabric-admin) / [Workspace Roles](https://learn.microsoft.com/en-us/fabric/fundamentals/roles-workspaces) / [Capacity Settings](https://learn.microsoft.com/en-us/fabric/admin/capacity-settings) |
| AM-5: Use only approved applications in VM | N/A | N/A | Not applicable | N/A per baseline | [Baseline AM-5](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#am-5-use-only-approved-applications-in-virtual-machine-na) |

---

## 6. Logging and Threat Detection (LT)

| MCSB Control | Responsibility | Implementation Type | Configuration | Baseline Guidance Summary | Source |
|---|---|---|---|---|---|
| LT-1: Enable threat detection capabilities | Customer | Platform Config | **Microsoft Purview Compliance Manager alerts; activity monitoring** | Monitor all known resource types for threats; configure alert filtering from log data | [Baseline LT-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#lt-1-enable-threat-detection-capabilities) / [Purview Compliance Manager Alerts](https://learn.microsoft.com/en-us/purview/compliance-manager-alert-policies) |
| LT-2: Enable threat detection for identity and access management | Customer | Platform Config | **Microsoft Defender for Cloud Apps + Sentinel** | Forward logs to SIEM; use Defender for Cloud Apps for anomaly detection | [Baseline LT-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#lt-2-enable-threat-detection-for-azure-identity-and-access-management) / [Defender for Cloud Apps in Fabric](https://learn.microsoft.com/en-us/fabric/governance/service-security-using-defender-for-cloud-apps-controls) / [Track Activities](https://learn.microsoft.com/en-us/power-bi/admin/service-admin-auditing) |
| LT-3: Enable logging for security investigation | Customer | Platform Config | **Admin monitoring workspace + Workspace monitoring + Log Analytics + OneLake Diagnostics** | Activity and audit logs enabled by default; additional workspace-level logging available | [Baseline LT-3](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#lt-3-enable-logging-for-security-investigation) / [Workspace Monitoring](https://learn.microsoft.com/en-us/fabric/fundamentals/workspace-monitoring-overview) / [Log Analytics](https://learn.microsoft.com/en-us/power-bi/transform-model/log-analytics/desktop-log-analytics-overview) / [OneLake Diagnostics](https://learn.microsoft.com/en-us/fabric/onelake/onelake-diagnostics-overview) |
| LT-3 | Customer | Tenant Setting | **Azure Log Analytics connections for workspace administrators** | Enable centralized logging to Log Analytics (referenced in baseline LT-3 via linked docs) | [Baseline LT-3](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#lt-3-enable-logging-for-security-investigation) / [Log Analytics Config](https://learn.microsoft.com/en-us/power-bi/transform-model/log-analytics/desktop-log-analytics-configure) |
| LT-3 | Customer | Tenant Setting | **Workspace admins can turn on monitoring for their workspaces** | Enable workspace-level monitoring (referenced in baseline LT-3 via linked docs) | [Baseline LT-3](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#lt-3-enable-logging-for-security-investigation) / [Enable Workspace Monitoring](https://learn.microsoft.com/en-us/fabric/fundamentals/enable-workspace-monitoring) |
| LT-3 † | Customer | Tenant Setting | **Include end-user identifiers in OneLake diagnostic logs** | Controls whether PII (email, IP) is captured in OneLake diagnostic logs | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-onelake) |
| LT-4: Enable network logging for security investigation | Shared | Platform Config | **Private Link logging and monitoring** | For customers using Private Links, configure available logging and monitoring | [Baseline LT-4](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#lt-4-enable-network-logging-for-security-investigation) / [Private Link Logging](https://learn.microsoft.com/en-us/azure/private-link/private-link-overview#logging-and-monitoring) |
| LT-5: Centralize security log management and analysis | Customer | Platform Config | **Unified Audit Log + Power BI Activity Log** | Fabric centralizes logs in two places: Power BI activity log (30 days) and Unified Audit Log (180 days) | [Baseline LT-5](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#lt-5-centralize-security-log-management-and-analysis) / [Operation List](https://learn.microsoft.com/en-us/fabric/admin/operation-list) / [Track User Activities](https://learn.microsoft.com/en-us/fabric/admin/track-user-activities) |
| LT-6: Configure log storage retention | Customer | Platform Config | **Audit log retention policies** | Configure retention per compliance and regulatory requirements | [Baseline LT-6](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#lt-6-configure-log-storage-retention) / [Audit Log Retention](https://learn.microsoft.com/en-us/purview/audit-log-retention-policies) |
| LT-7: Use approved time synchronization sources | Microsoft | Microsoft Managed | N/A - Microsoft manages time synchronization | Fabric relies on Microsoft time sources; not configurable | [Baseline LT-7](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#lt-7-use-approved-time-synchronization-sources) |

---

## 7. Incident Response (IR)

| MCSB Control | Responsibility | Implementation Type | Configuration | Baseline Guidance Summary | Source |
|---|---|---|---|---|---|
| IR-1: Preparation - update incident response plan | Customer | Process Control | **Update IR plan to include Fabric incidents** | Include handling of Fabric incidents; customize IR plan and playbook for cloud environment | [Baseline IR-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ir-1-preparation---update-incident-response-plan-and-handling-process) / [CAF Incident Response](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/secure/security-top-10#4-process-update-incident-response-processes-for-cloud) |
| IR-2: Preparation - setup incident notification | Customer | Platform Config | **Security contact in Defender for Cloud** | Set security incident contact information in Defender for Cloud | [Baseline IR-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ir-2-preparation---setup-incident-notification) / [Security Contact](https://learn.microsoft.com/en-us/azure/security-center/security-center-provide-security-contact-details) |
| IR-3: Detection and analysis - create incidents based on alerts | Customer | Platform Config | **Defender for Cloud alerts + Sentinel** | Use Defender for Cloud data connector to stream alerts to Sentinel | [Baseline IR-3](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ir-3-detection-and-analysis---create-incidents-based-on-high-quality-alerts) / [Stream Alerts to Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/connect-azure-security-center) |
| IR-4: Detection and analysis - investigate an incident | Customer | Process Control | **Use Fabric activity logs, audit logs, and Entra ID sign-in logs** | Access enabled-by-default activity/audit logs; export to Sentinel | [Baseline IR-4](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ir-4-detection-and-analysis---investigate-an-incident) / [Investigate with Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/tutorial-investigate-cases) / [Insider Risk Indicators](https://learn.microsoft.com/en-us/purview/insider-risk-management-settings-policy-indicators) |
| IR-5: Detection and analysis - prioritize incidents | Customer | Platform Config | **Defender for Cloud severity + Sentinel analytics rules** | Use Defender for Cloud severity assignment; customize per org needs | [Baseline IR-5](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ir-5-detection-and-analysis---prioritize-incidents) / [Sentinel Incidents](https://learn.microsoft.com/en-us/azure/sentinel/create-incidents-from-alerts) |
| IR-6: Containment, eradication, and recovery - automate handling | Customer | Platform Config | **Defender for Cloud workflow automation + Sentinel playbooks** | Use workflow automation to trigger actions or playbooks in response to alerts | [Baseline IR-6](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ir-6-containment-eradication-and-recovery---automate-the-incident-handling) / [Workflow Automation](https://learn.microsoft.com/en-us/azure/security-center/workflow-automation) / [Sentinel Playbooks](https://learn.microsoft.com/en-us/azure/sentinel/tutorial-respond-threats-playbook) |
| IR-7: Post-incident activity - lessons learned | Customer | Process Control | **Lessons learned; update IR plan, playbook, detection rules** | Use outcome from lessons learned to update IR plan and reincorporate findings | [Baseline IR-7](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ir-7-post-incident-activity---conduct-lessons-learned-and-retain-evidence) / [Post-Incident Cleanup](https://learn.microsoft.com/en-us/security/compass/incident-response-process#2-post-incident-cleanup) |

---

## 8. Posture and Vulnerability Management (PV)

| MCSB Control | Responsibility | Implementation Type | Configuration | Baseline Guidance Summary | Source |
|---|---|---|---|---|---|
| PV-1: Define and establish secure configurations | Customer | Process Control | **Use this MCSB baseline to define configuration standard** | Use Fabric MCSB baseline to define configuration baseline for each workload | [Baseline PV-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pv-1-define-and-establish-secure-configurations) / [Fabric Security](https://learn.microsoft.com/en-us/fabric/security/) |
| PV-2: Audit and enforce secure configurations | Customer | Platform Config | **Azure Policy + Defender for Cloud + Admin REST APIs** | Use Defender for Cloud to audit/enforce; use Admin REST APIs for monitoring | [Baseline PV-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pv-2-audit-and-enforce-secure-configurations) / [Azure Policy](https://learn.microsoft.com/en-us/azure/governance/policy/tutorials/create-and-manage) / [Admin REST API](https://learn.microsoft.com/en-us/rest/api/power-bi/admin) / [Fabric REST APIs](https://learn.microsoft.com/en-us/rest/api/fabric/articles/using-fabric-apis) |
| PV-2 † | Customer | Tenant Setting | **Block republish and disable package refresh** | Disable package refresh; only semantic model owner can publish updates | [Tenant Setting](https://learn.microsoft.com/en-us/fabric/admin/service-admin-portal-dataset-security#block-republish-and-disable-package-refresh) |
| PV-3: Define and establish secure configurations for compute | Shared | Tenant Setting | **Restrict Fabric item creation** | Ensure only authorized personnel can provision Fabric compute (Spark jobs) | [Baseline PV-3](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pv-3-define-and-establish-secure-configurations-for-compute-resources) |
| PV-4: Audit and enforce compute configurations | Microsoft | Microsoft Managed | N/A - underlying compute secured by Microsoft | Fabric SaaS compute is fully managed | [Baseline PV-4](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pv-4-audit-and-enforce-secure-configurations-for-compute-resources) |
| PV-5: Perform vulnerability assessments | Microsoft | Microsoft Managed + Process Control | **Microsoft performs regular assessments; customer may pen test** | Microsoft teams perform regular vulnerability testing per SDL; customers may conduct own assessment | [Baseline PV-5](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pv-5-perform-vulnerability-assessments) / [Pen Test Rules](https://www.microsoft.com/msrc/pentest-rules-of-engagement) |
| PV-6: Rapidly and automatically remediate vulnerabilities | Microsoft | Microsoft Managed | N/A - underlying compute managed by Microsoft | Fabric SaaS infrastructure managed by Microsoft | [Baseline PV-6](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pv-6-rapidly-and-automatically-remediate-vulnerabilities) |
| PV-7: Conduct regular red team operations | Shared | Process Control | **Penetration testing per Microsoft Rules of Engagement** | Conduct pen testing; follow Microsoft Cloud Penetration Testing Rules of Engagement | [Baseline PV-7](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#pv-7-conduct-regular-red-team-operations) / [Pen Test Rules](https://www.microsoft.com/msrc/pentest-rules-of-engagement) |

---

## 9. Endpoint Security (ES)

| MCSB Control | Responsibility | Implementation Type | Configuration | Baseline Guidance Summary | Source |
|---|---|---|---|---|---|
| ES (all): Endpoint detection and response | Microsoft | Microsoft Managed | N/A - no customer-facing compute resources | Fabric does not deploy customer-facing compute; underlying infrastructure EDR handled by Microsoft | [Baseline ES](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#endpoint-security) |

---

## 10. Backup and Recovery (BR)

| MCSB Control | Responsibility | Implementation Type | Configuration | Baseline Guidance Summary | Source |
|---|---|---|---|---|---|
| BR-1: Ensure regular automated backups | Shared | Platform Config | **Power BI semantic model backup; OneLake cross-region replication** | Power BI has built-in BCDR; additional backup options for high-value assets | [Baseline BR-1](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#br-1-ensure-regular-automated-backups) / [Backup/Restore Semantic Models](https://learn.microsoft.com/en-us/power-bi/enterprise/service-premium-backup-restore-dataset) / [Reliability in Fabric](https://learn.microsoft.com/en-us/azure/reliability/reliability-fabric) |
| BR-2: Protect backup and recovery data | Shared | Microsoft Managed + Platform Config | **Built-in BCDR managed by Microsoft** | Power BI is a fully managed service with built-in BCDR | [Baseline BR-2](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#br-2-protect-backup-and-recovery-data) / [Reliability in Fabric](https://learn.microsoft.com/en-us/azure/reliability/reliability-fabric) |

---

## Evidence Collection

For compliance purposes, the following methods can be used to demonstrate adherence to this baseline:

| Evidence Type | Method | Source |
|---|---|---|
| Tenant Settings Export | GET tenant settings via REST API | [Get Tenant Settings API](https://learn.microsoft.com/en-us/rest/api/fabric/admin/tenants/get-tenant-settings) |
| Activity Logs | Export via REST API or PowerShell | [Track User Activities](https://learn.microsoft.com/en-us/fabric/admin/track-user-activities) |
| Unified Audit Log | Microsoft Purview audit search | [Audit Log Search](https://learn.microsoft.com/en-us/purview/audit-search) |
| Metadata Scanning | Scanner API output | [Metadata Scanning](https://learn.microsoft.com/en-us/fabric/governance/metadata-scanning-run) |
| Sensitivity Label Status | Microsoft Purview Information Protection | [Fabric + Purview](https://learn.microsoft.com/en-us/purview/register-scan-fabric-tenant) |

---

## Notes
- This baseline is based on MCSB v1. Microsoft notes the Fabric Security Baseline may contain outdated guidance. Verify against current Fabric documentation.
- "N/A per baseline" means the MCSB Fabric Baseline explicitly marks that control as not applicable to Fabric.
- † = Setting is documented in the Tenant Settings Index but NOT explicitly referenced in the MCSB Fabric Baseline. Mapping to this control is inferred based on the control's stated purpose.
- All source links point to publicly available Microsoft documentation as of the date this artifact was created.
