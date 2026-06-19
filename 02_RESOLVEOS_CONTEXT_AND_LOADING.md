---
type: knowledge_bundle
scope: global
owner: ResolveOS
source_repository: https://github.com/simeonfab/ResolveOS
source_commit: 6a35ddf63574902deb53fb7aff11f45516e3fac6
generated: true
generated_date: 2026-06-19
included_paths:
  - 01-context/context-loading-rules.md
  - 01-context/missing-context-behaviour.md
  - 01-context/project-loading-rules.md
  - 01-context/role-loading-rules.md
  - 01-context/running-context.md
  - 01-context/startup-context.md
---

# Source: 01-context/context-loading-rules.md

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

---

# Source: 01-context/missing-context-behaviour.md

---
type: context
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration-review.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
  - docs/project-context/implementation-workflow.md
  - docs/ai-core/operational-clarity-framework.md
  - docs/ai-role-prompts/implementation-engineer-prompt.md
  - docs/ai-role-prompts/technical-strategy-lead-prompt.md
  - docs/ai-role-prompts/strategic-product-director-prompt.md
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
related_governance:
  - 06-governance/codex-working-rules.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/extraction-migration-guardrails.md
  - 06-governance/architecture-decisions.md
related_skills:
  - 03-skills/ticket-writing.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/user-feedback-processing.md
  - 03-skills/completion-reporting.md
review_required: true
---

# Purpose

Define what assistants, agents, Codex sessions, workflows, and roles should do when required context is missing, incomplete, stale, conflicting, inaccessible, or ambiguous.

Missing context behaviour exists to preserve ResolvePM's stop-and-explain discipline: do not work from memory when required context is missing, do not invent missing facts, do not hide uncertainty, and do not force work through unsupported assumptions.

This file is context governance. It is not a workflow, template, skill, or role.

# When To Use

Use this file when required context is:

- missing
- incomplete
- inaccessible
- stale
- contradictory
- ambiguous
- unsupported by evidence
- unavailable from the expected source of truth

Use it before:

- answering from incomplete evidence
- writing or refining tickets
- writing or reviewing acceptance criteria
- processing ambiguous feedback
- planning implementation
- changing code
- validating work
- reporting completion
- escalating blockers

# Inputs

Useful inputs include:

- admin instruction
- task, ticket, source item, briefing, or approved scope
- required ResolveOS context files
- required role file
- required skill or governance file
- project context
- current focus
- acceptance criteria
- requirements, assumptions, dependencies, and non-goals
- repository state, check output, or validation evidence where relevant
- source-system comments or blocker notes
- known conflicts between sources

If an input required for safe work is unavailable, classify the missing context before acting.

# Missing Context Principles

## Missing Context Is A Blocker By Default

Missing context is a blocker unless an approved fallback rule exists.

Do not treat missing context as permission to guess.

Do not continue from memory when the task depends on current source files, project context, tickets, requirements, acceptance criteria, credentials, configuration, repository state, or admin decisions.

## Evidence Over Invention

Prefer evidence over invention.

If the source context does not support a claim, say so.

Do not invent missing facts, requirements, acceptance criteria, stakeholder intent, schema fields, project decisions, roadmap direction, implementation details, validation results, or completion claims.

## Explicit Uncertainty

Do not hide uncertainty.

When evidence is incomplete:

- state what is known
- state what is missing
- state what is inferred
- state what needs admin review

Do not present inference, memory, or assumption as fact.

## Stop And Explain

If blocked:

- stop
- explain the blocker clearly
- explain why continuing would be unsafe or unsupported
- state what information, credential, config, source file, or admin decision is needed
- suggest the highest-leverage unblocker or follow-up action

Do not silently work around blockers.

## Current Ticket First

When work is tied to delivery, implementation, validation, or ticketing, start from the current ticket, source item, task, or approved scope.

Do not start future tickets, future epics, or adjacent work to compensate for missing current context.

# Context Classification

Classify missing or weak context before deciding how to proceed.

| Context State | Meaning | Default Behaviour |
| --- | --- | --- |
| Missing | Required context is not available. | Stop, identify the missing source, and ask for or locate it. |
| Incomplete | Some required context exists, but key details are absent. | Proceed only if the missing detail does not affect scope, safety, acceptance, or truthfulness. |
| Inaccessible | Context exists but cannot be accessed. | Use an approved fallback only if one exists; otherwise ask for the context. |
| Stale | Context may no longer reflect current project, ticket, repository, or decision state. | Flag staleness and verify before relying on it. |
| Contradictory | Two or more loaded sources conflict. | Follow precedence rules or escalate for admin review. |
| Ambiguous | The request or source context supports multiple meanings. | Ask a direct clarification question or proceed with explicit limitation only when safe. |
| Unsupported | A claim, requirement, or assumption has no source evidence. | Do not turn it into fact, scope, or acceptance criteria. |
| Blocked | Safe progress requires missing context, a decision, a prerequisite, credentials, config, or source access. | Stop and report the blocker. |

# Missing Context Behaviour

When context is missing:

1. Identify the exact missing context.
2. Explain why it matters.
3. Identify whether an approved fallback exists.
4. If no approved fallback exists, stop and ask for the missing context or admin decision.
5. If a fallback exists, state the fallback and its limitation before using it.
6. Preserve traceability to the source that is missing, unavailable, or substituted.

Do not make vague statements such as "context is unclear" when the missing item can be named.

For missing tickets or source items:

- ask for the ticket description or relevant comments if source-system access is unavailable
- do not guess missing acceptance criteria
- do not start implementation from an epic alone when child implementation tickets are missing

For missing requirements:

- identify the missing requirement, business rule, stakeholder detail, assumption, dependency, or open question
- do not make vague requirements look ready by formatting them neatly
- do not invent requirements

For missing acceptance criteria:

- do not guess missing acceptance criteria
- draft criteria only if clearly marked for review and supported by available context
- do not claim completion when acceptance cannot be verified

For missing dependencies:

- stop and identify the missing prerequisite
- do not retry a blocked dependent ticket until the prerequisite is complete
- do not invent schema, data fields, integrations, configuration, or implementation paths

For missing project context:

- do not import ResolvePM doctrine into another project
- use only loaded project context
- ask for project-specific strategy, roadmap, architecture, current focus, or local constraints when the decision depends on them

For missing role context:

- follow `01-context/role-loading-rules.md`
- do not invent role behaviour from a role name
- do not infer behaviour from empty placeholders

# Clarification Rules

Ask for clarification when the answer affects:

- scope
- acceptance
- priority
- stakeholder impact
- product direction
- implementation feasibility
- architecture
- dependency ordering
- validation
- security
- configuration
- source-of-truth alignment

Questions should be direct and specific.

Do not ask the admin to restate full context when the source ticket, briefing, project context, or documentation already exists and is available.

If only one narrow fact is missing, ask for that fact.

If multiple facts are missing, group them into the smallest useful set.

If the task can safely proceed with a limitation, state the limitation clearly before proceeding.

# Escalation Rules

Escalate to admin when:

- required context is missing and no approved fallback exists
- sources conflict and precedence does not resolve the conflict safely
- the missing context affects product direction, roadmap meaning, product scope, acceptance intent, architecture, security, cost, deployment, or approval authority
- a project-specific override may be needed
- a role boundary conflict appears
- proceeding would require invented facts, fake functionality, fake state, or unsupported assumptions
- repeated failures create a loop

