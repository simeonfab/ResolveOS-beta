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
User-facing role label:
- [Product Strategy Lead / Technical Strategy Lead / Implementation Engineer / QA / Validation Lead / Business Analyst / Feedback Curator / other clear label]

Use this role:
- [ResolveOS role file path]

Internal ResolveOS source:
- [Role, skill, or workflow path used for authority and behaviour]

Act as:
- [Role name]
```

User-facing labels may differ from internal ResolveOS role file names when clearer labels help the recipient understand value and action. Do not create a new role from a label. Map the label to an existing ResolveOS role, skill, or workflow.

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

Also use it when ResolveOS recommends a specialist chat, AI agent, coding agent, engineer, consultant, or real team member and the role should act now.

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

When a prompt is generated from a Recommended Team output, include the practical reason the role is needed now and the expected next action.

# Example

```text
Role

User-facing role label:
- Implementation Engineer

Use this role:
- 02-roles/implementation-engineer.md

Internal ResolveOS source:
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
