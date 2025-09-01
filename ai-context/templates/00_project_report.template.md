# Project: {{TITLE}}

**Owner:** {{OWNER}}  
**Date:** {{YYYY-MM-DD}}  
**Version:** {{v0.1}}  
<!-- NOTE: Keep this report business/context-only. Architecture is a separate artifact created later (see architecture/brief.md when it exists). -->

---

## 1) Motivation (Why)
- **Problem statement:** {{What problem are we solving?}}  
- **Who benefits & why now:** {{Users/stakeholders and the urgency}}  
- **Value if solved:** {{Business/science/UX impact, quantified where possible}}  
- **Non-goals:** {{What this project explicitly avoids at this time}}

**Success narrative (1–3 sentences):**  
{{Describe what “success” looks like from a user/stakeholder viewpoint.}}

---

## 2) Deployment Space (Where)
- **Primary users & usage contexts:** {{Personas, workflows, environments}}  
- **Operational constraints:**  
  - Latency/throughput: {{targets or bounds}}  
  - Cost: {{budget constraints, per-call caps}}  
  - Privacy/compliance: {{PII/PHI, policies, jurisdictions}}  
  - Hardware/runtime: {{edge/mobile/serverless/GPU/CPU}}  
  - Availability: {{SLA/SLO if known}}  
- **Integration targets:** {{APIs, services, data sources, platforms}}  
- **Release environments:** {{dev/stage/prod, on-prem/cloud}}

---

## 3) Context (What’s Known)
- **Prior art & baselines:** {{Links, papers, repos, internal systems}}  
- **Assumptions:** {{Data availability, user behavior, model feasibility}}  
- **Existing constraints:** {{Licensing, security, data retention, review boards}}  
- **Dependencies:** {{Teams, systems, contracts, datasets}}  
- **Open questions:** {{Critical unknowns to resolve early}}

---

## 4) Success Criteria (Measurable)
- **Primary KPIs (must-have):**  
  1. {{Metric name}} — target: {{value}} by {{date}}  
  2. {{…}}
- **Secondary KPIs (nice-to-have):**  
  - {{Metric}} — {{target}}
- **Guardrails / non-regression:**  
  - {{Metric/constraint that must not degrade}}  

**Evaluation plan (how measured):** {{Offline/online tests, benchmarks, user studies, A/B, etc.}}

---

## 5) Scope Boundaries
- **In scope (this phase):**  
  - {{Items clearly included}}
- **Out of scope:**  
  - {{Items explicitly excluded for now}}

---

## 6) Risks & Mitigations
| Risk | Likelihood | Impact | Mitigation / Spike |
|---|---|---|---|
| {{risk 1}} | {{L/M/H}} | {{L/M/H}} | {{action}} |
| {{risk 2}} | {{L/M/H}} | {{L/M/H}} | {{action}} |

---

## 7) Data & Ethics (If Applicable)
- **Data sources:** {{Names, owners, access paths}}  
- **Quality concerns:** {{Bias, missingness, drift}}  
- **Privacy & consent:** {{Policies, DSAR/RTBF handling}}  
- **Usage restrictions:** {{Licensing, TOS, model/card requirements}}  

---

## 8) Milestones (Preview Only)
- **M1 — {{Name}}:** {{One-line goal}} → **Deliverable:** {{Tangible artifact}}  
- **M2 — {{Name}}:** {{One-line goal}} → **Deliverable:** {{Tangible artifact}}  
- **M3 — {{Name}}:** {{One-line goal}} → **Deliverable:** {{Tangible artifact}}  
<!-- Detailed objectives and prompts will be created later under ai-context/milestone_X/. -->

---

## 9) Stakeholders & Roles
- **Sponsor/Decision-maker:** {{name}}  
- **Tech lead:** {{name}}  
- **Contributors:** {{names}}  
- **Reviewers/Approvers:** {{names}}  

---

## 10) Glossary (Optional)
- **{{Term}}** — {{definition}}  
- **{{Term}}** — {{definition}}

---

### Notes for Authors
- Keep this document **source-of-truth** for motivation, context, and success criteria.  
- Do **not** add system architecture here; create a separate **Architecture Brief** at the end of Milestone 1.  
- Cross-link related files as they are created (milestones, objectives, prompts).