Escalate to Product Manager when missing context affects product execution scope, acceptance intent, user-facing outcome, or feedback-to-work decisions.

Escalate to Business Analyst when missing context affects requirements, business rules, assumptions, requirement traceability, or acceptance criteria clarity.

Escalate to QA Tester when missing context affects validation evidence, defect evidence, regression risk, or quality gate status.

Escalate to Technical Strategy Lead when missing context affects architecture, sequencing, dependency mapping, delivery governance, implementation order, schema, or deployment integrity.

Escalate to Implementation Engineer when missing context requires local code investigation, debugging, check execution, or implementation reporting.

Escalate to Strategic Product Director when missing context affects strategy, roadmap coherence, positioning, prioritisation, or whether something should exist.

# Approved Fallback Rules

Fallbacks are allowed only when they are approved by ResolveOS governance, project context, or admin instruction.

Approved fallback behaviour includes:

- using approved briefing files when source-system access is unavailable
- using current loaded project context when it explicitly owns the decision
- using explicit limitations when answering a narrow question that does not depend on the missing context
- drafting for review when clearly labelled as draft and supported by available source context
- recommending a follow-up or prerequisite ticket instead of forcing current-scope implementation
- reporting partial or blocked status instead of claiming completion

Fallbacks must be explicit.

When using a fallback, state:

- what context is missing
- what fallback is being used
- why the fallback is allowed
- what limitation remains
- what would be needed to remove the limitation

Fallbacks must not:

- hide missing context
- invent acceptance criteria
- invent product or implementation facts
- create fake functionality
- imply validation, storage, ticketing, deployment, or completion happened when it did not
- override project source of truth

# Contradictory Context Handling

When sources conflict:

1. Identify the conflicting sources.
2. Apply the relevant migration or source-of-truth priority.
3. Preserve the contradiction in the output or completion report.
4. Escalate for admin review when the conflict affects scope, authority, strategy, architecture, acceptance, security, cost, or completion.

For migration work, use the migration priority supplied for the batch.

For project work, use source-of-truth rules:

- project-specific overrides and project context may override global ResolveOS behaviour for project-owned decisions
- ResolveOS standards and governance should not be overridden without explicit review
- active ticket, current focus, and approved scope govern current delivery work

Do not silently resolve contradictions by choosing the easier source.

# Stale Context Handling

Treat context as stale when it may no longer reflect:

- current repository state
- current ticket state
- current focus
- current architecture
- current project decision
- latest blocker or completion report
- latest admin instruction

When context may be stale:

- say what appears stale
- verify current state where practical
- ask for updated context when verification is not available
- avoid making irreversible or scope-changing decisions from stale context
- report any limitation if proceeding

Do not let documentation drift from reality.

If stale context reveals a documentation update need, report the update need. Do not create update-process rules here.

# Outputs

Missing-context handling may produce:

- missing context note
- explicit uncertainty statement
- blocker report
- clarification question
- escalation note
- approved fallback note
- contradiction note
- stale context note
- limitation statement
- traceability note
- suggested highest-leverage unblocker or follow-up action
- suggested prerequisite or follow-up ticket for review

Outputs should be plain, direct, and traceable.

Do not claim context was loaded, checked, verified, ticketed, implemented, tested, deployed, committed, or completed unless that happened.

# Anti-Patterns

Do not:

- work from memory when required context is missing
- invent missing facts
- invent requirements
- guess missing acceptance criteria
- infer stakeholder intent without source evidence
- infer product strategy from ResolvePM unless working in ResolvePM with that context loaded
- silently resolve contradictions
- hide stale context
- hide blockers
- silently work around blockers
- create fake functionality to satisfy unclear scope
- invent schema, data fields, integrations, credentials, configuration, validation evidence, or deployment state
- make vague requirements look ready by formatting them neatly
- claim completion when required context, checks, validation, or acceptance evidence is missing
- keep making random changes after repeated failure
- ask the admin to restate context that is already available and should be loaded
- use a fallback without naming it and stating its limitation

# Examples

## Missing Ticket

```text
Blocked:
- The current ticket or source item is missing.

Why it matters:
- The work depends on approved scope and acceptance criteria.

Highest-leverage unblocker:
- Provide the ticket description and relevant comments, or approve a clearly limited draft.
```

## Missing Acceptance Criteria

```text
Missing context:
- Acceptance criteria are not available.

Safe handling:
- Do not guess acceptance criteria.
- Draft criteria only if clearly marked for review and traceable to the available ticket goal.
```

## Contradictory Sources

```text
Contradiction:
- Project context says the feature is out of scope.
- The current ticket appears to request implementation.

Handling:
- Stop and ask for admin review because the conflict affects approved scope.
```

## Approved Fallback

```text
Missing context:
- Source-system ticket access is unavailable.

Approved fallback:
- Use the approved briefing file and pasted ticket comments.

Limitation:
- Completion cannot claim source-system ticket status was updated unless that update actually happens.
```

# Related Context

- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `migration-review.md`

# Related Governance

