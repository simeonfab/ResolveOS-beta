---
type: skill
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-extraction-audit.md
  - migration/resolvepm-extraction-map.md
related_skills:
  - 03-skills/ticket-writing.md
related_context:
  - 00-system/ai-operating-principles.md
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
related_governance:
  - 06-governance/codex-working-rules.md
  - 06-governance/extraction-migration-guardrails.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Completion Reporting

## Purpose

Define the canonical ResolveOS skill for reporting completed, partial, failed, blocked, or deferred work.

This skill preserves ResolvePM guidance about implementation honesty, blocker reporting, validation reporting, uncertainty, manual steps, changed files, command execution, deployment status, review status, and follow-up work.

This file is a skill, not a template. A future completion report template may be created separately after review.

Source references:

- Extraction map: `High Risk Migrations`
- Extraction map: `Global Working Preferences`
- Extraction map: `Assistant Anti-Patterns`
- Audit: `Risks / Things Not To Lose`
- Inline ADR instruction: ADR-012 says completion reporting consists of a skill and a future template; this batch creates only the skill.

## When To Use

Use this skill whenever an assistant, agent, or Codex reports the state of work.

Use it after:

- implementation
- migration batches
- audit or extraction work
- ticket refinement
- review work
- debugging
- failed or blocked attempts
- validation or testing
- deployment-related work

Use it even when work is partial, blocked, or failed. Completion reporting is not only for successful work.

Source references:

- Extraction table: `AGENTS.md.backup` completion response format
- Extraction table: `docs/ai-roles/implementation-engineer.md` required completion report format
- Extraction map: `Global Working Preferences`

## Inputs

Before reporting, identify:

- requested task, ticket, batch, or scope
- files created, modified, removed, or intentionally left untouched
- commands run
- checks run
- checks not run
- command outcomes
- validation performed
- validation not performed
- blockers encountered
- assumptions made
- deviations from the original plan
- known issues
- deferred work
- follow-up work
- deployment or commit status, if relevant

Do not infer these from memory when direct evidence is available.

Source references:

- Extraction map: `Global Working Preferences`
- Extraction table: `AGENTS.md.backup` completion response format
- ResolveOS: `00-system/ai-operating-principles.md`

## Completion Reporting Principles

### 1. Truthfulness Before Fluency

Do not claim work was done unless it was actually done.

Do not claim files were changed, tests were run, code was committed, a deployment happened, or a ticket was completed unless there is direct evidence.

Source references:

- ResolveOS: `00-system/ai-operating-principles.md`
- Extraction map: `Assistant Anti-Patterns`
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`

### 2. Implementation Honesty

Do not invent implementation claims.

Do not pretend code was committed or pushed. Do not pretend a check passed. Do not claim a ticket, batch, or file is complete if required checks failed or required scope was not finished.

Source references:

- ResolveOS: `00-system/ai-operating-principles.md`
- Extraction table: `AGENTS.md.backup` no direct commit and completion honesty rules
- Extraction map: `Assistant Anti-Patterns`

### 3. Explicit Limitations

Be explicit about limitations.

Report what was not done, what could not be verified, and what remains uncertain.

Do not imply success when status is unknown.

Source references:

- ResolveOS: `00-system/ai-operating-principles.md`
- ResolveOS: `06-governance/codex-working-rules.md`
- Audit: `Global User Working Preferences`

### 4. Preserve Reviewability

Completion reports should make the work reviewable.

They should identify:

- what changed
- why it changed
- where it changed
- what was checked
- what was not checked
- what remains risky, blocked, or deferred

Source references:

- ResolveOS: `06-governance/codex-working-rules.md`
- Extraction table: `docs/ai-roles/implementation-engineer.md` required completion workflow
- Extraction map: `Global Working Preferences`

## Reporting Completed Work

When work is complete, report:

- the task, ticket, or batch
- what was achieved
- why it matters, when useful for review
- files created or changed
- implementation path or extraction path
- validation performed
- result of validation
- known issues, if any
- manual steps for the admin, if any
- follow-up work, if any
- commit, deployment, or review status, if relevant

Do not overstate completion. If the work is complete only for the scoped batch, say that.

Source references:

- Extraction table: `AGENTS.md.backup` completion response format
- Extraction table: `docs/ai-roles/implementation-engineer.md` required completion report format
- Extraction map: `Global Ticket Writing Rules`

## Reporting Partial Work

When work is partially complete, say so directly.

Report:

- what was completed
- what remains incomplete
- why it remains incomplete
- whether acceptance criteria or task requirements are still unmet
- what decision, prerequisite, or follow-up is needed

Do not label partial work as complete.

Source references:

- Extraction table: `AGENTS.md.backup` if blocked or partially complete
- Extraction table: `AGENTS.md.backup` implementation drift reporting
- Audit: `Risks / Things Not To Lose`

## Reporting Failed Work

When work fails, do not silently leave the task in a failed state.

Report:

- what failed
- what command, check, or step failed
- the first clear error or failure reason when available
- what was tried
- what changed before the failure, if anything
- whether the failure is related to the scoped work
- what help, decision, config, or prerequisite is needed

Do not keep making random changes after repeated failure.

Source references:

- Extraction table: `AGENTS.md.backup` stuck-loop and failed-state behaviour
- Extraction map: `Assistant Anti-Patterns`
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`

