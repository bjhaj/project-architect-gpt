# Project Architect GPT — Starter Pack

Turn fuzzy AI ideas into structured, reproducible work: Report → Milestones → Objectives → one-by-one Prompts.

## Why this exists

- **High → low, not hype → code.** Business context first, prompts last
- **Clarify-first approach.** Ask questions, then draft; proceed with explicit **ASSUMPTIONS** and **OPEN QUESTIONS** when info is missing
- **Paths are contracts.** Every objective names exact file targets so Copilot edits the right files
- **Light validation.** JSON outputs conform to tiny schemas; human docs follow simple templates
- **Architecture is deferred.** Add design docs only if/when they're needed (post–M1)

## Quickstart

**Option A — Use this as a template repo**
1. Click **Use this template** on GitHub to create your project
2. Keep the `ai-context/` folder at the repo root

**Option B — Submodule into an existing project**
```bash
git submodule add https://github.com/<your-username>/project-architect-gpt ai-context
```

**ChatGPT flow with Project Architect GPT:**
1. "Start a new project: <TITLE>. Create the Comprehensive Report (mode: deep, rigor: strict)."
2. "Define 3 milestones (each ends with a usable deliverable and DoD)."
3. "Expand Milestone 1 into XS objectives with exact file targets and a single verification command."
4. "Create the PromptSpec for Objective 1 and render the Copilot prompt."

**Copilot pointer prompt (copy/paste this block):**
```
Use as context:
- ai-context/00_project_report.md
- ai-context/milestones.md
- ai-context/milestone_<k>/objective_<j>.md

Task: Implement Objective <j>. Only modify the files listed under "File Targets".
Before coding, list the File Targets, the Acceptance Criteria, and your single next action.
```

## What's inside

```
ai-context/
├── templates/
│   ├── 00_project_report.template.md    # business/context-only report
│   ├── milestones.template.md           # phases; each ends with deliverable + DoD
│   ├── objective.template.md            # one owner, one primary artifact, exact paths
│   ├── promptspec.template.json         # machine spec used to render Copilot prompt
│   ├── copilot_prompt.template.md       # ready-to-paste Copilot prompt
│   ├── readme_ai_context.template.md    # optional context documentation
│   └── _partials/
│       ├── assumptions_block.md         # insert when proceeding with defaults
│       └── open_questions_block.md      # track unresolved decisions
└── schema/
    ├── milestone.schema.json
    ├── objective.schema.json
    └── promptspec.schema.json
```

## How to use the flow

**Step 1: Report** → `ai-context/00_project_report.md`
- Motivation, deployment space, success criteria, in/out scope
- No architecture here

**Step 2: Milestones** → `ai-context/milestones.md`
- Each has a goal, tangible deliverable (with a path), DoD, and one verification step

**Step 3: Objectives** → `ai-context/milestone_<k>/objective_<j>.md`
- One owner; one primary artifact; **exact file targets**; acceptance criteria; verify command

**Step 4: Prompt** → use `promptspec.template.json` + `copilot_prompt.template.md`
- PromptSpec JSON validates against schema; paste rendered Copilot prompt

**Note on missing information:**
When details are missing, proceed and record them under **ASSUMPTIONS** (top) and **OPEN QUESTIONS** (end). Keep shipping.

## Example (optional)

See `examples/` folder for a small, filled-in project (e.g., RND for Sparse-Reward MiniGrid) showing:
- Report, milestones, and the first objective
- A PromptSpec and the rendered Copilot prompt
- Minimal repo files and verify commands

## Philosophy (short version)

- **Clarity > cleverness.** Favor simple, readable specs and commands
- **Small steps.** XS/S objectives finish in a sitting; split if they grow
- **Single source of truth.** Facts live in one place; link, don't duplicate
- **Safety rails.** Schemas and exact paths make Copilot predictable
- **Assumptions explicit.** Document what you don't know to keep moving
- **Verification built-in.** Every deliverable has a single command to check it works

## Versioning & CI (optional)

- Follow SemVer for template/schema changes (v0.1.0, v0.2.0, …)
- Add a tiny CI job to validate PromptSpecs against `ai-context/schema/promptspec.schema.json`
- Track notable changes in `CHANGELOG.md`

## Contributing

Issues and PRs welcome—keep changes minimal and focused on usability.
Please avoid adding heavyweight tooling or opinionated stacks.

## License

- Templates & code: MIT
- Documentation: CC BY 4.0

## Credits & Links

- Companion GPT: **Project Architect GPT** (use with these templates)
- Questions? Open an issue or start a discussion in this repo
