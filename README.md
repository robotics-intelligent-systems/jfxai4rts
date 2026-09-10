# JFXAI4RTS — Recruitment AI Open-Source Alternatives Evaluation & Integration Architecture

> Reframed architecture for an **AI-Powered Recruitment Tracking Platform**, using the alternatives listed in the source README as modular building blocks rather than as a flat dependency catalogue.

## 1. Source Direction

The source project is explicitly described as an **AI-Powered Recruitment Tracking Platform** and lists alternatives spanning ATS, HR/HCM, document intelligence, ECM, e-signature, enterprise portals, recruitment AI and supporting systems.

The source also preserves the engineering lifecycle:

```text
MBSE → CAD → CAM → CAS
```

with Arcadia/Capella for MBSE, CAD for design, CAM for manufacturing/assembly-oriented engineering stages, and CAS for end-to-end simulation/performance analysis.

---

# 2. Architectural Goal

The recommended architecture should optimize for this business path:

```text
Candidate / Recruiter / Hiring Manager
              |
              v
        Talent Portal
              |
              v
     Candidate / ATS Core
              |
      +-------+--------+
      |                |
      v                v
Document AI       Recruitment AI
      |                |
      +-------+--------+
              |
              v
      Human Review Gate
              |
              v
 Interviews / Offers / Contracts
              |
              v
         HR / HCM
              |
              v
 Payroll / Attendance / Employee Lifecycle
```

The system should keep **human decision authority** for consequential hiring decisions. AI can organize, extract, summarize, search, match against job-relevant criteria, flag inconsistencies, and generate evidence, but it should not make opaque autonomous hiring decisions.

---

# 3. Evaluation Criteria

Each alternative is evaluated against:

| Criterion | Meaning |
|---|---|
| Recruitment Fit | Direct usefulness for applicant/recruitment workflows |
| AI Leverage | Potential contribution to intelligent automation |
| Integration Value | Usefulness inside a modular architecture |
| Complexity | Expected integration/operational burden |
| Governance Risk | Relative sensitivity in an employment context |
| Recommended Role | Best position in the target architecture |

Scoring:

```text
5 = Excellent
4 = Strong
3 = Useful / contextual
2 = Limited
1 = Peripheral
```

The scores below are architectural judgments based on the source descriptions, not vendor certifications or production-readiness claims.

---

# 4. Tier A — Core Recruitment / ATS Candidates

## OpenCATS

**Source role:** Free and Open Source Candidate/Applicant Tracking System.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 5 |
| AI Leverage | 2 |
| Integration Value | 5 |
| Complexity | 3 |
| Governance Risk | 3 |

**Recommended role:** **Primary ATS baseline candidate**

Strengths:
- directly aligned with applicant tracking;
- clean conceptual fit as the system of record for recruitment workflow;
- suitable anchor for AI/document modules.

Best use:

```text
Candidate
   ↓
OpenCATS
   ↓
Pipeline / Status / Job / Applicant Record
   ↓
AI & Document Services
```

---

## SpotAxis

**Source role:** Open-source Applicant Tracking System.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 5 |
| AI Leverage | 2 |
| Integration Value | 4 |
| Complexity | 3 |
| Governance Risk | 3 |

**Recommended role:** **Alternative ATS core**

Use as a comparative implementation against OpenCATS.

---

## JuggleHire

**Source role:** Recruitment software designed to simplify hiring.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 5 |
| AI Leverage | 2 |
| Integration Value | 4 |
| Complexity | 3 |
| Governance Risk | 3 |

**Recommended role:** **Alternative recruitment workflow engine**

Best positioned as an ATS/workflow alternative rather than as the central AI engine.

---

## HIRE — Human Intelligence Recruitment Engine

**Source role:** AI-oriented recruitment platform.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 5 |
| AI Leverage | 5 |
| Integration Value | 4 |
| Complexity | 4 |
| Governance Risk | 5 |

