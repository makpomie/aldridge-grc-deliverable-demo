# Aldridge Financial Technologies — GRC Deliverable Set

**Packaged:** 9 September 2026 · **Files:** 15 · All documents are the final version produced.
Where a document was revised during the build, only the latest version is included.

Aldridge Financial Technologies is a fictional company created for this deliverable set.
Northgate Analytics, Verrio Cloud Services and Meridian BPO Solutions are fictional suppliers.

---

## Read in this order

| # | File | Ref | Version | Status |
|---|---|---|---|---|
| 1 | `Aldridge-Context-Pack.md` | AFT-CTX-01 | **2.2** | Canonical. Read first — every other document draws on it |
| 2 | `ISO27001-Gap-Analysis-Findings.docx` | AFT-ISMS-GAP-01 | **2.0** | Findings memo for the Executive Risk Committee |
| 3 | `ISO27001-Gap-Analysis.xlsx` | AFT-ISMS-GAP-01 | **2.0** | 93 Annex A controls + 25 clause requirements, with evidence, effort, cost, dependencies and a capacity check |
| 4 | `ISO27001-Statement-of-Applicability.xlsx` | AFT-ISMS-SOA-01 | **1.0** | Complete, **UNSIGNED**. Supersedes draft v0.3 |
| 5 | `NIST-Risk-Assessment.xlsx` | AFT-ISMS-RSK-01 | **2.0** | 55 risks, FIPS 199 categorisation, Risk Treatment Plan (**unsigned**) |
| 6 | `TPRM-Vendor-Assessment.xlsx` | AFT-TPRM-ASM-01 | **2.1** | 65 questions, 13 domains, 3 suppliers, 18 findings, jurisdiction and sanctions flow-down |
| 7 | `Security-Awareness-Programme.docx` | AFT-ISMS-PRG-01 | **1.2** | Includes Q2 2026 phishing results and the follow-up training matrix |

## Policies and standards

| # | File | Ref | Version | Status |
|---|---|---|---|---|
| 8 | `Acceptable-Use-Policy.docx` | AFT-ISMS-POL-01 | **3.0** | **DRAFT, UNAPPROVED** — v2.1 remains operative. Pending General Counsel and employment law sign-off |
| 9 | `Incident-Response-Policy.docx` | AFT-ISMS-POL-02 | **3.1** | Issued |
| 10 | `Access-Control-Policy.docx` | AFT-ISMS-POL-03 | **3.0** | Issued. Parameters relocated to STD-02 |
| 11 | `Data-Classification-Policy.docx` | AFT-ISMS-POL-04 | **3.0** | **DRAFT, UNAPPROVED** — v2.0 remains operative. Pending General Counsel and DPO sign-off |
| 12 | `Third-Party-Risk-Management-Policy.docx` | AFT-ISMS-POL-09 | **2.0** | **DRAFT, UNAPPROVED** — v1.3 remains operative. The policy the TPRM assessment is conducted under |
| 13 | `Authentication-Credential-Standard.docx` | AFT-ISMS-STD-02 | **1.0** | Issued |

## Documents referenced but not produced

The deliverable set cites a wider document library than it contains. The following are referenced
as existing within the Aldridge fiction but were not written: POL-06 Secure Development,
POL-07 Cryptography, POL-08 Business Continuity, STD-04 BYOD, STD-06 Privileged Access
Management, STD-08 Digital Evidence Handling, STD-09 Cryptographic Key Management, STD-11
Approved Tooling Register, PLN-01 Incident Response Plan, PLN-03 BCDR Plan, PRO-03 Joiner/Mover/
Leaver, SCH-01 Records Retention Schedule, LEG-POL-01 Data Protection Policy and HR-POL-02
Disciplinary Procedure.

One further document, **POL-05 Information Security Policy (Tier 1)**, is absent by design: its
non-existence is a deliberate finding of the gap analysis and a certification-blocking gap.

---

## Method

| # | File | Version | Purpose |
|---|---|---|---|
| 14 | `GRC-Agent-Master-Prompt.md` | 1.0 | System prompt for the GRC agent, drafted from the failure modes this build exposed |
| 15 | `MANIFEST.md` | — | This file |

---

## Four things to know before reading

**1. Five documents are deliberately unsigned or unapproved.** The Statement of Applicability, the Risk Treatment Plan (55 blank signature blocks), and the three draft policies (POL-01, POL-04, POL-09). These are not omissions. ISO/IEC 27001 clause 6.1.3(d) and (f) are not satisfied until those approvals are executed, and simulating an approval that has not occurred would misrepresent the organisation's position.

**2. Word files show an empty table of contents until refreshed.** The TOC is a live field. Open in Word and press F9.

**3. Excel figures are formula-driven.** Scores, ratings, appetite tests, approval levels, counts and heat maps recompute from the underlying inputs. Change an impact value and everything dependent on it moves.

**4. Two open decisions are recorded but not resolved.** The certification timetable re-baseline (Stage 1 Q2 2027 / Stage 2 Q4 2027) is a recommendation the ERC has not ruled on. The Meridian continuation under finding F-16 is a deviation from the standard consequence for a Critical rating and requires ERC approval with Board Audit Committee visibility. Both are flagged as open in the context pack rather than presented as settled.
