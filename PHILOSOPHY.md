# PHILOSOPHY — PROJECT ARCHITECT GPT AND THE ai-context METHOD

# Purpose of this document
This is the long-form explanation of why the method exists, what problems it solves, and how to use it day-to-day with your custom GPT and GitHub Copilot. It’s intentionally thorough and opinionated so you can run projects the same way every time, alone or with collaborators.

---

## 1. Motivation: why another "method" at all?

AI projects stall for predictable reasons:

- We start coding before we've written down the problem, the deployment context, or success criteria.
- "Milestones" are timeboxes, not outcomes; they don't retire risk or produce a testable deliverable.
- Objectives are vague ("improve training"), so assistants generate the wrong thing in the wrong place.
- Architecture appears too early, becomes fiction, and then reality bends to it (badly).
- Assistants drift: Copilot edits files you didn't intend; ChatGPT generates artifacts that don't fit the repo.
- Reproducibility is an afterthought; nobody remembers how we decided X or why we chose Y.

The method fixes this by forcing a **high → low flow** and by turning every step into a tiny, verifiable artifact that the next step can safely consume.

### The one-line goal:

> Turn fuzzy ideas into structured, reproducible work via a short chain of small, testable documents that direct human or AI labor without micromanaging it.

---

## 2. The core idea: high → low (context before construction)

### Stages (in order):

**A. Comprehensive Report:** business/context only. State the motivation, deployment space (who/where/constraints), success criteria (KPIs and guardrails), and scope boundaries. No design promises here.

**B. Milestones:** a short sequence of phases that each end with a usable deliverable and a simple, objective Definition of Done (DoD). Milestones should reduce uncertainty for what comes next.

**C. Objectives:** within the current milestone, define small, concrete units of work. One owner, one primary artifact, exact file targets, and a single verification step.

**D. Prompts:** one detailed prompt per objective, derived from a machine-readable PromptSpec, ready for Copilot to act on.

Architecture is deferred. Add a one-page brief only after the first milestone proves what’s real. Expand to a larger architecture overview in early milestone two only if warranted by actual decisions, external interfaces, or meaningful non-functional requirements.

### Why deferral matters:

- Early design is an attractive trap; you commit to imaginary constraints.
- Small, real outputs give you evidence; evidence informs design.
- You keep velocity high and rework low.

---

## 3. Design principles (the rules that keep it minimal and powerful)

1. **Context before construction:** you cannot choose good tactics without a clear why/where/what.
2. **Clarify-first:** assistants must ask targeted questions, then draft. Missing data should never block progress; proceed with assumptions, but capture them explicitly.
3. **Paths are contracts:** objectives must list exact output paths. Assistants modify only those paths. This is what makes Copilot safe.
4. **Small steps:** XS/S objectives finish in one sitting; split if they grow. Momentum is king.
5. **Minimal validation:** tiny JSON schemas catch drift without red tape; human docs use simple templates.
6. **Single source of truth:** each fact lives in one file; link rather than duplicating.
7. **Progress over perfection:** ship a useful draft; refine on the next turn.
8. **Deferred architecture:** only design what reality demands.

---

## 4. The artifacts and why they exist

### Report (`ai-context/00_project_report.md`)
**Purpose:** align on motivation, deployment space, success criteria, and scope boundaries.  
**Why it exists:** business clarity prevents later thrash. The report is deliberately free of architecture.

Milestones (ai-context/milestones.md)
Purpose: create a small number of phases that each end with a tangible deliverable and a one-step verification.
Why it exists: timeboxes don’t guarantee outcomes; deliverables with DoD do.

### Objectives (`ai-context/milestone_<k>/objective_<j>.md`)
**Purpose:** define work so that an assistant can implement safely. One owner, one primary artifact, exact file targets, acceptance criteria, and a verification command.  
**Why it exists:** eliminates ambiguity, prevents scope creep, and tells Copilot where to write.

### PromptSpec + Copilot prompt (`ai-context/templates/promptspec.template.json` and `copilot_prompt.template.md`)
**Purpose:** bind an objective to deterministic instructions that render into a paste-ready prompt for Copilot.  
**Why it exists:** consistent, repeatable assistant handoffs.

### Two small partials used across docs
**ASSUMPTIONS** block at the top when you proceed with defaults; **OPEN QUESTIONS** at the end for unresolved decisions. These keep momentum while making uncertainty explicit.

### Lightweight schemas (optional but recommended)
Tiny JSON schemas for milestones, objectives, and PromptSpec enforce that key fields exist and are well-formed, without turning your process into bureaucracy.

