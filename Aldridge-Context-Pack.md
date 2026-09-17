# Aldridge Financial Technologies — Organisation Context Pack

**Reference:** AFT-CTX-01 · **Version:** 2.3 · **Date:** 9 September 2026
**Status:** Canonical. This document is the single source of truth for all Aldridge deliverables.

---

## 0. How to use this pack

This pack exists so that every deliverable produced about Aldridge Financial Technologies is
internally consistent with every other one. It is an **input**, not an output.

**Rules for any agent or author working on an Aldridge deliverable:**

1. Read this pack in full before writing anything.
2. Never invent a role holder, system, vendor, document reference, date or scale value that is
   not in this pack. If something you need is missing, add it here first, increment the version,
   and note it in section 12 — then write the deliverable.
3. Where this pack and a previously issued deliverable disagree, **this pack wins** and the
   deliverable is corrected.
4. Use the scales in sections 7, 8 and 9 verbatim. Do not re-derive, re-band or re-word them.
5. The seeded weaknesses in section 10 are the company's real current state. Every deliverable
   must be consistent with them: the gap analysis must find them, the risk register must carry
   them, and the remediation plans must not claim they are already fixed.

**House conventions:** British English throughout. Dates written as `1 October 2026`. Personnel
are referred to as *workers* (defined in AFT-ISMS-POL-01). Currency in USD unless the context is
the UK entity, in which case GBP. Incident severities are `S1`–`S4` only.

---

## 1. Company profile

| Attribute | Value |
|---|---|
| Legal entities | Aldridge Financial Technologies, Inc. (Delaware) · Aldridge Financial Technologies (UK) Ltd (England & Wales, no. 10847213) |
| Founded | 2016 |
| Headquarters | Austin, Texas, United States |
| Other locations | London, United Kingdom (UK subsidiary, opened 2021) |
| Sector | Financial technology — embedded payments and small-business lending |
| Ownership | Private; Series D, backed by three institutional investors. No IPO process live. |
| Headcount | 610 total — 470 US, 140 UK |
| Revenue | USD 186m (FY2025), growing ~28% year on year |
| Annualised payment volume | USD 14.2bn |
| Customers | ~2,400 platform and merchant customers; ~38,000 SME borrowers |

### 1.1 Products

| Product | Description | Data sensitivity |
|---|---|---|
| **Aldridge Pay** | Embedded payments and merchant acquiring, sold to B2B software platforms who resell to their own merchants. | Cardholder data — Restricted |
| **Aldridge Credit** | Working-capital lending to small businesses. Originates, underwrites and services. | Credit files, bank data — Restricted |
| **Aldridge Ledger** | Reconciliation and treasury API layer used by both other products and sold standalone. | Transaction data — Confidential |

### 1.2 Regulatory and contractual obligations

| Obligation | Applies to | Notes |
|---|---|---|
| PCI DSS v4.0 | Group (Aldridge Pay) | Level 1 service provider. Current AOC expires 30 April 2027. |
| US state money transmitter licences | US entity | Licensed in 44 states. Sponsor bank arrangement with a partner bank for deposit and settlement. |
| FCA authorisation | UK entity | Authorised Electronic Money Institution. |
| UK GDPR / Data Protection Act 2018 | UK entity, and group where UK data is processed | DPO appointed. |
| US state breach notification laws | US entity | 50-state analysis maintained by Legal. |
| SOC 2 Type II | Group | Annual; most recent report issued March 2026 with two exceptions. |
| **ISO/IEC 27001:2022** | Group | **Not yet certified.** Stage 1 audit targeted Q2 2027. This is the driver for the gap analysis. |
| BSA/AML programme | US entity | Required as a money services business and under the sponsor bank's oversight. Covers the CIP/KYC programme, transaction monitoring, and independent testing. |
| OFAC sanctions screening | US entity, and group where US persons or USD clearing are involved | Screening of merchants, borrowers and payment counterparties against SDN and consolidated lists. Strict liability regime — no knowledge requirement. |
| SAR filing (FinCEN) | US entity | Suspicious activity reporting, including for cyber-events and cyber-enabled crime, per FinCEN's 2016 advisory on that subject. A security incident can itself be a reportable event. |
| NYDFS Part 500 | US entity (New York licence) | Cybersecurity regulation for licensed entities: 72-hour notification of a cybersecurity event, annual CISO certification to the Superintendent, and specific programme requirements. |
| UK Money Laundering Regulations 2017 | UK entity | Customer due diligence, ongoing monitoring, and reporting to the NCA via SARs. |
| FCA financial crime obligations | UK entity | SYSC 6.3 and the Financial Crime Guide; senior manager accountability under SM&CR. |

### 1.3 Why ISO 27001 now

Three enterprise prospects in the last two quarters made certification a condition of contract.
The Executive Risk Committee approved a certification programme in July 2026 with a Stage 1
target of Q2 2027. The company has a mature-ish control environment inherited from PCI DSS and
SOC 2, but no ISMS as such — no Statement of Applicability, no risk treatment plan, no
management review cycle.

### 1.4 ISO 27001 scope statement (draft, not yet approved)

