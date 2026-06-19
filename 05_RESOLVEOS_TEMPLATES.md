---
type: knowledge_bundle
scope: global
owner: ResolveOS
source_repository: https://github.com/simeonfab/ResolveOS
source_commit: 83eace0995e7699e3ed6e38c0a92a52fcec60e1e
generated: true
generated_date: 2026-06-19
included_paths:
  - 04-templates/blocker-report-template.md
  - 04-templates/briefing-template.md
  - 04-templates/chat-handoff-template.md
  - 04-templates/completion-report-template.md
  - 04-templates/decision-log-template.md
  - 04-templates/role-prompt-template.md
  - 04-templates/ticket-context-template.md
---

# Source: 04-templates/blocker-report-template.md

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

---

# Source: 04-templates/briefing-template.md

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
  - docs/project-context/implementation-workflow.md
  - docs/codex-briefings/
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/missing-context-behaviour.md
  - 01-context/project-loading-rules.md
related_templates:
  - 04-templates/ticket-context-template.md
  - 04-templates/blocker-report-template.md
  - 04-templates/completion-report-template.md
related_workflows:
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/implementation-review-loop.md
related_governance:
  - 06-governance/decision-maker-reporting.md
  - 06-governance/architecture-decisions.md
  - 06-governance/source-of-truth-rules.md
review_required: true
---

# Purpose

Provide the canonical ResolveOS briefing template.

A briefing captures reviewed context for a role, task, ticket, project, decision, or implementation session when direct source-system context may be incomplete, scattered, inaccessible, or in need of consolidation.

This template supports context loading, ticket context, role loading, project loading, implementation planning, review, and decision-making. It is a briefing structure, not a source-of-truth replacement, workflow, skill, role, ticket template, or approval record.

Source references:

- `04-templates/ticket-context-template.md` > source, scope, missing context, validation, next action
- `01-context/role-loading-rules.md` > role, project, briefing, and ticket context
- `01-context/project-loading-rules.md` > project context and traceability
- `01-context/missing-context-behaviour.md` > approved briefing fallback and limitations
- `05-workflows/ticket-to-implementation.md` > approved briefing when source-system access is unavailable
- `05-workflows/implementation-review-loop.md` > missing context and evidence handling
- `06-governance/decision-maker-reporting.md` > decision-maker context
- `AGENTS.md.backup` > short task understanding and persistent context discipline
- `docs/project-context/implementation-workflow.md` > briefing files
- `docs/codex-briefings/` > repeated briefing structures
- `migration/resolvepm-residual-audit.md` > `briefing-template.md`

# Template

Use the sections below as the briefing structure.

The briefing should let a reviewer quickly answer:

- What context is being consolidated?
- Which sources informed it?
- What are we trying to achieve?
- Why does it matter?
- What is approved?
- What is excluded?
- Which decisions, constraints, dependencies, risks, assumptions, and missing context matter?
- Which roles, skills, validation, review, or next action should be loaded?

# Briefing Title

```text
[Short title for the role, task, ticket, project, decision, implementation session, or context area.]
```

# Purpose

```text
[Why this briefing exists and what work or decision it supports.]
```

# Source Context

```text
Canonical source system or source files:
-

Source status:
- Current / Draft / Reviewed / Incomplete / Inaccessible / Stale / Contradictory / Unknown

Source facts:
-

Interpretation or synthesis:
-

Source limitations:
-
```

# What We Are Trying To Achieve

```text
[Plain-English statement of the intended objective or outcome.]
```

# Why It Matters

```text
[Short explanation of the product, operational, delivery, review, decision, technical, or admin value.]
```

# Background

```text
Relevant background:
-

Prior context, ticket sequence, decision, review, or project state:
-
```

# Approved Scope

```text
In scope:
-

Approved use of this briefing:
-
```

# Out Of Scope

```text
Not included:
-

Future work, adjacent work, or tempting extras that must not be started from this briefing:
-
```

# Key Decisions

```text
Known decisions:
-

Decision owner or source:
-

Decision status:
- Approved / Draft / Needs review / Superseded / Unknown
```

# Constraints

```text
Product, business, technical, security, cost, configuration, source-of-truth, role-boundary, or workflow constraints:
-
```

# Dependencies

```text
Prerequisites:
-

Related dependency state:
- Complete / Incomplete / Unknown / Blocked / Not applicable

Dependency notes:
-
```

# Risks

```text
Risks:
-

Risk impact:
-
```

# Assumptions

```text
Known assumptions:
-

Assumptions requiring review:
-
```

# Missing Context

```text
Missing, stale, contradictory, inaccessible, ambiguous, or unsupported context:
-

Why it matters:
-

Approved fallback, if any:
-

Limitation of fallback:
-
```

# Relevant Roles

```text
Primary role:
- [Role]

Supporting roles:
-

Role-loading notes:
-
```

# Relevant Skills

```text
Relevant skills:
-

Skill-loading notes:
-
```

# Validation / Review Expectations

```text
Review needed:
-

Validation expected:
-

What confirms this briefing is usable:
-
```

# Highest-Leverage Activity

```text
Highest-leverage activity:
-

Owner:
- Admin / Product Manager / Business Analyst / QA Tester / Technical Strategy Lead / Implementation Engineer / Strategic Product Director / Project owner / Unknown

Top 3 recommended actions:
- [prioritised, concrete, outcome-focused, practical, time-bounded where possible]
- [prioritised, concrete, outcome-focused, practical, time-bounded where possible]
- [prioritised, concrete, outcome-focused, practical, time-bounded where possible]
```

# Notes

```text
-
```

# Usage Guidance

Use this template when context needs to be consolidated before a role, task, ticket, project, decision, implementation, review, or migration session.

This template inherits behaviour from:

- `01-context/context-loading-rules.md`
- `01-context/role-loading-rules.md`
- `01-context/project-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`
- `06-governance/decision-maker-reporting.md`

Briefings may support ticket context, role loading, project loading, implementation planning, or decision-making when source context is scattered, inaccessible, or needs consolidation.

Briefings do not replace canonical source systems unless explicitly approved as fallback context.

When a briefing is used as fallback context, state:

- what source context is unavailable
- why the briefing is allowed as fallback
- what limitation remains
- what source update, admin review, or verification is still needed

Keep source facts separate from interpretation, assumptions, and recommendations.

If this briefing reveals a blocker, use `04-templates/blocker-report-template.md`.

If this briefing is used to populate ticket context, use `04-templates/ticket-context-template.md`.

# Example

