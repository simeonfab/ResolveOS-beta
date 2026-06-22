---
type: context
scope: global
owner: ResolveOS
version: 0.1
status: draft
---

# Context Loading Rules

## Purpose

Define how ResolveOS and project repositories should load context before work begins.

This file prevents agents, assistants, and Codex from working from memory when required files are available or required.

## Core Rule

Do not proceed from memory when required context files are missing.

If a required role file, project context file, briefing file, current focus file, or ticket file is unavailable, stop and ask for it or explicitly state what is missing.

## Loading Order

Load context in this order:

```text
1. ResolveOS file standards
2. ResolveOS metadata standards
3. ResolveOS migration and governance rules
4. ResolveOS context-loading rules
5. ResolveOS role file
6. ResolveOS skill file
7. Project context
8. Current focus
9. Briefing
10. Ticket / task
11. User's current instruction
```

## Precedence Rules

More specific context normally overrides broader context.

Use this precedence order:

```text
Current user instruction
    ↓
Ticket / task
    ↓
Briefing
    ↓
Current focus
    ↓
Project context
    ↓
ResolveOS skill
    ↓
ResolveOS role
    ↓
ResolveOS context
    ↓
ResolveOS governance
    ↓
ResolveOS standards
```

However, user instructions, tickets, and project context must not silently override global safety, source-of-truth, or governance rules.

If there is a conflict, flag it for review.

## Required Inputs

Before role-based work begins, the assistant or agent should have:

- Relevant ResolveOS role file.
- Relevant ResolveOS skill file if a specific task method is needed.
- Project context file.
- Current focus file when available.
- Briefing file when available.
- Ticket or task file when working on specific delivery work.

## Missing Context Behaviour

If a required file is missing:

1. Stop.
2. Name the missing file or context type.
3. Explain why it is needed.
4. Ask for it or proceed only with an explicit limitation.

Do not pretend the context was loaded.

Do not infer missing project facts from memory.

Do not create implementation output that depends on missing files.

## Role-Based Chat Startup

Every role-based chat should begin by referencing:

- The role prompt or role file.
- The current project context.
- The current focus file.
- The current ticket or briefing, if relevant.

Role prompts should not duplicate ticket descriptions.

Role prompts should reference:

- The relevant role file.
- The current Jira or task ticket.
- The current briefing file.
- The current focus file.

## Expansion Rules

The assistant may expand beyond the loaded files only when:

- Performing a design review.
- Resolving a blocker.
- Handling architecture risk.
- Correcting a failed implementation.
- The user explicitly asks for broader reasoning.

When expanding beyond loaded files, distinguish clearly between:

- Loaded source context.
- Reasoned inference.
- Recommendation.
- Open question.

## Project Override Rules

Project repositories may define project-specific overrides.

Overrides must:

- Be explicit.
- Be documented.
- Explain why the global rule is not sufficient.
- Avoid copying global content unnecessarily.

## Context Drift Rules

If a file appears outdated, inconsistent, or contradicted by newer context:

- Flag the contradiction.
- Do not silently choose one version.
- Prefer canonical source-of-truth files where defined.
- Ask for review where the correct source is unclear.

## Codex Usage Rules

When Codex is asked to work:

- It should read relevant standards before creating files.
- It should read source-of-truth rules before moving or duplicating content.
- It should read migration guardrails before extracting content.
- It should avoid broad rewrites unless explicitly requested.
- It should produce reviewable diffs.

## Completion Requirement

Context loading is complete enough when:

1. Required global standards are known.
2. Required role and skill guidance is known.
3. Required project context is known.
4. Required current focus or ticket context is known.
5. Missing context has been flagged.
6. Conflicts have been surfaced rather than hidden.