> The information security management system supporting the design, development, operation and
> support of the Aldridge Pay, Aldridge Credit and Aldridge Ledger platforms, and the corporate
> functions that support them, delivered from AWS regions `us-east-1`, `us-west-2` and
> `eu-west-2` and from the company's offices in Austin, Texas and London, United Kingdom.
> In accordance with Statement of Applicability version 0.3 (draft).

---

## 2. Organisation and role holders

Use these names and titles verbatim. Do not introduce others.

### 2.1 Executive

| Name | Title | Relevance |
|---|---|---|
| Priya Raghunathan | Chief Executive Officer | S1 escalation; chairs Executive Risk Committee |
| Daniel Okonkwo | Chief Financial Officer | Cyber insurance; owns finance systems; S1 escalation |
| Marcus Lindqvist | Chief Technology Officer | Owns engineering and platform |
| Amara Diallo | Chief Product Officer | Owns product data decisions |
| **Helen Achebe-Ward** | **Chief Information Security Officer** | **Owns all four Tier 2 policies; owns the ISMS** |
| Jonathan Reyes | General Counsel | Notification determinations; legal hold; external statements |

### 2.2 Second line and functional

| Name | Title | Relevance |
|---|---|---|
| Chidi Eze | Head of Security Governance (GRC) | Authored policy v1.0 set (2023); runs the ISO programme |
| Tomas Vidal | Head of Security Operations | Runs the SOC; incident triage and severity |
| Ruth Nakamura | Head of Identity and Access | Owns ACP operations, IAM/PAM platforms |
| Sanjay Mehta | Head of Platform Engineering | Owns AWS estate and Kubernetes |
| Oliver Trent | Head of Payments | Owns the cardholder data environment |
| Claire Bennett | Head of Information Governance | Asset register, data catalogue, retention schedule |
| Sofia Kallio | Data Protection Officer (London) | UK GDPR; personal data breach assessment |
| Grace Lindberg | VP People Operations | Joiner/mover/leaver source of truth; disciplinary |
| Nadia Haddad | Director of Corporate Communications | All incident messaging |
| Faisal Rahman | Head of Internal Audit | Reports to Audit Committee, not to the CISO |
| Elena Petrova | Head of Procurement | Owns supplier onboarding, gatekeeps TPRM |

### 2.3 Governance bodies

| Body | Chair | Cadence | Remit |
|---|---|---|---|
| Board Audit Committee | Non-executive chair | Quarterly | Receives Internal Audit; approves audit plan |
| Executive Risk Committee (ERC) | Priya Raghunathan | Monthly | Approves policy; accepts risk at High and above; oversees incident closure |
| Security Steering Group | Helen Achebe-Ward | Fortnightly | Operational security prioritisation; feeds the ERC |
| Change Advisory Board | Sanjay Mehta | Twice weekly | Production change approval |

---

## 3. Technology estate

### 3.1 Environments

| Environment | Platform | Region | Notes |
|---|---|---|---|
| Production — US | AWS | `us-east-1` (primary), `us-west-2` (DR) | EKS, Aurora PostgreSQL, Kafka |
| Production — UK | AWS | `eu-west-2` | Separate account; UK data residency |
| Cardholder data environment (CDE) | AWS | Dedicated accounts, both regions | Network-segregated; PCI in-scope |
| Secure data zone | AWS | Dedicated accounts | Credit files, borrower personal data |
| Non-production | AWS | `us-east-1` | Development, test, staging |
| Corporate | SaaS | n/a | Identity, productivity, finance, HR |

### 3.2 Core tooling

Real product names are used to describe the internal stack. This is description only — no
control-effectiveness or risk claims are made about these products anywhere in the deliverable
set. All parties who are *assessed* (section 6) are fictional.

| Function | Product |
|---|---|
| Identity provider | Okta |
| Privileged access management | CyberArk |
| Secrets management | HashiCorp Vault |
| Endpoint detection and response | CrowdStrike Falcon |
| Device management | Jamf (macOS), Intune (Windows) |
| Cloud security posture | Wiz |
| SIEM | Splunk |
| Source control and CI | GitHub Enterprise Cloud, GitHub Actions |
| Data warehouse | Snowflake |
| Collaboration | Google Workspace, Slack |
| Service management | Jira Service Management |
| GRC platform | **None — tracked in spreadsheets** (see section 10) |
| Security awareness | KnowBe4 |

### 3.3 Engineering profile

- ~230 engineers across 26 teams. Trunk-based development, deploys ~40 times per day.
- Languages: Go (services), TypeScript (front end and BFF), Python (data and risk models).
- Infrastructure as code via Terraform. Roughly 80% of the estate is codified; the remainder,
  largely older Aldridge Pay components, is not.

---

## 4. Information asset inventory

Asset IDs are canonical. Use them in the risk register and gap analysis.

