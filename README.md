---
type: knowledge_bundle
scope: global
owner: ResolveOS
source_repository: https://github.com/simeonfab/ResolveOS
source_commit: 80dfe965e5027fbd1d7b80fcef226bfc40184411
generated: true
status: draft
---

# ResolveOS ChatGPT Project Setup Guide

## What is ResolveOS?

ResolveOS helps you turn ideas and messy project context into a clear plan of action.

It works out what state your project is in, what matters now, what team or specialist support is needed, what is blocked, and how to move forward.

You can use ResolveOS with a new idea, GitHub repository, Notion workspace, Jira project, existing docs, business process, partially complete project, or notes about what is blocked.

ResolveOS gives your AI assistant one clear starting point, but the guidance is not limited to AI-only work. A recommended role can be handled by you, a real team member, a specialist chat, an AI assistant, a coding agent, an engineer, or a consultant.

## What ResolveOS Will Do For You

ResolveOS helps you:

- organise scattered project context into a usable operating model
- identify the current objective, reliable context, missing information, risks, and blockers
- understand whether the project is ready for discovery, planning, implementation, or validation
- see the Recommended Team for the current stage without needing to understand internal role files
- get practical next actions, mitigations, prompts, and handoffs instead of static status reports
- continue stale or interrupted projects without restarting from memory
- store feedback, notes, handoffs, and conversation outputs into the right existing documentation structure where possible

ResolveOS should keep internal framework complexity internal. You should not need to choose workflows, file-loading rules, governance hierarchy, ADRs, or internal routing.

## How To Get The Most Out Of ResolveOS

Use ResolveOS with real project context.

Tell it what you are trying to achieve, whether you are working solo or with a team, and where the current source of truth lives if you know it.

Useful context includes:

- repo links or pasted repository context
- Jira, Notion, GitHub Issues, Azure DevOps, roadmap, or planning links
- current tasks, blockers, decisions, risks, feedback, or validation notes
- a latest handoff, current-focus note, running context, or completion report

If you do not know which source is authoritative, say that. ResolveOS should help identify the source of truth and give a practical path forward.

When you ask ResolveOS to save, store, document, or put something in Notion or another workspace tool, it should avoid random top-level pages, documents, files, folders, or databases. It should identify the information type, storage model, source owner, and location, then report where it stored the content and why.

## Recommended Team

ResolveOS may show a Recommended Team when role coverage matters.

It should show only the roles needed now, briefly explain why, and say clearly if no additional specialist role is needed.

User-facing labels may be clearer than internal ResolveOS role file names. Examples include Product Strategy Lead, Technical Strategy Lead, Implementation Engineer, QA / Validation Lead, Business Analyst, and Feedback Curator. These labels map to existing ResolveOS roles, skills, or workflows; they do not create duplicate roles.

If a specialist role should act now, ResolveOS should generate the controlling prompt or handoff immediately unless you ask it not to.

## Setup

### Step 1: Create A ChatGPT Project

Create a new ChatGPT Project and give it a clear project name.

### Step 2: Upload Files

Upload:

- `README.md`
- `01_RESOLVEOS_CORE.md`
- `02_RESOLVEOS_CONTEXT_AND_LOADING.md`
- `03_RESOLVEOS_ROLES.md`
- `04_RESOLVEOS_SKILLS_AND_WORKFLOWS.md`
- `05_RESOLVEOS_TEMPLATES.md`
- `06_RESOLVEOS_GOVERNANCE.md`

### Step 3: Paste Project Instructions

Paste this exact text into the ChatGPT Project instructions field:

```text
Always begin by loading and following 00-system/resolveos-entrypoint.md.

Do not bypass it.
```

### Step 4: Start Chatting Normally

Start with a plain-English message, for example:

```text
I want to use ResolveOS for this project. Here is what I have and what I want help with: ...
```

ResolveOS should identify whether your project is new, existing, or already in progress. It should ask only for missing essentials and recommend the highest-leverage activity plus practical next actions.

## Example Things You Can Ask

- New project: "I have an idea for a project and want help turning it into a clear plan."
- Existing project adoption: "Here is my GitHub repo / Notion workspace / Jira project. Help me understand what exists and what should happen next."
- Existing project continuation: "Continue this project and tell me where we are, what is blocked, and what the highest-leverage activity is."
- Status: "Where are we with this project?"
- Planning: "Help me prioritise the roadmap and decide what to do next."
- Team setup: "Tell me the Recommended Team for this stage and generate any specialist prompts needed now."
- Readiness: "Assess whether this is ready for implementation or validation and give me mitigations for anything that is not ready."
- Stale chat restart: "Show a Project Snapshot from the latest reliable context and give me the practical plan forward."

## Quick Test

Create a new chat and enter:

```text
I want to build a SaaS that helps agencies manage client approvals.
```

Expected behaviour:

- project classification
- readiness assessment
- objective identification
- Recommended Team determination
- highest-leverage activity, only if genuinely meaningful
- recommended actions
- mitigations for material gaps, risks, or blockers
- prompt or handoff generation when a specialist role should act now

If those occur, ResolveOS is functioning correctly.

## Source

These files are static upload snapshots from:

```text
https://github.com/simeonfab/ResolveOS
```

Source commit:

```text
80dfe965e5027fbd1d7b80fcef226bfc40184411
```

Uploaded ChatGPT Project files do not update automatically. Re-upload the refreshed files when ResolveOS is updated.
