# Copilot Prompt — Objective {{O_ID}}

> Paste this entire prompt into Copilot Chat from the repository root.  
> Copilot should use the workspace files listed below for context.

---

## Context Files (read carefully)
- `ai-context/00_project_report.md`
- `ai-context/milestones.md`
- `ai-context/milestone_{{MILESTONE_INDEX}}/objective_{{O_ID}}.md`

*(If any file is missing, proceed with assumptions and note them.)*

---

## Task
Think deeply and complete **Objective {{O_ID}}** exactly as specified in the Objective doc.  
Extract constraints and success criteria from the context files above. Produce only the listed deliverables and write them to the exact **File Targets**.

---

## Constraints
- **Scope:** one objective = one **primary** artifact (plus optional supporting files). No scope creep.
- **Placement:** write outputs to the exact paths in **File Targets**.
- **Clarity:** prefer simple, readable solutions; keep dependencies minimal.
- **Conventions:** follow repo naming, structure, and any referenced schemas/templates.
- **Assumptions:** if information is missing, state explicit assumptions at the top of the produced artifact(s) under an **ASSUMPTIONS** section and proceed.
- **No unsolicited additions:** do not introduce new libraries/services/APIs unless the objective explicitly allows it.

---

## Deliverables
- {{PRIMARY_ARTIFACT_DESCRIPTION}}
- {{OPTIONAL_SUPPORTING_ARTIFACT_DESCRIPTION}}

---

## File Targets (write to these exact paths)
- `{{REPO/PATH/PRIMARY_ARTIFACT}}`
- `{{REPO/PATH/SUPPORTING_ARTIFACT}}`

---

## Acceptance Criteria (Definition of Done)
- {{AC1 — objective, verifiable}}
- {{AC2}}
- {{AC3}}

---

## Verification (run and validate)
> Provide commands or steps to verify the output meets the Acceptance Criteria. If none are specified in the Objective, propose minimal checks.

```bash
# Example (replace with real checks from the Objective):
# 1) Lint/typecheck
{{LINT_OR_TYPECHECK_COMMAND}}

# 2) Tests/validation
{{TEST_OR_VALIDATION_COMMAND}}

# 3) Build/preview (if applicable)
{{BUILD_OR_PREVIEW_COMMAND}}
