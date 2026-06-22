---
type: template
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-residual-audit.md
  - migration-review.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
  - DEBUGGING.md
related_context:
  - 01-context/missing-context-behaviour.md
related_skills:
  - 03-skills/completion-reporting.md
related_workflows:
  - 05-workflows/implementation-review-loop.md
related_governance:
  - 06-governance/decision-maker-reporting.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Provide the canonical ResolveOS blocker report template.

Use this template to communicate blockers, missing context, failed validation, dependency issues, contradictory information, technical uncertainty, escalation needs, and required decisions.

This template implements existing ResolveOS blocker, missing-context, completion-reporting, implementation-review, and decision-maker-reporting behaviour. It is a communication structure, not a behavioural definition.

Source references:

- `01-context/missing-context-behaviour.md` > `Stop And Explain`
- `01-context/missing-context-behaviour.md` > `Missing Context Behaviour`
- `05-workflows/implementation-review-loop.md` > `Blocker Handling`
- `05-workflows/implementation-review-loop.md` > `Failed Validation Handling`
- `03-skills/completion-reporting.md` > `Reporting Blockers`
- `06-governance/decision-maker-reporting.md` > `Required Reporting Layers`
- `AGENTS.md.backup` > `If blocked`
- `AGENTS.md.backup` > stuck-loop blocker comment format
- `migration/resolvepm-residual-audit.md` > `blocker-report-template.md`

# Template

Use the sections below as the blocker report structure.

The report should let a reviewer quickly answer:

- What are we trying to achieve?
- What is blocking progress?
- Why does the blocker matter?
- Can we safely proceed?
- What options exist?
- What decision is required?
- What should happen next?

# Blocker Summary

```text
Status:
- Blocked / Partially complete / Failed validation / Missing context / Dependency issue / Requires decision

Short summary:
- [Plain-English summary of the blocker.]
```

# What We Are Trying To Achieve

```text
Ticket, task, source item, approved batch, or scope:
- [Identifier and title, if available.]

Objective:
- [Plain-English statement of the intended outcome.]
```

# What Is Blocking Progress

```text
Current blocker:
- [Specific error, missing context, missing credential, unclear decision, dependency issue, contradictory source, failed validation, configuration issue, architecture problem, or prerequisite.]

Where it appears:
- [Command, file, page, route, source item, validation step, dependency, or context source.]

What happened:
- [Plain-English summary of the observed issue.]
```

# Why This Matters

```text
Impact:
- [What cannot be completed, validated, reviewed, accepted, deployed, or safely decided yet.]
```

# Why It Cannot Be Safely Worked Around

```text
Reason:
- [Why continuing would require guessing, invented context, fake functionality, unsafe implementation, unsupported assumptions, hidden risk, or ignored governance.]
```

# Information Missing

```text
Missing information, credential, config, source file, prerequisite, validation evidence, or decision:
-

Why it is needed:
-
```

# Options Considered

```text
Option 1:
- [Option]
- Benefit:
- Risk:
- Why accepted or rejected:

Option 2:
- [Option]
- Benefit:
- Risk:
- Why accepted or rejected:
```

# Highest-Leverage Unblocker

```text
Highest-leverage unblocker:
- [The action expected to most effectively resolve, narrow, or safely escalate the blocker.]
```

# Decision Required

```text
Decision needed:
- [Admin, role, source-owner, stakeholder, project owner, or reviewer decision required.]

Decision owner:
- [Admin / Product Manager / Business Analyst / QA Tester / Technical Strategy Lead / Implementation Engineer / Strategic Product Director / Project owner / Unknown]

Decision options:
-
```

# Risks Of Proceeding

```text
-
```

# Risks Of Not Proceeding

```text
-
```

# Related Tickets / Dependencies

```text
Related tickets, source items, prerequisites, dependencies, blocker notes, or follow-up work:
-
```

# Verification Status

```text
Verification status:
- Verified blocker / Partially verified / Not verified / Inferred / Requires admin review

Evidence:
-

Validation performed:
-

Validation not performed:
-

Limitations:
-
```

# Notes

```text
-
```

# Usage Guidance

Use this template when progress is blocked by missing context, failed validation, dependency issues, contradictory information, technical uncertainty, source-of-truth uncertainty, repeated failure, or a required decision.

This template inherits behaviour from:

- `01-context/missing-context-behaviour.md`
- `05-workflows/implementation-review-loop.md`
- `03-skills/completion-reporting.md`
- `06-governance/decision-maker-reporting.md`

