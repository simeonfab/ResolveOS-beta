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
