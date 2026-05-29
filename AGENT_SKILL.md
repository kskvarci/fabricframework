# Agent Skill: Fabric Security Configuration Baseline Generator

## Purpose

This skill documents how to create (or recreate from scratch) the `fabric-security-configuration-baseline.md` artifact. The document maps every control in the Microsoft Cloud Security Benchmark (MCSB) Fabric Security Baseline to documented Fabric implementation settings/configurations.

## Scope Constraints

- **ONLY** include what is publicly documented in:
  1. The MCSB Fabric Security Baseline
  2. The Fabric Tenant Settings Index
- **DO NOT** expose feature gaps, make prescriptive recommendations, or include undocumented capabilities
- **DO NOT** add content that goes beyond what Microsoft has published
- Every row must have a verifiable source URL

## Source Documents

| Source | URL | What to Extract |
|--------|-----|-----------------|
| MCSB Fabric Security Baseline | https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline | All controls (NS through BR), their responsibility assignments, implementation guidance, and referenced settings |
| Fabric Tenant Settings Index | https://learn.microsoft.com/en-us/fabric/admin/tenant-settings-index | All tenant settings — paginated across multiple pages (page 1 = main, page 2-4 via links at bottom) |
| MCSB Overview / Domain Pages | https://learn.microsoft.com/en-us/security/benchmark/azure/overview | Regulatory framework mappings (NIST SP 800-53, CIS Controls v8, PCI-DSS v3.2.1) for each control |

### MCSB Domain Page URLs (for framework mappings)

- Network Security: `https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-network-security`
- Identity Management: `https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-identity-management`
- Privileged Access: `https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-privileged-access`
- Data Protection: `https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-data-protection`
- Asset Management: `https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-asset-management`
- Logging and Threat Detection: `https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-logging-threat-detection`
- Incident Response: `https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-incident-response`
- Posture and Vulnerability Management: `https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-posture-vulnerability-management`
- Endpoint Security: `https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-endpoint-security`
- Backup and Recovery: `https://learn.microsoft.com/en-us/security/benchmark/azure/mcsb-backup-recovery`

## Document Structure

The output markdown file has the following sections in order:

```
1. Title & Purpose
2. Sources (with URLs)
3. Legend (explains † marker)
4. Regulatory Framework Mappings table (all MCSB controls → NIST/CIS/PCI-DSS)
5. How to Use (column definitions)
6. Implementation Types (definitions)
7. Where This Fits: SaaS Service Enablement for Regulated Industries
   - 10-step enablement lifecycle (demand → assessment → config → operate)
   - Roles table (who owns each phase)
8. How This Relates to Compliance Frameworks, the MCSB, and Internal Policies
   - 5-layer hierarchy diagram (Regulations → Internal Policy → MCSB → This Doc → Posture Decisions)
   - Traceability chain example (setting → control → NIST → policy → regulation)
   - "Answered by which layer" table
   - Common customer confusions and how the layering resolves them
9. --- separator ---
10. Section 1: Network Security (NS)
11. Section 2: Identity Management (IM)
12. Section 3: Privileged Access (PA)
13. Section 4: Data Protection (DP)
14. Section 5: Asset Management (AM)
15. Section 6: Logging and Threat Detection (LT)
16. Section 7: Incident Response (IR)
17. Section 8: Posture and Vulnerability Management (PV)
18. Section 9: Endpoint Security (ES)
19. Section 10: Backup and Recovery (BR)
20. Section 11: Evidence Collection
21. Notes
```

## Step-by-Step Recreation Process

### Phase 1: Fetch the MCSB Fabric Security Baseline

1. Fetch the full page at the baseline URL
2. For each of the 10 MCSB domains (NS, IM, PA, DP, AM, LT, IR, PV, ES, BR):
   - Extract every control listed (e.g., NS-1, NS-2, ..., NS-10)
   - For each control, extract:
     - **Control ID and name** (e.g., "NS-2: Secure cloud native services with network controls")
     - **Responsibility** (Customer, Microsoft, or Shared)
     - **Feature name(s)** listed under the control
     - **Description / guidance text** for each feature
     - **Configuration guidance** (the prescriptive text Microsoft provides)
     - **Reference links** (URLs to settings or docs pages)
   - Note: Some controls will say "Not Applicable" or have no Fabric-specific guidance — still include them with "N/A" or "Microsoft Managed"

### Phase 2: Fetch the Tenant Settings Index

1. Fetch the main Tenant Settings Index page
2. **Important**: The settings are paginated. Follow pagination links to get ALL settings (typically 4 pages, 170+ total settings)
3. For each setting, extract:
   - Setting name
   - Category/group it belongs to
   - Brief description (from the index or linked detail page)
   - URL to its documentation