```text
Briefing Title

Current implementation session briefing

Purpose

Capture reviewed context for an implementation session where the source ticket exists but comments and dependencies are scattered across project files.

Source Context

Canonical source system or source files:
- Source ticket
- Current focus
- Project context

Source status:
- Reviewed

Source facts:
- The source ticket defines the current objective.
- A project context file identifies a prerequisite.

Interpretation or synthesis:
- The current ticket can proceed only after the prerequisite state is confirmed.

Source limitations:
- Source-system comments may not be fully loaded.

What We Are Trying To Achieve

Make the implementation context clear enough to start safely or report a blocker.

Why It Matters

The implementer needs enough context to avoid guessing, hidden scope expansion, and false completion.

Background

Relevant background:
- The work belongs to an approved ticket sequence.

Prior context, ticket sequence, decision, review, or project state:
- Previous-ticket state may affect whether the current ticket can start.

Approved Scope

In scope:
- Load current ticket context.
- Confirm prerequisite state.
- Identify blockers before implementation.

Approved use of this briefing:
- Context loading and implementation planning.

Out Of Scope

Not included:
- Future ticket implementation.
- Project roadmap changes.

Future work, adjacent work, or tempting extras that must not be started from this briefing:
- Adjacent refactors.

Key Decisions

Known decisions:
- Current ticket first.

Decision owner or source:
- ResolveOS workflow and project source context.

Decision status:
- Approved

Constraints

Product, business, technical, security, cost, configuration, source-of-truth, role-boundary, or workflow constraints:
- Do not start future tickets unless explicitly asked.

Dependencies

Prerequisites:
- Previous-ticket outcome should be checked.

Related dependency state:
- Unknown

Risks

Risks:
- Starting without dependency confirmation may create false completion risk.

Risk impact:
- Implementation may need to stop and report a blocker.

Assumptions

Known assumptions:
- The source ticket remains the primary scope source.

Assumptions requiring review:
- Whether the previous ticket is complete enough.

Missing Context

Missing, stale, contradictory, inaccessible, ambiguous, or unsupported context:
- Previous-ticket outcome.

Why it matters:
- It may affect implementation safety.

Approved fallback, if any:
- Use available briefing only for planning, not for claiming source-system status.

Limitation of fallback:
- Source-system status cannot be reported as updated unless actually updated.

Relevant Roles

Primary role:
- Implementation Engineer

Supporting roles:
- Technical Strategy Lead, if dependency sequencing is blocked.

Relevant Skills

Relevant skills:
- ticket-writing
- acceptance-criteria
- completion-reporting

Validation / Review Expectations

Review needed:
- Confirm the briefing accurately reflects source context.

Validation expected:
- Confirm prerequisite state before implementation.

What confirms this briefing is usable:
- The current ticket, scope, dependency, and next action are clear.

Highest-Leverage Activity

Highest-leverage activity:
- Check previous-ticket outcome and then populate ticket context.

Owner:
- Implementation Engineer

Top 3 recommended actions:
- Confirm previous-ticket outcome.
- Populate ticket context from source evidence.
- Identify any blocker or missing prerequisite before implementation starts.

Notes

- This briefing is not implementation approval by itself.
```

# Anti-Patterns

Do not:

- invent missing facts
- blur source facts, assumptions, interpretations, and recommendations
- treat a briefing as canonical source-system truth unless explicitly approved as fallback context
- use a briefing to start implementation when child ticket scope or approved scope is missing
- hide missing, stale, contradictory, inaccessible, ambiguous, or unsupported context
- omit source limitations
- silently expand scope
- use project-specific ticket keys, routes, product doctrine, local commands, provider names, deployment targets, or roadmap details as global ResolveOS content
- turn this template into a role, skill, workflow, governance file, ticket template, or source-of-truth replacement

# Related Templates

- `04-templates/ticket-context-template.md`
- `04-templates/blocker-report-template.md`
- `04-templates/completion-report-template.md`

# Related Context

- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- `01-context/project-loading-rules.md`

# Related Workflows

- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`

# Related Governance

- `06-governance/decision-maker-reporting.md`
- `06-governance/architecture-decisions.md`
- `06-governance/source-of-truth-rules.md`

# Deferred Items

Deferred because they belong in future templates, skills, workflows, governance, or project context:

- role prompt template
- decision log template
- source-tracker comment template
- epic completion summary template
- phase-readiness review template
- dependency-management skill
- requirement-traceability skill
- backlog-refinement skill
- documentation update assessment skill or governance
- project-specific briefing fields, ticket keys, local commands, routes, deployment targets, provider names, environment variables, roadmap themes, and product terminology

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether briefings require explicit admin approval before they can be used as fallback context
- whether every briefing must separate `Source facts` from `Interpretation or synthesis`
- whether epic briefings should use this general briefing template or a future epic-specific template
- whether briefings should include a formal freshness or last-reviewed field
- whether role-loading notes should remain inside this template or be handled only by `01-context/role-loading-rules.md`

# What This Template Must Not Do

This template must not:

- replace canonical source systems
- replace `01-context/missing-context-behaviour.md`
- replace `01-context/role-loading-rules.md`
- replace `01-context/project-loading-rules.md`
- replace `04-templates/ticket-context-template.md`
- approve implementation scope
- define role authority
- define workflow sequence
- create project-specific doctrine in ResolveOS

---

# Source: 04-templates/chat-handoff-template.md

---
type: template
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolveos-architecture-review.md
  - migration/template-layer-review.md
  - migration/resolvepm-residual-audit.md
  - AGENTS.md.backup
related_context:
  - 01-context/running-context.md
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
related_templates:
  - 04-templates/briefing-template.md
  - 04-templates/completion-report-template.md
  - 04-templates/blocker-report-template.md
  - 04-templates/decision-log-template.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/update-process.md
  - 06-governance/duplication-control.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Provide the canonical ResolveOS chat handoff template for migrating context from one long chat, Codex session, or agent session to another.

A chat handoff preserves session continuity when a chat becomes too long, stale, interrupted, or needs migration.

This is a concise context-transfer structure. It is not a transcript template, running-context replacement, completion report, blocker report, briefing, decision log, workflow, skill, role, or governance file.

Source references:

- `01-context/running-context.md` > current-state focus
- `06-governance/update-process.md` > update ownership and running-context update rules
- `06-governance/duplication-control.md` > avoid duplicate context dumps
- `06-governance/decision-maker-reporting.md` > reviewability
- `migration/resolveos-architecture-review.md` > running-context integration gap

# Template

Use this structure when a new chat, session, or agent needs enough context to continue without relying on memory.

# Handoff Title

```text
[Short title for the handoff.]
```

# Date Created

```text
[YYYY-MM-DD]
```

# Source Chat / Session

```text
Source chat, Codex session, agent session, thread, or context source:
-

Reason for handoff:
- Long-running chat / stale context / interruption / session migration / role switch / other
```

# Current Objective

```text
[Plain-English statement of the current objective.]
```

# What Has Been Completed

```text
Completed work:
-

Evidence:
-
```

# Current State

```text
Current state:
-

Current phase:
-

Current scope:
-
```

# Decisions Made

```text
Decisions made in this session:
-