**Recommended role:** **Strategic AI recruitment candidate**

Best use:
- candidate workflow assistance;
- recruiter copilot;
- job/candidate matching support;
- AI-assisted candidate intelligence.

Because employment is a consequential domain, HIRE-like functionality should be placed behind a **Human Review / Policy Gate**.

---

# 5. Tier A — AI Candidate & Document Intelligence

## PrismaIA

**Source role:** Open-source framework for bias-free candidate evaluation using LLMs.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 5 |
| AI Leverage | 5 |
| Integration Value | 5 |
| Complexity | 4 |
| Governance Risk | 5 |

**Recommended role:** **AI evaluation-assistance layer**

Best position:

```text
Job Criteria
    +
Candidate Evidence
    |
    v
PrismaIA-style Evaluation
    |
Evidence / Explanation
    |
    v
Human Recruiter
```

Recommended constraint:
- evaluate only job-relevant skills/experience;
- exclude protected or sensitive personal characteristics;
- retain an auditable explanation of criteria and evidence;
- no final autonomous hire/reject decision.

---

## deepdoctection

**Source role:** Python library for scan/PDF layout analysis, OCR, document and token classification.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 4 |
| AI Leverage | 5 |
| Integration Value | 5 |
| Complexity | 3 |
| Governance Risk | 2 |

**Recommended role:** **Resume / document ingestion engine**

High-value use cases:
- CV parsing;
- certificate extraction;
- structured form extraction;
- document layout understanding;
- normalized candidate records.

Strong candidate for the ingestion pipeline.

---

## Paperless-AI

**Source role:** AI extension for Paperless-ngx providing automatic classification, tagging and semantic search through OpenAI-compatible APIs and Ollama.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 4 |
| AI Leverage | 5 |
| Integration Value | 5 |
| Complexity | 3 |
| Governance Risk | 3 |

**Recommended role:** **Candidate document knowledge layer**

Useful for:
- automatic CV/document classification;
- smart tags;
- semantic retrieval;
- document knowledge base;
- local/private AI integration.

---

## localGPT-Vision

**Source role:** End-to-end vision-based RAG system.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 3 |
| AI Leverage | 5 |
| Integration Value | 4 |
| Complexity | 4 |
| Governance Risk | 4 |

**Recommended role:** **Multimodal document RAG**

Good uses:
- scanned certificates;
- document screenshots;
- visually structured forms;
- portfolio/document retrieval.

Do **not** use visual candidate appearance as a hiring signal.

---

## CLIP

**Source role:** Contrastive Language-Image Pretraining; predicts relevant text from an image.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 2 |
| AI Leverage | 4 |
| Integration Value | 3 |
| Complexity | 3 |
| Governance Risk | 5 |

**Recommended role:** **Restricted document/media retrieval research**

Appropriate:
- semantic indexing of non-personal visual assets;
- document page retrieval;
- portfolio media organization.

Not recommended:
- scoring candidate appearance;
- inferring personality, demographic attributes, health, ethnicity, age, attractiveness, or "culture fit" from images.

Therefore CLIP should **not** participate in candidate ranking.

---

# 6. Tier A/B — HR & HCM Integration

These tools become important after recruitment, or when JFXAI4RTS grows into a full Talent Lifecycle platform.

## Frappe HR

**Source role:** Open-source HR and payroll software.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 4 |
| Post-Hire Value | 5 |
| Integration Value | 5 |
| Complexity | 3 |

**Recommended role:** **Preferred HR/HCM integration candidate**

Architecture:

```text
ATS
 ↓
Accepted Candidate
 ↓
Employee Onboarding
 ↓
Frappe HR
 ↓
HR / Payroll / Employee Lifecycle
```

---

## OrangeHRM

**Source role:** Comprehensive Human Resource Management system.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 3 |
| Post-Hire Value | 5 |
| Integration Value | 4 |
| Complexity | 3 |

**Recommended role:** **Alternative HRMS**

---

## Horilla