| ID | Asset | Owner | Classification | Availability need |
|---|---|---|---|---|
| A-01 | Aldridge Pay transaction processing service | Oliver Trent | Restricted | Critical — RTO 1h |
| A-02 | Cardholder data vault (tokenisation) | Oliver Trent | Restricted | Critical — RTO 1h |
| A-03 | Aldridge Credit origination platform | Amara Diallo | Restricted | High — RTO 4h |
| A-04 | Aldridge Credit servicing and collections | Amara Diallo | Restricted | High — RTO 4h |
| A-05 | Borrower credit file store (secure data zone) | Amara Diallo | Restricted | High — RTO 4h |
| A-06 | Aldridge Ledger reconciliation API | Marcus Lindqvist | Confidential | High — RTO 4h |
| A-07 | Customer portal and merchant dashboard | Amara Diallo | Confidential | High — RTO 4h |
| A-08 | Public marketing website | Nadia Haddad | Public | Low — RTO 24h |
| A-09 | Snowflake analytics warehouse | Claire Bennett | Confidential | Moderate — RTO 24h |
| A-10 | Fraud decisioning integration | Oliver Trent | Restricted | Critical — RTO 1h |
| A-11 | Okta identity provider | Ruth Nakamura | Restricted | Critical — RTO 1h |
| A-12 | HashiCorp Vault secrets store | Sanjay Mehta | Restricted | Critical — RTO 1h |
| A-13 | GitHub source code repositories | Marcus Lindqvist | Confidential | High — RTO 4h |
| A-14 | CI/CD pipeline and deployment tooling | Sanjay Mehta | Confidential | High — RTO 4h |
| A-15 | AWS management and organisation accounts | Sanjay Mehta | Restricted | Critical — RTO 1h |
| A-16 | Splunk SIEM and log archive | Tomas Vidal | Confidential | High — RTO 4h |
| A-17 | Google Workspace (mail, drive, docs) | Grace Lindberg | Confidential | High — RTO 4h |
| A-18 | HR information system | Grace Lindberg | Confidential | Moderate — RTO 24h |
| A-19 | Finance and ERP system | Daniel Okonkwo | Confidential | Moderate — RTO 24h |
| A-20 | Corporate endpoints (610 devices) | Ruth Nakamura | Varies | Moderate |
| A-21 | Austin office and comms room | Grace Lindberg | Internal | Moderate |
| A-22 | London office (leased, landlord-managed access) | Grace Lindberg | Internal | Moderate |

---

## 5. Data classification scheme

Canonical, as published in AFT-ISMS-POL-04. Four levels, no others.

| Level | Definition | Examples |
|---|---|---|
| **Restricted** | Unauthorised disclosure would cause severe harm or breach a statutory or payment brand obligation. | Cardholder data, bank account and routing details, government identifiers, credentials and keys, borrower credit files, vulnerability details |
| **Confidential** | Unauthorised disclosure would cause significant harm to the company or a counterparty. | Customer contracts, unreleased results, source code, M&A material, employee records, internal audit reports |
| **Internal** | For use within the company; disclosure would cause limited harm. | Policies, internal announcements, project plans, org charts |
| **Public** | Approved for release outside the company. | Marketing material, published pricing, statutory filings |

Aggregation rule: combined information takes the highest classification present. Default where
unclear: Confidential.

---

## 6. Third parties in scope for assessment

These three vendors are **fictional**. They are the subjects of the TPRM deliverable and must not
be conflated with the real products in section 3.2.

| ID | Vendor | Service | Data accessed | Tier |
|---|---|---|---|---|
| V-01 | **Northgate Analytics Ltd** (London, UK) | Machine-learning fraud scoring and risk decisioning, called synchronously in the payment authorisation path. | Cardholder data (PAN truncated + BIN), transaction metadata, merchant data — **Restricted** | Tier 1 — Critical |
| V-02 | **Verrio Cloud Services, Inc.** (Denver, US) | Document generation and e-signature for loan agreements and disclosures. | Borrower personal data, credit decision output, signed agreements — **Restricted** | Tier 2 — High |
| V-03 | **Meridian BPO Solutions** (Manila, Philippines) | Outsourced customer support and payment dispute handling, tier 1 and tier 2. | Customer personal data, partial account data, dispute correspondence — **Confidential** with Restricted access on escalation | Tier 2 — High |

Deliberate spread: V-01 is a critical-path technical integration, V-02 is a data-at-rest
processor, V-03 is a human-access offshore operation. Each should surface a different class of
finding.

---

## 7. Risk scales

Used in the risk register, the gap analysis and the vendor assessments. Do not vary.

### 7.1 Impact

| Score | Band | Financial | Regulatory | Customer / operational |
|---|---|---|---|---|
| 5 | Severe | > USD 10m | Licence condition, enforcement action or authorisation at risk | > 25% of customers affected; core service down > 8h |
| 4 | Major | USD 2m – 10m | Formal regulatory finding; payment brand fine | 10–25% affected; core service down 4–8h |
| 3 | Moderate | USD 500k – 2m | Reportable breach; supervisory correspondence | 2–10% affected; degraded service 1–4h |
| 2 | Minor | USD 50k – 500k | Internal finding; no external report | < 2% affected; minor degradation |
| 1 | Negligible | < USD 50k | None | Negligible; absorbed in normal operations |

### 7.2 Likelihood

| Score | Band | Frequency anchor |
|---|---|---|
| 5 | Almost certain | Expected more than once in 12 months, or already occurring |
| 4 | Likely | Expected once in 12 months |
| 3 | Possible | Expected once in 1–3 years |
| 2 | Unlikely | Expected once in 3–10 years |
| 1 | Rare | Less than once in 10 years |

### 7.3 Risk rating

Rating = Impact × Likelihood.