Related ADRs or decision logs:
-
```

# Open Decisions

```text
Open decisions:
-

Decision owner:
-
```

# Active Risks

```text
Active risks:
-

Risk owner or reviewer:
-
```

# Blockers

```text
Current blockers:
-

Needed context, source, credential, prerequisite, or decision:
-
```

# Next Recommended Step

```text
Next recommended step:
-

Why this is next:
-
```

# Source-Of-Truth References

```text
Canonical files, tickets, source systems, reports, or project records:
-

Context that must be loaded before continuing:
-
```

# Files Changed Or Relevant Files

```text
Files changed:
-

Relevant files not changed:
-
```

# What Not To Repeat

```text
Do not repeat:
-
```

# Notes

```text
-
```

# Usage Guidance

Use this template for:

- ChatGPT chat migration
- Codex session migration
- long-running project handoff
- role-switch handoff
- interrupted work recovery
- concise non-technical review of current session state

Keep the handoff short.

The handoff should preserve:

- current objective
- completed work
- current state
- unresolved decisions
- active risks
- blockers
- next recommended step
- source-of-truth references

Use running context for shared current ResolveOS state.

Use a chat handoff when session-specific continuity is needed or when running context should not be bloated with chat-specific detail.

# Anti-Patterns

Do not:

- turn the handoff into a full transcript
- duplicate running context
- duplicate migration reports
- duplicate ADRs
- hide blockers or uncertainty
- claim files, tests, commits, pushes, tickets, deployments, or source-system updates happened without evidence
- include project-specific secrets, credentials, or private local details
- use a handoff to approve new scope
- use a handoff to bypass source-of-truth loading

# Related Context

- `01-context/running-context.md`
- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`

# Related Templates

- `04-templates/briefing-template.md`
- `04-templates/completion-report-template.md`
- `04-templates/blocker-report-template.md`
- `04-templates/decision-log-template.md`

# Related Governance

- `06-governance/source-of-truth-rules.md`
- `06-governance/update-process.md`
- `06-governance/duplication-control.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred because they belong elsewhere:

- source-system posting format belongs in a future source-tracker handoff/comment template
- full project briefing structure belongs in `04-templates/briefing-template.md`
- completion status reporting belongs in `04-templates/completion-report-template.md`
- blocker reporting belongs in `04-templates/blocker-report-template.md`
- durable decision rationale belongs in `04-templates/decision-log-template.md`

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether chat handoff files should be stored in projects, temporary migration folders, or generated ad hoc
- whether chat handoffs should include branch and commit state by default for Codex sessions
- whether handoffs should include a maximum length guideline

# What This Template Must Not Do

This template must not:

- replace running context
- replace briefing templates
- replace completion reports
- replace blocker reports
- replace decision logs
- become a transcript format
- create role, skill, workflow, or governance behaviour
- promote project-specific doctrine into ResolveOS

---

# Source: 04-templates/completion-report-template.md

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
related_roles:
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/qa-tester.md
  - 02-roles/technical-strategy-lead.md
  - 02-roles/implementation-engineer.md
  - 02-roles/strategic-product-director.md
related_skills:
  - 03-skills/completion-reporting.md
related_workflows:
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/implementation-review-loop.md
related_governance:
  - 06-governance/decision-maker-reporting.md
  - 06-governance/architecture-decisions.md
  - 06-governance/source-of-truth-rules.md
review_required: true
---

# Purpose

Provide the canonical ResolveOS completion report template for completed, partial, blocked, failed, deferred, or not-verified work.

This template implements existing completion-reporting, decision-maker-reporting, ticket-to-implementation, and implementation-review behaviour. It is a communication structure, not a behavioural definition.

Use this template to make completion reports readable for non-technical review and specific enough for technical validation.

Source references:

- `06-governance/decision-maker-reporting.md` > `Required Reporting Layers`
- `03-skills/completion-reporting.md` > `Outputs`
- `05-workflows/ticket-to-implementation.md` > `Completion Reporting`
- `05-workflows/implementation-review-loop.md` > `Outputs`
- `AGENTS.md.backup` > required completion format
- `migration/resolvepm-residual-audit.md` > `completion-report-template.md`

# Template

Use the sections below as the completion report structure.

Keep the report as short as the work allows, but do not remove sections that are needed to answer:

- Did the AI understand the objective?
- Did it solve the correct problem?
- Did it stay within scope?
- What changed?
- How was it validated?
- What risks remain?
- What should happen next?

# Ticket

```text
Ticket, task, source item, approved batch, or scope:
- [Identifier and title]

Status:
- Complete / Partially complete / Blocked / Failed / Not verified / Deferred
```

# What I Think We Are Achieving

```text
[Plain-English statement of the objective, problem being solved, intended outcome, and scope.]

Assumptions:
-

Non-goals or out-of-scope items:
-
```

# What Was Achieved

```text
[Plain-English summary of what was actually completed, found, changed, reviewed, or produced.]
```

# Why It Matters

```text
[Short explanation of the business, product, operational, review, delivery, or validation impact.]
```

# Did This Differ From The Original Plan?

```text
No / Yes / Not applicable

If yes:
- Original plan:
- What changed:
- Why it changed:
- Impact:
- Follow-up needed:
```

# Implementation Summary

```text
Implementation path:
- [Brief explanation of the actual steps taken.]

Technical impact:
- [Technical change, dependency, architecture, integration, data, configuration, or documentation impact.]

Business or product impact:
- [User-facing, stakeholder, workflow, requirement, prioritisation, or acceptance impact.]
```

# Files Created

```text
-
```

# Files Updated

```text
-
```

# Validation Performed

```text
Checks, tests, review steps, or validation performed:
-

Result:
- Passed / Failed / Partial / Not run / Not applicable

What this proves:
-

Validation not performed:
-

Why not performed:
-

Residual validation risk:
-
```

# Scope Completed

```text
-
```

# Scope Deferred

```text
-

Reason deferred:
-
```

# Known Issues

```text
-
```

# Risks

```text
-
```

# Blockers

```text
Current blocker:
- [Specific missing context, failed check, credential, configuration, prerequisite, source file, admin decision, or architecture issue.]

Why continuing would be unsafe or unsupported:
-

Needed input, config, source, credential, prerequisite, or decision:
-

Highest-leverage unblocker or follow-up action:
-
```

# Suggested Follow-Up Work

```text
Suggested follow-up tickets or tasks:
-

Why separate:
-

Required or optional:
-
```

# Next Recommended Ticket

```text
-
```

# Verification Status

```text
Verification status:
- Verified / Partially verified / Not verified / Blocked / Failed / Requires admin review

Evidence:
-

Limitations:
-
```

# Notes

```text
-
```

# Usage Guidance

Use this template after implementation, migration, review, debugging, validation, failed work, blocked work, or deferred work when a structured completion report is needed.

This template inherits behaviour from:

- `03-skills/completion-reporting.md`
- `06-governance/decision-maker-reporting.md`
- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`

