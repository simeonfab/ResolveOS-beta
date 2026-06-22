---
type: workflow
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
  - DEBUGGING.md
  - docs/project-context/implementation-workflow.md
  - docs/codex-briefings/
related_roles:
  - 02-roles/implementation-engineer.md
  - 02-roles/qa-tester.md
  - 02-roles/technical-strategy-lead.md
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/strategic-product-director.md
related_skills:
  - 03-skills/completion-reporting.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/ticket-writing.md
related_workflows:
  - 05-workflows/ticket-to-implementation.md
related_context:
  - 01-context/missing-context-behaviour.md
  - 01-context/project-loading-rules.md
  - 01-context/role-loading-rules.md
  - 01-context/context-loading-rules.md
related_governance:
  - 00-system/ai-operating-principles.md
  - 06-governance/codex-working-rules.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define the canonical ResolveOS workflow for reviewing implementation when work is incomplete, repeatedly failing, drifting from scope, blocked, uncertain, or not ready to report as complete.

This workflow is the stop-and-review loop for implementation execution. It prevents false completion, hidden blockers, repeated random changes, fake functionality, future-ticket leakage, documentation drift, and unsupported claims that implementation is done.

This is not a retrospective template, QA sign-off workflow, debugging skill, ticket template, or role definition.

# Trigger

Use this workflow when implementation work shows one or more review triggers:

- repeated implementation failure
- stuck loop
- failed build, lint, test, deployment, runtime check, or validation
- missing context during implementation
- unclear or missing acceptance criteria during implementation
- implementation drift from approved scope
- discovered dependency or prerequisite issue
- schema, architecture, configuration, credential, or source-of-truth blocker
- technical uncertainty that makes continued changes unsafe
- partial completion
- future-ticket leakage
- possible fake functionality or fake state
- documentation drift from implementation reality
- uncertainty about whether work can be reported as complete

Use it before claiming completion when any of these conditions exist.

# Inputs

Use the smallest relevant evidence needed to review the implementation state.

Inputs may include:

- current ticket, task, source item, or approved batch
- approved scope and acceptance criteria
- implementation notes and manual test steps
- ticket comments, blocker notes, and prerequisite warnings
- current repository state
- changed files
- command output
- failed check output
- first clear error
- validation results
- manual test observations
- current project context
- relevant briefing
- previous ticket outcome where dependencies or sequencing affect the current work
- known dependencies, prerequisites, assumptions, non-goals, and follow-up notes
- relevant ResolveOS role, context, skill, workflow, and governance files

Do not infer missing implementation evidence from memory.

# Workflow Principles

## Stop Before False Completion

Do not pretend the ticket is complete.

Do not claim work was completed, tested, deployed, committed, pushed, accepted, or source-ticket-updated unless there is direct evidence.

If the work is partial, blocked, failed, or not verified, say so directly.

## Current Ticket First

Current ticket first.

Review the current ticket, task, source item, or approved batch before considering future work.

Do not turn implementation review into future-ticket implementation.

Do not add unrelated scope while trying to resolve the failure.

## Evidence Over More Changes

When implementation starts failing or drifting, gather evidence before making more changes.

Inspect the current state, identify the first clear error where practical, and separate real failures from future-only features.

Do not keep making random changes after repeated failure.

## Real State Over Fake State

Empty state is better than fake state.

Do not use fake buttons, fake integrations, fake operational data, fake generated output, fake schema, fake success states, fake local fallback data, or pretend workflow behaviour to make implementation appear complete.

## Reviewability

Review output must make the state of work understandable.

It should state what happened, what was tried, what changed, what failed, what remains uncertain, and what highest-leverage unblocker or follow-up action is needed.

# Review Triggers

Start this workflow when any of the following happen:

- a required check fails and cannot be quickly resolved inside approved scope
- validation fails or cannot be performed
- manual testing is not possible
- acceptance criteria are unclear, missing, contradicted, or no longer satisfied
- implementation differs significantly from the original ticket plan
- scope starts expanding silently
- a future ticket is being implemented early
- a prerequisite is missing
- source context is missing or stale
- a dependency, schema, helper, migration, configuration, credential, or architecture gap appears
- repeated changes do not improve the failure
- the implementation path becomes unclear
- a security, paid API, deployment, or source-of-truth decision is needed
- documentation no longer matches implementation reality
- completion status cannot be stated honestly

# Stuck Loop Handling

If implementation enters a loop, repeated error, failed build cycle, dependency conflict, or unclear implementation path:

- stop after a reasonable number of attempts
- do not keep making random changes
- explain the issue in plain English
- explain what was tried
- explain the current state of the code or work
- explain what decision, help, source context, or prerequisite is needed
- mark the result as blocked or partially complete

Do not silently leave work in a failed state.

Do not pretend the ticket is complete.

When available evidence supports it, identify:

- exact command, page, route, action, or validation step involved
- first clear error
- related file or component
- whether the failure appears related to scoped work
- whether the failure appears unrelated or pre-existing
- highest-leverage unblocker or follow-up action

