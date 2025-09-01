# Objective {{ID}} — {{NAME}}

**Milestone:** {{MILESTONE_ID}}  
**Owner:** {{OWNER}}  
**Effort:** {{XS|S|M|L}}  
**Priority:** {{P0|P1|P2}}  
**Status:** {{planned|in-progress|done}}  
**Target Date:** {{YYYY-MM-DD}}

> **Note:** If this objective is created with missing details, include an **ASSUMPTIONS** block below and list **OPEN QUESTIONS** at the end.

---

## 1) Purpose (Why this objective exists)
- {{Short, outcome-focused statement connecting to milestone goal and success criteria in the report}}

---

## 2) Context References
- `ai-context/00_project_report.md` — sections: {{Motivation / Deployment / Success}}  
- `ai-context/milestones.md` — {{Milestone summary}}  
- {{Any other files, datasets, specs}}

---

## 3) Inputs (Dependencies)
- {{Files, data sources, approvals, prior objectives}}
- {{External APIs/services}}

---

## 4) Outputs (Artifacts)
- **Primary:** `{{repo/path/to/primary_artifact}}`  
- **Supporting (optional):** `{{repo/path/to/supporting_artifact}}`

---

## 5) Acceptance Criteria (Definition of Done)
- {{AC1 — objective, verifiable}}
- {{AC2}}
- {{AC3}}

---

## 6) Constraints & Conventions
- {{Tooling/language/version constraints}}
- {{Style/structure conventions; naming rules; schema adherence}}
- {{Performance/footprint boundaries if relevant}}

---

## 7) Sequence / Dependencies Among Objectives
- **Must follow:** {{Objective IDs}}  
- **Unblocks:** {{Objective IDs}}  

---

## 8) Verification (How DoD is checked)
- **Procedure/Command(s):**  
  ```bash
  {{commands or steps to validate}}

## 9) File Targets (write outputs to these exact paths)

- `{{repo/path/to/primary_artifact}}`
- `{{repo/path/to/supporting_artifact}}`

## 10) Notes / Non-goals

- {{Clarifications and explicit exclusions}}

## ASSUMPTIONS *(include only if proceeding with assumptions)*

- {{Assumption A — rationale}}
- {{Assumption B — rationale}}

## OPEN QUESTIONS

- {{Q1}}
- {{Q2}}

## Machine-Readable Summary *(aligns with objective.schema.json)*

'''json
{
  "id": "{{ID}}",
  "name": "{{NAME}}",
  "owner": "{{OWNER}}",
  "inputs": ["{{file-or-dependency-1}}", "{{file-or-dependency-2}}"],
  "outputs": ["{{repo/path/to/primary_artifact}}", "{{repo/path/to/supporting_artifact}}"],
  "acceptance_criteria": ["{{AC1}}", "{{AC2}}", "{{AC3}}"],
  "files": ["{{repo/path/to/primary_artifact}}", "{{repo/path/to/supporting_artifact}}"]
}'''

## Next Step *(Prompt Construction)*

When ready, request: **“Create the PromptSpec for Objective {{ID}}.”**

That prompt will reference:
- this file (`ai-context/milestone_{{MILESTONE_INDEX}}/objective_{{ID}}.md`),
- the project report, and
- the milestones document.