Do not use this template to redefine completion honesty, validation rules, role authority, workflow sequence, source-of-truth precedence, or project-specific verification commands.

For checks or commands that were run, report the method and result. For checks or commands not run, say they were not run, explain why, and state the residual risk.

Follow-up work must remain separate from completed scope unless the admin explicitly approves expanding the current scope.

# Example

```text
Ticket

Ticket, task, source item, approved batch, or scope:
- Batch 4C.2.1B - Completion Report Template

Status:
- Complete for the requested scope

What I Think We Are Achieving

Create a reusable completion report template that preserves ResolvePM's rich reporting structure while relying on existing ResolveOS behaviour files for rules.

What Was Achieved

Created the completion report template and added the related architecture decision.

Why It Matters

The admin and reviewers can understand intent, outcome, validation, risk, and next steps without losing technical evidence.

Did This Differ From The Original Plan?

No.

Implementation Summary

Implementation path:
- Extracted the structure from existing reporting governance, completion reporting skill, workflows, and ResolvePM source material.

Files Created

- 04-templates/completion-report-template.md

Files Updated

- 06-governance/architecture-decisions.md

Validation Performed

Checks, tests, review steps, or validation performed:
- Reviewed the created template and ADR update.

Result:
- Passed

Validation not performed:
- No project test suite was run because this is a markdown governance/template change.

Scope Completed

- Completion report template created.
- ADR added.

Scope Deferred

- Blocker report template.
- Ticket context template.

Known Issues

- None identified.

Risks

- Admin may decide a shorter default report is needed later.

Blockers

- None.

Suggested Follow-Up Work

- Create blocker report template in a later approved batch.

Next Recommended Ticket

- Create the next approved template or governance file from the migration plan.

Verification Status

Verification status:
- Requires admin review

Evidence:
- Template and ADR are present in the repository.

Notes

- This template implements existing behaviour; it does not redefine it.
```

# Anti-Patterns

Do not:

- claim work was done unless it was actually done
- claim checks, tests, deployment, commits, pushes, source-ticket updates, or admin approval happened without direct evidence
- bury failed validation, blockers, known issues, risk, deferred scope, or uncertainty
- report follow-up work as completed scope
- remove the decision-maker context when it is needed for review
- replace technical evidence with a polished business summary
- replace business impact with only file names and command output
- make project-specific commands, ticket keys, routes, tools, or deployment processes global
- turn this template into a role, skill, workflow, or governance file

# Related Skills

- `03-skills/completion-reporting.md`

# Related Workflows

- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`

# Related Governance

- `06-governance/decision-maker-reporting.md`
- `06-governance/architecture-decisions.md`
- `06-governance/source-of-truth-rules.md`

# Deferred Items

Deferred because they belong in future templates, skills, workflows, or project context:

- blocker report template
- ticket context prompt template
- briefing template
- decision log template
- exact source-tracker comment format
- implementation-review skill
- debugging-support skill
- project-specific command lists, local routes, ticket keys, deployment targets, provider names, and environment variables

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether every completion report must include every section, or whether some sections may be marked `Not applicable`
- whether `Next Recommended Ticket` should always be present or only when sequencing exists
- whether file removals should become a dedicated first-class section or be reported in `Implementation Summary` and `Notes`
- whether manual git commands should be part of a future Codex-specific template rather than this global completion report template

# What This Template Must Not Do

This template must not:

- define completion-reporting behaviour
- redefine role responsibilities
- redefine workflow sequence
- replace validation or source-of-truth governance
- promote ResolvePM product doctrine into ResolveOS
- imply that project-specific verification commands are global ResolveOS requirements

---

# Source: 04-templates/decision-log-template.md

---
type: template
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
  - AGENTS.md.backup
related_context:
  - 01-context/running-context.md
  - 01-context/context-loading-rules.md
  - 01-context/project-loading-rules.md
related_templates:
  - 04-templates/completion-report-template.md
  - 04-templates/blocker-report-template.md
  - 04-templates/briefing-template.md
related_governance:
  - 06-governance/decision-maker-reporting.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Provide the canonical ResolveOS decision-log template.

Use this template to capture durable decisions, rationale, alternatives considered, trade-offs, risks accepted, consequences, and follow-up actions without relying on chat history, memory, or informal notes.

This template supports both technical and non-technical review. It exists to preserve why a decision was made, not merely what was decided.

This is a communication structure. It is not an ADR, changelog, ticket history, implementation report, workflow, skill, role, or governance file.

Source references:

- `06-governance/decision-maker-reporting.md` > decision-maker context and required reporting layers
- `01-context/running-context.md` > source-of-truth references and deferred decision records
- `06-governance/architecture-decisions.md` > ADR rules and rationale preservation
- `04-templates/completion-report-template.md` > why it matters, drift, risks, follow-up, and verification status
- `04-templates/blocker-report-template.md` > options considered, decision required, risks, and evidence
- `04-templates/briefing-template.md` > source facts, interpretation, known decisions, constraints, assumptions, and missing context
- `migration/template-layer-review.md` > decision-log template candidate
- `migration/resolvepm-residual-audit.md` > decision and traceability residual evidence
- `AGENTS.md.backup` > implementation drift, blocker, completion, and follow-up decision concepts

# Template

Use the sections below as the decision-log structure.

The decision log should let a reviewer quickly answer:

- What decision was made?
- Why was it made?
- What alternatives were considered?
- What trade-offs were accepted?
- What risks were accepted?
- What should happen next?
- How should this decision be revisited?

# Decision

```text
Decision title:
- [Short title for the decision.]

Decision status:
- Proposed / Active / Superseded / Rejected

Short decision summary:
- [One or two plain-English sentences describing the decision.]
```

# Date

```text
Decision date:
- [YYYY-MM-DD]

Logged date, if different:
- [YYYY-MM-DD / Not applicable]
```

# Decision Owner

```text
Decision owner:
- Admin / Product Manager / Business Analyst / QA Tester / Technical Strategy Lead / Implementation Engineer / Strategic Product Director / Project owner / Other / Unknown

Reviewers or consulted roles:
-
```

# What Problem Are We Solving?

```text
[Plain-English statement of the problem, decision point, ambiguity, blocker, trade-off, risk, or opportunity that required a decision.]
```

# Why It Matters

```text
[Short explanation of the product, operational, delivery, review, technical, governance, cost, security, source-of-truth, or admin impact.]
```

# Context

```text
Relevant source context:
-

Source facts:
-

Interpretation or synthesis:
-

Assumptions:
-

Missing, stale, contradictory, inaccessible, ambiguous, or unsupported context:
-
```

# Options Considered

```text
Option 1:
- [Option]

Benefits:
-