Do not use this template to redefine blocker handling, missing-context rules, escalation authority, validation requirements, workflow sequence, or role responsibility.

If the blocker is a failed check or validation step, include the first clear failure where practical and say whether the failure appears related to the scoped work.

If the blocker is missing context, name the exact missing context. Do not use vague phrasing such as "context is unclear" when the missing item can be identified.

If a source-system or ticket comment is required, use this template as the structure but keep source-system-specific fields and posting rules in project context.

# Example

```text
Blocker Summary

Status:
- Blocked

Short summary:
- The requested implementation depends on acceptance criteria that are not available.

What We Are Trying To Achieve

Ticket, task, source item, approved batch, or scope:
- Current approved implementation task

Objective:
- Implement the requested change without expanding scope or inventing acceptance conditions.

What Is Blocking Progress

Current blocker:
- Missing acceptance criteria.

Where it appears:
- The available task context has an objective, but no testable completion conditions.

What happened:
- I can describe the likely work, but I cannot verify what success should look like.

Why This Matters

Impact:
- Implementation would require guessing what counts as complete.

Why It Cannot Be Safely Worked Around

Reason:
- Guessing acceptance criteria could create invented scope and a false completion claim.

Information Missing

Missing information, credential, config, source file, prerequisite, validation evidence, or decision:
- Acceptance criteria or admin approval to draft criteria for review.

Why it is needed:
- The work cannot be honestly reported as complete without a way to validate it.

Options Considered

Option 1:
- Stop and ask for acceptance criteria.
- Benefit: safest and most accurate.
- Risk: pauses implementation.
- Why accepted or rejected: accepted as the recommended path.

Option 2:
- Draft criteria for review.
- Benefit: may help unblock planning.
- Risk: cannot be treated as approved implementation scope.
- Why accepted or rejected: usable only if admin approves a draft.

Highest-Leverage Unblocker

Highest-leverage unblocker:
- Provide acceptance criteria or approve a clearly marked draft for review.

Decision Required

Decision needed:
- Whether to provide criteria or allow draft criteria for review.

Decision owner:
- Admin

Risks Of Proceeding

- Invented requirements.
- False completion.
- Scope drift.

Risks Of Not Proceeding

- The task remains blocked.

Related Tickets / Dependencies

- Current task context.

Verification Status

Verification status:
- Verified blocker

Evidence:
- Acceptance criteria are absent from the available context.

Validation performed:
- Reviewed available task context.

Validation not performed:
- Implementation validation.

Limitations:
- No implementation was attempted.

Notes

- This is a blocker report, not a request to expand scope.
```

# Anti-Patterns

Do not:

- hide blockers
- silently work around blockers
- make partial, blocked, failed, or not-verified work sound complete
- continue by inventing missing context, requirements, schema, credentials, configuration, validation evidence, or source facts
- omit why continuing would be unsafe when the blocker affects safe progress
- omit what decision or information is required
- bury risks inside vague wording
- report only technical errors when a reviewer needs decision context
- turn the blocker report into implementation scope
- make project-specific source-system, command, route, ticket-key, or deployment rules global
- redefine blocker handling, missing-context behaviour, workflow sequence, role authority, or completion-reporting behaviour

# Related Context

- `01-context/missing-context-behaviour.md`

# Related Skills

- `03-skills/completion-reporting.md`

# Related Workflows

- `05-workflows/implementation-review-loop.md`

# Related Governance

- `06-governance/decision-maker-reporting.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred because they belong in future templates, skills, workflows, governance, or project context:

- source-tracker blocker comment template
- debugging-support skill
- implementation-review skill
- dependency-management skill
- decision-log template
- exact source-system posting rules
- project-specific command lists, routes, provider names, environment variables, deployment targets, ticket keys, and local paths
- formal maximum failed-attempt count before stopping

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether source-tracker blocker comments should be mandatory when source-system access exists
- whether every blocker report must include options considered
- whether `Risks Of Not Proceeding` should be required for small blockers or marked `Not applicable`
- whether dependency blockers need a separate dependency report template
- whether repeated-failure blockers should use this template or a future debugging-support template

# What This Template Must Not Do

This template must not:

- define blocker-handling behaviour
- replace `01-context/missing-context-behaviour.md`
- replace `05-workflows/implementation-review-loop.md`
- replace `03-skills/completion-reporting.md`
- create role authority or escalation authority
- create workflow sequence
- define project-specific verification commands
- promote ResolvePM project doctrine into ResolveOS
