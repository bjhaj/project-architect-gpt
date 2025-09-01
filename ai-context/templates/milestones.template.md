# Milestones — {{PROJECT_TITLE}}

**Owner:** {{OWNER}}  
**Date:** {{YYYY-MM-DD}}  
**Version:** {{v0.1}}  
<!-- NOTE: Keep this document focused on phase planning. Architecture is a separate artifact:
     - End of M1 → create ai-context/architecture/brief.md
     - Early M2 (if warranted) → expand to architecture_overview.md -->

---

## 0) How to Use This Template
- Define **n milestones**. Each must end with a **usable deliverable** and reduce uncertainty for the next phase.
- For each milestone, fill: **Goal**, **Deliverable**, **Dependencies**, **Exit Criteria (DoD)**, **Verification**, **Risks addressed**, **Owners/Reviewers**, and **File Targets**.
- Create matching objective files under `ai-context/milestone_<k>/objective_<j>.md` when you expand a milestone.

---

## 1) Milestone Map (Summary Table)

| ID | Name | One-line Goal | Deliverable | Depends On | Exit Criteria (short) | Owner | Target Date | Status |
|---|---|---|---|---|---|---|---|---|
| M1 | {{NAME}} | {{GOAL}} | {{ARTIFACT}} | {{–}} | {{DoD short}} | {{OWNER}} | {{YYYY-MM-DD}} | {{planned}} |
| M2 | {{NAME}} | {{GOAL}} | {{ARTIFACT}} | {{M1}} | {{DoD short}} | {{OWNER}} | {{YYYY-MM-DD}} | {{planned}} |
| M3 | {{NAME}} | {{GOAL}} | {{ARTIFACT}} | {{M2}} | {{DoD short}} | {{OWNER}} | {{YYYY-MM-DD}} | {{planned}} |

> Add/remove rows as needed. Keep one-line goals crisp.

---

## 2) Milestones (Detailed)

### Milestone {{ID}} — {{NAME}}
**One-line goal:** {{WHAT THIS MILESTONE ACHIEVES}}  
**Owner:** {{OWNER}} • **Target date:** {{YYYY-MM-DD}} • **Status:** {{planned/in-progress/done}}

#### 2.1 Goal (Why this milestone exists)
- {{Clear, outcome-focused statement that reduces uncertainty for the next phase}}

#### 2.2 Deliverable (Tangible outcome)
- {{Repo state / artifact / demo / document}}
- **File targets (if applicable):**
  - `{{repo/path/to/artifact}}`
  - `{{ai-context/path/to/supporting-docs}}`

#### 2.3 Dependencies (What must exist before starting)
- {{Milestones, approvals, data access, contracts}}
- {{External teams/services/APIs}}

#### 2.4 Exit Criteria — Definition of Done (DoD)
- {{Check 1 (objective, verifiable)}}
- {{Check 2}}
- {{Check 3}}

#### 2.5 Verification (How DoD is verified)
- {{Command, test, validation procedure, reviewer checklist}}
- {{Link to CI job / validation script if applicable}}

#### 2.6 Risks addressed in this milestone
- {{Risk A}} → {{how this milestone mitigates it}}
- {{Risk B}} → {{mitigation}}

#### 2.7 Owners, Reviewers, Sign-off
- **Owner(s):** {{names}}  
- **Reviewers:** {{names/roles}}  
- **Sign-off:** {{person/role}}  

#### 2.8 Notes / Non-goals
- {{Important clarifications, exclusions}}

#### 2.9 Related Objectives (to be created under `ai-context/milestone_{{K}}/`)
- Objective stubs: {{O1 name}}, {{O2 name}}, {{O3 name}} (create detailed objective files later)

#### 2.10 Machine-Readable Summary (optional; aligns with milestone.schema.json)
```json
{
  "id": "{{ID}}",
  "name": "{{NAME}}",
  "goal": "{{Outcome-focused goal}}",
  "deliverable": "{{Primary artifact/state}}",
  "dependencies": ["{{M0 or external dep}}"],
  "objectives_hint": ["{{O1}}", "{{O2}}", "{{O3}}"]
}