---

## 5. Clarify-first behavior (how questions work)

Default mode: deep. Before creating any artifact, the GPT asks 5–7 high-leverage questions tied to exact fields it will fill in the target template or schema.

What makes a good clarifying question?
* If answered incorrectly, it would force a rewrite of the artifact.
* It references the specific section it will fill (“This is for Success Criteria”).
* It prefers A/B choices to reduce back-and-forth (“env: ObstructedMaze-1Q or DoorKey-8x8?”).
* It never asks for info already present in the conversation or the files.

If you reply “assume and proceed,” the GPT must continue immediately, inserting an ASSUMPTIONS block at the top and OPEN QUESTIONS at the end. This is how you stay unblocked without losing rigor.

Rigor toggle:
Strict: if KPIs or DoD are missing, the GPT asks again before drafting.
Relaxed: proceed with assumptions and call out the gap.

---

## 6. File targets are contracts (why this matters so much)

Copilot and similar tools are great at transforming code in known locations and risky at guessing where things should go. Requiring exact output paths in every objective:
* Prevents assistants from spraying changes across the repo.
* Makes diffs predictable and reviewable.
* Forces you to think in artifacts rather than vague goals.
* Enables safe automation (CI, scripts) keyed to known locations.

Rules of thumb:
* One objective = one owner = one primary artifact.
* Always list exact output paths under “File Targets.”
* If the path is wrong, update the objective first; don’t let code define the contract after the fact.

---

## 7. Minimal validation: small schemas, big payoff

The method doesn’t need heavy process. It needs a few must-haves that catch drift:
* Objective schema: id, name, owner, outputs (exact paths), acceptance\_criteria.
* Milestone schema: id, name, deliverable (optionally goal, dependencies).
* PromptSpec schema: objective\_id, context\_files, instructions, file\_targets (optionally constraints, deliverables, acceptance\_criteria).

This lets the GPT self-correct and lets CI reject malformed specs. It’s enough structure to be reliable, not enough to be annoying.

---

## 8. Day-to-day usage (solo)

1) Kickoff (Report). In the GPT: “Start a new project: <title>. Create the Comprehensive Report (mode: deep, rigor: strict). Ask questions first.” Answer once; accept the generated file.
2) Plan (Milestones). “Define 3 milestones (deep, strict). Each must end in a usable deliverable with a one-step verification.”
3) Scope (Objectives for current milestone). “Expand Milestone 1 into 3 XS objectives (deep, strict). One owner, one primary artifact with exact file targets; include a single verification command.”
4) Build (Prompt). “Create the PromptSpec for Objective <ID> and render the Copilot prompt (strict schema conformance).”
5) Implement with Copilot. Start a new Copilot chat. Point it to three files (report, milestones, current objective). Ask it to summarize file targets, acceptance criteria, and propose a single next action before coding. Approve or correct; run the verify command.

If Copilot drifts: post a tiny “mini-pack” reminder that lists current objective, file targets, acceptance criteria, and the single next action. Reserve full context packs for rare resets.

---

## 9. Day-to-day usage (team)

- **Ownership:** one objective, one owner. If more people are needed, split objectives.
- **Reviews:** check against three micro-rubric items—primary artifact path is exact, acceptance criteria are testable, and a verification command exists.
- **Changes:** if a decision changes scope, update the single source of truth (objective or milestone) and then regenerate the prompt.
- **Hand-offs:** use the pointer prompt or a 100–120 word mini-pack, not long narratives.

---

## 10. Scoping heuristics (XS/S/M)

**XS (30–90 minutes):** one script/file, trivial config, no new dependencies, one verify command.  
**S (half day):** a small runner/module plus trivial tests, 2–4 files.  
**M (one day):** several files, light refactor, a slightly wider config surface.

If an objective exceeds a sitting, split it. The biggest failure mode is over-stuffed objectives.

---

## 11. Success criteria and guardrails (how to write them well)

**KPIs** are how you declare victory; **guardrails** are what you must not break.  
Write one to three KPIs and at least one guardrail.

### Examples for an RL mini-project:

- **KPI:** reach ≥95% success on DoorKey-8x8 in ≤30 minutes wall-clock on a single A100.
- **KPI:** five-seed reproducibility with mean ± std reported.
- **Guardrail:** peak GPU memory ≤8 GB; training script must run without error on CPU for a 1k-step smoke test.

Make them measurable and testable. Your verify commands should reflect them as early as possible.

---

## 12. Quality gates (micro-rubrics)