| Score | Rating | Treatment requirement | Approval to accept |
|---|---|---|---|
| 16–25 | **Critical** | Immediate treatment; remediation plan within 5 business days | Board Audit Committee |
| 10–15 | **High** | Treatment plan within 20 business days; monthly ERC reporting | Executive Risk Committee |
| 5–9 | **Moderate** | Treatment plan within 60 business days; quarterly reporting | CISO |
| 1–4 | **Low** | Monitor; treat where cost-effective | Asset owner |

### 7.4 Risk appetite

| Category | Appetite | Statement |
|---|---|---|
| Cardholder and borrower data confidentiality | **Averse** | No residual risk above Moderate is accepted. |
| Regulatory compliance | **Averse** | No knowing non-compliance. Exceptions require ERC approval. |
| Service availability | **Minimal** | Residual risk up to High accepted for non-critical services only. |
| Change and innovation velocity | **Open** | High residual risk accepted where reversible and monitored. |
| Third-party concentration | **Cautious** | Tier 1 single points of failure require a documented exit plan. |

---

## 8. Control assessment scales

For the ISO 27001 gap analysis.

### 8.1 Implementation status

| Status | Meaning |
|---|---|
| Implemented | Control is designed appropriately, operating, and evidenced. |
| Partially implemented | Control exists but has a design or operating deficiency, or lacks evidence. |
| Not implemented | Control is absent or exists only as intent. |
| Not applicable | Control does not apply; justification required in the Statement of Applicability. |

### 8.2 Maturity

| Level | Name | Meaning |
|---|---|---|
| 0 | Non-existent | No recognisable activity. |
| 1 | Initial | Ad hoc, dependent on individuals, undocumented. |
| 2 | Repeatable | Consistent in practice but not formally defined. |
| 3 | Defined | Documented, communicated, and performed consistently. |
| 4 | Managed | Measured, monitored, and reported with metrics. |
| 5 | Optimised | Continuously improved against measured outcomes. |

**Certification threshold:** maturity 3 is the minimum for a control to be certifiable. Gaps are
raised for any applicable control below 3.

### 8.3 Gap priority

Priority answers **when** a gap must close, not how severe it is. The four criteria are mutually
exclusive; assign the first one that applies, reading down.

| Priority | Criterion | Target |
|---|---|---|
| **P1** | **Prerequisite for audit readiness.** The ISMS cannot be assessed until this exists. Typically a clause 4–10 requirement, or an Annex A control that the scope statement or risk assessment depends on. | Close by 31 January 2027 |
| **P2** | **Would generate a major nonconformity at Stage 2.** An applicable control absent, or present but failing systemically across the estate. | Close by 31 March 2027 |
| **P3** | **Would generate a minor nonconformity or an observation.** An isolated lapse, or a control that operates but cannot be evidenced. | Close by 30 June 2027 |
| **P4** | **Improvement opportunity.** Would not be raised as a finding at audit. | Post-certification |

**Note on the P1/P2 boundary.** A major nonconformity does block certification, so "blocks
certification" cannot distinguish the two. The distinction is *audit sequence*: P1 items must
exist before an auditor can begin assessing the ISMS at all, whereas P2 items are assessed and
found wanting. If a Stage 1 auditor would stop and say the organisation is not ready to proceed,
it is P1. If a Stage 2 auditor would raise it as a finding against a system they were able to
assess, it is P2.

---

## 9. Vendor risk scales

For the TPRM deliverable.

### 9.1 Tiering

Tier is set by the highest data classification accessed and by business criticality.

| Tier | Criteria | Assessment depth | Reassessment |
|---|---|---|---|
| Tier 1 — Critical | Restricted data **and** in a critical transaction path, or no viable short-term substitute | Full questionnaire, evidence review, annual on-site or virtual audit right exercised | Annual |
| Tier 2 — High | Restricted data, or Confidential data at volume | Full questionnaire plus evidence review | Annual |
| Tier 3 — Moderate | Confidential data, non-critical | Short questionnaire, certification review | Every 2 years |
| Tier 4 — Low | Internal or Public data only | Registration and attestation only | Every 3 years |

### 9.2 Domain scoring

Each questionnaire domain scores 0–4. Weighted domain scores produce an overall score of 0–100.

| Score | Meaning |
|---|---|
| 4 | Strong — control evidenced, independently assured |
| 3 | Adequate — control evidenced, self-attested |
| 2 | Developing — control partially in place |
| 1 | Weak — control asserted but unevidenced |
| 0 | Absent — no control, or refused to answer |

### 9.3 Overall vendor rating

| Score | Rating | Consequence |
|---|---|---|
| 85–100 | Low risk | Approve. Standard reassessment cycle. |
| 70–84 | Moderate risk | Approve with conditions. Remediation plan agreed. |
| 50–69 | High risk | Approve only with ERC sign-off, compensating controls and a dated remediation plan. |
| 0–49 | Critical risk | Do not approve, or terminate. Exit plan required. |

**Automatic escalation regardless of score:** any critical finding in encryption of Restricted
data, access control, incident notification commitment, or subcontractor disclosure escalates the
rating one band worse.

---

## 10. Current state — seeded weaknesses

These are the company's actual conditions as at September 2026. Every deliverable must be
consistent with them. The gap analysis must find them; the risk register must carry them; no
remediation narrative may assume they are already resolved.