**Source role:** Free and Open Source HRMS.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 3 |
| Post-Hire Value | 5 |
| Integration Value | 4 |
| Complexity | 3 |

**Recommended role:** **Alternative open HRMS**

---

## minthcm.org

**Source role:** Open-source, AI-native HCM platform.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 4 |
| AI Leverage | 5 |
| Post-Hire Value | 5 |
| Integration Value | 4 |
| Complexity | 4 |

**Recommended role:** **Strategic AI-HCM alternative**

Particularly interesting if the project evolves beyond ATS into:

```text
Recruitment
   ↓
Onboarding
   ↓
Talent Management
   ↓
Performance / Employee Lifecycle
```

---

## Biometric Attendance Sync Tool for ERPNext

| Dimension | Score |
|---|---:|
| Recruitment Fit | 1 |
| Post-Hire Value | 4 |
| Integration Value | 3 |
| Complexity | 2 |
| Governance Risk | 4 |

**Recommended role:** **Optional post-hire integration**

Not part of the recruitment core. Biometric data should be treated as highly sensitive and isolated from candidate evaluation.

---

# 7. Tier B — ECM & Candidate Document Management

## Alfresco

**Source role:** Enterprise Content Management platform.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 3 |
| Document Value | 5 |
| Integration Value | 5 |
| Complexity | 4 |

**Recommended role:** **Enterprise document repository**

Use for:
- CVs;
- contracts;
- certificates;
- hiring documentation;
- policy documents;
- retention workflows.

---

## OpenKM

**Source role:** Document management software.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 3 |
| Document Value | 5 |
| Integration Value | 4 |
| Complexity | 3 |

**Recommended role:** **Lighter ECM alternative**

Architecturally, choose **Alfresco OR OpenKM** for most deployments rather than both.

---

# 8. Tier B — Contract & E-Signature

## OpenSign

**Source role:** Open-source document e-signing solution.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 4 |
| Integration Value | 5 |
| Complexity | 2 |

**Recommended role:** **Preferred offer / employment document e-signature block**

```text
Approved Candidate
      ↓
Offer Document
      ↓
OpenSign
      ↓
Signed Agreement
      ↓
ECM / HRMS
```

---

## OSC — Contract Tracking Tool

| Dimension | Score |
|---|---:|
| Recruitment Fit | 3 |
| Contract Value | 4 |
| Integration Value | 3 |

**Recommended role:** **Contract tracking support**

---

## ContractManager

**Source role:** Contract management software for the Jameica platform.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 2 |
| Contract Value | 4 |
| Integration Value | 2 |

**Recommended role:** **Research / alternative contract-management component**

OpenSign + ECM + HRMS is likely a cleaner target architecture than introducing multiple overlapping contract systems.

---

# 9. Tier B — Portal & Experience

## Liferay

**Source role:** Open-source enterprise portal.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 4 |
| Integration Value | 5 |
| Complexity | 4 |

**Recommended role:** **Enterprise Talent Portal**

Possible portal roles:

```text
Candidate Portal
Recruiter Portal
Hiring Manager Portal
Employee Onboarding Portal
Career Site
Knowledge Portal
```

Liferay should remain separate from the ATS core.

---

# 10. Tier C — Knowledge / Library Platforms

## FOLIO

**Source role:** Open-source, cloud-hostable, app-store-based library platform.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 1 |
| Knowledge Value | 3 |
| Integration Value | 2 |

**Recommended role:** **Optional knowledge-library research reference**

Possible secondary use:
- internal learning resources;
- training catalogues;
- corporate knowledge collections.

Not recommended for ATS core.

---

## Koha

**Source role:** Free software Integrated Library System.

| Dimension | Score |
|---|---:|
| Recruitment Fit | 1 |
| Knowledge Value | 3 |
| Integration Value | 2 |

**Recommended role:** **Optional library/learning reference**

Useful only if JFXAI4RTS expands toward training or corporate-library services.

