---
type: standard
scope: global
owner: ResolveOS
version: 0.1
status: draft
related_context:
  - 01-context/running-context.md
  - 01-context/missing-context-behaviour.md
related_workflows:
  - 05-workflows/project-initiation.md
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/implementation-review-loop.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/project-readiness.md
  - 06-governance/architecture-decisions.md
related_skills:
  - 03-skills/information-architecture.md
review_required: true
---

# ResolveOS Entrypoint

## Purpose

Provide the single authoritative entrypoint for ResolveOS interactions.

This file determines:

- what type of interaction is occurring
- which files must be loaded
- which workflow governs the interaction
- when the assistant must stop because required context is missing

This file does not duplicate workflow logic, role behaviour, skill procedure, governance rules, project strategy, roadmap detail, ticket scope, implementation instructions, or validation criteria.

## When To Use

Use this file before every ResolveOS interaction.

ChatGPT Project instructions, project prompts, role prompts, and assistant startup messages should reference this file instead of copying ResolveOS routing behaviour.

## Required Startup Behaviour

Before responding, the assistant must:

1. Classify the interaction using the routing table.
2. Load every required file listed for that interaction type.
3. Follow the governing workflow named for that interaction type.
4. Use project source-of-truth where available.
5. Apply `03-skills/information-architecture.md` before writing to documentation, workspace, knowledge-base, project-management, repository, or local storage tools.
6. Apply the missing-context response rules if required context is unavailable.

Do not proceed using assumptions when required context exists but has not been loaded.

Do not substitute chat memory for a required file.

Do not ask the user to choose a workflow when the routing table determines one.

## Project Instruction Text

Use this exact text for ResolveOS ChatGPT Project instructions:

```text
Always begin by loading and following 00-system/resolveos-entrypoint.md.

Do not bypass it.
```

## Classification Rules

Classify by the user's current intent.

The example phrases in the routing table are illustrative only.

Users do not need to use exact trigger phrases.

Classify based on:

- user intent
- available context
- requested outcome
- the work the user appears to be asking ResolveOS to govern

Do not force users to speak ResolveOS terminology.

If multiple interaction types apply, choose the first matching type in the routing table unless the user explicitly states a narrower intent.

If classification is unclear:

1. Load `01-context/missing-context-behaviour.md`.
2. State that the interaction type is unclear.
3. Ask the smallest clarification needed to classify the interaction.
4. Stop until the interaction type can be classified.

## Routing Table

| Interaction type | Examples | Required files | Governing workflow |
| --- | --- | --- | --- |
| New Project | "I have an idea", "I want to build", "I want to start" | `05-workflows/project-initiation.md`, `06-governance/project-readiness.md`, `06-governance/source-of-truth-rules.md` | `05-workflows/project-initiation.md` |
| Existing Project Adoption | "Here is my repo", "Here is my Notion", "Review this project" | `05-workflows/project-initiation.md`, `06-governance/project-readiness.md`, `06-governance/source-of-truth-rules.md` | `05-workflows/project-initiation.md` |
| Existing Project Continuation | "Continue this project", "We were working on", "What's next" | `05-workflows/project-initiation.md`, `01-context/running-context.md`, `06-governance/project-readiness.md`, `06-governance/source-of-truth-rules.md` | `05-workflows/project-initiation.md` |
| Project Status Request | "Where are we?", "Status update", "Summarise the project" | `01-context/running-context.md`, `06-governance/project-readiness.md` | `05-workflows/project-initiation.md` |
| Product Strategy | "Pricing", "Positioning", "Market validation", "Roadmap", "JTBD" | `05-workflows/project-initiation.md`, `01-context/running-context.md`, `06-governance/project-readiness.md` | `05-workflows/project-initiation.md` |
| Planning / Prioritisation | "Roadmap", "Backlog", "Priorities", "Sequencing" | `01-context/running-context.md`, `06-governance/source-of-truth-rules.md` | `05-workflows/project-initiation.md` |
| Requirements / Analysis | "User stories", "Acceptance criteria", "Functional requirements", "Process mapping" | `05-workflows/project-initiation.md`, `01-context/running-context.md` | `05-workflows/project-initiation.md` |
| Architecture / Technical Strategy | "Architecture", "Technical design", "System design", "Integration strategy" | `06-governance/architecture-decisions.md`, `01-context/running-context.md`, `06-governance/source-of-truth-rules.md` | `05-workflows/project-initiation.md` |
| Implementation Planning | "Break this into tasks", "Prepare implementation", "Create engineering brief" | `01-context/running-context.md`, `06-governance/source-of-truth-rules.md`, `06-governance/architecture-decisions.md` | `05-workflows/ticket-to-implementation.md` |
| Validation / Testing | "QA", "Validation", "Review", "Test strategy" | `06-governance/project-readiness.md`, `01-context/running-context.md` | `05-workflows/implementation-review-loop.md` |
| Commercial Strategy | "Sales", "Go-to-market", "Monetisation", "Customer acquisition" | `01-context/running-context.md`, `06-governance/project-readiness.md` | `05-workflows/project-initiation.md` |
| Information Architecture / Storage | "Save this", "Store this", "Put this in Notion", "Save this feedback", "Store these risks", "Save COMBO-INTEL-001", "Create documentation from this conversation" | `03-skills/information-architecture.md`, `06-governance/source-of-truth-rules.md`, `01-context/missing-context-behaviour.md` | `03-skills/information-architecture.md` |
| General Project Guidance | "Project management questions", "Delivery questions", "Team questions" | `05-workflows/project-initiation.md`, `01-context/running-context.md` | `05-workflows/project-initiation.md` |

