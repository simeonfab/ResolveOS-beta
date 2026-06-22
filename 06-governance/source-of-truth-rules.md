---
type: governance
scope: global
owner: ResolveOS
version: 0.1
status: draft
---

# Source Of Truth Rules

## Purpose

Define which files own which types of information, how conflicts are resolved, and how changes flow between ResolveOS and project repositories.

This file prevents duplicated guidance, conflicting instructions, and uncertainty about where a rule should live.

## Core Principle

Every important rule should have one canonical home.

Copies, summaries, references, and derived versions may exist.

Ownership must exist in one place only.

When ResolveOS surfaces a source-of-truth issue, it should also state whether the issue blocks current progress and the practical resolution path.

## Ownership Hierarchy

### ResolveOS Owns

ResolveOS is the source of truth for:

- Global operating principles.
- Global AI behaviour.
- Global assistant constraints.
- Global governance.
- Global communication rules.
- Global working preferences.
- Global context-loading rules.
- Global role definitions.
- Global skill definitions.
- Global templates.
- Global workflows.
- Global standards.

### Project Repositories Own

Project repositories are the source of truth for:

- Product vision.
- Product strategy.
- Roadmaps.
- Planning state, including objectives, active work, backlog, blockers, risks, and next actions.
- Project decisions.
- Active tickets.
- Validation evidence, assumptions, confidence, and project-specific acceptance state.
- Domain-specific terminology.
- Project-specific workflows.
- Feature design.
- Architecture decisions.
- User research.
- Project-specific constraints.

Examples:

- ResolvePM owns ResolvePM product direction.
- ResolveYGO owns ResolveYGO deck logic and testing methodology.

## Conflict Resolution Order

When instructions conflict:

```text
Admin Review
    ↓
Project-Specific Override
    ↓
Project Context
    ↓
ResolveOS Context
    ↓
ResolveOS Skills
    ↓
ResolveOS Roles
    ↓
ResolveOS Standards
```

Conflicts should be documented rather than silently resolved.

Conflict output should identify:

- which sources conflict
- what decision, evidence, or source owner can resolve the conflict
- whether the conflict blocks the current objective
- what can safely continue, if anything
- the smallest mitigation or next action
- whether a prompt, handoff, decision note, or source-owner review is needed

## Context Loading Hierarchy

Recommended loading order:

```text
ResolveOS Standards
    ↓
ResolveOS Governance
    ↓
ResolveOS Context
    ↓
ResolveOS Role
    ↓
ResolveOS Skill
    ↓
Project Context
    ↓
Current Focus
    ↓
Ticket / Task
```

More specific context may override broader context.

Global standards should not be overridden without explicit review.

## Migration Rules

When content is extracted from a project:

1. Audit.
2. Classify.
3. Extract.
4. Standardise.
5. Review.
6. Refactor.

Never skip directly to refactoring.

## Duplication Rules

Avoid storing the same rule in multiple places.

If duplication exists:

1. Identify the canonical source.
2. Preserve wording if wording matters.
3. Replace duplicates with references where practical.
4. Record exceptions.

## ResolvePM To ResolveOS Promotion Rules

Content may move from ResolvePM into ResolveOS only if:

- Reusable across projects.
- Not tied to ResolvePM product decisions.
- Not tied to ResolvePM roadmap decisions.
- Not tied to ResolvePM implementation details.
- Useful to future projects.

## ResolveOS To Project Consumption Rules

Projects should consume ResolveOS.

Projects should not permanently fork ResolveOS rules unless they require project-specific overrides.

If a project declares Jira, Notion, GitHub Issues, Azure DevOps, or another external system as the planning, decision, ticket, or validation source of truth, ResolveOS should use that source instead of creating a competing project-owned planning or validation record.

If no external planning source exists, the project may use a lightweight project-owned current-focus, running-context, plan, or equivalent file. That file belongs to the project, not ResolveOS.

Storage model and location are part of source-of-truth discipline. If an existing canonical database, page, section, ticket, comment, repository path, folder, file, document, ADR process, or temporary holding area owns the information, ResolveOS must use that model and location instead of creating a new one.

Existing storage is evidence, not approval. ResolveOS should not treat an existing page, database, file, folder, ticket, or section as canonical merely because it already exists.

When reviewing existing structures, ResolveOS should classify the information, identify the ideal storage model, identify the current storage model, compare current vs ideal, and recommend whether to keep, move, convert, wrap with a record, merge, mark historical, or keep temporarily with a migration note.

Before writing to Notion, GitHub markdown, Google Docs, SharePoint, Confluence, local files, Jira, Linear, GitHub Issues, or similar storage tools, ResolveOS should apply `03-skills/information-architecture.md`.

New top-level pages, documents, files, folders, or database structures should be created only when the content represents a new major project, product area, system, database, or durable knowledge domain.

Routine feedback, notes, decisions, risks, meeting outputs, implementation context, discovery items, research items, validation findings, and conversation summaries should usually be stored inside the relevant existing structure using the storage model appropriate to the information type.

When an override exists:

- The override should be documented.
- The reason should be documented.
- The override should be reviewed periodically.

When a source conflict does not block current work, ResolveOS should say so and proceed with an explicit limitation.

When a source conflict blocks implementation, validation, approval, or project direction, ResolveOS should stop before that work and name the smallest required confirmation.

## Review Requirements

Review is required before:

- New global standards.
- New global roles.
- New global skills.
- Major context-loading changes.
- Role consolidation.
- Large migrations.
- Deletion of migrated source material.

## High-Risk Content

The following categories require explicit review:

- Specialist roles.
- Ticket-writing rules.
- Feedback-handling rules.
- Completion reporting.
- Context-loading behaviour.
- Assistant anti-patterns.
- Cost-safe AI/API rules.
- No-direct-commit rules.
- No-fake-functionality rules.
- Documentation and storage architecture rules.

## ResolveOS Standards Precedence

The following files should be treated as foundational standards:

```text
00-system/file-standard.md
00-system/file-metadata-standard.md
00-system/resolveos-migration-strategy.md
06-governance/extraction-migration-guardrails.md
06-governance/source-of-truth-rules.md
```

Future files should align with these standards.

If a contradiction is discovered:

- Flag it.
- Review it.
- Update the canonical file.
- State whether the contradiction blocks current progress.
- State the smallest practical mitigation.

Do not silently create competing standards.

## Enforcement

When creating new files:

- Follow the file standard.
- Follow the metadata standard.
- Follow migration guardrails.
- Follow source-of-truth ownership.

If ownership is unclear:

Classify the content before implementation.

Do not guess.