# Implementation Drift Handling

Implementation drift exists when implementation differs significantly from the original ticket plan.

Examples include:

- using a different library or framework approach than expected
- changing file structure substantially
- discovering the ticket depends on another piece of work
- implementing a smaller workaround instead of the intended solution
- splitting the ticket into partial implementation plus follow-up work
- removing or changing a visible feature to avoid fake functionality
- not being able to follow the acceptance criteria exactly

When drift occurs, report:

```text
Original plan:
- What the ticket appeared to ask for.

What actually happened:
- What was implemented instead.

Why it changed:
- The reason for the difference.

Impact:
- Whether this affects the acceptance criteria, future tickets, or user testing.

Follow-up needed:
- Any new ticket or decision required.
```

If the drift affects the acceptance criteria, do not mark the ticket complete unless the criteria are still satisfied.

If the drift changes product meaning, escalate to Product Manager.

If the drift changes requirement meaning, escalate to Business Analyst.

If the drift changes sequencing, architecture, dependency, build, or deployment risk, escalate to Technical Strategy Lead.

If the drift exposes strategy or roadmap risk, escalate to Strategic Product Director.

# Blocker Handling

If blocked:

- stop
- explain the blocker clearly
- explain why continuing would be unsafe or unsupported
- state what information, credential, config, source file, prerequisite, or admin decision is needed
- suggest the highest-leverage unblocker or follow-up action
- suggest whether a new prerequisite or follow-up ticket is needed

Do not silently work around blockers.

Do not work around security, architecture, source-of-truth, schema, dependency, configuration, paid API, or acceptance-criteria requirements just to continue.

Do not invent schema, fake functionality, fake data, fake integrations, fake generated output, or fake success states to make the ticket appear complete.

# Failed Validation Handling

If build, lint, test, runtime, deployment, manual validation, acceptance review, or QA validation fails:

- identify what failed
- identify the command, check, page, action, or criterion involved
- identify the first clear error when practical
- determine whether the failure is related to the scoped work
- fix related failures when practical and safe
- document unrelated or blocked failures clearly
- do not hide the failure
- do not claim completion while required validation fails

Manual testing must be possible for completed implementation work.

If manual testing is not possible, report the work as not verified, partial, or blocked unless admin explicitly accepts the limitation.

Project-specific command names, routes, deployment targets, and validation procedures belong in project context.

# Missing Context Handling

If required context is missing during implementation:

- stop or proceed only with an explicit limitation when safe
- name the missing context
- explain why it matters
- identify whether the missing context blocks implementation, validation, completion reporting, or source-of-truth confidence
- ask for the missing context or use an approved fallback
- state the limitation of any fallback

Do not guess missing acceptance criteria.

Do not infer missing project facts from memory.

Do not create implementation output that depends on missing files, source comments, tickets, credentials, configuration, schema, or decisions.

If the current source contradicts existing project context or ResolveOS governance, flag the contradiction instead of silently choosing the easier path.

# Role Responsibilities

Roles participate in this workflow without changing their authority.

Implementation Engineer:

- identifies implementation failure, drift, blockers, and validation state
- gathers evidence from current implementation and checks
- stops when repeated failure or unsafe assumptions appear
- reports complete, partial, blocked, failed, or not verified status only when evidence supports it

QA Tester:

- reviews validation evidence, acceptance criteria satisfaction, defect evidence, regression risk, and quality-gate status
- may identify or create defect tickets when evidence supports them
- does not approve product scope or own code execution

Technical Strategy Lead:

- reviews sequencing, dependency, architecture, implementation-governance, and delivery risk
- decides whether prerequisite work, ticket splitting, or implementation resequencing is needed
- stops further ticket progression when dependency, architecture, build, deployment, or source-of-truth risk makes continuation unsafe

Product Manager:

- reviews product scope, acceptance intent, product meaning, and product-side completion risk
- decides whether implementation drift still satisfies approved product objectives within low-risk clarification bounds

Business Analyst:

- reviews unclear requirements, business rules, assumptions, traceability, and acceptance criteria ambiguity
- helps prevent invented requirements or vague criteria from being treated as ready

Strategic Product Director:

- reviews strategy, roadmap, prioritisation, positioning, or whether something should exist when implementation exposes strategic drift

# Escalation Rules

Escalate to admin when:

- required source context is missing or contradictory
- continuing would require invented requirements, fake functionality, fake state, or unsupported assumptions
- repeated failures create a loop
- a failed check cannot be resolved safely
- completion status cannot be stated honestly
- manual approval is needed for git, deployment, paid API use, credentials, security, product scope, or source-of-truth changes

Escalate to Technical Strategy Lead when:

- dependencies are incomplete
- prerequisite tickets are needed
- build or deployment integrity breaks
- architecture direction changes
- implementation sequencing changes
- the current ticket cannot safely continue in the current order

Escalate to QA Tester when:

- validation ownership, defect verification, regression thinking, or quality-gate status is needed
- failed validation needs defect evidence or retest judgement