| # | Weakness | Primarily surfaces in |
|---|---|---|
| W-01 | No approved Statement of Applicability. Draft v0.3 exists, unreviewed. | Gap analysis |
| W-02 | No documented information security risk assessment methodology and no risk treatment plan. Risk is tracked in a spreadsheet by Chidi Eze. | Gap analysis, risk assessment |
| W-03 | No ISMS management review cycle; the ERC receives security reporting but not against ISMS clauses. | Gap analysis |
| W-04 | Asset inventory covers infrastructure well but is materially incomplete for SaaS. Approximately 40 unregistered SaaS applications identified by the CASB in August 2026. | Gap analysis, risk assessment |
| W-05 | Threat intelligence is consumed informally by the SOC; no defined requirements, sources or dissemination. | Gap analysis |
| W-06 | Secure development lifecycle lacks formal threat modelling. Code review and SAST/DAST are in place. | Gap analysis, risk assessment |
| W-07 | Business continuity and disaster recovery plans exist but have not been tested end-to-end since March 2025. Component-level failover is tested quarterly. | Gap analysis, risk assessment |
| W-08 | Supplier assessments are performed at onboarding but reassessment is inconsistent — 11 of 34 Tier 1 and Tier 2 vendors are overdue. Northgate (V-01) last assessed October 2024. | Gap analysis, TPRM |
| W-09 | Records Retention Schedule is published but not technically enforced. Snowflake holds borrower data beyond the stated retention period. | Gap analysis, risk assessment |
| W-10 | Logging coverage is strong for Aldridge Pay but has gaps in Aldridge Credit servicing; approximately 15% of that estate does not ship to Splunk. | Gap analysis, risk assessment |
| W-11 | London office physical access is administered by the building landlord; the company cannot produce an access list on demand. | Gap analysis |
| W-12 | ~20% of the Aldridge Pay estate is not managed by Terraform; changes there are semi-manual. | Gap analysis, risk assessment |
| W-13 | No GRC tooling. Policies, exceptions, risks and access reviews are tracked across five spreadsheets with no version control. | Gap analysis |
| W-14 | Security awareness training completion is 91%; the residual 9% is concentrated in Sales and in the London office. | Gap analysis, awareness programme |
| W-15 | Phishing simulation runs quarterly but results are not tied to targeted follow-up training. | Awareness programme |
| W-16 | Cryptographic key inventory is incomplete; ownership of several legacy Aldridge Pay keys is unclear. | Gap analysis, risk assessment |

### 10.1 Assessment outcomes

Carry these forward. The risk assessment must be consistent with them and must not re-derive a
different picture of the same estate.

| Measure | Result |
|---|---|
| Annex A controls implemented at maturity 3+ | 46 of 92 applicable (50%) |
| Annex A controls partially implemented | 43 |
| Annex A controls not implemented | 3 — A.5.7, A.5.21, A.8.34 |
| Annex A controls not applicable | 1 — A.8.30, no outsourced development |
| Clause 4–10 requirements met | 1 of 25 — clause 7.1 Resources only |
| Total gaps | 70 — 46 Annex A, 24 clause |
| Gaps by priority | P1 17 · P2 37 · P3 14 · P4 2 |
| Gap rate by theme | Organisational 59% · Technological 50% · Physical 36% · People 25% |

**Risk assessment outcome (AFT-ISMS-RSK-01 v1.0).** 30 risks assessed against the 22 catalogued
assets. Residual profile: 1 Critical · 11 High · 17 Moderate · 1 Low. Twelve risks sit outside
the appetite at section 7.4 and require treatment or formal acceptance. Overall FIPS 199
categorisation is **High**. Supplier-related risks already assessed and not to be re-derived:
R-07 (Northgate compromise, residual 15), R-08 (Northgate outage, residual 8), R-09 (undisclosed
fourth parties, residual 12), R-10 (Meridian insider exfiltration, residual 12). The vendor
assessment must reconcile to these, not restate them at different values.

**Vendor assessment outcome (AFT-TPRM-ASM-01 v1.0).** 55-question instrument across 11 weighted
domains. V-01 Northgate scored 75.4 (Moderate), escalated to **High** on absent subcontractor
disclosure. V-02 Verrio scored 90.3 — **Low**, approved without conditions. V-03 Meridian scored
52.6 (High), escalated to **Critical** on absent MFA for agent access to customer data. Sixteen
findings raised, five of them Critical or High-severity preconditions of continued engagement.

**Open decision for the ERC (F-16):** the model's standard consequence for V-03's Critical rating
is termination. The assessment recommends against immediate termination — Meridian handles live
regulated dispute volume — and instead proposes interim compensating controls within 14 days, a
six-month ERC risk acceptance, a parallel exit-capability assessment, and a re-score at 31 March
2027. This is a recorded deviation from POL-09 and has not yet been approved.

**Open recommendation, not yet decided:** the gap analysis recommends re-baselining certification
to Stage 1 in Q2 2027 and Stage 2 in Q4 2027, on the grounds that clauses 8.2, 8.3, 9.2 and 9.3
require operating records that accrue over elapsed time. The ERC has not yet ruled on this.
Treat the approved target as Stage 1 Q2 2027 until it does.

### 10.2 Known strengths

So the picture is not uniformly negative, and so the gap analysis is credible:

