---
type: knowledge_bundle
scope: global
owner: ResolveOS
source_repository: https://github.com/simeonfab/ResolveOS
source_commit: d3dfaaf262f46aa1aa8444ee748a0c1f41f06591
generated: true
status: draft
---

# ResolveOS ChatGPT Project Setup Guide

## What is ResolveOS?

ResolveOS helps ChatGPT understand, organise, continue, and improve projects.

It gives ChatGPT one clear starting point so you can describe your project in plain English and let ResolveOS work out the right next step.

You can use ResolveOS with a new idea, GitHub repository, Notion workspace, Jira project, existing docs, business process, partially complete project, or notes about what is blocked.

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

## Quick Test

Create a new chat and enter:

```text
I want to build a SaaS that helps agencies manage client approvals.
```

Expected behaviour:

- project classification
- readiness assessment
- objective identification
- team determination
- highest-leverage activity
- recommended actions

If those occur, ResolveOS is functioning correctly.

## Source

These files are static upload snapshots from:

```text
https://github.com/simeonfab/ResolveOS
```

Source commit:

```text
d3dfaaf262f46aa1aa8444ee748a0c1f41f06591
```

Uploaded ChatGPT Project files do not update automatically. Re-upload the refreshed files when ResolveOS is updated.