Costs or risks:
-

Notes:
-

Option 2:
- [Option]

Benefits:
-

Costs or risks:
-

Notes:
-
```

# Recommended Option

```text
Recommended option:
- [Option]

Why this option is recommended:
-

Who recommended it:
-
```

# Final Decision

```text
Final decision:
- [The decision actually made.]

Decision status:
- Proposed / Active / Superseded / Rejected

Approval or source of decision:
-

Supersedes, if applicable:
-

Superseded by, if applicable:
-

Reason rejected, if applicable:
-
```

# Why This Option Was Chosen

```text
Rationale:
-

Evidence:
-

Why this better preserves admin intent or source-of-truth discipline:
-
```

# Trade-Offs Accepted

```text
Accepted trade-offs:
-

What this improves:
-

What this makes harder, slower, narrower, riskier, or more expensive:
-
```

# Risks Accepted

```text
Accepted risks:
-

Risk owner:
-

Mitigation or monitoring:
-

Residual uncertainty:
-
```

# Alternatives Rejected

```text
Rejected alternatives:
-

Why rejected:
-

What would need to change for reconsideration:
-
```

# Consequences

```text
Expected consequences:
-

Impact on roles, skills, workflows, templates, context, governance, project records, tickets, or source systems:
-

Potential unintended consequences:
-
```

# Follow-Up Actions

```text
Follow-up actions:
-

Owner:
-

Required or optional:
- Required / Optional / Deferred / Needs review

Due date or trigger:
-
```

# Related ADRs

```text
Related ADRs:
-

ADR relationship:
- Supports / Complements / Supersedes / Requires future ADR / Not applicable
```

# Related Tickets

```text
Related tickets, tasks, source items, briefings, blockers, reports, or project records:
-

Source-system update needed?
- Yes / No / Unknown / Project-owned
```

# Review Date

```text
Review date:
- [YYYY-MM-DD / Trigger-based / Not required / Unknown]

Review trigger:
- [Condition that should cause this decision to be revisited.]
```

# Notes

```text
-
```

# Usage Guidance

Use this template when a durable decision needs to be preserved for later review, handoff, governance, project records, or source-of-truth clarity.

Use it for decisions where the rationale matters, especially when:

- multiple options were considered
- trade-offs were accepted
- risks were accepted
- the decision affects future work
- the decision may need to be revisited
- the decision needs to be understandable to technical and non-technical reviewers
- source context is scattered or would otherwise remain only in chat history

This template inherits behaviour from:

- `06-governance/decision-maker-reporting.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`
- `01-context/running-context.md`

If the decision is an architecture decision affecting reusable ResolveOS behaviours, migration boundaries, source ownership, or future file creation, record or update the relevant ADR in `06-governance/architecture-decisions.md`.

If the decision is current working state only, update running context instead of creating a durable decision log.

If the decision belongs to a project repository, keep the decision in the project-owned source of truth and use this template only as a structure if the project adopts it.

# Example

```text
Decision

Decision title:
- Choose the next template-layer artifact.

Decision status:
- Approved

Short decision summary:
- Create the decision-log template before the source-tracker handoff template.

Date

Decision date:
- 2026-06-12

Decision Owner

Decision owner:
- Admin

Reviewers or consulted roles:
- Technical Strategy Lead, if governance impact needs review.

What Problem Are We Solving?

The template layer review identified both decision logging and source-tracker handoff as remaining gaps. The next batch needed to choose one to avoid broadening scope.

Why It Matters

Decision rationale can disappear into chat history if it is not captured. A reusable decision-log template preserves why decisions were made before source-system handoff structure is created.

Context

Relevant source context:
- migration/template-layer-review.md
- 01-context/running-context.md

Source facts:
- The template review recommends either decision-log template or source-tracker handoff/comment template.

Interpretation or synthesis:
- Decision logging is the narrower durable-context artifact.

Options Considered

Option 1:
- Create decision-log template.

Benefits:
- Preserves rationale, alternatives, trade-offs, and risks.

Costs or risks:
- Source-tracker handoff remains deferred.

Option 2:
- Create source-tracker handoff/comment template.

Benefits:
- Improves external ticket/comment updates.

Costs or risks:
- Project-specific posting rules may need more review.

Recommended Option

Recommended option:
- Create decision-log template first.

Why this option is recommended:
- It captures reusable durable decision context without requiring project-specific source-system rules.

Final Decision

Final decision:
- Create decision-log template first.

Decision status:
- Approved

Why This Option Was Chosen

Rationale:
- It preserves decision context and supports later handoff work.

Trade-Offs Accepted

Accepted trade-offs:
- Source-tracker handoff remains a future template candidate.

Risks Accepted

Accepted risks:
- Some source-system comment structure remains unresolved.

Alternatives Rejected

Rejected alternatives:
- Create both templates in one batch.

Why rejected:
- The batch should remain reviewable and avoid broadening template scope.

Consequences

Expected consequences:
- Future decisions can be captured in a consistent structure.

Follow-Up Actions

Follow-up actions:
- Consider source-tracker handoff/comment template in a later approved batch.

Related ADRs

Related ADRs:
- ADR-043

Related Tickets

Related tickets, tasks, source items, briefings, blockers, reports, or project records:
- Batch 4D.2

Review Date

Review date:
- Admin review required before active use.

Notes

- This is a decision log example, not an implementation report.
```

# Anti-Patterns

Do not:

- record only what was decided and omit why it was decided
- hide trade-offs, risks, rejected alternatives, missing context, or uncertainty
- turn this template into an implementation report
- turn this template into a changelog
- turn this template into ticket history
- duplicate ADR content when an ADR is the canonical source
- use a decision log to bypass admin approval, role authority, workflow sequence, or source-of-truth rules
- use polished wording to make an unresolved, rejected, deferred, or risky decision look final
- mix recommendations into final decisions without clearly labelling what was actually decided
- make project-specific ticket keys, commands, routes, deployment targets, provider names, product doctrine, or source-system posting rules global
- turn this template into a role, skill, workflow, or governance file

# Related Context

- `01-context/running-context.md`
- `01-context/context-loading-rules.md`
- `01-context/project-loading-rules.md`

# Related Templates

- `04-templates/completion-report-template.md`
- `04-templates/blocker-report-template.md`
- `04-templates/briefing-template.md`

# Related Governance

- `06-governance/decision-maker-reporting.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred because they belong in future templates, skills, workflows, governance, ADRs, or project context:

- source-tracker handoff/comment template
- decision-log-writing skill
- exact source-system posting rules
- project-specific decision registers or source-system fields
- project-specific approval workflows
- changelog template
- implementation report behaviour already owned by completion reporting and completion report template
- architecture decisions that should be recorded directly in ADRs

# Candidate Future Templates

Candidate future templates:

- `04-templates/source-tracker-handoff-template.md`
- `04-templates/source-tracker-comment-template.md`
- `04-templates/changelog-template.md`

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether decision logs should be stored as individual project files, grouped project records, source-system comments, or generated artifacts
- whether every decision log requires a review date or whether some may be marked `Not required`
- whether a future decision-log-writing skill is needed, or whether this template plus decision-maker reporting is enough
- whether project repositories should adopt this template directly or define project-specific decision-log variants
- whether source-system update requirements should remain in this template or move entirely to a future source-tracker handoff template

# What This Template Must Not Do

This template must not:

- replace ADRs
- replace running context
- replace project source-of-truth files
- replace completion reports
- replace blocker reports
- replace changelogs
- define role authority
- define workflow sequence
- create approval authority
- promote ResolvePM product doctrine into ResolveOS

---

# Source: 04-templates/role-prompt-template.md

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
  - docs/ai-role-prompts/implementation-engineer-prompt.md
  - docs/ai-role-prompts/technical-strategy-lead-prompt.md
  - docs/ai-role-prompts/strategic-product-director-prompt.md
  - docs/ai-roles/technical-strategy-lead.md
related_roles:
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/qa-tester.md
  - 02-roles/technical-strategy-lead.md
  - 02-roles/implementation-engineer.md
  - 02-roles/strategic-product-director.md
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/missing-context-behaviour.md
  - 01-context/project-loading-rules.md
related_templates:
  - 04-templates/briefing-template.md
  - 04-templates/ticket-context-template.md
related_governance:
  - 06-governance/decision-maker-reporting.md
  - 06-governance/architecture-decisions.md
  - 06-governance/source-of-truth-rules.md
review_required: true
---

# Purpose

Provide the canonical ResolveOS role-prompt template.

Use this template to create short, focused startup prompts for ResolveOS roles without flattening specialist roles or duplicating behaviour already owned by role files, governance, context files, workflows, skills, templates, or project context.

Role prompts define startup guidance and focus areas for a role. They exist to improve startup effectiveness, not to become a second role definition.

Source references:

- `01-context/role-loading-rules.md` > `Role Prompt Rules`
- `01-context/role-loading-rules.md` > `Role Files Are Canonical`
- `01-context/role-loading-rules.md` > `Load Only Relevant Context`
- `01-context/context-loading-rules.md` > `Role-Based Chat Startup`
- `01-context/project-loading-rules.md` > project context boundaries
- `04-templates/briefing-template.md`
- `04-templates/ticket-context-template.md`
- `06-governance/decision-maker-reporting.md`
- `docs/ai-role-prompts/implementation-engineer-prompt.md`
- `docs/ai-role-prompts/technical-strategy-lead-prompt.md`
- `docs/ai-role-prompts/strategic-product-director-prompt.md`
- `docs/ai-roles/technical-strategy-lead.md` > prompt generation discipline
- `migration/resolvepm-residual-audit.md` > `role-prompt-template.md`

# Template

Use the sections below as the role prompt structure.

Keep the prompt short and reference-based. Do not paste full role files, project context, tickets, briefings, skills, workflows, or governance into the prompt when those files can be referenced.

# Role

```text
Use this role:
- [ResolveOS role file path]

Act as:
- [Role name]
```

# Purpose

```text
[One or two sentences explaining why this role is being loaded for this session.]
```

# Startup Context

```text
Also load or reference:
- [ResolveOS context files]
- [ResolveOS governance files]
- [Project context files]
- [Current focus file, if relevant]
- [Briefing file, if relevant]
- [Ticket, task, source item, or approved scope, if relevant]
```

# Current Objective

```text
[Plain-English statement of the current objective.]
```

# Focus Areas

```text
Focus on:
-
```

# Success Criteria

```text
This role prompt is successful when:
-
```

# Relevant Project Context

```text
Project context to use:
-

Project-owned constraints or overrides:
-

Project context not loaded or unavailable:
-
```

# Relevant Roles

```text
Primary role:
- [Role]

Supporting roles, only if needed:
-

Why supporting roles are needed:
-
```

# Relevant Skills

```text
Relevant skills:
-

Skill-loading notes:
-
```

# Relevant Workflows

```text
Relevant workflows:
-

Workflow-loading notes:
-
```

# Decision Boundaries

```text
This role may decide or recommend:
-

This role must not decide:
-
```

# Escalation Boundaries

```text
Escalate when:
-

Escalate to:
-
```

# Reporting Expectations

```text
Report using:
- plain English
- decision-maker context where appropriate
- evidence and source references where relevant
- explicit blockers, assumptions, uncertainty, and deferred work
```

# Constraints

```text
Known constraints:
-

Temporary or unusual constraints:
-

Extra instructions and why they are necessary:
-
```

# Recommended First Actions

```text
Recommended first actions:
1. Confirm the loaded role file and active project context.
2. Confirm the current objective, ticket, task, briefing, or approved scope.
3. Identify missing context, contradictions, blockers, or role-boundary risks.
4. Proceed only within the role's authority and the approved scope.
```

# Notes

```text
-
```

# Usage Guidance

Use this template when creating a role startup prompt for a ResolveOS role.

This template inherits behaviour from:

- `01-context/role-loading-rules.md`
- `01-context/context-loading-rules.md`
- `01-context/project-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- the relevant `02-roles/` role file
- relevant skills and workflows for the current task
- `06-governance/decision-maker-reporting.md`
- `06-governance/source-of-truth-rules.md`

Role prompts should reference existing ResolveOS governance, context, roles, skills, workflows, templates, and project context rather than duplicating them.

Role prompts must not redefine role responsibilities already owned by role files.

Use longer role prompts only when required scope is missing, comments or source context reveal a blocker, the ticket contradicts the current repository state, the task is unusually risky, the admin asks for work outside the current ticket or approved scope, or design-only, planning-only, audit-only, or review-only constraints must be explicit.

If extra instructions are added, keep them minimal and explain why they are necessary.

# Example

```text
Role

Use this role:
- 02-roles/implementation-engineer.md

Act as:
- Implementation Engineer

Purpose

Start an implementation-focused session for the current approved ticket.

Startup Context

Also load or reference:
- 01-context/role-loading-rules.md
- 01-context/project-loading-rules.md
- 04-templates/ticket-context-template.md
- relevant project context
- current briefing
- current ticket

Current Objective

Implement only the current approved ticket.

Focus Areas

Focus on:
- scoped implementation
- existing project patterns
- validation evidence
- blocker reporting
- completion reporting

Success Criteria

This role prompt is successful when:
- the implementation starts from the current ticket context
- no future ticket is started
- blockers and missing context are surfaced before unsafe work

Relevant Project Context

Project context to use:
- active project context and current focus

Project-owned constraints or overrides:
- project-specific verification commands and repository markers

Relevant Roles

Primary role:
- Implementation Engineer