The method uses tiny, decisive gates to prevent drift:

- **Report:** motivation and deployment clear in ≤10 lines; at least one KPI and one guardrail; explicit in-scope and out-of-scope.
- **Milestone:** goal reduces uncertainty; tangible deliverable has a path; DoD is verifiable with one step/command.
- **Objective:** one owner; one primary artifact with exact file targets; objective, testable acceptance criteria; single verification command.
- **Prompt:** references context files; lists deliverables and exact targets; acceptance criteria match the objective.

Failing any gate triggers one of two actions: revise the artifact or proceed with an **ASSUMPTIONS** block and record **OPEN QUESTIONS**.

---

## 13. Anti-patterns to avoid

* Starting code before the objective exists and names file targets.
* Packing multiple unrelated deliverables into a single objective.
* Vague acceptance criteria (“works well”) or missing verification commands.
* Copying the same fact into multiple docs; change one and forget the other.
* Baking architecture into the report; designing too early.
* Blocking because of unknowns rather than proceeding with assumptions.

---

## 14. Working with Copilot (practicalities)

Default prompt to begin a new Copilot chat:
Use these files as your sole context:
– ai-context/00\_project\_report.md
– ai-context/milestones.md
– ai-context/milestone\_<k>/objective\_<j>.md
Task: Implement Objective <j>. Only modify the files listed under “File Targets”. Before coding, list the File Targets you will write to, the Acceptance Criteria you must satisfy, and your single next action.

Why this works:
* It forces Copilot to read the contracts.
* It creates a quick confirmation loop before edits.
* It protects the rest of the repo.

If Copilot loses context, re-issue the pointer prompt or paste a 100–120 word mini-pack; don’t flood the chat window.

---

## 15. When to add architecture (and when not to)

Write an Architecture Brief at the end of the first milestone only if two or more are true:
* There’s an external dependency or interface you must design against.
* Non-functional requirements (latency, cost, privacy, availability) have become meaningful.
* You’ve confirmed multiple components with distinct responsibilities.
* A decision with several viable options exists and trade-offs matter.

Expand to an Architecture Overview in early milestone two only if the brief’s decisions need elaboration. Use ADRs sparingly: capture a decision only if there were real alternatives and the consequences are worth remembering.

---

## 16. Versioning, CI, and change management

**SemVer** for template/schema changes is enough (v0.1.0, v0.2.0).  
A tiny CI job can validate any PromptSpec JSON against the schema and fail fast on PRs.  
Keep a brief changelog. Backward compatibility is nice but not mandatory for templates; clarity is more important.

---

## 17. Privacy, publication, and knowledge hygiene

Keep sensitive details out of the GPT’s Knowledge. The canonical files live in your repo; the GPT refers to them by path. If you publish a public GPT, link to your GitHub repo and upload only non-sensitive templates/schemas to Knowledge.

---

## 18. Example lifecycle (RND on MiniGrid)

A. Report declares motivation (“fast RND baseline”), deployment (single GPU), success (≥95% success ≤30 min; reproducibility; memory guardrail), in/out scope.
B. Milestones set three phases: M1 runnable slice, M2 pass criteria, M3 report and tiny ablations.
C. Objectives for M1: O1 repo skeleton and env harness; O2 RND module shapes and intrinsic reward; O3 training runner and logging. Each with exact file targets and a verification command.
D. PromptSpec for O1 generates a Copilot prompt; Copilot implements outputs strictly at the specified paths; you run the verify command; update ASSUMPTIONS and OPEN QUESTIONS.
E. Iterate through O2 and O3; mark M1 done; decide if an Architecture Brief is warranted.

---

## 19. What to measure (to prove the method helps)

- **Lead time:** idea → first runnable thing (target hours, not days).
- **Rework rate:** number of times file targets changed after implementation started (should drop).
- **Assistant precision:** percentage of changes confined to file targets (should be near 100%).
- **Verification pass rate:** objectives that pass their verification command on first run.
- **Reproducibility:** variance across seeds/runs; time to reproduce M1 run from scratch.

---

## 20. Final thoughts

The value is not in the documents themselves; it’s in the rhythm they create. You ask hard questions at the top, capture the minimum needed to proceed, and then you move. Each artifact is tiny and useful; each handoff to an assistant is safe because the contract is explicit. If you keep the rules light—clarify-first, paths are contracts, ship small—you’ll move faster, make better decisions, and avoid the slow grind of rework.

If you ever feel the process getting heavy, cut it back. If you feel drift, add a question or a schema field. The method is a scaffold, not a ceremony.