- `00-system/file-standard.md`
- `00-system/file-metadata-standard.md`
- `00-system/resolveos-migration-strategy.md`
- `00-system/ai-operating-principles.md`
- `06-governance/codex-working-rules.md`
- `06-governance/extraction-migration-guardrails.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred because they belong in future files:

- Project-root markers, repository path verification, and project-specific context loading belong in future `01-context/project-loading-rules.md`.
- Role selection and role-boundary loading details belong in `01-context/role-loading-rules.md`.
- Ticket-to-implementation blocker steps belong in a future workflow.
- Implementation review loop handling belongs in a future workflow.
- Full blocker report and completion report formats belong in future templates or existing completion-reporting skill.
- Documentation update timing labels belong in future update-process governance.

# Ambiguous Items For Admin Review

Admin review is needed for:

- Whether missing context should always stop execution, or whether some low-risk read-only answers may proceed with explicit limitations.
- Whether ResolveOS should define a formal stale-context age threshold or leave staleness to project context.
- Whether approved briefing files should always be valid fallbacks when source-system access is unavailable.
- Whether contradiction reports should use a future template or remain plain text.

---

# Source: 01-context/project-loading-rules.md

---
type: context
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration-review.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
  - docs/project-context/implementation-workflow.md
  - docs/ai-role-prompts/implementation-engineer-prompt.md
  - docs/ai-role-prompts/technical-strategy-lead-prompt.md
  - docs/ai-role-prompts/strategic-product-director-prompt.md
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/missing-context-behaviour.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/extraction-migration-guardrails.md
  - 06-governance/codex-working-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define how assistants, agents, workflows, and Codex sessions should identify, load, validate, and operate within project-specific context.

Project loading exists to keep ResolveOS global behaviour separate from project-owned doctrine, commands, terminology, tickets, roadmaps, architecture decisions, and local constraints.

This file is context governance. It is not a workflow, template, role, or skill.

# When To Use

Use this file whenever work depends on a specific project.

Use it before:

- answering project-specific questions
- loading project context
- applying project-specific overrides
- using project-specific terminology
- referencing project roadmap or tickets
- running project-specific commands
- validating an active project root
- comparing multiple projects
- migrating reusable behaviour out of a project
- deciding whether content belongs in ResolveOS or a project repository

Do not use this file to:

- define project strategy
- define project workflows
- create project templates
- replace project source-of-truth files
- import one project's doctrine into ResolveOS

# Inputs

Useful inputs include:

- admin instruction
- active project name or repository path
- project root markers
- project context files
- current focus
- active ticket, task, source item, or approved scope
- project roadmap, product vision, architecture, or strategy files
- project-specific ADRs or decisions
- project-specific commands and validation expectations
- project-specific terminology and domain rules
- ResolveOS context, role, skill, and governance files
- source-of-truth hierarchy and project overrides

If the active project is unclear, identify it before acting.

# Project Loading Principles

## Project Repositories Own Project Context

Project repositories own:

- product vision
- product strategy
- roadmaps
- project decisions
- active tickets
- domain-specific terminology
- project-specific workflows
- feature design
- architecture decisions
- user research
- project-specific constraints
- project-specific commands

ResolveOS owns reusable global behaviour. It must not become the home for one project's product doctrine, roadmap, local setup, ticket sequence, terminology, or implementation details.

## Current Project First

Load and operate within the current project before using older, adjacent, or remembered project context.

Do not mix project contexts.

Do not use ResolvePM project context to answer ResolveYGO questions, or ResolveYGO context to answer ResolvePM questions.

Do not infer project facts from memory when project files are available or required.

## Validate The Active Project

Before project-specific implementation, migration, refactoring, ticket completion, command execution, or governance decisions, confirm the active project and relevant project context.

Project-root validation should use project-owned markers rather than a hard-coded ResolvePM path.

Markers may include files or folders such as:

- repository metadata
- project entry instructions
- package or build files
- source folders
- docs folders
- project context folders
- project-specific config

Exact marker names belong to project context.

## Keep Project Doctrine Project-Owned

Do not import project-specific product doctrine into ResolveOS.

Do not globalise:

- product identity
- strategic filters
- roadmap themes
- ticket keys
- route names
- database schema
- deployment URLs
- local paths
- domain terminology
- release names
- provider configuration
- verification commands

Project-specific doctrine may be used when loaded from that project. It must not become a ResolveOS rule unless separately reviewed and proven reusable.

## Preserve Traceability

When using project context, keep the answer traceable to the loaded project file, ticket, briefing, decision, or command output.

If a conclusion depends on project context, name the source type or file where practical.

Do not present project-specific inference as global ResolveOS behaviour.

# Project Identification

Identify the active project before acting when:

- more than one project exists in the workspace
- the current directory does not clearly match the requested repository
- the admin names a repository or source repository
- the task depends on project-specific files
- the task involves implementation, migration, refactoring, ticketing, verification, or governance

Project identification may use:

- repository name
- current working directory
- git remote
- project root markers
- project context files
- admin instruction
- source file paths
- ticket prefixes where project-owned

If project identity is ambiguous, stop or proceed only as low-risk read-only analysis with explicit limitations under ADR-029.

# Context Precedence

Use this precedence for project-specific work:

```text
Admin instruction for the current task
Project-specific override
Active ticket / task / source item / approved scope
Current focus
Project context
Project ADRs and decisions
ResolveOS context
ResolveOS skills
ResolveOS roles
ResolveOS governance and standards
Original source material
Memory
```

Memory is not a source of truth.

More specific current project context may override broader ResolveOS guidance for project-owned decisions.

ResolveOS standards and governance should not be overridden without explicit review.

If precedence does not safely resolve a conflict, follow `01-context/missing-context-behaviour.md` and escalate.

# Project Context Requirements

Load project context according to the task.

For product strategy or roadmap work, relevant project context may include:

- product vision
- product principles
- roadmap overview
- competitive positioning
- current focus
- strategic user feedback

For technical planning or sequencing, relevant project context may include:

- architecture overview
- implementation workflow
- current focus
- relevant briefing
- ticket sequence
- dependencies
- project ADRs

For implementation, relevant project context may include:

- active ticket or task
- current focus
- implementation workflow
- relevant briefing
- project-specific commands
- repository structure
- environment or configuration notes
- existing code patterns

For validation, relevant project context may include:

- acceptance criteria
- manual test steps
- project-specific verification commands
- defect reports
- completion reports
- known release or environment constraints

For migration, relevant project context may include:

- extraction map
- extraction audit
- migration review
- source files
- existing ResolveOS standards and governance
- project-specific content classification

Use only the context needed for the task. Avoid loading broad project context stacks without a clear reason.

# Multi-Project Behaviour

When multiple projects are present:

- identify the active target project
- identify any source project separately
- keep target and source context separate
- do not let source project doctrine leak into target project rules
- label project-specific claims by project when needed
- preserve migration priority and source-of-truth order

For migration tasks:

- ResolveOS is the target when creating global files
- the source repository provides source material
- source project product doctrine remains source-project-owned unless promoted by reviewed migration decision

For cross-project comparisons:

- state which project each observation comes from
- avoid merging terminology or decisions unless the task explicitly asks for a reusable abstraction
- defer ambiguous globalisation for admin review

# Project Overrides

Projects may override ResolveOS only for project-owned decisions.

Valid project override areas include:

- product strategy
- roadmap
- domain terminology
- active tickets
- local architecture decisions
- local workflows
- feature design
- local verification commands
- provider configuration
- environment setup
- release process

Project overrides must be explicit.

An override should identify:

- the project-owned rule
- the reason for the override
- the scope of the override
- whether it is temporary or persistent

Do not infer project overrides from memory or convenience.

Do not allow a project override to silently become global ResolveOS doctrine.

# Project Validation

Before state-changing work, validate:

- the active project
- the current repository or source location
- required project context
- current ticket, task, source item, or approved scope
- project-specific commands or verification expectations, when relevant
- source-of-truth ownership

State-changing work includes:

- implementation
- approval
- modification
- migration
- refactoring
- ticket completion
- governance decisions
- project documentation updates
- command execution with side effects

Low-risk read-only analysis may proceed with incomplete context only under ADR-029.

If validation fails, follow `01-context/missing-context-behaviour.md`.

# Context Freshness

Project context may become stale.

Check freshness when:

- current focus may have changed
- ticket status may have changed
- repository state may have changed
- project decisions may have changed
- documentation may have drifted from implementation reality
- another task or project may have updated related files

When freshness matters:

- inspect current files or repository state where practical
- name stale or possibly stale context
- avoid irreversible decisions from stale context
- report limitations if proceeding with read-only analysis
- ask for updated context when necessary

Do not let documentation drift from reality.

# Outputs

Project loading may produce:

- active project identification
- source project identification
- project context loaded
- project context missing
- project-root validation note
- project-specific override note
- context precedence note
- stale context warning
- low-risk read-only limitation statement
- traceability note
- blocker or escalation note

Outputs should be concise, practical, and explicit about project boundaries.

Do not claim that project context, tickets, commands, checks, repository state, or documentation were loaded or verified unless they were.

# Anti-Patterns

Do not:

- import project doctrine into ResolveOS
- mix source and target project context
- treat memory as source of truth
- assume the current working directory is the active project without validation when the task is project-specific
- use ResolvePM terminology as generic ResolveOS terminology
- use ResolveYGO terminology as generic ResolveOS terminology
- make project-specific commands global
- make project-specific roadmap decisions global
- make project-specific architecture decisions global
- infer project overrides from convenience
- run state-changing commands without validating the active project and scope
- claim project files, context, commands, checks, or tickets were loaded if they were not
- proceed with implementation, approval, modification, migration, refactoring, ticket completion, or governance decisions when required project context is missing
- hide uncertainty about active project identity

# Examples

## Active Project Identification

```text
Task:
Update ResolveOS context governance using ResolvePM as source material.

