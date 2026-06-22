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

User-facing role labels may differ from internal ResolveOS role file names when clearer labels help users understand value and next action. These labels must map to existing ResolveOS roles, skills, or workflows and must not create duplicate roles.

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

## Recommended Team Is User-Facing

Use `Recommended Team` for user-facing role recommendations.

Do not use `AI Coverage`.

Recommended Team output should:

- show only roles or specialist support relevant to the current stage
- explain briefly why each visible role is needed
- state whether the role is needed now or later
- explain how to action the role
- say clearly when no additional specialist role is needed
- avoid a large all-role yes/no table in normal user output
- avoid making the user choose internal ResolveOS role files, workflows, modes, or loading rules

A recommended role can be handled by the user, a real team member, a specialist chat, an AI assistant, an AI agent, a coding agent, an engineer, a consultant, or a mix.

During setup, adoption, or continuation, ask or infer whether the user is working solo, with a team, with AI or automation support, or with a mix only when that changes the recommendation or handoff.

If the setup is unknown and not blocking, use a labelled assumption rather than stopping:

```text
Assumption: I will treat this as a solo setup for now unless you tell me otherwise.
```

## User-Facing Label Mapping

Use clear user-facing labels where they communicate value better than internal file names.

| User-facing label | Internal ResolveOS source |
| --- | --- |
| Product Strategy Lead | `02-roles/strategic-product-director.md` |
| Technical Strategy Lead | `02-roles/technical-strategy-lead.md` |
| Implementation Engineer | `02-roles/implementation-engineer.md` |
| QA / Validation Lead | `02-roles/qa-tester.md` |
| Business Analyst | `02-roles/business-analyst.md` |
| Feedback Curator | `03-skills/user-feedback-processing.md` and `05-workflows/feedback-to-ticket.md` |

Mapping rules:

- Do not force user-facing labels to match internal file names.
- Do not create a new role automatically when an exact role does not exist.
- Use the closest existing role, skill, or workflow only when its boundary fits.
- State the mapping when it affects handoff, ownership, or review.
- Preserve the internal role boundary even when the user-facing label is broader.

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

## Prompt And Handoff Generation

When ResolveOS recommends that a specialist chat, AI agent, coding agent, engineer, consultant, or real team member should act now, generate the controlling prompt or handoff immediately unless the user has asked not to.

Use:

- `04-templates/role-prompt-template.md` for role startup prompts
- `04-templates/chat-handoff-template.md` when a session, role, or agent needs transfer context
- project-owned ticket, current-focus, source item, or briefing context when the prompt is project-specific

The generated prompt or handoff should include:

- the user-facing role label
- the internal ResolveOS role, skill, or workflow source
- the current objective
- the source context to load
- what the role should do now
- constraints, blockers, assumptions, and escalation boundaries
- the expected output

Do not generate a prompt when the role is not needed yet. Instead, state when it would become needed.

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