- PCI DSS Level 1 compliance is mature and independently assessed annually.
- Identity, MFA and privileged access management are strong (Okta + CyberArk, just-in-time).
- Vulnerability management and patching meet defined SLAs with good evidence.
- Encryption at rest and in transit is comprehensive and centrally managed.
- Incident response is well drilled operationally, with two tabletop exercises completed in 2026.

---

## 11. Awareness programme baseline

For the security awareness deliverable.

| Metric | Current value | Source |
|---|---|---|
| Headcount in scope | 610 | HRIS, September 2026 |
| Annual training completion | 91% | KnowBe4 |
| Phishing simulation cadence | Quarterly | Security Operations |
| Most recent campaign | Q2 2026, 610 recipients | KnowBe4 |
| Click rate, most recent | 14.2% | KnowBe4 |
| Credential submission rate | 4.6% | KnowBe4 |
| Report rate | 31.0% | Report Phishing button telemetry |
| Median time to first report | 11 minutes | Security Operations |
| Repeat clickers (2+ campaigns) | 47 workers | KnowBe4 |

### 11.1 Population for segmentation

| Department | Headcount |
|---|---|
| Engineering and Platform | 230 |
| Customer Operations and Support | 118 |
| Sales and Partnerships | 84 |
| Risk, Credit and Underwriting | 62 |
| Finance and Legal | 44 |
| Product and Design | 38 |
| People, Marketing and Corporate | 34 |

---

## 12. Document register

Canonical reference numbering. Anything cited in a deliverable must appear here.

| Reference | Title | Status |
|---|---|---|
| AFT-CTX-01 | Organisation Context Pack (this document) | Issued v1.0 |
| AFT-ISMS-POL-01 | Acceptable Use Policy | **v3.0 draft, UNAPPROVED** — v2.1 operative |
| AFT-ISMS-POL-02 | Information Security Incident Response Policy | **Issued v3.1** — financial crime referral added |
| AFT-ISMS-POL-03 | Access Control Policy | **Issued v3.0** — parameters moved to STD-02 |
| AFT-ISMS-POL-04 | Data Classification and Handling Policy | **v3.0 draft, UNAPPROVED** — v2.0 operative |
| AFT-ISMS-POL-05 | Information Security Policy (Tier 1, apex) | Not written — gap |
| AFT-ISMS-POL-06 | Secure Development Policy | Issued v1.4 |
| AFT-ISMS-POL-07 | Cryptography Policy | Issued v1.2 |
| AFT-ISMS-POL-08 | Business Continuity Policy | Issued v2.0 |
| AFT-ISMS-POL-09 | Third-Party Risk Management Policy | **v2.0 draft, UNAPPROVED** — v1.3 operative. Adds lifecycle, exit, fourth-party, deviation route |
| AFT-ISMS-STD-02 | Authentication and Credential Standard | **Issued v1.0** — holds all authentication parameters |
| AFT-ISMS-STD-04 | Bring Your Own Device Standard | Issued |
| AFT-ISMS-STD-06 | Privileged Access Management Standard | Issued |
| AFT-ISMS-STD-08 | Digital Evidence Handling Standard | Issued |
| AFT-ISMS-STD-09 | Cryptographic Key Management Standard | Issued |
| AFT-ISMS-STD-11 | Approved Tooling Register | Issued |
| AFT-ISMS-PLN-01 | Cyber Incident Response Plan and runbooks | Issued |
| AFT-ISMS-PLN-03 | Business Continuity and Disaster Recovery Plan | Issued, untested (W-07) |
| AFT-ISMS-PRO-03 | Joiner, Mover and Leaver Procedure | Issued |
| AFT-ISMS-SOA-01 | Statement of Applicability | **Issued v1.0 — complete, UNSIGNED.** Approval pending SaaS triage |
| AFT-ISMS-RSK-01 | Information Security Risk Register | **Issued v2.0** — 55 risks; 1 Critical, 22 High; treatment plan UNSIGNED |
| AFT-ISMS-GAP-01 | ISO/IEC 27001:2022 Gap Analysis | **Issued v2.0** — 70 gaps; evidence, effort and dependencies added |
| AFT-TPRM-ASM-01 | Third-Party Risk Assessment — V-01 to V-03 | **Issued v2.1** — 18 findings; jurisdiction and sanctions flow-down added |
| AFT-ISMS-PRG-01 | Security Awareness and Training Programme | **Issued v1.2** — statutory financial crime training added |
| AFT-IG-SCH-01 | Records Retention Schedule | Issued, unenforced (W-09) |
| AFT-LEG-POL-01 | Data Protection Policy | Issued |
| AFT-LEG-PRO-02 | Personal Data Breach Assessment Procedure | Issued |
| AFT-HR-POL-02 | Disciplinary Procedure | Issued |

---

## 14. Threat profile

The threat sources below are the assessed adversary set for this organisation. Every risk in
AFT-ISMS-RSK-01 names one of them. Do not introduce a threat source that is not on this list
without adding it here first.