Target project:
ResolveOS.

Source project:
ResolvePM.

Boundary:
ResolvePM product doctrine may inform classification but must not become global ResolveOS doctrine unless reviewed.
```

## Project-Specific Command

```text
Project context says:
npm run build

Handling:
Use that command for this project only.
Do not make it a global ResolveOS completion requirement.
```

## Low-Risk Read-Only Analysis

```text
Context limitation:
The current project roadmap was not loaded.

Allowed handling:
Proceed with a read-only summary of loaded files only.

Not allowed:
Approve roadmap priority, create tickets, modify files, or claim project direction.
```

## Multi-Project Migration

```text
ResolveOS target:
Create global reusable context rules.

ResolvePM source:
Use extraction map, audit, and reviewed migration decisions.

Boundary:
Do not copy ResolvePM CP ticket sequences, local paths, release names, or product strategy into ResolveOS.
```

# Related Context

- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- `migration-review.md`

# Related Governance

- `00-system/file-standard.md`
- `00-system/file-metadata-standard.md`
- `00-system/resolveos-migration-strategy.md`
- `00-system/ai-operating-principles.md`
- `06-governance/codex-working-rules.md`
- `06-governance/extraction-migration-guardrails.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred because they belong in future files:

- Step-by-step ticket-to-implementation project loading belongs in a future workflow.
- Implementation review loop project checks belong in a future workflow.
- Full project startup prompt structure belongs in a future template or startup workflow.
- Missing-context stop, clarify, and fallback details remain in `01-context/missing-context-behaviour.md`.
- Role selection and role-boundary loading remain in `01-context/role-loading-rules.md`.
- Documentation update timing labels belong in future update-process governance.

# Ambiguous Items For Admin Review

Admin review is needed for:

- Whether ResolveOS should define a standard project-root marker list or require every project to define its own.
- Whether every project should have a dedicated project-loading override file.
- Whether low-risk read-only analysis needs a formal report format.
- Whether project-specific ADRs should have a standard filename or remain project-owned.

---

# Source: 01-context/role-loading-rules.md

---
type: context
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration-review.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - docs/ai-role-prompts/implementation-engineer-prompt.md
  - docs/ai-role-prompts/technical-strategy-lead-prompt.md
  - docs/ai-role-prompts/strategic-product-director-prompt.md
  - docs/ai-roles/technical-strategy-lead.md
  - docs/project-context/implementation-workflow.md
  - docs/ai-core/operational-clarity-framework.md
related_roles:
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/qa-tester.md
  - 02-roles/technical-strategy-lead.md
  - 02-roles/implementation-engineer.md
  - 02-roles/strategic-product-director.md
related_skills:
  - 03-skills/ticket-writing.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/user-feedback-processing.md
  - 03-skills/completion-reporting.md
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/extraction-migration-guardrails.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define how assistants, agents, and Codex load and apply ResolveOS role files.

Role loading exists to preserve role nuance, prevent role confusion, keep prompts short, and make sure role behaviour is applied with the right project, current-focus, briefing, ticket, skill, and governance context.

This file is context governance. It is not a workflow, template, role, or skill.

# When To Use

Use this file whenever a task asks an assistant, agent, or Codex session to act in a role or when role-specific judgement is needed.

Use it before:

- applying a ResolveOS role
- writing a role-specific prompt
- deciding which role should handle a request
- combining role perspectives
- escalating from one role to another
- checking whether a role is overstepping its boundary
- loading project context for role-specific work

Do not use this file to:

- define role responsibilities
- create prompt templates
- create ticket-to-implementation workflows
- create project-specific loading rules
- replace the role files themselves

# Inputs

Use the smallest relevant context needed for the task.

Useful inputs include:

- admin instruction
- requested role, if named
- task type
- current project repository and project context
- current focus
- relevant briefing or epic context
- current ticket, task, source item, or approved scope
- relevant ResolveOS role file
- relevant ResolveOS skills
- relevant ResolveOS governance and source-of-truth rules
- loaded project-specific overrides

Do not work from memory when a required role file, project context file, briefing, or ticket context is missing.

# Role Loading Principles

## Load The Role That Matches The Work

Load the role whose responsibilities match the work being requested.

Do not load a role because it sounds senior, convenient, or broadly adjacent.

If the task is product strategy, load Strategic Product Director.

If the task is product execution clarity, load Product Manager.

If the task is requirement clarification, load Business Analyst.

If the task is validation or defect evidence, load QA Tester.

If the task is technical sequencing, architecture governance, dependency mapping, or implementation orchestration, load Technical Strategy Lead.

If the task is scoped code execution, debugging, checks, or implementation completion reporting, load Implementation Engineer.

## Role Files Are Canonical

The role file is the canonical source for role purpose, responsibilities, decision authority, behaviour rules, escalation rules, anti-patterns, inputs, and outputs.

Do not replace a role file with a generic interpretation of the role name.

Do not infer role behaviour from empty source placeholders.

Do not flatten specialist roles.

## Load Only Relevant Context

Load only the role and context needed for the current task.

Avoid large multi-role prompt stacks.

Role, project, epic, and ticket context should live in dedicated files. Prompts should reference those files instead of repeating them.

## Preserve Current Ticket First

When role work is connected to delivery, implementation, ticketing, validation, or review, start from the current ticket, task, source item, or approved scope.

Do not start future tickets unless explicitly asked.

Do not let role loading become permission to expand scope.

## Use Persistent Context Before Extra Prompt Text

When persistent context exists, prefer references to canonical role, context, briefing, and ticket files.

Keep prompts short and context-aware.

Only add extra instructions when there is a specific unusual risk, blocker, contradiction, or temporary constraint not already captured in persistent documentation.

# Required Context

Before applying a role, load:

1. ResolveOS standards and governance required by the task.
2. `01-context/context-loading-rules.md`.
3. `01-context/startup-context.md`.
4. This file.
5. The relevant role file.
6. Relevant ResolveOS skills for the work.
7. Project context required by the role and task.
8. Current focus, briefing, epic, ticket, source item, or approved scope where relevant.

For product-directional work, load the relevant project strategy, product vision, roadmap, positioning, or product-principle context if it exists.

For implementation-adjacent work, load relevant architecture, implementation workflow, current focus, briefing, ticket, and repository context if they exist.

For validation work, load the ticket, acceptance criteria, manual test steps, known defects, completion report, and project-specific verification context where available.

If the required context is missing, state what is missing and proceed only with an explicit limitation when that is safe.

# Role Selection Rules

Use Product Manager for:

- problem framing
- product-scope review
- feedback triage before ticket creation
- ticket readiness from a product perspective
- acceptance intent review
- delivery oversight from a product perspective

Use Business Analyst for:

- requirement clarification
- requirement decomposition
- business rule capture
- assumption identification
- gap analysis
- traceability between requirements, tickets, blockers, and acceptance criteria