---

# 11. Recommended Target Architecture

```text
                        USERS
           Candidates / Recruiters / Managers
                          |
                          v
               +----------------------+
               | TALENT PORTAL        |
               | Liferay / Web/Mobile |
               +----------+-----------+
                          |
                          v
               +----------------------+
               | ATS DOMAIN API       |
               | Canonical Candidate  |
               | / Job / Application  |
               +----------+-----------+
                          |
            +-------------+-------------+
            |                           |
            v                           v
+------------------------+   +---------------------------+
| ATS CORE               |   | DOCUMENT INTELLIGENCE     |
| OpenCATS               |   | deepdoctection            |
| OR SpotAxis            |   | Paperless-AI              |
| OR JuggleHire          |   | localGPT-Vision           |
+-----------+------------+   +-------------+-------------+
            |                              |
            +---------------+--------------+
                            |
                            v
               +--------------------------+
               | RECRUITMENT AI LAYER     |
               | HIRE / PrismaIA          |
               | RAG / explanations       |
               | skills evidence          |
               +------------+-------------+
                            |
                            v
               +--------------------------+
               | POLICY + HUMAN REVIEW    |
               | Audit / criteria /       |
               | recruiter approval       |
               +------------+-------------+
                            |
           +----------------+----------------+
           |                                 |
           v                                 v
+----------------------+        +--------------------------+
| OFFER / CONTRACT     |        | HR / HCM                 |
| OpenSign             |        | Frappe HR                |
| OSC / ECM            |        | OR OrangeHRM / Horilla   |
+----------+-----------+        | OR minthcm               |
           |                    +-------------+------------+
           +----------------------------------+
                            |
                            v
               +--------------------------+
               | ENTERPRISE CONTENT       |
               | Alfresco OR OpenKM       |
               +--------------------------+
```

---

# 12. Recommended Composition Profiles

## Profile A — Lean Open ATS

```text
Liferay / simple Web UI
        ↓
OpenCATS
        ↓
deepdoctection
        ↓
Paperless-AI
        ↓
OpenSign
        ↓
Frappe HR
```

**Assessment:** Best balance of simplicity and coverage.

---

## Profile B — AI-First Recruitment

```text
Talent Portal
     ↓
OpenCATS / SpotAxis
     ↓
deepdoctection
     ↓
Paperless-AI / localGPT-Vision
     ↓
HIRE
     ↓
PrismaIA
     ↓
Human Review
     ↓
OpenSign
     ↓
minthcm / Frappe HR
```

**Assessment:** Highest AI potential, but also highest governance burden.

---

## Profile C — Enterprise Recruitment

```text
Liferay
   ↓
ATS Core
   ↓
AI Recruitment Services
   ↓
Alfresco
   ↓
OpenSign
   ↓
OrangeHRM / Frappe HR
```

**Assessment:** Stronger document/governance architecture; higher infrastructure complexity.

---

# 13. Priority Ranking

## Priority 1 — Build / Evaluate First

1. **OpenCATS**
2. **deepdoctection**
3. **Paperless-AI**
4. **PrismaIA**
5. **OpenSign**
6. **Frappe HR**

These six form the strongest initial building-block path:

```text
ATS
 ↓
Document Understanding
 ↓
Semantic Knowledge
 ↓
AI-Assisted Evaluation
 ↓
Human Approval
 ↓
Contract
 ↓
HR
```

---

## Priority 2 — Strong Alternatives / Extensions

- SpotAxis
- JuggleHire
- HIRE
- minthcm
- OrangeHRM
- Horilla
- Liferay
- Alfresco
- OpenKM
- localGPT-Vision

---

## Priority 3 — Specialized / Contextual

- OSC
- ContractManager
- Biometric Attendance Sync Tool

---

## Priority 4 — Research / Peripheral

- CLIP
- FOLIO
- Koha

These are not useless; they simply have weaker direct alignment with the recruitment core.

---