### Phase 3: Fetch Regulatory Framework Mappings

1. For each of the 10 MCSB domain pages:
   - Find the framework mapping section
   - Extract: CIS Controls v8 IDs, NIST SP 800-53 r4 IDs, PCI-DSS v3.2.1 IDs
   - Map each control (e.g., NS-1, NS-2) to its framework references

### Phase 4: Build the Explicit Rows

For each control in the baseline that has Fabric-specific guidance:

1. Create a row with:
   - MCSB Control ID
   - Responsibility (from baseline)
   - Implementation Type (classify as: Tenant Setting, Platform Config, Process Control, or Microsoft Managed)
   - Configuration name (bold)
   - Baseline Guidance Summary (summarized from the baseline text)
   - Source URL

2. **Explicitly referenced** = the baseline text names the setting, describes it, or links to the page that documents it. These rows get NO marker.

### Phase 5: Map Tenant Settings by Inference

1. Take the full list of tenant settings from Phase 2
2. Remove any settings already captured in Phase 4 (explicitly referenced)
3. For each remaining setting, evaluate:
   - Is this security-relevant? (If purely cosmetic/UX with no security implication → exclude)
   - Which MCSB control does it most closely map to based on the control's stated purpose?
4. Create rows for security-relevant settings with the **†** (dagger / Unicode U+2020) marker on the MCSB Control ID
5. Map settings to domains using this logic:

| Setting Category | Likely Domain |
|-----------------|---------------|
| Data sharing / export / embedding controls | DP-2 (Monitor anomalies targeting sensitive data) |
| Data residency / cross-geo processing | DP-3 (Encrypt sensitive data in transit) |
| Sensitivity labels / classification | DP-1 (Discover, classify, label) |
| SSO token forwarding to external services | IM-8 (Restrict credential/secret exposure) |
| Third-party code/workloads/visuals | AM-2 (Use only approved services) |
| Admin API exposure | PA-1 (Separate/limit privileged users) |
| Access control granularity | PA-7 (Just enough administration) |
| Audit logging / diagnostics content | LT-3 (Enable logging for security investigation) |
| Change control / republish controls | PV-2 (Audit and enforce secure configurations) |
| Network access / private links | NS-2 (Secure cloud native services with network controls) |

### Phase 6: Build the Context Sections

Before the domain tables, include two contextual sections that explain where this document fits:

#### 6a. "Where This Fits: SaaS Service Enablement for Regulated Industries"

Include an ASCII diagram showing the 10-step lifecycle regulated enterprises follow when enabling a new SaaS service:

1. Business Use Case Identification
2. Third-Party Risk Management (TPRM) / Vendor Assessment
3. Service-Level Security Assessment (map to internal framework)
4. Gap Analysis & Risk Acceptance
5. **Security Configuration Baseline ← THIS DOCUMENT**
6. Posture Decision & Policy Authoring (customer decides enable/disable)
7. Tenant Provisioning & Baseline Deployment
8. Validation & Compliance Evidence
9. Ongoing Monitoring & Alerting
10. Periodic Reassessment

Emphasize that this document is Step 5 — it inventories the levers but does NOT prescribe which way to set them. Include a roles table mapping each phase to organizational owners.

#### 6b. "How This Relates to Compliance Frameworks, the MCSB, and Internal Policies"

Include a 5-layer hierarchy diagram showing the control chain:

```
Layer 1: External Regulations (NIST, PCI-DSS, HIPAA, DORA, etc.)
         ▼ mapped into
Layer 2: Customer's Internal Security Framework / Policy
         ▼ satisfied by
Layer 3: Microsoft Cloud Security Benchmark (MCSB)
         ▼ implemented by
Layer 4: THIS DOCUMENT (Fabric settings mapped to MCSB controls)
         ▼ drives
Layer 5: Customer's Posture Decisions (enable/disable per setting)
```

Include:
- A concrete traceability chain example (single setting traced from Fabric config up to regulation)
- A table answering "which layer answers which question"
- A "common customer confusions" section explaining where organizations typically get stuck (between Layer 3 and Layer 4) and how this document resolves it

### Phase 7: Assemble the Domain Tables

1. Write the header sections (Purpose, Sources, Legend)
2. Build the Regulatory Framework Mappings table (one row per control, all 67 controls)
3. Write How to Use and Implementation Types sections
4. Write the context sections (6a and 6b above)
5. For each domain section (1-10):
   - Create the markdown table header: `| MCSB Control | Responsibility | Implementation Type | Configuration | Baseline Guidance Summary | Source |`
   - Write explicit rows first (no marker)
   - Write inferred rows after (with † on the control ID)
   - Controls with no Fabric implementation → single row noting "N/A — Microsoft Managed" or "N/A — Not applicable to SaaS"