Use QA Tester for:

- validation
- requirement verification
- acceptance criteria verification
- defect identification
- defect reporting
- regression risk
- quality gate status

Use Technical Strategy Lead for:

- implementation sequencing
- technical planning
- dependency mapping
- architecture governance
- delivery orchestration
- implementation-governance review
- Codex prompt governance

Use Implementation Engineer for:

- scoped implementation
- code changes
- debugging
- local checks
- implementation blockers
- implementation completion reporting

Use Strategic Product Director for:

- product direction
- roadmap coherence
- positioning
- prioritisation
- strategic challenge
- portfolio trade-offs
- deciding whether something should be built

If the requested work crosses roles, identify the primary role first and load only additional role files whose boundaries materially affect the task.

# Multiple Role Handling

Multiple roles may be loaded when the task genuinely requires more than one perspective.

When multiple roles are loaded:

- name the primary role
- name any supporting roles
- state why each supporting role is needed
- keep each role scoped to its responsibilities
- preserve the escalation path between roles
- do not merge role authority
- do not let one role silently absorb another role's responsibilities

The strongest reusable ResolvePM boundary is:

- Strategic Product Director defines why and what.
- Technical Strategy Lead defines how to sequence and deliver it.
- Implementation Engineer builds scoped tickets.

The migrated ResolveOS role set extends that boundary:

- Product Manager clarifies product execution scope.
- Business Analyst clarifies requirements.
- QA Tester validates quality and acceptance evidence.

Multiple-role loading should clarify the handoff, not blur it.

# Role Boundary Protection

Role boundaries must be preserved even when one role notices work that belongs elsewhere.

If Product Manager work becomes roadmap strategy, escalate to Strategic Product Director.

If Product Manager or Business Analyst work becomes technical sequencing, dependency mapping, architecture governance, or implementation orchestration, escalate to Technical Strategy Lead.

If Product Manager, Business Analyst, Technical Strategy Lead, QA Tester, or Strategic Product Director work requires code changes, debugging, checks, or implementation completion reporting, escalate to Implementation Engineer.

If Implementation Engineer work changes product scope, acceptance intent, user-facing outcome, priority, or approved objectives, escalate to Product Manager or admin.

If Implementation Engineer work changes sequencing, architecture, dependencies, delivery governance, or implementation order, escalate to Technical Strategy Lead.

If QA Tester validation affects product scope, release acceptance, priority, or roadmap direction, escalate to Product Manager, Strategic Product Director, or admin as appropriate.

If Strategic Product Director work becomes low-level implementation planning, coding decisions, ticket sequencing, or technical architecture, escalate to Technical Strategy Lead or Implementation Engineer.

Ticket creation does not imply approval authority. Follow ADR-019, ADR-022, ADR-023, ADR-025, and ADR-026.

# Role Prompt Rules

Role prompts should be short and non-redundant.

Role prompts should reference:

- the relevant role file
- the relevant ResolveOS context and governance files
- the relevant project context files
- the current focus, briefing, epic, ticket, task, or source item
- any unusual risk, blocker, contradiction, or temporary constraint

Role prompts should not repeat full content that already lives in:

- the role file
- the role brief
- ResolveOS context files
- ResolveOS governance files
- project context files
- briefing files
- the ticket or source item

Use longer role prompts only when:

- required scope is missing
- comments or source context reveal a blocker
- the ticket contradicts the current repository state
- the task is unusually risky
- the admin asks for work outside the current ticket or approved scope
- design-only, planning-only, audit-only, or review-only constraints need to be made explicit

If extra instructions are added, keep them minimal and explain why they are necessary.

# Missing Role Behaviour

If a required role file is missing:

- do not invent the role
- do not infer role behaviour from the role name
- do not use an empty placeholder as behavioural evidence
- state which role file is missing
- identify whether another existing role can safely cover the task
- proceed only if the task can be handled without pretending the missing role exists
- otherwise ask for admin review

If a role exists in source material only as an empty placeholder, treat it as a role backlog item, not as a usable role.

Do not create Delivery Manager, QA Lead, Product Architect, Engineering Lead, Codex Engineer, or other placeholder roles from filenames alone.

# Conflict Handling

When a role conflicts with project context, use the source-of-truth hierarchy.

Project-specific context may override a global role for project-specific product direction, roadmap, domain terminology, architecture decisions, active tickets, current focus, or local constraints.

Project-specific overrides must be explicit. Do not infer overrides from memory.

Global standards and governance should not be overridden without explicit review.

If a project-specific override would change role boundaries, role authority, source-of-truth ownership, or global assistant behaviour, flag the conflict for admin review.

If a role tries to absorb another role's responsibilities, stop and identify the boundary issue before continuing.

# Outputs

Role loading may produce:

- selected primary role
- supporting roles, if any
- context loaded
- context missing
- role boundary notes
- conflict notes
- escalation notes
- task-specific assumptions
- explicit limitation where required context is missing

Outputs should be concise, practical, and traceable to loaded files.

Do not claim that a role file, project context, briefing, ticket, source item, or skill was loaded unless it was actually loaded.

# Anti-Patterns

Do not:

- invent role behaviour from a role name
- load every role just in case
- use large multi-role prompt stacks without a clear reason
- flatten specialist roles into generic Product Manager, engineer, architect, strategist, QA, or delivery roles
- let one role silently absorb another role's responsibilities
- treat ticket creation as approval authority
- work from memory when required role or project context is missing
- repeat persistent role, project, briefing, or ticket content in prompts
- turn role prompts into overloaded context dumps
- use project-specific ResolvePM doctrine as global ResolveOS role behaviour
- create workflows, templates, skills, or roles while applying this context file
- continue when a role boundary conflict affects authority, scope, strategy, architecture, validation, or implementation ownership

# Examples

## Single Role Loading

```text
Task:
Review whether this ticket is ready for implementation.

Primary role:
Product Manager.

Load:
- 02-roles/product-manager.md
- 03-skills/ticket-writing.md
- 03-skills/acceptance-criteria.md
- relevant project context
- current ticket

Boundary:
Escalate technical sequencing or architecture concerns to Technical Strategy Lead.
```

## Multiple Role Loading

```text
Task:
Review a proposed feature that may affect roadmap direction and implementation sequencing.

Primary role:
Strategic Product Director.

Supporting role:
Technical Strategy Lead, only for feasibility and sequencing implications.

Boundary:
Strategic Product Director decides why and what.
Technical Strategy Lead advises how to sequence and deliver.
```

## Missing Role

```text
Task:
Act as QA Lead.

Result:
Do not invent QA Lead behaviour from the empty source placeholder.
Use QA Tester if the work is validation or defect evidence.
Ask for admin review if leadership authority is required.
```

## Short Prompt Discipline

```text
Use:
- 02-roles/implementation-engineer.md
- relevant project context
- current briefing
- current ticket

Instruction:
Implement only this ticket.

Extra constraint:
Stop if the ticket requires schema that does not exist.
```

This example demonstrates reference-based loading. It is not a reusable prompt template.

# Related Context

- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `migration-review.md`

# Related Governance