# 14. Value vs Complexity Matrix

```text
                         HIGH VALUE
                             |
         PrismaIA        OpenCATS        Frappe HR
              \         Paperless-AI     OpenSign
               \        deepdoctection
                \
                 HIRE / minthcm
                     |
 LOW COMPLEXITY ------+---------------- HIGH COMPLEXITY
                     |
             OpenKM   |    Alfresco / Liferay
                     |
             Koha     |    localGPT-Vision
             FOLIO    |
                     |
                         LOW DIRECT VALUE
```

---

# 15. AI Governance Boundary

Because recruitment is a consequential employment domain, AI should be designed as:

```text
Evidence Extraction
       ↓
Job-Relevant Matching
       ↓
Explanation
       ↓
Human Review
       ↓
Decision
```

Not:

```text
Photo / Sensitive Trait
       ↓
Opaque AI Score
       ↓
Automatic Reject
```

Recommended safeguards:

- explicitly defined job-related criteria;
- no inference of protected characteristics;
- no biometric or facial analysis for candidate ranking;
- separation of attendance biometrics from recruitment;
- human review for shortlist/reject decisions;
- audit logs;
- versioned models/prompts;
- candidate-data minimization;
- explainable evidence trail;
- bias/fairness evaluation;
- retention and deletion policies.

---

# 16. MBSE → CAD → CAM → CAS Adaptation

The source engineering structure can be adapted to the recruitment platform as:

```text
MBSE
Requirements / Capella / business capabilities
      ↓
CAD
UX / API / data / workflow design
      ↓
CAM
Implementation / CI/CD / deployment assembly
      ↓
CAS
End-to-end simulation / performance / AI evaluation
```

For CAS, simulate:

- candidate ingestion;
- CV parsing;
- search;
- recruiter workflow;
- AI-assistance;
- offer flow;
- HR onboarding;
- failure scenarios;
- performance;
- governance controls.

---

# 17. Recommended MVP

```text
Candidate Portal
       ↓
OpenCATS
       ↓
deepdoctection
       ↓
Paperless-AI
       ↓
PrismaIA-style Job-Relevant Evidence
       ↓
Human Recruiter Review
       ↓
OpenSign
       ↓
Frappe HR
```

### MVP capabilities

- job publication;
- candidate registration;
- application tracking;
- CV/document ingestion;
- structured extraction;
- semantic candidate-document search;
- job-relevant evidence summaries;
- recruiter notes;
- explicit human approval;
- offer generation;
- electronic signature;
- employee onboarding.

---

# 18. Final Categorization

| Category | Preferred | Alternatives | Research / Secondary |
|---|---|---|---|
| ATS | OpenCATS | SpotAxis, JuggleHire | — |
| AI Recruitment | PrismaIA | HIRE | — |
| HCM/HRMS | Frappe HR | minthcm, OrangeHRM, Horilla | — |
| Document AI | deepdoctection, Paperless-AI | localGPT-Vision | CLIP |
| ECM | Alfresco | OpenKM | — |
| Portal | Liferay | Custom Web UI | — |
| E-Signature | OpenSign | — | — |
| Contract Tracking | OSC | ContractManager | — |
| Attendance | — | Biometric Attendance Sync | Post-hire only |
| Knowledge Library | — | — | FOLIO, Koha |

---

# 19. Strategic Recommendation

The strongest architecture is not a monolithic HR suite. It is a composable platform:

```text
OpenCATS
   +
deepdoctection
   +
Paperless-AI
   +
PrismaIA
   +
Human Review
   +
OpenSign
   +
Frappe HR
```

with **Liferay**, **Alfresco/OpenKM**, **HIRE**, **minthcm**, **SpotAxis**, **JuggleHire**, and **localGPT-Vision** available as replaceable enterprise or AI extensions.

The most important design principle is:

> **Use AI to structure evidence, improve search, explain job-relevant matches and assist recruiters—while keeping consequential employment decisions under transparent human control.**