## Reporting Blockers

If blocked:

- stop
- explain the blocker clearly
- explain why continuing would be unsafe or unsupported
- state what information, credential, config, source file, or admin decision is needed
- suggest the highest-leverage unblocker or follow-up action

Do not silently work around blockers.

Do not work around security or architecture requirements just to continue.

Source references:

- ResolveOS: `00-system/ai-operating-principles.md`
- ResolveOS: `06-governance/codex-working-rules.md`
- Extraction table: `AGENTS.md.backup` blocker handling
- Extraction table: `docs/project-context/implementation-workflow.md` blocker behaviour

## Reporting Validation

Report validation honestly.

For checks or commands that were run, include:

- command or validation method
- outcome
- important failure or warning, if any
- what the check proves, when useful

For checks or commands not run, say:

- not run
- why not run
- residual risk, if any

Project verification commands remain project-specific. Do not make global claims that every project must use the same lint, build, test, smoke, or deployment commands.

Source references:

- Extraction table: `AGENTS.md.backup` checks run and manual test steps
- Extraction map: `Global Working Preferences`
- ResolveOS: `06-governance/codex-working-rules.md`
- Inline ADR instruction: ADR-013 says project verification commands remain project-specific.

## Reporting Risk And Uncertainty

Report uncertainty explicitly.

Use clear labels when needed:

- known
- not verified
- inferred
- blocked
- deferred
- requires admin review

Do not hide uncertainty. Do not imply success when status is unknown.

If implementation differs from the original plan, explain:

- original plan
- what actually happened
- why it changed
- impact
- follow-up needed

Source references:

- Extraction table: `AGENTS.md.backup` implementation drift reporting template
- ResolveOS: `00-system/ai-operating-principles.md`
- Audit: `Risks / Things Not To Lose`

## Reporting Follow-Up Work

Report follow-up work separately from completed scope.

Follow-up work should identify:

- suggested follow-up ticket or task
- why it is separate
- whether it is required or optional
- whether it blocks future work

If useful extra work was noticed, do not imply it was implemented unless it actually was.

Source references:

- Extraction table: `AGENTS.md.backup` suggested follow-up tickets rule
- Extraction map: `Global Working Preferences`
- ResolveOS: `03-skills/ticket-writing.md`

## Reporting Manual Steps

Manual steps should be short and clear.

Explain what the admin is doing, not just what command to run.

If jargon is unavoidable, briefly explain it.

When manual git, deployment, migration, or validation steps are needed, report them as admin actions rather than implying the assistant performed them.

Source references:

- Extraction table: `AGENTS.md.backup` manual step communication rules
- Extraction table: `AGENTS.md.backup` manual git command rules
- Audit: `Risks / Things Not To Lose`

## Reporting Deployment, Commit, And Review Status

Do not pretend code was committed or pushed.

Do not pretend deployment happened.

Do not treat deployment as complete until the real deployment status is known.

When review is expected, report that work is ready for review rather than presenting it as merged, committed, pushed, or deployed.

If manual git commands are provided, make clear they are commands for the admin to run.

Source references:

- Extraction table: `AGENTS.md.backup` no direct commit and git reporting rules
- ResolveOS: `06-governance/codex-working-rules.md`
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`

## Outputs

A completion report should produce a concise, reviewable account of:

- status
- completed work
- partial or failed work, if any
- files changed
- commands or checks run
- commands or checks not run
- validation result
- blockers
- assumptions
- uncertainty
- known issues
- deferred work
- follow-up work
- manual steps
- commit, deployment, or review status, if relevant

The report should be as short as the task allows, but it must not omit important truth, limitations, or blockers.

Source references:

- Extraction table: `AGENTS.md.backup` completion response format
- Extraction map: `Global Working Preferences`
- Audit: `Global Skill Candidates`

## Anti-Patterns

Do not:

- claim work was done unless it was done
- claim files changed unless files actually changed
- pretend code was committed or pushed
- pretend tests, checks, deployment, or validation ran
- imply success when status is unknown
- hide blockers
- hide uncertainty
- hide failed checks
- describe partial work as complete
- silently leave work in a failed state
- keep making random changes after repeated failure
- bury important limitations in vague summaries
- replace specific completion-reporting rules with generic status-report language

Source references:

- Extraction map: `Assistant Anti-Patterns`
- Extraction map: `High Risk Migrations`
- Audit: `Global Assistant Anti-Patterns / Prohibited Behaviours`
- ResolveOS: `06-governance/extraction-migration-guardrails.md`

## Examples

### Completed Work

```text
Status:
Complete for the requested scope.

Files changed:
- [file path]

Validation:
- Ran [command/check]: passed.
- Not run: [command/check]. Reason: [reason].

Known issues:
- None identified / [issue].

Follow-up:
- [follow-up item, or None].
```

### Partial Work

```text
Status:
Partially complete.

Completed:
- [what was completed]

Not completed:
- [what remains]

Reason:
- [blocker, decision, missing context, or failed validation]

Next step:
- [highest-leverage unblocker or follow-up action]
```

### Blocked Work

```text
Status:
Blocked.

Current blocker:
[Specific missing context, credential, configuration, dependency, source file, or admin decision]

Why continuing is unsafe:
[Why proceeding would require guessing, fake functionality, or unsupported assumptions]

Highest-leverage unblocker or follow-up action:
[What is needed next]
```

These examples are guidance for the skill. They are not a canonical completion report template.

Source references:

- Extraction table: `AGENTS.md.backup` completion and blocker report formats
- Inline ADR instruction: ADR-012 says a future template is separate from this skill.

## Related Skills

- `03-skills/ticket-writing.md`

Future related skills or templates may include:

- acceptance criteria
- implementation review
- completion report template

## Related Governance

- `00-system/ai-operating-principles.md`
- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `06-governance/codex-working-rules.md`
- `06-governance/extraction-migration-guardrails.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

## Source Merge Notes

Multiple source variants were consolidated:

- The strongest completion-reporting structure came from `AGENTS.md.backup`.
- The strongest implementation honesty rules came from `AGENTS.md.backup`, Batch 1 `ai-operating-principles.md`, and `codex-working-rules.md`.
- The strongest blocker wording came from `AGENTS.md.backup` and `docs/project-context/implementation-workflow.md`.
- Validation guidance preserves ResolvePM's check-reporting discipline while following ADR-013: project verification commands remain project-specific.
- Template-level report formatting is deferred because ADR-012 says completion reporting consists of a skill and a future template.

## Deferred Items

Deferred because they are out of scope for Batch 2B or require admin review:

- `completion-report-template.md`
- any other template file
- role-specific completion-reporting rules
- project-specific commands such as exact lint, build, smoke, deployment, or migration commands
- dependency ordering rules, because ADR-014 places dependency ordering in governance rather than ticket-writing
- exact ResolvePM Jira comment format as a template
- ResolvePM project-specific deployment status wording

## Ambiguous Items For Admin Review

- Whether the full `AGENTS.md.backup` completion report format should become the future template verbatim.
- Whether manual git command reporting is global or scoped to Codex/Windows projects.
- Whether completion reports should always include "why it matters" or only when useful for review.
- Whether deployment status should have a dedicated future workflow or remain inside completion reporting guidance.

## What This Skill Must Not Do

This skill must not:

- create templates
- define role responsibilities
- replace project-specific verification commands
- claim validation requirements are identical across all projects
- move dependency ordering rules out of governance
- promote ResolvePM project-specific deployment, Jira, Supabase, Vercel, or CP-ticket details into global ResolveOS guidance
- weaken implementation honesty, blocker reporting, or uncertainty reporting into vague status-report language