Supporting roles, only if needed:
- Technical Strategy Lead for sequencing or dependency risk
- Product Manager for product-scope drift

Relevant Skills

Relevant skills:
- completion-reporting
- acceptance-criteria, if acceptance review is needed

Relevant Workflows

Relevant workflows:
- ticket-to-implementation
- implementation-review-loop, if blocked or failing

Decision Boundaries

This role may decide or recommend:
- local implementation path inside approved scope
- blocker or follow-up recommendations

This role must not decide:
- product scope changes
- roadmap priority
- architecture direction outside approved scope

Escalation Boundaries

Escalate when:
- implementation changes product scope
- sequencing, architecture, dependency, build, or deployment risk appears
- required context is missing

Escalate to:
- Product Manager, Technical Strategy Lead, or admin as appropriate

Reporting Expectations

Report using:
- plain English
- decision-maker context where appropriate
- validation evidence
- explicit blockers and uncertainty

Constraints

Known constraints:
- Work one ticket at a time.
- Do not create fake functionality.
- Do not claim commits, pushes, deployments, checks, or source-system updates happened unless they happened.

Recommended First Actions

1. Confirm the active project context.
2. Confirm the current ticket context.
3. Identify dependencies and blockers.
4. Implement only approved scope.
```

# Anti-Patterns

Do not:

- redefine role responsibilities already owned by role files
- flatten specialist roles into generic role behaviour
- invent role behaviour from a role name
- use a role prompt instead of loading the role file
- load every role just in case
- create large multi-role prompt stacks without a clear reason
- duplicate full content from role files, governance files, context files, workflows, skills, project context, briefings, or tickets
- let one role silently absorb another role's responsibilities
- treat ticket creation as approval authority
- use project-specific doctrine as global ResolveOS role behaviour
- turn this template into a role, skill, workflow, or governance file

# Related Context

- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- `01-context/project-loading-rules.md`

# Related Templates

- `04-templates/briefing-template.md`
- `04-templates/ticket-context-template.md`

# Related Governance

- `06-governance/decision-maker-reporting.md`
- `06-governance/architecture-decisions.md`
- `06-governance/source-of-truth-rules.md`

# Deferred Items

Deferred because they belong in future skills, workflows, governance, templates, or project context:

- role-prompt-writing skill
- role-based chat startup workflow
- duplication-control governance
- project-specific role prompt locations
- project-specific repository path requirements
- project-specific verification commands
- project-specific ticket keys, briefing files, current focus files, roadmap terms, provider names, deployment targets, and environment variables

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether role prompts should always include success criteria or only for implementation/review sessions
- whether role prompt examples should remain in `01-context/role-loading-rules.md` now that this template exists
- whether project repositories should keep local role-prompt files or generate prompts from this template on demand
- whether a separate role-prompt-writing skill is needed, or whether this template plus role-loading rules is enough
- whether multi-role prompts need a separate template

# What This Template Must Not Do

This template must not:

- replace role files
- replace `01-context/role-loading-rules.md`
- replace project context
- define role authority
- define workflow sequence
- create skills, workflows, roles, or governance
- promote ResolvePM project doctrine into ResolveOS

---

# Source: 04-templates/ticket-context-template.md

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
  - docs/project-context/implementation-workflow.md
  - docs/codex-briefings/
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/missing-context-behaviour.md
  - 01-context/project-loading-rules.md
related_skills:
  - 03-skills/ticket-writing.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/completion-reporting.md
related_workflows:
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/implementation-review-loop.md
related_governance:
  - 06-governance/decision-maker-reporting.md
  - 06-governance/architecture-decisions.md
  - 06-governance/source-of-truth-rules.md
review_required: true
---

# Purpose

Provide the canonical ResolveOS ticket-context template.

Use this template to capture enough ticket, task, source-item, or approved-batch context before work begins.

This template supports role loading, project loading, implementation planning, acceptance criteria review, blocker detection, validation planning, and completion reporting. It is a context structure, not a ticket-writing skill, acceptance-criteria skill, implementation workflow, role definition, or approval record.

Source references:

- `03-skills/ticket-writing.md` > `Inputs`
- `03-skills/ticket-writing.md` > `Ticket Structure`
- `03-skills/acceptance-criteria.md` > `Inputs`
- `05-workflows/ticket-to-implementation.md` > `Inputs`
- `05-workflows/ticket-to-implementation.md` > `Confirm Scope`
- `01-context/role-loading-rules.md` > current ticket and role-loading context
- `01-context/missing-context-behaviour.md` > missing acceptance criteria and missing context
- `06-governance/decision-maker-reporting.md` > decision-maker context
- `AGENTS.md.backup` > per-ticket startup prompt
- `migration/resolvepm-residual-audit.md` > `ticket-context-template.md`

# Template

Use the sections below as the ticket-context structure.

The template should let a reviewer quickly answer:

- What is this work trying to achieve?
- Why does it matter?
- What is approved?
- What is excluded?
- What acceptance criteria must be satisfied?
- What dependencies or blockers exist?
- How will success be validated?
- What should not be started yet?

# Ticket

```text
Ticket, task, source item, approved batch, or scope:
- [Identifier]

Source system or source file:
- [Jira, GitHub issue, project document, briefing, admin instruction, or other source]

Source status:
- Draft / Approved / In review / Blocked / In progress / Complete / Unknown
```

# Title

```text
[Short title that describes the intended outcome.]
```

# What We Are Trying To Achieve

```text
[Plain-English statement of what the work is trying to achieve.]
```

# Why It Matters

```text
[Short explanation of the product, business, operational, delivery, review, or technical value.]
```

# Background

```text
Relevant context:
-

Source notes or comments:
-

Previous-ticket or briefing context, if relevant:
-
```

# Approved Scope

```text
In scope:
-

Approved implementation, review, planning, migration, or analysis work:
-
```

# Out Of Scope

```text
Not included:
-

Future tickets, adjacent work, or tempting extras that must not be started yet:
-
```

# Acceptance Criteria

```text
Acceptance criteria:
-

Acceptance criteria source:
- Ticket / Source item / Briefing / Admin instruction / Draft for review / Missing

If acceptance criteria are missing or incomplete:
- [Name the gap. Do not guess missing acceptance criteria.]
```

# Constraints

```text
Technical constraints:
-

Product, business, security, cost, configuration, source-of-truth, or role-boundary constraints:
-
```

# Dependencies

```text
Prerequisites:
-

Related dependency state:
- Complete / Incomplete / Unknown / Blocked / Not applicable

Dependency notes:
-
```

# Assumptions

```text
Known assumptions:
-

Assumptions requiring review:
-
```

# Risks

```text
Implementation, validation, delivery, security, cost, dependency, source-of-truth, or scope risks:
-
```

# Missing Context

```text
Missing, stale, contradictory, inaccessible, ambiguous, or unsupported context:
-