## Required Context Handling

Required files are mandatory.

Before answering:

1. Check that each required file exists.
2. Load each required file.
3. Identify any project-owned source-of-truth needed by the loaded workflow.
4. Load available project-owned source-of-truth before making project-specific claims.
5. If required context is missing, use the tiered missing-context response below.

Do not invent project facts.

Do not proceed as though context was loaded when it was not loaded.

Do not make project-specific recommendations, claims, readiness judgements, implementation statements, validation claims, evidence claims, or decision claims from missing context.

## Missing-Context Response

When required context is missing, choose one of these responses.

### A. Ask For The Smallest Missing Input

Use this when the request needs project-specific context and the smallest unblocker can be named.

Ask only for the missing input needed to continue safely.

### B. Provide Clearly Caveated General Guidance

Use this only when the request is low-risk and useful general guidance can be given without pretending to know the project.

The response must clearly state:

- what context is missing
- that the answer is general guidance only
- that project-specific recommendations require the missing context

### C. Stop

Stop when proceeding would risk:

- inventing project facts
- misrepresenting project state
- making project-specific recommendations without source context
- claiming evidence, decisions, readiness, or implementation state that has not been loaded
- changing project direction without authoritative context

When stopping, use this format:

```text
Blocked: required context is missing.

Missing:
- [file or source]

Why it matters:
- [short reason]

Next step:
- [smallest unblocker]
```

## Source-Of-Truth Behaviour

Use `06-governance/source-of-truth-rules.md` when project source ownership matters.

Project repositories and project source systems own project-specific facts, including product strategy, roadmaps, active tickets, current planning state, decisions, architecture, validation evidence, commands, environments, and constraints.

ResolveOS owns reusable routing, workflows, roles, skills, templates, context-loading behaviour, and governance.

Do not copy project facts into ResolveOS global files.

Do not create a competing planning, decision, architecture, ticket, or validation source when a project source of truth exists.

Do not create new documentation or storage locations when an existing canonical page, section, database, ticket, folder, file, or workspace structure owns the information.

When a user asks to save, store, document, capture, or preserve information, apply `03-skills/information-architecture.md` before using tools.

## Workflow Boundary Rules

This entrypoint only routes work.

After the interaction is classified and required files are loaded, follow the governing workflow.

Do not restate workflow steps from this file.

Do not use this file to:

- approve implementation
- write tickets
- define acceptance criteria
- perform QA sign-off
- create roles
- create skills
- create templates
- create workflows
- create governance rules
- override source-of-truth rules
- override project-specific context
- replace running context
- replace architecture decisions

## Anti-Patterns

Do not:

- bypass this entrypoint
- answer before classifying the interaction
- proceed before loading required files
- infer workflow choice when the routing table is deterministic
- rely on chat memory when required context exists
- ask the user to choose internal ResolveOS files
- duplicate workflow logic in project instructions
- duplicate role behaviour in project instructions
- duplicate governance rules in project instructions
- continue governed project-specific work when required context is missing