6. Add the Evidence Collection section
7. Add Notes section explaining the † legend

### Phase 8: Validate

1. Verify every explicit row has a matching reference in the baseline text
2. Verify every † row corresponds to a real setting in the Tenant Settings Index
3. Verify no setting appears in multiple domain sections (no duplicates)
4. Verify all URLs are well-formed (link to learn.microsoft.com)
5. Count: expect ~160 implementation rows total (will grow as Microsoft adds settings)

## Column Definitions

| Column | Description |
|--------|-------------|
| MCSB Control | Control ID + name. Add `†` after ID if inferred. |
| Responsibility | `Customer`, `Microsoft`, or `Shared` — as stated in baseline |
| Implementation Type | One of: `Tenant Setting`, `Platform Config`, `Process Control`, `Microsoft Managed` |
| Configuration | Setting or action name in **bold** |
| Baseline Guidance Summary | 1-2 sentence summary. For explicit: paraphrase from baseline. For inferred: describe what the setting does and its security relevance. |
| Source | Markdown link to the documentation page |

## Legend System

```
† (dagger, U+2020) = Setting is documented in the Tenant Settings Index but NOT explicitly 
referenced in the MCSB Fabric Security Baseline. Mapped to this control by inference based 
on the control's stated purpose.

No marker = Setting/configuration is explicitly named or linked in the MCSB Fabric Security 
Baseline document.
```

## Implementation Type Classification Rules

| Type | When to Use |
|------|-------------|
| Tenant Setting | Setting appears in the Fabric Admin Portal (Tenant Settings Index) |
| Platform Config | Configured in Entra ID, Azure Portal, Microsoft Purview, or Defender for Cloud Apps — not in Fabric Admin Portal |
| Process Control | Requires an organizational procedure, policy, or manual review — no toggle/setting exists |
| Microsoft Managed | Microsoft handles this; customer has no configuration option |

## Key Design Decisions

1. **No prescriptive recommendations**: The document is a pure factual mapping. It does NOT say "set this to Disabled" — that layer is added separately by the consulting team or customer.

2. **Silence signals gaps**: If an MCSB control has no implementation rows (or says N/A), it means Fabric doesn't have a mechanism to satisfy that control. We don't call this out explicitly — we let the absence speak.

3. **Single source of truth**: Every row ties back to exactly one source URL. No invented content.

4. **Conservative inference**: When mapping tenant settings by inference, only include settings with clear security relevance. Purely cosmetic/UX settings (dashboard themes, default views) are excluded.

## Maintenance / Refresh Triggers

Recreate or update the document when:
- Microsoft updates the MCSB Fabric Security Baseline (check version date at top of page)
- New tenant settings are added to the Fabric Admin Portal (check Tenant Settings Index)
- MCSB framework mappings change (rare — check domain pages)
- Fabric adds new security features documented in learn.microsoft.com

## Technical Notes

- The Tenant Settings Index is paginated — you must fetch all pages (typically 4)
- Some settings share a documentation page (e.g., multiple SSO settings link to the same integration page) — this is expected
- The MCSB Fabric Baseline is stated as based on "MCSB v1" — note this in any delivery
- Controls ES-1 through ES-3 (Endpoint Security) have no Fabric-specific implementation — mark as N/A
- BR controls are mostly Microsoft Managed for SaaS — only platform config rows for BCDR documentation

## Example Row Formats

**Explicit row (no marker):**
```
| NS-2: Secure cloud native services with network controls | Customer | Tenant Setting | **Azure Private Links** | Use private endpoints to allow secure access to Fabric. Disable public access if private links are required. | [Baseline](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline#ns-2-secure-cloud-native-services-with-network-controls) |
```

**Inferred row (with † marker):**
```
| DP-2 † | Customer | Tenant Setting | **Allow XMLA endpoints and Analyze in Excel with on-premises semantic models** | Allows direct model access via XMLA protocol and Excel live connections (bypasses report-level controls) | [Tenant Setting](https://learn.microsoft.com/en-us/power-bi/collaborate-share/service-analyze-in-excel) |
```

**N/A row:**
```
| ES-1: Use Endpoint Detection and Response | Microsoft | N/A | N/A — Not applicable to SaaS platform | Endpoint protection is managed by Microsoft for the Fabric service infrastructure | [Baseline](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/fabric-security-baseline) |
```