| ID | Threat source | Motivation | Typical techniques | Principal targets | Capability | Intent |
|---|---|---|---|---|---|---|
| TA-01 | Organised cybercriminal (extortion) | Financial — ransom and data extortion | Initial access via phishing or edge device exploitation; credential theft; lateral movement; backup destruction then encryption; double extortion | [[A-01]]–[[A-06]], A-15 | High | High |
| TA-02 | Payment fraud syndicate | Financial — direct value extraction | Merchant account takeover; BIN enumeration and card testing; refund and chargeback abuse; compromised merchant credentials | A-01, A-07, A-10 | High | High |
| TA-03 | Lending fraud ring | Financial — fraudulent credit | Synthetic identity construction; document forgery; first-party fraud; bust-out schemes; exploitation of automated decisioning thresholds | A-03, A-05 | Moderate | High |
| TA-04 | Initial access broker / phishing crew | Financial — resale of access | Credential harvesting at scale; MFA fatigue and push bombing; adversary-in-the-middle phishing kits; session token theft | A-11, A-17, A-20 | High | High |
| TA-05 | Malicious or coerced insider | Financial, grievance, or coercion | Bulk data access within entitlement; exfiltration through unmonitored channels; abuse of standing privilege. Includes supplier personnel with named access. | A-04, A-05, A-09, A-13 | Moderate | Low–Moderate |
| TA-06 | Supply chain / sub-processor compromise | Varies — access to the ultimate target | Compromise of a supplier holding Aldridge data; poisoned software dependency; compromise of a fourth party invisible to Aldridge | A-10, A-13, A-14, supplier estate | High | Moderate |
| TA-07 | Hacktivist or DDoS extortion actor | Ideological or financial | Volumetric and application-layer denial of service; extortion demand ahead of attack; opportunistic defacement | A-01, A-07, A-08 | Moderate | Low |
| TA-08 | State-aligned actor | Intelligence, pre-positioning in financial infrastructure | Long-dwell intrusion; living-off-the-land techniques; supply chain access; targeting of payment rails | A-01, A-02, A-15 | Very high | Low |
| TA-09 | Sanctions evader / money launderer | Financial — abuse of the platform rather than attack on it | Onboarding through synthetic or nominee entities; structuring; layering through merchant settlement; exploitation of onboarding automation | A-01, A-03 (as a channel, not a target) | Moderate | High |
| TA-10 | Non-adversarial | None — error or failure | Misconfiguration; accidental disclosure; supplier outage; process failure; expired certificates and keys | Estate-wide | n/a | n/a |

**Note on TA-09.** This is the threat source most often omitted from a security risk assessment,
because the platform is the instrument of the offence rather than its victim. It belongs here:
the control failures that permit it (onboarding, screening, monitoring) overlap materially with
information security controls, the regulatory consequence is severe and strict-liability in the
US sanctions case, and a cyber-event can itself trigger a SAR filing obligation.

---

## 15. Control framework crosswalk

Held once, here. Deliverables reference this rather than re-deriving their own mappings.
Crosswalk is at theme level; control-level mapping is held in [[AFT-ISMS-SOA-01]].

| ISO/IEC 27001:2022 theme | NIST CSF 2.0 | PCI DSS v4.0 | SOC 2 TSC | NYDFS Part 500 |
|---|---|---|---|---|
| A.5.1–A.5.8 Governance, roles, threat intel | GV.PO, GV.RR, GV.OC, ID.RA-02 | 12.1, 12.5 | CC1.1–CC1.5, CC3.1 | 500.03, 500.04 |
| A.5.9–A.5.14 Asset inventory, classification, transfer | ID.AM-01/02/07, PR.DS-01/02 | 3.1, 9.4, 12.5.1 | CC6.1, CC6.7 | 500.13 |
| A.5.15–A.5.18 Access control and identity | PR.AA-01 to PR.AA-06 | 7.1–7.3, 8.1–8.6 | CC6.1–CC6.3 | 500.07, 500.12 |
| A.5.19–A.5.23 Supplier and cloud security | GV.SC-01 to GV.SC-10, ID.RA-09 | 12.8, 12.9 | CC9.2 | 500.11 |
| A.5.24–A.5.28 Incident management | RS.MA, RS.AN, RS.CO, RC.RP, RC.CO | 12.10 | CC7.3–CC7.5 | 500.16, 500.17 |
| A.5.29–A.5.30 Continuity and ICT readiness | RC.RP-01 to RC.RP-06 | 12.10.1 | A1.2, A1.3 | 500.16 |
| A.5.31–A.5.37 Compliance, records, review | GV.OC-03, GV.OV, ID.IM-02 | 12.4, 12.11 | CC2.2, CC4.1, CC5.3 | 500.06, 500.17 |
| A.6.1–A.6.8 People controls | GV.RR-04, PR.AT-01, PR.AT-02 | 12.6, 12.7 | CC1.4, CC1.5 | 500.10, 500.14(a) |
| A.7.1–A.7.14 Physical controls | PR.AA-06, PR.DS-10 | 9.1–9.5 | CC6.4, CC6.5 | — |
| A.8.1–A.8.5 Endpoint and access enforcement | PR.AA-05, PR.PS-01 | 7.2, 8.3 | CC6.1, CC6.6 | 500.07, 500.12, 500.14 |
| A.8.6–A.8.14 Operations, malware, vulnerability, data protection | ID.RA-01, PR.PS-02, PR.DS-11, DE.CM-09 | 5.1–5.4, 6.3, 11.3 | CC7.1, CC7.2, A1.1 | 500.05, 500.14(b) |
| A.8.15–A.8.19 Logging, monitoring, utilities | DE.CM-01 to DE.CM-09, DE.AE-02/03 | 10.1–10.7 | CC7.2 | 500.06, 500.14(a) |
| A.8.20–A.8.24 Network and cryptography | PR.IR-01, PR.DS-01/02 | 1.1–1.5, 4.1, 4.2 | CC6.6, CC6.7 | 500.15 |
| A.8.25–A.8.34 Secure development and change | PR.PS-06, ID.RA-01 | 6.1–6.5, 11.3.1 | CC8.1 | 500.08 |

