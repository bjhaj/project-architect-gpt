# ai-context/ — Project Knowledge Base

**Project:** {{PROJECT_TITLE}}  
**Owner:** {{OWNER}}  
**Date:** {{YYYY-MM-DD}}  
**Version:** {{v0.1}}

> This folder is the **single source of truth** for context that guides GPT/Copilot.  
> Keep it lightweight: capture only what unblocks decisions and implementation.

---

## What lives here (minimal set)

- `00_project_report.md` — **Comprehensive Report** (why/where/what success looks like).  
- `milestones.md` — High-level **milestone plan** (each ends with a usable deliverable).  
- `milestone_<k>/objective_<j>.md` — One **objective** per file (owner, outputs, DoD, file targets).  
- *(Optional when needed)* `architecture/` — Brief/Overview, contracts, ADRs (created later).

---

## How to use this folder (fast path)

1. **Write the report** → `00_project_report.md` (no architecture; business/context only).  
2. **Define milestones** → `milestones.md` (goal, deliverable, exit criteria).  
3. **Expand Milestone k into objectives** → `milestone_k/objective_j.md`.  
4. **Generate a PromptSpec** for each objective and paste the **Copilot prompt** into Copilot Chat.  
5. **Commit outputs** to the exact **File Targets** listed in the objective.

> If information is missing, proceed with **ASSUMPTIONS** (top of doc) and list **OPEN QUESTIONS** (end of doc).

---

## Clarify-first (keep it minimal)

- Ask **≤3 concise questions** before drafting each artifact.  
- If you say “assume and proceed,” generate the artifact with **ASSUMPTIONS** + **OPEN QUESTIONS** sections.

---

## Micro-rubrics (3 checks per artifact)

Embed these checks mentally (or as comments) before moving on:

- **Report:** Motivation & Deployment clear (≤10 lines) • ≥1 KPI + ≥1 guardrail • Scope has explicit in/out.  
- **Milestone:** Clear goal • Tangible deliverable with a path • DoD verifiable in one step/command.  
- **Objective:** One owner + one primary artifact **with exact path** • DoD objective & testable • Verification step/command listed.  
- **Prompt:** Lists context files, deliverables, **exact file targets** • Instructions match objective • DoD mirrors acceptance criteria.

---

## Conventions

- **One objective = one owner = one primary artifact.**  
- **Paths are contracts.** Write outputs to the **exact** File Targets.  
- **No duplication.** Each fact lives in one place; link instead of copying.  
- **Scope discipline.** If it grows, split into a new objective.  
- **Plain Markdown + JSON.** Human docs in `.md`; machine specs (PromptSpec) in `.json`.

---

## Naming & layout
ai-context/
├─ 00_project_report.md
├─ milestones.md
├─ milestone_1/
│ ├─ objective_1.md
│ └─ objective_2.md
└─ (later, if needed) architecture/
├─ brief.md
└─ architecture_overview.md


File naming:
- Milestones: `milestone_<k>/`
- Objectives: `objective_<j>.md`
- Use **kebab-case** for filenames outside the above patterns.

---

## Hand-offs to Copilot

For each objective:
1. Generate `promptspec.json` (machine-readable).  
2. Paste the rendered **Copilot prompt** into Copilot Chat.  
3. Ensure outputs land at **File Targets** and meet the **Acceptance Criteria**.  
4. If assumptions were made, keep them at the top of the produced artifact.

---

## Maintenance

- Update this folder **before** writing code (context drives implementation).  
- When facts change, update the **single source** and link from elsewhere.  
- Keep objectives small; mark **Status** and **Target Date** in each file.

---

## Optional add-ons (only when you feel the need)

- `architecture/brief.md` → after M1 (1 page, no diagrams).  
- `architecture/architecture_overview.md` → early M2 if warranted.  
- `architecture/adr/ADR-0001.md` → when a real decision has competing options.  
- `changelog.md` / `run_manifest.json` → if reproducibility or audits matter.

---

## Quick checklist (copy/paste)

- [ ] Report written (motivation, deployment, KPIs, scope).  
- [ ] Milestones defined (goal, deliverable, DoD, date).  
- [ ] Objective created (owner, outputs, DoD, **file targets**).  
- [ ] Prompt generated → Copilot run → outputs at paths.  
- [ ] Assumptions recorded; open questions listed or resolved.

---

*This template is intentionally minimal. Add structure only when it removes friction or prevents rework.*