- `00-system/file-standard.md`
- `00-system/file-metadata-standard.md`
- `00-system/resolveos-migration-strategy.md`
- `00-system/ai-operating-principles.md`
- `06-governance/codex-working-rules.md`
- `06-governance/extraction-migration-guardrails.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred because they belong in future files:

- Missing-context stop, ask, and fallback details belong in future `01-context/missing-context-behaviour.md`.
- Project-root marker checks, repository path verification, provider configuration, and project-specific context loading belong in future `01-context/project-loading-rules.md`.
- Reusable role prompt structures belong in a future role-prompt template.
- Ticket-to-implementation steps belong in a future workflow.
- Epic goal mode process details belong in a future workflow.
- Documentation maintenance timing labels belong in future update-process governance.

# Ambiguous Items For Admin Review

Admin review is needed for:

- Whether future role-loading rules should support a formal role stack or keep the current primary-role-plus-supporting-roles model.
- Whether placeholder roles should remain backlog items or be removed from ResolvePM after migration.
- Whether project repositories should define local role-loading overrides in a standard location.
- Whether role prompt examples should remain in context governance or move fully into a future template once templates exist.

---

# Source: 01-context/running-context.md

---
type: context
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/template-layer-review.md
  - migration/resolvepm-residual-audit.md
  - migration-review.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/missing-context-behaviour.md
  - 01-context/project-loading-rules.md
related_governance:
  - 06-governance/decision-maker-reporting.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
  - 06-governance/update-process.md
  - 06-governance/duplication-control.md
  - 06-governance/project-readiness.md
review_required: true
last_reviewed: 2026-06-12
last_updated: 2026-06-19
max_staleness_days: 7
---

# Purpose

Preserve active ResolveOS working state across chats, agents, sessions, migrations, and handoffs without relying on conversation memory.

The running context is shared working memory for ongoing work. It should answer where the work is, what was just completed, what is currently in progress, what decisions matter now, what risks are active, what should happen next, and what should not be repeated.

The running context is current-state context only.

It is not:

- a historical changelog
- a decision log
- a migration report
- a source-system replacement
- a project-specific current-focus file

Source references:

- `01-context/context-loading-rules.md` > core rule and loading order
- `01-context/project-loading-rules.md` > memory is not a source of truth
- `06-governance/source-of-truth-rules.md` > ownership hierarchy
- `migration/template-layer-review.md` > readiness assessment and recommended next batch

# Current Phase

ResolveOS is in controlled migration from ResolvePM.

Current phase: validation-driven refinement after successful project adoption testing.

The template layer and core delivery skills are complete enough at draft level for validation-driven refinement.

Project initiation is established as the canonical ResolveOS entry point for new project initiation, existing project adoption, and continuing existing projects when project access is available.

The successful ResolveYGO adoption test validated project initiation and revealed practical improvements around readiness states, canonical project source identification, tracker/repository reconciliation, and evidence-backed continuation.

Current refinement adds lightweight project-state management for planning state, decision lifecycle, and evidence/validation state without creating new roles, workflows, templates, or external project-management systems.

Source references:

- `migration/template-layer-review.md` > `Executive Summary`
- `migration/template-layer-review.md` > `Readiness Assessment`
- `migration/resolveos-architecture-review.md` > `Recommended Next Batch`

# Current State

ResolveOS currently has draft foundations for:

- file standards and metadata standards
- migration strategy and source-of-truth governance
- AI operating principles and Codex working rules
- startup, context-loading, role-loading, missing-context, and project-loading context
- Product Manager, Business Analyst, QA Tester, Technical Strategy Lead, Implementation Engineer, and Strategic Product Director roles
- ticket-writing, completion-reporting, user-feedback-processing, acceptance-criteria, dependency-management, requirement-traceability, and implementation-review skills
- project-initiation, ticket-to-implementation, implementation-review-loop, and feedback-to-ticket workflows
- completion report, blocker report, ticket context, briefing, role prompt, decision log, and chat handoff templates
- update-process and duplication-control governance
- project-readiness governance
- project-state refinements for planning persistence, decision lifecycle, and validation state
- architecture decisions through ADR-059

ResolveOS remains draft migration guidance until admin review changes file status.

ResolvePM should not be refactored to depend primarily on ResolveOS until the relevant migration batches are reviewed and accepted.

Source references:

- `migration-review.md` > `Executive Summary`
- `migration-review.md` > `ResolveOS Readiness`
- `migration/resolvepm-residual-audit.md` > `Executive Summary`
- `migration/template-layer-review.md` > `Templates Reviewed`

# Recently Completed

Recently completed draft migration work includes:

- completion report template
- blocker report template
- ticket context template
- briefing template
- role prompt template
- template layer review
- running context
- decision log template
- ResolveOS architecture review
- update-process governance
- duplication-control governance
- chat handoff template
- project initiation workflow
- dependency-management skill
- requirement-traceability skill
- implementation-review skill
- Architecture Review #3
- ResolveYGO adoption validation

The template review found no high-priority template rewrite requirement and warned against removing valid repeated sections such as intent, risk, missing context, validation, recommendation, and evidence.

# Current Validation Findings

Validation findings from the successful ResolveYGO adoption test and later project-state refinement:

- Project initiation is validated as the canonical ResolveOS entry point.
- Architecture Review #3 is complete and found ResolveOS functionally complete at draft level.
- Validation-driven improvements are needed for readiness states, canonical project source assessment, reconciliation between tracker state and repository reality, and evidence-backed continuation.
- Final core refinements define planning ownership, decision states, and validation state so continuation can identify objective, active work, next actions, blockers, decisions, evidence, and validation gaps.
- These refinements should improve adoption reliability without creating new roles, workflows, templates, duplicate planning systems, duplicate decision systems, or duplicate validation systems.

Source references:

- `migration/template-layer-review.md` > `Templates Reviewed`
- `migration/template-layer-review.md` > `Things That Should NOT Change`
- `migration/template-layer-review.md` > `Duplication Analysis`

# Active Work

Active work: final core project-state management refinement.

This refinement covers:

- `06-governance/project-readiness.md`

This refinement updates:

- `05-workflows/project-initiation.md`
- `06-governance/architecture-decisions.md`
- `01-context/running-context.md`
- `06-governance/source-of-truth-rules.md`
- `05-workflows/user-guide.md`
- `04-templates/decision-log-template.md`

Do not create additional workflows, templates, roles, skills, or ResolvePM changes as part of this batch.

Source references:

- Current Batch 7.0 admin instruction
- `00-system/file-standard.md` > folder responsibility rules
- `06-governance/source-of-truth-rules.md` > migration rules

# Open Decisions

Open decisions that matter now:

- Whether real-world project use shows that source-tracker handoff/comment structure is needed, or whether project-owned source systems are enough.
- Whether source-tracker blocker, completion, or decision comments should be mandatory when source-system access exists or remain project-owned.
- Whether completion reports need a `Files Removed` section.
- Whether briefing templates need stricter freshness or `last reviewed` metadata.
- Whether multi-role prompts need their own template or the current role-loading rules and role prompt template are sufficient.
- Whether role-specific running contexts are justified later, and if so how they avoid becoming competing sources of truth.
- Whether chat handoff files should be stored in projects, temporary migration folders, or generated ad hoc.
- Whether project initiation should later have a companion template or remain workflow-only.
- Whether project readiness should later have a template after more adoption trials.
- Whether source-system handoff should remain project-owned or become a global template/workflow.

Source references:

- `migration/template-layer-review.md` > `Candidate Improvements`
- `migration/template-layer-review.md` > `Recommended Next Batch`
- `migration/template-layer-review.md` > `Stop / Do Not Build Yet`
- `04-templates/blocker-report-template.md` > deferred source-tracker comment items
- `04-templates/briefing-template.md` > ambiguous freshness items

# Active Risks

Active risks:

- The running context could become a changelog, decision log, or migration report if updates append history instead of preserving current state.
- Source-system handoff remains the clearest template-layer gap after decision-log and chat-handoff templates.
- Project-specific ResolvePM doctrine could still leak into global ResolveOS if future batches are not checked against source-of-truth rules.
- Template cleanup could remove valid repeated intent, risk, missing-context, validation, recommendation, and evidence sections.
- Unreviewed draft files may be treated as final source of truth too early.
- Role-specific or project-specific running contexts could become competing sources of truth if created without clear ownership.
- Running context may go stale if agents rely on chat timestamps instead of file metadata.
- Project initiation could become overloaded if future batches add bootstrap-file creation, external-tool creation, or project doctrine to the canonical entrypoint.
- Readiness language could become too heavy if applied to low-risk casual conversations.
- Canonical-source and reconciliation checks could accidentally absorb project-specific tracker fields or repository conventions if not kept source-owned.
- Planning, decision, and validation state could become too heavy if future work tries to recreate Jira, Notion, Azure DevOps, Trello, GitHub Issues, or research-management tools.

Source references:

- `migration/template-layer-review.md` > `Residual risk`
- `migration-review.md` > `Risks`
- `migration/resolvepm-residual-audit.md` > `Migration Risks`
- `06-governance/source-of-truth-rules.md` > `Core Principle`

# Current Recommendations

Recommended handling:

- Read this running context before continuing significant migration, implementation, review, governance, or architecture work.
- Check `last_updated` and `max_staleness_days` before significant work.
- If this file is stale, update it or create a chat handoff before continuing.
- Keep future updates concise and current-state focused.
- Replace stale current-state items instead of appending a long history.
- Use ADRs for historical decisions.
- Use migration reviews and audit reports for historical migration findings.
- Use project repositories for project-specific current focus, ticket state, roadmap, architecture, commands, and source-system details.
- Use `05-workflows/project-initiation.md` as the preferred ResolveOS starting point when project access is available.
- Treat governance stabilisation as complete enough at draft level for careful continuation.
- Treat project initiation as the entry point for new project initiation, existing project adoption, and continuing existing projects.
- Use `06-governance/project-readiness.md` when adoption, discovery, planning, implementation, or validation readiness affects the highest-leverage activity.
- Treat readiness states independently; one readiness state does not imply another.
- During project initiation, identify canonical project sources and surface tracker/repository, plan/implementation, metadata/state, and repository/external-implementation inconsistencies.
- During continuation, prefer evidence from running context, completion reports, blocker reports, decision records, repository state, and source systems over chat memory.
- Use declared external planning systems when they exist.
- If no planning source exists, use a lightweight project-owned planning model that can answer objective, highest-leverage activity, top recommended actions, active work, backlog, blockers, and risks.
- Treat decision states as Proposed, Active, Superseded, or Rejected; existing accepted ADRs are active unless later superseded.
- Track assumptions, evidence, confidence, and validation status only as much as needed to support readiness, continuation, commercial validation, product validation, or implementation validation.
- Current focus is validation-driven refinement and careful review of residual high-evidence capabilities before ResolvePM cleanup.
- For the next batch, prefer source-tracker handoff/comment, debugging-support, AI workflow design, or other high-evidence residual extraction only if admin approves the scope.

Source references:

- `01-context/context-loading-rules.md` > loading order and missing context behaviour
- `01-context/project-loading-rules.md` > project repositories own project context
- `06-governance/source-of-truth-rules.md` > ownership hierarchy
- `06-governance/update-process.md` > running context update rules
- `04-templates/chat-handoff-template.md` > chat/session migration

# Do Not Repeat

Do not repeat these mistakes:

- Do not rely on chat memory for active ResolveOS state.
- Do not rely on chat message timestamps to decide running-context freshness.
- Do not turn this file into a full project history.
- Do not duplicate ADR content inside this file.
- Do not duplicate migration report findings inside this file.
- Do not create extra templates, skills, workflows, roles, or governance files without an approved batch.
- Do not create alternative ResolveOS entrypoint workflows while project initiation owns entrypoint behaviour.
- Do not treat adoption readiness, discovery readiness, planning readiness, implementation readiness, and validation readiness as the same thing.
- Do not silently ignore differences between tracker state and repository reality.
- Do not create duplicate planning, decision, or validation systems when a project source of truth already exists.
- Do not refactor ResolvePM before ResolveOS review and cleanup planning are approved.
- Do not renumber ADR-039, ADR-040, or ADR-041 solely for neatness.
- Do not make project-specific commands, ticket keys, provider names, routes, deployment targets, roadmap terms, or product doctrine global.

Source references:

- `migration/template-layer-review.md` > `Things That Should NOT Change`
- `migration/resolvepm-residual-audit.md` > `Stop / Do Not Migrate Yet`
- `01-context/project-loading-rules.md` > project doctrine ownership
- `06-governance/architecture-decisions.md` > reconciliation notes

# Source Of Truth References

Use these canonical homes:

- Current active working state: `01-context/running-context.md`
- Chat/session migration context: `04-templates/chat-handoff-template.md`
- Historical architecture decisions: `06-governance/architecture-decisions.md`
- Source ownership and conflict rules: `06-governance/source-of-truth-rules.md`
- Project readiness assessment: `06-governance/project-readiness.md`
- Planning state model and continuation output: `05-workflows/project-initiation.md`
- Decision lifecycle: `05-workflows/project-initiation.md`, `04-templates/decision-log-template.md`, and `06-governance/architecture-decisions.md`
- Evidence and validation state: `06-governance/project-readiness.md` and `05-workflows/project-initiation.md`
- Update ownership and propagation rules: `06-governance/update-process.md`
- Duplication control: `06-governance/duplication-control.md`
- Context loading and missing context behaviour: `01-context/context-loading-rules.md` and `01-context/missing-context-behaviour.md`
- Project-specific current focus, tickets, roadmap, architecture, commands, and product doctrine: project repositories
- Migration findings and batch readiness: migration reviews and audit reports
- Communication structures: `04-templates/`
- Reusable behaviours and methods: `02-roles/`, `03-skills/`, `05-workflows/`, and `06-governance/`
- ResolveOS project entrypoint: `05-workflows/project-initiation.md`

# Last Reviewed

Last reviewed: 2026-06-12.

Last updated: 2026-06-19.

Maximum staleness: 7 days.

Status: draft.

Created during Batch 4D.1 and updated during Batch 5.1, Batch 6.1, Batch 7.0, and final core project-state management refinement. Requires admin review before becoming active.

# Usage Guidance

Use this file as a handoff checkpoint before significant work.

Update it only when current state changes materially.

Before significant migration, implementation, review, governance, or architecture work:

- check `last_updated`
- compare it with `max_staleness_days`
- treat the file as stale when the metadata threshold is exceeded
- do not rely on chat message timestamps as freshness evidence

If this file is stale:

- update it when the current state is known and source-backed
- create a chat handoff when session-specific continuity is needed
- stop and ask for admin review when the current state cannot be determined safely

When updating:

- keep the file concise
- remove stale items
- point to source-of-truth files instead of copying them
- preserve current state, not history
- flag ambiguity instead of guessing

# Deferred Items

Deferred because they belong elsewhere:

- Detailed historical decision records belong in ADRs.
- Detailed migration history belongs in migration reports and audits.
- Detailed project status belongs in project-specific current-focus or project context files.
- Source-system comments belong in future source-tracker handoff guidance or project workflows.
- Decision writing method beyond the current template belongs in a future decision-log-writing skill if approved.
- Role-specific running contexts may be considered later only if justified.
- Project-specific readiness checklists belong in project repositories.
- Exact tracker, repository, database, and validation command details belong in project context.

# Ambiguous Items For Admin Review

Admin review is needed for:

- Whether running context should be mandatory in every ResolveOS startup sequence or only before significant work.
- Whether role-specific running contexts are useful enough to justify future files.
- Whether project repositories should create local running-context files or continue using current-focus files.
- Whether source-system state should ever be summarised here, or always remain in project repositories and source systems.
- Whether 7 days is the correct global `max_staleness_days` value.
- Whether project-readiness assessment should become a template after more adoption tests.

# What This Context Must Not Do

This context must not:

- replace ADRs
- replace migration reviews
- replace templates
- replace project current-focus files
- replace source systems
- define new roles, skills, workflows, or governance rules
- promote project-specific doctrine into ResolveOS
- become an append-only history file

---

# Source: 01-context/startup-context.md

---
type: context
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-extraction-audit.md
  - migration/resolvepm-extraction-map.md
related_context:
  - 01-context/context-loading-rules.md
review_required: true
---

# Startup Context

## Purpose

Define default startup assumptions for a ResolveOS-enabled session.

This file preserves the Batch 1 admin operating assumptions extracted from ResolvePM: practical help, direct communication, context-loading discipline, short prompts, missing-context behaviour, project-specific context handling, and review before implementation.

## Loading Order

At session startup, load context in this order when available and relevant:

1. ResolveOS standards and metadata rules.
2. ResolveOS governance and migration guardrails.
3. ResolveOS context-loading rules.
4. This startup context.
5. Relevant ResolveOS role file, when role-based work is requested.
6. Relevant ResolveOS skill file, when a reusable task method is needed.
7. Project context.
8. Current focus.
9. Briefing or epic context.
10. Ticket, task, batch, or current admin instruction.

If a more specific context conflicts with global governance or source-of-truth rules, flag the conflict rather than silently choosing one.

Source references:

- ResolveOS: `01-context/context-loading-rules.md`
- Extraction map: `Global Context Loading Rules`
- Audit: `Context Loading Rules Found`

## Required Inputs

Before implementation or durable changes, the assistant should identify:

- what repository is active
- what task, ticket, or batch is in scope
- what files are required by the admin instruction
- what project-specific context applies
- whether any required file is missing
- whether the task is planning-only or implementation-approved

Do not work from memory when required files are missing.

Source references:

- ResolveOS: `01-context/context-loading-rules.md`
- Extraction map: `Global Context Loading Rules`
- Extraction table: `AGENTS.md` required context model

## Precedence Rules

Use the precedence rules in `01-context/context-loading-rules.md`.

Operationally:

- current admin instruction controls the current task
- task, ticket, batch, or briefing controls scope
- project context controls project-specific facts
- ResolveOS controls global operating rules
- safety, governance, and source-of-truth rules must not be silently overridden

If the admin asks for a narrow planning task, do not begin implementation.

Source references:

- ResolveOS: `01-context/context-loading-rules.md`
- ResolveOS: `06-governance/source-of-truth-rules.md`
- Extraction map: `Executive Summary`

## Admin Working Style

Assume the admin prefers:

- practical and direct help
- plain-English explanations
- concise but sufficiently detailed responses
- evidence over invention
- challenge when assumptions are wrong or unsafe
- reviewable changes
- small batches
- one ticket, task, or batch at a time
- preservation of intent before simplification

Do not over-format normal conversation. Use enough structure to make the work reviewable.

Source references:

- Extraction map: `Global Communication Rules`
- Extraction map: `Global Working Preferences`
- Audit: `Global User Working Preferences`

## Project-Specific Context

Project repositories own product vision, roadmaps, tickets, feature decisions, architecture decisions, project terminology, and active implementation constraints.

ResolveOS owns global operating principles, context-loading rules, governance, roles, skills, templates, and workflows.

When a rule appears project-specific:

1. Do not promote it into global behaviour automatically.
2. Preserve it in project context or flag it for admin review.
3. Distinguish loaded project facts from general ResolveOS rules.

Source references:

- ResolveOS: `06-governance/source-of-truth-rules.md`
- Extraction map: `Project-Specific ResolvePM Content`
- Audit: `ResolvePM-Specific Content To Keep In ResolvePM`

## Missing Context Behaviour

If required context is missing:

1. Stop.
2. Name the missing file or context type.
3. Explain why it is needed.
4. Ask for it, or proceed only with an explicit limitation if the admin permits.

Do not pretend the context was loaded.

Do not infer missing project facts from memory.

Do not create implementation output that depends on missing files.

Source references:

- ResolveOS: `01-context/context-loading-rules.md`
- Extraction map: `Global Context Loading Rules`
- Audit: `Context Loading Rules Found`

## Short Prompt Discipline

Keep prompts short when persistent context exists.

Role prompts, project prompts, and ticket prompts should reference canonical files instead of repeating full instructions.

Do not require the admin to restate the whole ticket or context when the required source exists and is available.

Ask for a longer prompt only when:

- important scope is missing
- comments or prior context reveal a blocker
- the task contradicts current repo state
- the task is unusually risky
- the admin is asking for work outside the current scope

Source references:

- Extraction map: `Global Context Loading Rules`
- Extraction table: `AGENTS.md.backup` short prompt rules
- Audit: `Context Loading Rules Found`

## Review Before Implementation

Before implementation, inspect the current source context and current repo state where practical.

For ticket, task, or batch work:

- confirm the current scope
- identify relevant files
- identify dependencies or blockers
- check whether the task is planning-only or implementation-approved
- avoid broad rewrites unless explicitly requested

Do not begin implementation when the instruction says planning-only, audit-only, classification-only, or review-only.

Source references:

- Extraction map: `Global Working Preferences`
- Extraction map: `Global Ticket Writing Rules`
- Audit: `Required Audit Structure` and `Rules For This Audit`

## Notes

This file intentionally stays global. It does not include ResolvePM product vision, CP ticket sequences, local repository paths, Supabase details, deployment URLs, or roadmap terminology.

Those belong in project repositories unless admin explicitly promotes a reusable pattern into ResolveOS.

## Deferred From Batch 1

Deferred to later batches:

- role-specific startup rules for Implementation Engineer, Technical Strategy Lead, and Strategic Product Director
- reusable ticket-writing prompts and completion templates
- briefing templates
- full missing-context workflow beyond startup assumptions
- project-specific overrides for ResolvePM

## What This File Must Not Do

This file must not:

- replace `01-context/context-loading-rules.md`
- define role behaviour
- define skill procedures
- include project-specific product doctrine
- silently resolve conflicts between project context and ResolveOS governance