**Not covered by ISO/IEC 27001.** BSA/AML programme requirements, OFAC screening, SAR and CTR
filing, and CIP/KYC obligations have no Annex A equivalent. They are tracked in the Legal
obligations register and assessed in AFT-ISMS-RSK-01 under threat source [[TA-09]]. An ISMS scope
statement does not discharge them, and a gap analysis against Annex A alone will not surface them.

---

## 16. Sign-off and acceptance conventions

Applies to every register and plan in the deliverable set.

| Artefact | Who signs | What they are attesting | Where recorded |
|---|---|---|---|
| Risk treatment decision | Named risk owner (the executive accountable for the affected process) | That the treatment is appropriate and that they accept the residual risk pending closure | Risk Treatment Plan, sign-off columns |
| Residual risk acceptance, Moderate | CISO | Acceptance on behalf of the organisation | Risk register |
| Residual risk acceptance, High | Executive Risk Committee | Acceptance, minuted | ERC minutes, referenced from the register |
| Residual risk acceptance, Critical | Board Audit Committee | Acceptance, minuted | Audit Committee minutes |
| Statement of Applicability | CISO prepares, ERC approves | That the control selection and exclusions are justified and complete | SoA approval block |
| Policy | CISO owns, ERC approves | Tier 1 and Tier 2 documents only. Standards are approved by the CISO alone. | Policy document control block |
| Supplier rating deviation | Executive Risk Committee, with Board Audit Committee visibility | That the deviation from the standard consequence is justified | ERC minutes; TPRM findings |

**Policy tier convention.** Tier 1 is the apex Information Security Policy (POL-05, not yet
written). Tier 2 policies state principles and obligations and are approved by the ERC. Standards
(STD-nn) hold the specific parameters — key lengths, timeouts, thresholds — and are approved by
the CISO so that a parameter change does not require executive re-approval. Parameters must not
appear in a Tier 2 policy.

---

## 13. Change log

| Version | Date | Change |
|---|---|---|
| 1.0 | 9 September 2026 | Initial issue. Derived from the four issued Tier 2 policies (POL-01 to POL-04) and extended with organisation, asset, vendor, scale and current-state content required by deliverables 2 to 5. |
| 1.1 | 9 September 2026 | Section 8.3 gap priority criteria rewritten. The v1.0 P1 criterion ("blocks Stage 1 or Stage 2 certification") overlapped the P2 criterion, since a major nonconformity also blocks certification; the two are now separated by audit sequence and a note on applying the boundary has been added. Section 10.1 added recording the AFT-ISMS-GAP-01 outcome and the open timetable recommendation; former 10.1 renumbered to 10.2. Document register updated to show GAP-01 issued. |
| 1.2 | 9 September 2026 | Section 10.1 extended with the AFT-ISMS-RSK-01 risk assessment outcome, including the four supplier-related residual ratings the vendor assessment must reconcile to. Section heading generalised to 'Assessment outcomes'. Document register updated to show RSK-01 issued. |
| 1.3 | 9 September 2026 | Section 10.1 extended with the AFT-TPRM-ASM-01 outcome and the open ERC decision on V-03 (finding F-16). Document register updated to show TPRM-ASM-01 issued. |
| 1.4 | 9 September 2026 | Document register updated to show PRG-01 issued. Deliverables 1 to 5 complete. |
| 2.0 | 9 September 2026 | Major revision following expert review. Section 1.2 extended with BSA/AML, OFAC, SAR, NYDFS Part 500 and UK MLR obligations. New section 14 threat profile (TA-01 to TA-10, including TA-09 platform abuse). New section 15 control framework crosswalk, held centrally so deliverables stop re-deriving mappings. New section 16 sign-off and acceptance conventions, including the policy/standard tier rule that parameters belong in standards, not policies. |
| 2.1 | 9 September 2026 | Document register updated: SOA-01 issued unsigned, STD-02 issued, POL-02 v3.1, POL-03 v3.0, GAP-01 v2.0, RSK-01 v2.0, TPRM-ASM-01 v2.0, PRG-01 v1.1. |
| 2.2 | 9 September 2026 | POL-01 and POL-04 rebuilt to v3.0 under the revised agent prompt, both unapproved pending legal sign-off. Restricted — Controlled Access category introduced at POL-04 s4.1 for tipping-off material. TPRM v2.1 adds jurisdiction and sanctions flow-down analysis (findings F-17, F-18). PRG-01 v1.2 adds statutory financial crime training. |
| 2.3 | 9 September 2026 | POL-09 rebuilt to v2.0, unapproved pending legal, DPO and financial crime sign-off. Remediates the A.5.19, A.5.20, A.5.21 and A.5.22 gaps by adding the engagement lifecycle, ongoing monitoring, reassessment escalation, exit and offboarding, fourth-party requirements and the section 7 deviation route. |