Why it matters:
-

Approved fallback, if any:
-
```

# Validation Expectations

```text
Validation or review expected:
-

Manual test expectations:
-

Project-specific checks or commands, if provided by project context:
-

What confirms success:
-
```

# Documentation Expectations

```text
Documentation or persistent context likely affected:
-

Documentation update required in this scope?
- Yes / No / Unknown / Follow-up

Notes:
-
```

# Related Tickets

```text
Previous ticket, if sequencing matters:
-

Follow-up, prerequisite, dependency, blocker, or related tickets:
-
```

# Current Status

```text
Status:
- Ready for implementation / Ready for review / Needs clarification / Blocked / Partially ready / Draft only / Unknown

Reason:
-
```

# Highest-Leverage Activity

```text
Highest-leverage activity:
-

Owner:
- Admin / Product Manager / Business Analyst / QA Tester / Technical Strategy Lead / Implementation Engineer / Strategic Product Director / Project owner / Unknown

Top 3 recommended actions:
-
-
-
```

# Notes

```text
-
```

# Usage Guidance

Use this template before work begins when a ticket, task, source item, approved batch, or briefing needs to be loaded into a ResolveOS-enabled session.

This template inherits behaviour from:

- `03-skills/ticket-writing.md`
- `03-skills/acceptance-criteria.md`
- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`
- `01-context/role-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- `01-context/project-loading-rules.md`
- `06-governance/decision-maker-reporting.md`

Do not use this template to approve work, write new ticket rules, define acceptance criteria behaviour, redefine implementation workflow sequence, or override project source-of-truth rules.

If acceptance criteria are missing, mark them as missing. Do not guess them.

If the work is based on an approved fallback such as a briefing, state the fallback and its limitation.

If context reveals a blocker, use `04-templates/blocker-report-template.md` for the blocker report.

If work completes, use `04-templates/completion-report-template.md` for the completion report.

# Example

```text
Ticket

Ticket, task, source item, approved batch, or scope:
- CP-XX

Source system or source file:
- Source ticket

Source status:
- Approved

Title

Prepare the implementation-ready context for the current ticket.

What We Are Trying To Achieve

Make the current ticket clear enough that an implementation role can work from approved scope without guessing.

Why It Matters

The work needs enough intent, scope, acceptance, dependency, and validation context to avoid hidden scope expansion and false completion.

Background

Relevant context:
- The ticket is part of an approved sequence.

Source notes or comments:
- Comments mention a dependency that should be checked before implementation.

Approved Scope

In scope:
- Capture the current ticket context.
- Identify acceptance criteria, dependencies, and validation expectations.

Out Of Scope

Not included:
- Future ticket implementation.
- Adjacent refactors.

Acceptance Criteria

Acceptance criteria:
- Given the ticket context is loaded, when implementation planning starts, then the implementer can identify objective, scope, exclusions, dependencies, and validation expectations.

Acceptance criteria source:
- Ticket

Constraints

Technical constraints:
- Use existing project patterns.

Product, business, security, cost, configuration, source-of-truth, or role-boundary constraints:
- Do not expand current scope without admin approval.

Dependencies

Prerequisites:
- Previous ticket outcome should be checked because sequencing matters.

Related dependency state:
- Unknown

Assumptions

Known assumptions:
- The source ticket is the current source of detailed scope.

Risks

Implementation, validation, delivery, security, cost, dependency, source-of-truth, or scope risks:
- Missing dependency state may block implementation.

Missing Context

Missing, stale, contradictory, inaccessible, ambiguous, or unsupported context:
- Previous-ticket outcome is not yet checked.

Why it matters:
- It may affect whether the current ticket can start safely.

Validation Expectations

Validation or review expected:
- Confirm acceptance criteria are present and testable.

Manual test expectations:
- Not applicable at context-loading stage.

What confirms success:
- Context is ready or blocker is reported clearly.

Documentation Expectations

Documentation or persistent context likely affected:
- Unknown.

Documentation update required in this scope?
- Unknown

Related Tickets

Previous ticket, if sequencing matters:
- Previous sequence item.

Follow-up, prerequisite, dependency, blocker, or related tickets:
- To be identified if dependency is incomplete.

Current Status

Status:
- Needs clarification

Reason:
- Previous-ticket state needs checking before implementation starts.

Highest-Leverage Activity

Highest-leverage activity:
- Check the previous ticket outcome and current repository state before implementation.

Owner:
- Implementation Engineer

Top 3 recommended actions:
- Confirm previous-ticket outcome.
- Check current repository state.
- Identify any blocker or missing prerequisite before implementation starts.

Notes

- This context does not authorise future-ticket implementation.
```

# Anti-Patterns

Do not:

- use this template to start future tickets unless explicitly asked
- treat an epic or briefing as implementation approval when child implementation scope is missing
- silently expand scope
- hide out-of-scope items
- guess missing acceptance criteria
- invent requirements, dependencies, validation expectations, source facts, or project context
- treat ticket creation or context capture as approval authority
- omit dependencies or blockers because they are inconvenient
- make project-specific ticket keys, commands, routes, deployment targets, provider names, or product doctrine global
- turn this template into a role, skill, workflow, or governance file

# Related Context

- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `01-context/missing-context-behaviour.md`
- `01-context/project-loading-rules.md`

# Related Skills

- `03-skills/ticket-writing.md`
- `03-skills/acceptance-criteria.md`
- `03-skills/completion-reporting.md`

# Related Workflows

- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`

# Related Governance

- `06-governance/decision-maker-reporting.md`
- `06-governance/architecture-decisions.md`
- `06-governance/source-of-truth-rules.md`

# Deferred Items

Deferred because they belong in future templates, skills, workflows, governance, or project context:

- role prompt template
- briefing template
- source-tracker comment template
- decision log template
- dependency-management skill
- requirement-traceability skill
- backlog-refinement skill
- documentation update assessment skill or governance
- project-specific ticket fields, local commands, routes, deployment targets, provider names, environment variables, ticket keys, and product terminology

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether `Ticket` and `Title` should be separate sections or combined in future revisions
- whether every ticket context must include `Why It Matters`, or whether small technical tasks may mark it `Not applicable`
- whether approved briefing files can always populate this template when source-system access is unavailable
- whether related tickets should distinguish previous, prerequisite, follow-up, duplicate, and blocked-by relationships in a richer schema
- whether ticket context should include a dedicated role-loading section or rely on `01-context/role-loading-rules.md`

# What This Template Must Not Do

This template must not:

- replace `03-skills/ticket-writing.md`
- replace `03-skills/acceptance-criteria.md`
- replace `05-workflows/ticket-to-implementation.md`
- replace `01-context/role-loading-rules.md`
- approve implementation scope
- define role authority
- define workflow sequence
- create or modify tickets automatically
- promote ResolvePM project doctrine into ResolveOS