Escalate to Product Manager or Business Analyst when:

- product scope, acceptance intent, requirements, assumptions, traceability, or acceptance criteria are unclear or affected by implementation reality

Escalate to Strategic Product Director when:

- implementation exposes product strategy drift, roadmap coherence risk, positioning risk, or a question about whether the feature should exist

# Outputs

This workflow may produce:

- blocked status
- partially complete status
- failed status
- not verified status
- implementation drift report
- stuck-loop report
- failed-validation report
- blocker report
- missing-context report
- dependency or prerequisite report
- suggested follow-up ticket
- suggested documentation update
- escalation note
- admin-review question

Outputs should be plain, direct, practical, and traceable to available evidence.

# Anti-Patterns

Do not:

- keep making random changes after repeated failure
- silently leave work in a failed state
- silently work around blockers
- hide build, lint, test, deployment, runtime, manual validation, or acceptance failures
- claim completion when required checks or validation failed
- claim completion when acceptance criteria are missing, unclear, contradicted, or no longer satisfied
- pretend the ticket is complete
- invent schema, requirements, integrations, configuration, credentials, source context, validation evidence, or success states
- create fake functionality to pass review
- build future tickets early while resolving current-ticket failure
- add unrelated scope while debugging
- reclassify failed or partial work as complete because the report would be inconvenient
- bury blockers or uncertainty inside vague summaries
- make project-specific commands or paths global
- turn this workflow into a completion report template or debugging skill

# Examples

## Repeated Build Failure

```text
Trigger:
- The build fails repeatedly after scoped changes.

Handling:
- Stop after reasonable attempts.
- Identify the first clear error.
- State what was tried.
- State whether the failure appears related to scoped work.
- Mark the result blocked or partially complete.
- Suggest the highest-leverage unblocker or follow-up action.
```

## Drift From Scope

```text
Trigger:
- The implementation requires removing a visible feature to avoid fake functionality.

Handling:
- Report the original plan, what changed, why it changed, impact, and follow-up needed.
- Check whether acceptance criteria are still satisfied.
- Do not mark complete if the criteria are no longer satisfied.
```

## Missing Acceptance Criteria

```text
Trigger:
- Implementation reveals the source ticket has no testable acceptance criteria.

Handling:
- Stop before claiming completion.
- State that acceptance criteria are missing.
- Ask for criteria or escalate to Product Manager / Business Analyst.
- Do not guess the criteria.
```

## Dependency Blocker

```text
Trigger:
- Current implementation references schema, helper, migration, or configuration that does not exist.

Handling:
- Stop.
- Explain why continuing would require invented state or fake functionality.
- Suggest the prerequisite fix or ticket.
- Escalate sequencing to Technical Strategy Lead.
```

# Related Roles

- `02-roles/implementation-engineer.md`
- `02-roles/qa-tester.md`
- `02-roles/technical-strategy-lead.md`
- `02-roles/product-manager.md`
- `02-roles/business-analyst.md`
- `02-roles/strategic-product-director.md`

# Related Skills

- `03-skills/completion-reporting.md`
- `03-skills/acceptance-criteria.md`
- `03-skills/ticket-writing.md`

Future related skills may include:

- implementation review
- debugging support
- dependency management
- defect reporting
- smoke testing
- regression testing
- documentation update assessment
- risk assessment

# Related Workflows

- `05-workflows/ticket-to-implementation.md`

# Related Context

- `01-context/missing-context-behaviour.md`
- `01-context/project-loading-rules.md`
- `01-context/role-loading-rules.md`
- `01-context/context-loading-rules.md`

# Related Governance

- `00-system/ai-operating-principles.md`
- `06-governance/codex-working-rules.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred because they belong in later files or require admin review:

- full completion report and blocker comment templates
- exact source-tracker comment format
- exact project-specific command lists, route names, paths, build tools, provider names, deployment targets, and environment variables
- standalone debugging-support skill
- standalone implementation-review skill
- standalone dependency-management skill
- standalone defect-reporting, smoke-testing, and regression-testing skills
- update-process governance and documentation timing labels
- global git, commit, push, and deploy procedure
- project-specific release/version handling

# Ambiguous Items For Admin Review

Admin review is needed for:

- whether this workflow should define a formal maximum number of failed attempts before stopping
- whether every project should provide a project-specific validation checklist consumed by this workflow
- whether source-tracker blocker comments should be mandatory when source-system access exists or left to project workflow
- whether documentation drift should block completion or only require a reported follow-up
- whether stuck-loop reports should become a reusable template

# What This Workflow Must Not Do

This workflow must not:

- create templates
- create skills
- create roles
- replace `05-workflows/ticket-to-implementation.md`
- replace `03-skills/completion-reporting.md`
- replace `01-context/missing-context-behaviour.md`
- own QA sign-off
- own product scope approval
- own architecture governance outside Technical Strategy Lead authority
- make project-specific commands global
- promote ResolvePM product doctrine into ResolveOS
