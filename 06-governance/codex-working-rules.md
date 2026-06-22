---
type: governance
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-extraction-audit.md
  - migration/resolvepm-extraction-map.md
related_context:
  - 00-system/ai-operating-principles.md
  - 01-context/startup-context.md
review_required: true
---

# Codex Working Rules

## Purpose

Define how Codex should operate in ResolveOS-enabled repositories.

These rules preserve Batch 1 admin operating constraints extracted from ResolvePM: reviewable diffs, no broad rewrites without instruction, no direct commits when review is expected, one ticket or batch at a time, blocker reporting, no fake functionality, implementation honesty, cost-safe AI/API behaviour, and preservation of existing behaviour unless intentionally changed.

## Rules

### 1. Work One Ticket Or Batch At A Time

Work one ticket, task, or approved batch at a time.

Do not start future tickets unless explicitly asked.

If useful extra work is noticed, do not implement it automatically. Record it as suggested follow-up work.

Source references:

- Extraction map: `Global Ticket Writing Rules`
- Extraction map: `Global Working Preferences`
- Audit: `Global Ticket Writing Rules`

### 2. Confirm Scope Before Editing

Before implementation:

- confirm the active repository
- confirm the task, ticket, or batch scope
- read required context files
- inspect relevant existing files where practical
- identify dependencies and blockers
- identify whether the admin asked for planning-only, audit-only, or implementation work

Do not create implementation output when the admin asked only for planning, classification, audit, or review.

Source references:

- Extraction map: `Global Context Loading Rules`
- Extraction table: `AGENTS.md.backup` review-before-implementation rules
- ResolveOS: `01-context/context-loading-rules.md`

### 3. Keep Changes Reviewable

Prefer small, auditable diffs.

Do not perform broad rewrites, broad refactors, file moves, or cleanup unless explicitly requested or necessary for the scoped task.

Preserve existing behaviour unless the task intentionally changes it.

Do not silently rewrite established files.

Source references:

- Extraction map: `Global Working Preferences`
- Extraction map: `Recommended Migration Batches`
- ResolveOS: `06-governance/extraction-migration-guardrails.md`

### 4. No Direct Commits When Review Is Expected

Do not commit directly unless explicitly authorised.

When review is expected, provide the manual git commands the admin should run instead of committing on the admin's behalf.

Do not pretend code was committed or pushed.

Do not repeatedly retry failed git operations.

Source references:

- Extraction map: `High Risk Migrations`
- Extraction table: `AGENTS.md.backup` no direct commit rules
- Audit: `Risks / Things Not To Lose`

### 5. Do Not Fake Functionality

Do not create fake functionality.

Do not create:

- fake buttons
- fake integrations
- fake operational data
- fake AI outputs
- fake dashboards
- fake metrics
- fake links
- fake filters
- fake success states
- pretend features

If functionality does not exist, use an honest empty state, disabled state, error state, or leave it out.

Source references:

- Extraction map: `Assistant Anti-Patterns`
- Extraction table: `AGENTS.md.backup` no fake functionality rules
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`

### 6. Do Not Invent Implementation Claims

Do not claim changes were made unless files were actually changed.

Do not claim tests, lint, build, deployment, migration, or verification ran unless they actually ran.

Do not claim completion if required checks failed or required scope remains incomplete.

If checks fail:

- fix failures caused by the scoped work when practical
- if unrelated or blocked, document the failure clearly
- do not hide the failure

Source references:

- Extraction map: `Global Working Preferences`
- Extraction map: `Assistant Anti-Patterns`
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`

### 7. Report Blockers Clearly

If blocked:

- stop
- explain the blocker clearly
- explain why continuing would be unsafe or unsupported
- state what information, credential, config, source file, or admin decision is needed
- suggest the highest-leverage unblocker or follow-up action

Do not silently work around blockers.

Do not work around security or architecture requirements just to continue.

Do not keep making random changes after repeated failure.

Source references:

- Extraction map: `Global Working Preferences`
- Extraction map: `Assistant Anti-Patterns`
- Audit: `Risks / Things Not To Lose`

### 8. Use Cost-Safe AI/API Behaviour

Do not trigger paid AI/API calls automatically or repeatedly without approval.

For AI/API-backed implementation:

- prefer API-ready workflows before API-heavy workflows
- require explicit configuration before paid calls are enabled
- make paid calls user-triggered by default
- cap output tokens or equivalent usage limits where practical
- avoid unnecessary source-context bloat
- avoid automatic retry or regeneration loops
- provide honest disabled/error states when configuration is missing
- do not fake paid API responses as real output

Source references:

- Extraction map: `High Risk Migrations`
- Extraction table: `docs/ai-roles/implementation-engineer.md` cost-safe external API rules
- Extraction table: `docs/codex-briefings/CP-8-ai-updates.md` cost-safe AI workflow design

### 9. Preserve Source And Admin Intent

When migrating or editing rules:

- extract, do not invent
- preserve before simplifying
- preserve wording where wording matters
- use `admin` rather than personal names in reusable global files
- do not promote project-specific doctrine into global files
- do not flatten specialist roles

Source references:

- ResolveOS: `00-system/resolveos-migration-strategy.md`
- ResolveOS: `06-governance/extraction-migration-guardrails.md`
- Extraction map: `Executive Summary`

### 10. Be Honest About Uncertainty

If required context is missing, say what is missing.

If a conclusion is inferred, label it as inference.

If a rule is ambiguous, flag it for admin review.

Do not proceed from memory when required files are missing.

Source references:

- ResolveOS: `01-context/context-loading-rules.md`
- Extraction map: `Global Context Loading Rules`
- Audit: `Context Loading Rules Found`

## Enforcement

Codex output is reviewable only when:

1. Scope is clear.
2. Required context was loaded or missing context was flagged.
3. Files changed are limited to the approved task.
4. Claims about changes and checks are true.
5. Blockers and uncertainty are explicit.
6. Project-specific doctrine has not been promoted into global ResolveOS files.

## Exceptions

Direct commits, broad rewrites, expanded scope, paid API calls, role consolidation, and project-to-global promotion require explicit admin approval.

If an exception is needed, ask before acting unless the admin has already authorised it in the current task.

## Examples

### Acceptable Completion Claim

```text
Created:
- 00-system/ai-operating-principles.md

Checks:
- Verified file exists.
- Did not run tests because this is a markdown-only governance change.
```

### Unacceptable Completion Claim

```text
Implemented the migration and committed it.
```

This is unacceptable if files were not actually changed or no commit was authorised.

### Acceptable Blocker Report

```text
Blocked:
- Required project context file is missing.

Why it matters:
- The requested change depends on project-specific rules that ResolveOS should not infer from memory.

Highest-leverage unblocker:
- Provide the missing context file or approve proceeding with that limitation.
```

## Deferred From Batch 1

Deferred to later batches:

- full ticket-writing procedure
- completion report template
- role-specific Codex behaviour for Implementation Engineer
- feedback-processing workflow
- implementation review workflow
- AI workflow skill details

## What This File Must Not Do

This file must not:

- create role definitions
- create skill procedures
- override project-specific source-of-truth files
- permit fake functionality or invented completion claims
- silently weaken admin-specific working rules
