---
type: knowledge_bundle
scope: global
owner: ResolveOS
source_repository: https://github.com/simeonfab/ResolveOS
source_commit: fcde866ede5144d996a0e4bd2c34ccbcf010c524
generated: true
generated_date: 2026-06-22
included_paths:
  - 06-governance/architecture-decisions.md
  - 06-governance/codex-working-rules.md
  - 06-governance/decision-maker-reporting.md
  - 06-governance/duplication-control.md
  - 06-governance/project-readiness.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/update-process.md
---

# Source: 06-governance/architecture-decisions.md

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
review_required: true
---

# Architecture Decisions

# Purpose

Record ResolveOS architecture decisions that affect reusable behaviours, migration boundaries, source ownership, and future file creation.

This file is the single canonical architecture decision log for ResolveOS migration decisions.

# Rules

Architecture decisions should:

- preserve the decision
- preserve the rationale
- identify impact
- avoid inventing missing prior decisions without source context
- distinguish global ResolveOS decisions from project-specific project decisions
- preserve the strongest reviewed wording when duplicate or differing wording exists

# ADR-001: ResolveOS Is A Global Dependency

## Status

Accepted for draft migration.

## Decision

Use Model B: ResolveOS as a global dependency.

ResolveOS is not a monorepo for every project.

Project repositories consume ResolveOS guidance, roles, skills, standards, and context-loading rules.

## Rationale

The implementation plan confirms ResolveOS as the reusable global layer. Project repositories should keep project-specific context while depending on ResolveOS for global behaviours and reusable operating files.

## Impact

ResolveOS owns global roles, skills, standards, context, templates, workflows, and governance.

Project repositories own product direction, roadmaps, tickets, domain context, architecture decisions, active constraints, and project-specific overrides.

Source references:

- `00-system/resolveos-implementation-plan.md` > `Confirmed architecture decisions`
- `06-governance/source-of-truth-rules.md` > `Ownership Hierarchy`

# ADR-002: Roles And Skills Are Separate

## Status

Accepted for draft migration.

## Decision

Separate roles and skills.

Roles define reusable behaviour and responsibility.

Skills define reusable task methods.

A role may invoke multiple skills.

A skill may be used by multiple roles.

## Rationale

The implementation plan explicitly confirms this separation. ResolveOS file standards also define separate role and skill formats.

## Impact

Role files should not become workflow or template files.

Skill files should not define role authority.

Shared methods such as ticket writing, acceptance criteria, completion reporting, and feedback processing remain reusable across roles.

Source references:

- `00-system/resolveos-implementation-plan.md` > `Confirmed architecture decisions`
- `00-system/file-standard.md` > `Role File Format`
- `00-system/file-standard.md` > `Skill File Format`

# ADR-003: Context Loading Is A Dedicated Layer

## Status

Accepted for draft migration.

## Decision

Add a dedicated context layer.

Context loading is a first-class concern.

ResolveOS defines how chats, agents, Codex, and project repositories load global context and project context.

## Rationale

ResolvePM extraction identified context loading, short prompts, source-of-truth discipline, missing-context behaviour, and role-based startup as high-value reusable behaviour.

## Impact

Context files live under `01-context/`.

Role, skill, governance, project context, briefing, current focus, and ticket inputs should be loaded intentionally rather than copied into every prompt.

Missing required context must be flagged rather than guessed.

Source references:

- `00-system/resolveos-implementation-plan.md` > `Confirmed architecture decisions`
- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`

# ADR-004: Markdown Files Use YAML Frontmatter Metadata

## Status

Accepted for draft migration.

## Decision

Every markdown file should begin with structured YAML frontmatter metadata.

## Rationale

The implementation plan confirms YAML frontmatter as the preferred metadata style. File and metadata standards make this mandatory for ResolveOS markdown files.

## Impact

ResolveOS markdown files should include at least:

```yaml
---
type:
scope:
owner:
version:
status:
---
```

Source references:

- `00-system/resolveos-implementation-plan.md` > `Confirmed architecture decisions`
- `00-system/file-standard.md` > `Required YAML Frontmatter`
- `00-system/file-metadata-standard.md` > `Required Fields`

# ADR-005: Project Context Stays Out Of ResolveOS

## Status

Accepted for draft migration.

## Decision

Keep project context out of ResolveOS.

ResolveOS contains global AI behaviours, roles, skills, context-loading rules, standards, templates, governance, and general working preferences.

Project repositories contain product goals, roadmaps, tickets, domain context, project-specific workflows, feature decisions, architecture decisions, active implementation constraints, and project-specific overrides.

## Rationale

The implementation plan and source-of-truth rules both separate global ResolveOS content from project-specific repositories.

## Impact

ResolvePM product vision, roadmap, CP ticket sequences, Supabase implementation details, deployment URLs, local paths, and product terminology remain in ResolvePM unless admin explicitly promotes a reusable pattern.

Source references:

- `00-system/resolveos-implementation-plan.md` > `Confirmed architecture decisions`
- `06-governance/source-of-truth-rules.md` > `ResolvePM To ResolveOS Promotion Rules`
- `migration/resolvepm-extraction-map.md` > `Project-Specific ResolvePM Content`

# ADR-006: AI Operating Principles Are The Global Home For Assistant Behaviour

## Status

Accepted for draft migration.

## Decision

`00-system/ai-operating-principles.md` is the canonical global home for assistant and agent operating principles.

## Rationale

Batch 1 extracted reusable assistant behaviour from ResolvePM: truthfulness, evidence over invention, plain-English communication, direct challenge, explicit uncertainty, no fake functionality, implementation honesty, blocker handling, scope discipline, and cost-safe AI/API behaviour.

## Impact

Future roles, skills, workflows, and project prompts should reference the global operating principles instead of duplicating the full behaviour list.

Project-specific overrides may add local constraints but must not weaken global safety, truthfulness, blocker, or no-fake-functionality rules without admin review.

Source references:

- `00-system/ai-operating-principles.md`
- `05-workflows/batch-1-admin-operating-rules-codex-prompt.md`
- `migration/resolvepm-extraction-map.md` > `Global Working Preferences`

# ADR-007: Startup Context Defines Default ResolveOS Session Assumptions

## Status

Accepted for draft migration.

## Decision

`01-context/startup-context.md` defines default startup assumptions for ResolveOS-enabled sessions.

## Rationale

Batch 1 extracted admin working style, practical help, direct communication, context-loading discipline, short prompts, missing-context behaviour, project-specific context handling, and review-before-implementation assumptions.

## Impact

ResolveOS sessions should identify active repository, task or batch scope, required context, project-specific context, and whether implementation is approved before durable changes.

Startup context must not replace role files, skill procedures, or project-specific source-of-truth files.

Source references:

- `01-context/startup-context.md`
- `01-context/context-loading-rules.md`
- `05-workflows/batch-1-admin-operating-rules-codex-prompt.md`

# ADR-008: Codex Working Rules Are The Canonical Codex Execution Constraints

## Status

Accepted for draft migration.

## Decision

`06-governance/codex-working-rules.md` defines how Codex should operate in ResolveOS-enabled repositories.

## Rationale

Batch 1 extracted reviewable diffs, no broad rewrites without instruction, no direct commits when review is expected, one-ticket-or-batch-at-a-time work, blocker reporting, no fake functionality, implementation honesty, cost-safe AI/API behaviour, and preservation of existing behaviour unless intentionally changed.

## Impact

Codex should follow these rules when creating or modifying files, reporting completion, handling blockers, and deciding whether broader edits are allowed.

Project repositories may define local overrides, but direct commits, broad rewrites, expanded scope, paid API calls, role consolidation, and project-to-global promotion require explicit admin approval.

Source references:

- `06-governance/codex-working-rules.md`
- `05-workflows/batch-1-admin-operating-rules-codex-prompt.md`
- `migration/resolvepm-extraction-map.md` > `Global Working Preferences`

# ADR-009: No Fake Functionality Is A Global Hard Rule

## Status

Accepted for draft migration.

## Decision

No fake functionality is a global ResolveOS hard rule.

Do not create fake buttons, fake integrations, fake operational data, fake AI outputs, fake dashboards, fake metrics, fake links, fake filters, fake success states, or pretend features.

Every visible feature must either actually work, be clearly marked as not yet implemented, or not be shown.

## Rationale

The extraction map identifies no-fake-functionality behaviour as one of the highest-risk migrations. It appears repeatedly across ResolvePM role, workflow, and briefing files.

## Impact

Roles, skills, workflows, and project prompts must not approve fake state as a way around missing prerequisites, schema gaps, configuration gaps, paid API constraints, or incomplete implementation.

Explicit empty states, disabled states, and error states are preferred over deceptive UX.

Source references:

- `00-system/ai-operating-principles.md` > `No Fake Functionality`
- `06-governance/codex-working-rules.md` > `Do Not Fake Functionality`
- `migration/resolvepm-extraction-map.md` > `Assistant Anti-Patterns`

# ADR-010: Cost-Safe AI/API Behaviour Is Global, Configuration Is Project-Owned

## Status

Accepted for draft migration.

## Decision

Cost-safe AI/API behaviour is global ResolveOS behaviour.

Provider-specific configuration, model names, environment variables, enable flags, and usage limits are project-owned unless admin explicitly promotes them.

## Rationale

ResolvePM repeatedly requires paid AI/API usage to be disabled by default, explicitly configured, user-triggered, token-capped or usage-limited where practical, and honest when unavailable.

Provider names and model defaults can become stale or project-specific, so the global rule preserves the behaviour while leaving exact configuration to projects.

## Impact

ResolveOS roles and skills should preserve cost-safe defaults and no hidden spend.

Project repositories should define exact providers, model tiers, environment variables, local enable flags, and project-specific caps.

Source references:

- `00-system/ai-operating-principles.md` > `Cost-Safe AI/API Behaviour`
- `06-governance/codex-working-rules.md` > `Use Cost-Safe AI/API Behaviour`
- `migration/resolvepm-extraction-map.md` > `High Risk Migrations`

# ADR-011: Given / When / Then Is Recommended, Not Mandatory

## Status

Accepted for draft migration.

## Decision

Given / When / Then is recommended, not mandatory.

Use it where it improves clarity.

Do not force it into tickets where simpler criteria are clearer.

## Rationale

Batch 2 acceptance-criteria extraction found repeated Given / When / Then examples in ResolvePM briefings, but the accepted skill constrains the format to avoid over-formatting small or simple tickets.

## Impact

Acceptance criteria should describe observable, testable outcomes. Given / When / Then may be used when it improves precision, especially for workflow behaviour, persistence, empty states, error states, permissions, validation, and build or deployment gates.

Projects may locally require the format as an override.

Source references:

- `03-skills/acceptance-criteria.md` > `Given / When / Then Guidance`
- `03-skills/ticket-writing.md` > `Acceptance Criteria Guidance`

# ADR-012: Completion Reporting Is A Skill And Future Template

## Status

Accepted for draft migration.

## Decision

Completion reporting consists of a reusable skill and a future template.

Batch 2 created only the skill.

## Rationale

ResolvePM contains a rich completion report format. The accepted migration preserved the reporting behaviour in `03-skills/completion-reporting.md` while deferring a canonical template to avoid creating extra files outside the batch scope.

## Impact

Completion reporting guidance lives in the skill for now.

A future completion report template may be created after review.

Source references:

- `03-skills/completion-reporting.md` > `Purpose`
- `03-skills/completion-reporting.md` > `Source Merge Notes`
- `migration/resolvepm-extraction-map.md` > `High Risk Migrations`

# ADR-013: Project Verification Commands Remain Project-Specific

## Status

Accepted for draft migration.

## Decision

Project verification commands remain project-specific.

ResolveOS may require honest validation reporting, but it must not globally require one project's lint, build, test, smoke, deployment, or migration commands.

## Rationale

ResolvePM has concrete check commands, but those commands depend on its stack and project setup. ResolveOS should preserve check discipline without turning ResolvePM commands into global requirements.

## Impact

Roles and skills should report which checks ran, which did not run, why they did not run, and any residual risk.

Project repositories should define their own required verification commands.

Source references:

- `03-skills/completion-reporting.md` > `Reporting Validation`
- `03-skills/acceptance-criteria.md` > `Validation Guidance`
- `03-skills/ticket-writing.md` > `Testing Guidance`

# ADR-014: Dependency Ordering Belongs In Governance

## Status

Accepted for draft migration.

## Decision

Dependency ordering belongs in governance rather than ticket-writing.

Ticket-writing may identify dependencies and prerequisites, but dependency commit order, dependent-ticket progression, and deployment-order risk are governance concerns.

## Rationale

ResolvePM contains dependency ordering rules across Technical Strategy Lead, Implementation Engineer, and implementation workflow sources. The accepted completion-reporting skill explicitly deferred dependency ordering because ADR-014 places it in governance rather than ticket-writing.

## Impact

Ticket-writing should identify dependencies.

Technical Strategy Lead and future governance/workflow files may own dependency progression and commit/deployment ordering rules.

Implementation Engineer should surface dependency risk but should not own governance policy.

Source references:

- `03-skills/completion-reporting.md` > `Deferred Items`
- `02-roles/technical-strategy-lead.md` > `Dependency Commit Order Governance`
- `03-skills/ticket-writing.md` > `Define Sequencing And Dependencies`

# ADR-015: Feedback Processing Uses A Minimal Canonical Schema

## Status

Accepted for draft migration.

## Decision

Feedback processing uses a minimal canonical schema:

- `category`
- `message`
- `user`
- `timestamp`

Projects may extend the schema.

## Rationale

ResolvePM extraction found these fields as the explicit minimum feedback fields. The migration map identifies feedback handling as high risk because the current rule is intentionally simple and should not be over-formatted without admin approval.

## Impact

ResolveOS feedback-processing guidance should preserve this minimal schema as the global baseline.

Projects may add fields such as severity, source URL, product area, workflow area, duplicate reference, or review status when their context requires it.

ResolveOS should not impose a heavy feedback taxonomy globally without admin review.

Source references:

- `migration/resolvepm-extraction-audit.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `Global Feedback Handling Rules`
- `03-skills/user-feedback-processing.md` > `Inputs`

# ADR-016: Treating Messages As Feedback By Default Is Project-Level

## Status

Accepted for draft migration.

## Decision

Treating messages as feedback by default is a project-level decision.

ResolveOS does not enforce this behaviour globally.

## Rationale

The extraction map flags feedback classification and taxonomy as high risk and ambiguous. User or admin messages may be feedback, instructions, corrections, blockers, questions, or context-loading signals. Enforcing message-as-feedback globally would risk scope creep and incorrect classification.

## Impact

ResolveOS skills may say that messages can be feedback when appropriate.

Projects decide whether messages should be treated as feedback by default in that project.

Assistants should preserve the raw message and classify uncertainty rather than automatically converting every message into feedback or a ticket.

Source references:

- `migration/resolvepm-extraction-map.md` > `Ambiguous Classifications Requiring Admin Decision`
- `03-skills/user-feedback-processing.md` > `Classifying Feedback`
- `03-skills/user-feedback-processing.md` > `Ambiguous Items For Admin Review`

# ADR-017: Project-Specific Prioritisation Filters Remain Project-Owned

## Status

Accepted for draft migration.

## Decision

Project-specific prioritisation filters remain project-owned unless proven reusable across multiple projects.

## Rationale

ResolveOS owns reusable behaviour. Project repositories own product vision, strategy, roadmap, feature decisions, domain terminology, and project-specific constraints. The ResolvePM feedback strategic filter may be valuable, but the extraction map identifies project/global ambiguity and warns against making ResolvePM doctrine global.

## Impact

ResolveOS may define generic feedback-processing and ticket-writing methods.

ResolveOS must not impose ResolvePM-specific prioritisation doctrine on other projects.

Project repositories may define local prioritisation filters and reference ResolveOS skills for capture, preservation, classification, and ticket conversion.

Source references:

- `06-governance/source-of-truth-rules.md` > `Project Repositories Own`
- `00-system/resolveos-migration-strategy.md` > `Promotion Rules`
- `migration/resolvepm-extraction-map.md` > `Project-Specific ResolvePM Content`
- `03-skills/user-feedback-processing.md` > `Prioritisation Guidance`

# ADR-018: Product Manager Is A Product Execution Role Distinct From Strategic Product Director

## Status

Accepted for draft migration.

## Decision

Product Manager is the canonical product execution clarity role.

Strategic Product Director remains a distinct product strategy role.

Product Manager should not absorb strategy-level roadmap coherence, product positioning, or deciding whether something should exist.

## Rationale

Batch 3A.1 created Product Manager from distributed product execution behaviour. The extraction map separately preserves Strategic Product Director as a distinct specialist role that owns roadmap coherence, positioning, strategic challenge, product risk, and deciding whether something should be built.

## Impact

Product Manager may clarify product execution scope, prepare ticket-ready scope, review acceptance criteria, and preserve product-side traceability inside approved objectives.

Strategic Product Director remains responsible for strategy-level product direction and challenge.

Source references:

- `02-roles/product-manager.md` > `Purpose`
- `02-roles/product-manager.md` > `Escalation Rules`
- `migration/resolvepm-extraction-map.md` > `Global Role Behaviour`
- `docs/ai-roles/strategic-product-director.md` > role boundary source

# ADR-019: Product Managers May Create Tickets But Ticket Creation Does Not Imply Approval Authority

## Status

Accepted for draft migration.

## Decision

Product Managers may create tickets, draft ticket-ready scope, and prepare acceptance criteria when enough context exists.

Ticket creation does not imply approval authority.

Final approval remains with admin or the relevant project source of truth.

## Rationale

Batch 3A.1 created the Product Manager role from distributed ResolvePM product execution behaviour. The role owns product execution clarity, ticket-ready scope, feedback-to-work discipline, and acceptance criteria review, but ResolvePM migration guardrails require role boundaries and admin decision rights to be preserved.

Allowing Product Managers to create tickets reflects ticket-writing behaviour already extracted into ResolveOS. Treating creation as approval would silently expand Product Manager authority beyond the reviewed source material.

## Impact

Product Manager and Business Analyst roles may prepare or create reviewed ticket candidates where task context permits.

Created tickets must still preserve source context, assumptions, non-goals, dependencies, acceptance criteria, and traceability.

Creation, drafting, or decomposition must not be represented as admin approval, roadmap approval, implementation approval, or strategic prioritisation approval.

Source references:

- `02-roles/product-manager.md` > `Decision Authority`
- `03-skills/ticket-writing.md` > `Ticket Writing Process`
- `06-governance/extraction-migration-guardrails.md` > role preservation rules
- `migration/resolvepm-extraction-map.md` > `Global Ticket Writing Rules`

# ADR-020: Product Managers May Make Low-Risk Scope Clarification Decisions Within Approved Objectives

## Status

Accepted for draft migration.

## Decision

Product Managers may make low-risk scope clarification decisions within approved objectives.

They may narrow wording, clarify non-goals, separate follow-up work, and align ticket-ready scope with the approved outcome when the decision does not change product strategy, roadmap direction, stakeholder promise, architecture, implementation sequencing, security posture, cost profile, or acceptance intent.

## Rationale

ResolvePM repeatedly preserves scope discipline, one-ticket-at-a-time work, explicit assumptions, and follow-up tickets instead of hidden expansion. Batch 3A.1 identified Product Manager responsibility for product execution clarity.

Low-risk clarification authority allows the Product Manager role to reduce ambiguity without sending every wording-level decision back to admin. It does not grant authority to change approved objectives.

## Impact

Product Managers may clarify scope when the clarification is traceable, low-risk, and inside an already approved objective.

Product Managers must escalate when clarification would change priority, acceptance, roadmap meaning, implementation risk, stakeholder expectation, or project source-of-truth content.

Business Analysts may support these decisions by identifying requirement gaps, assumptions, and traceability concerns, but they do not own product approval authority.

Source references:

- `02-roles/product-manager.md` > `Decision Authority`
- `03-skills/ticket-writing.md` > `Keep Scope Small, Safe, And Reversible`
- `03-skills/acceptance-criteria.md` > `Review Expectations`
- `migration/resolvepm-extraction-map.md` > `Global Working Preferences`

# ADR-021: Documentation Hygiene Is Primarily Owned By Product Manager And Shared With Business Analyst

## Status

Accepted for draft migration.

## Decision

Documentation hygiene is primarily owned by Product Manager and shared with Business Analyst.

Product Manager owns product-side documentation alignment for scope, outcome, ticket-ready context, and persistent product/project context.

Business Analyst shares responsibility for requirement, assumption, business rule, traceability, and acceptance-criteria documentation alignment.

## Rationale

ResolvePM repeatedly warns: `Do not let documentation drift from reality.`

Technical Strategy Lead source material contains the strongest documentation timing labels, but Batch 3A role boundaries should avoid making technical delivery roles the default owner for product and requirement documentation hygiene.

Product Manager is the better primary owner for product-scope documentation hygiene. Business Analyst is the shared owner where requirement clarity, traceability, and acceptance criteria are the documentation concern.

## Impact

Product Manager and Business Analyst roles should flag documentation updates when product scope, requirements, assumptions, blockers, acceptance criteria, or persistent project context changes.

Technical Strategy Lead still owns documentation hygiene for architecture direction, implementation workflow, delivery sequencing, and Codex briefing context where those are the active concern.

Implementation Engineer should continue to flag suggested documentation updates when implementation reveals information that affects future work, but does not own global documentation hygiene.

Source references:

- `02-roles/product-manager.md` > `Responsibilities`
- `02-roles/business-analyst.md` > `Behaviour Rules`
- `AGENTS.md.backup` > `Do not let documentation drift from reality.`
- `docs/project-context/implementation-workflow.md` > `Documentation Maintenance Rule`
- `docs/ai-roles/technical-strategy-lead.md` > documentation maintenance timing labels
- `docs/ai-roles/implementation-engineer.md` > documentation update flagging

# ADR-022: Business Analysts May Create Tickets But Ticket Creation Does Not Imply Approval Authority

## Status

Accepted for draft migration.

## Decision

Business Analysts may create tickets.

Business Analysts may also prepare ticket-ready requirements.

Ticket creation does not imply approval authority.

Product Manager remains accountable for product scope alignment.

## Rationale

Batch 3A.2 created the Business Analyst role from distributed ResolvePM requirement-clarity behaviour. The role may clarify requirements, decompose requirements, preserve traceability, support acceptance criteria, and prepare ticket-ready inputs.

ResolvePM migration guardrails require role boundaries to remain explicit. Allowing Business Analysts to create or prepare tickets supports requirements-to-work conversion, but approval authority remains separate from ticket creation.

Product Manager remains accountable for product scope alignment because the Product Manager role owns product execution clarity and scope alignment inside approved objectives.

## Impact

Business Analysts may create tickets or ticket-ready requirements when enough source context exists.

Business Analysts must preserve source context, assumptions, non-goals, dependencies, acceptance criteria, traceability, and ambiguity notes.

Business Analyst ticket creation must not be represented as admin approval, product approval, roadmap approval, prioritisation approval, or implementation approval.

Product Manager should review product scope alignment when BA-created tickets affect product outcome, scope, priority, stakeholder meaning, or approved objectives.

Source references:

- `02-roles/business-analyst.md` > `Decision Authority`
- `02-roles/product-manager.md` > `Responsibilities`
- `03-skills/ticket-writing.md` > `Ticket Writing Process`
- `06-governance/extraction-migration-guardrails.md` > role preservation rules
- `migration/resolvepm-extraction-map.md` > `Global Ticket Writing Rules`

# ADR-023: QA Testers May Create Defect Tickets But Ticket Creation Does Not Imply Approval Authority

## Status

Accepted for draft migration.

## Decision

QA Testers may create defect tickets.

Defect ticket creation does not imply approval authority.

Product scope approval remains with Product Manager/admin.

## Rationale

Batch 3A.3 created the QA Tester role from scattered ResolvePM validation behaviour. That role may identify defects, report blockers, recommend follow-up defect tickets, and make validation findings traceable to source tickets, acceptance criteria, manual test steps, or defect reports.

Allowing QA Testers to create defect tickets preserves practical defect-reporting behaviour while keeping authority boundaries explicit. Defect creation records evidence and follow-up work; it does not approve product scope, roadmap direction, prioritisation, or acceptance intent.

Product Manager and admin authority remains required where a defect ticket affects product scope, product outcome, release acceptance, or future prioritisation.

## Impact

QA Testers may create defect tickets when validation evidence supports the defect.

Defect tickets should preserve expected result, actual result, reproduction context where available, affected scope or acceptance criteria, blocker status, and highest-leverage follow-up action.

QA defect ticket creation must not be represented as product approval, roadmap approval, prioritisation approval, implementation approval, or final acceptance.

Product Manager/admin review remains required when a defect affects product scope, acceptance, priority, release readiness, or approved objectives.

Source references:

- `02-roles/qa-tester.md` > `Decision Authority`
- `02-roles/qa-tester.md` > `Behaviour Rules`
- `03-skills/ticket-writing.md` > `Ticket Writing Process`
- `03-skills/acceptance-criteria.md` > `Validation Guidance`
- `migration/resolvepm-extraction-map.md` > `Global Ticket Writing Rules`

# ADR-024: QA Tester Is The Canonical QA Role

## Status

Accepted for draft migration.

## Decision

QA Tester is the canonical QA role.

QA Lead should not be introduced until materially distinct leadership responsibilities are identified.

## Rationale

The ResolvePM audit identifies `docs/ai-roles/qa-lead.md` as an empty placeholder file. The Batch 3A.3 QA Tester role was extracted from scattered validation, check, blocker, defect, acceptance criteria, and tester-readiness behaviour rather than invented from the empty QA Lead placeholder.

Creating a separate QA Lead role now would violate migration guardrails by inventing leadership behaviour that is not materially present in reviewed source material.

## Impact

ResolveOS should use `02-roles/qa-tester.md` as the canonical QA role for now.

Future QA Lead extraction requires materially distinct leadership behaviour, source evidence, and admin review.

Smoke testing, regression testing, and defect reporting may become future skills if repeated enough, but they do not require a separate QA Lead role at this stage.

Source references:

- `02-roles/qa-tester.md` > `Purpose`
- `migration/resolvepm-extraction-audit.md` > empty QA Lead placeholder finding
- `migration/resolvepm-extraction-map.md` > empty role files as placeholders only
- `06-governance/extraction-migration-guardrails.md` > role preservation rules

# ADR-025: Technical Strategy Lead May Create Technical Tickets But Ticket Creation Does Not Imply Product Approval Authority

## Status

Accepted for draft migration.

## Decision

Technical Strategy Lead may create technical tickets.

Technical ticket creation does not imply product approval authority.

Product approval remains with Product Manager/admin.

## Rationale

Batch 3B.1 created Technical Strategy Lead as the specialist role for delivery orchestration, technical planning, dependency mapping, sequencing, architecture governance, prompt governance, and implementation governance.

ResolvePM source material gives Technical Strategy Lead authority to create tickets, sequence implementation, split or refactor ticket scope, recommend architecture adjustments, stop unsafe implementation direction, and recommend follow-up tickets.

Ticket creation is necessary for technical prerequisites, dependency work, sequencing corrections, and implementation-governance follow-up. It must not become product approval, roadmap approval, prioritisation approval, or strategic product direction.

## Impact

Technical Strategy Lead may create technical, prerequisite, dependency, sequencing, architecture, implementation-governance, or blocker-resolution tickets when enough source context exists.

Technical tickets must preserve source context, assumptions, dependencies, non-goals, acceptance criteria or validation expectations, and traceability.

Technical Strategy Lead-created tickets require Product Manager/admin review when they affect product scope, product outcome, acceptance intent, priority, roadmap meaning, stakeholder expectation, cost profile, or approved objectives.

Source references:

- `02-roles/technical-strategy-lead.md` > `Decision Authority`
- `docs/ai-roles/technical-strategy-lead.md` > `Decision Rights`
- `docs/project-context/implementation-workflow.md` > `Technical Strategy Lead`
- `migration/resolvepm-extraction-map.md` > `Global Role Behaviour`

# ADR-026: Implementation Engineers May Propose Tickets But Should Not Independently Create New Work

## Status

Accepted for draft migration.

## Decision

Implementation Engineers may propose tickets.

Implementation Engineers should not independently create new work without instruction, approval, or an established workflow.

Implementation Engineers should surface findings, blockers, technical debt, and future work as recommendations rather than automatically creating scope.

## Rationale

Batch 3B.2 created Implementation Engineer as the specialist role for scoped ticket execution, code changes, debugging, checks, validation, blocker escalation, and implementation completion reports.

ResolvePM source material allows Implementation Engineer to suggest follow-up tickets, challenge local implementation practicality, identify blockers, and propose implementation-specific improvements. It also explicitly says Implementation Engineer should not create Jira tickets directly unless asked and should not redesign roadmap direction, massively expand scope, or implement future tickets proactively.

This decision preserves implementation learning without letting execution work silently become product, roadmap, prioritisation, or technical-governance scope creation.

## Impact

Implementation Engineers may recommend prerequisite, follow-up, blocker, technical debt, defect, or implementation-improvement tickets.

Recommendations should preserve evidence, source context, blocker details, affected files or systems where relevant, and why the work should be separate.

Implementation Engineer recommendations require instruction, approval, or an established workflow before becoming created tickets or current implementation scope.

Product Manager/admin review remains required when proposed work affects product scope, product outcome, priority, acceptance intent, roadmap meaning, stakeholder expectation, or approved objectives.

Technical Strategy Lead review remains required when proposed work affects sequencing, architecture, dependencies, delivery governance, or implementation order.

Source references:

- `02-roles/implementation-engineer.md` > `Decision Authority`
- `02-roles/implementation-engineer.md` > `Behaviour Rules`
- `docs/ai-roles/implementation-engineer.md` > `Decision Rights`
- `docs/project-context/implementation-workflow.md` > `Implementation Engineer`
- `migration/resolvepm-extraction-map.md` > `Global Role Behaviour`

# ADR-027: Roles Are Completed Before Workflow Extraction

## Status

Accepted for draft migration.

## Decision

Roles are completed before workflow extraction.

ResolveOS establishes governance, context, core skills, and roles before workflow extraction begins.

Workflows depend on stable role boundaries.

## Rationale

The migration review identifies role loading as the next context governance layer and warns that workflows, templates, and missing skills should not be extracted before role boundaries are stable.

ResolvePM source material repeatedly separates role responsibility from workflow execution. Strategic Product Director defines why and what, Technical Strategy Lead defines how to sequence and deliver it, and Implementation Engineer builds scoped tickets. The migrated Product Manager, Business Analyst, and QA Tester roles add product execution clarity, requirement clarity, and validation boundaries that workflows must preserve.

Extracting workflows before these role boundaries are loaded consistently would risk flattening specialist roles, hiding approval boundaries, or letting one role absorb another role's responsibilities.

## Impact

ResolveOS should complete and review role-loading governance before creating ticket-to-implementation, implementation-review-loop, feedback-to-ticket, role-based startup, or other workflow files.

Future workflows must reference stable role boundaries instead of redefining role responsibilities.

Workflow extraction must not reopen settled role boundaries unless a contradiction is discovered and admin review approves the change.

Source references:

- `migration-review.md` > `Recommended Batch Order`
- `migration-review.md` > `Role-Boundary Assessment`
- `migration-review.md` > `ResolveOS Readiness`
- `01-context/role-loading-rules.md` > `Role Boundary Protection`
- `06-governance/extraction-migration-guardrails.md` > `Preserve Prompt and Context-Loading Discipline`
- `migration/resolvepm-extraction-map.md` > `Global Role Behaviour`

# ADR-028: Missing Context Requires Clarification, Escalation, Or Explicit Uncertainty

## Status

Accepted for draft migration.

## Decision

When required context is missing, incomplete, inaccessible, stale, or contradictory, assistants must prefer clarification, escalation, or explicit uncertainty over assumption and invention.

Missing context is a blocker unless an approved fallback rule exists.

## Rationale

ResolvePM repeatedly treats missing context as a risk to truthfulness, scope control, acceptance, implementation safety, and trust. The extraction map and migration review identify missing-context behaviour as a dedicated context governance candidate because blocker handling, explicit uncertainty, source access fallback, short prompts, ticket comments, acceptance criteria, and no-invention rules appear across roles, skills, context files, and governance.

Without a canonical missing-context rule, assistants may silently infer missing requirements, invent acceptance criteria, work from memory, hide blockers, or force implementation through unsupported assumptions.

## Impact

Assistants must classify missing, incomplete, inaccessible, stale, contradictory, ambiguous, or unsupported context before acting when that context affects safe work.

Assistants must stop and explain when missing context blocks safe progress.

Assistants may use fallbacks only when ResolveOS governance, project context, or admin instruction approves the fallback, and must state the fallback and its limitation.

Future workflows, role prompts, skills, and project-loading rules must preserve this blocker behaviour and must not weaken it into generic best-practice language.

Source references:

- `01-context/missing-context-behaviour.md` > `Missing Context Principles`
- `01-context/context-loading-rules.md` > `Missing Context`
- `01-context/role-loading-rules.md` > `Missing Role Behaviour`
- `00-system/ai-operating-principles.md` > `Explicit Uncertainty`
- `06-governance/codex-working-rules.md` > `Report Blockers Clearly`
- `03-skills/ticket-writing.md` > `Blocker Handling`
- `03-skills/acceptance-criteria.md` > `Do not guess missing acceptance criteria`
- `migration-review.md` > `Missing Governance Candidates`
- `migration/resolvepm-extraction-map.md` > `Global Context Loading Rules`

# ADR-029: Low-Risk Read-Only Analysis May Proceed With Explicit Limitations

## Status

Accepted for draft migration.

## Decision

Low-risk read-only analysis may proceed when context is incomplete if:

- limitations are stated
- assumptions are identified
- missing context is identified
- no state-changing action is taken
- conclusions remain traceable to available evidence

Implementation, approval, modification, migration, refactoring, ticket completion, and governance decisions remain blocked unless required context exists or an approved fallback applies.

## Rationale

ADR-028 establishes missing context as a blocker unless an approved fallback exists. Batch 4A.3 clarifies the boundary for read-only work: incomplete context does not always prevent analysis, but it does prevent state-changing or authority-bearing action.

ResolvePM source material repeatedly distinguishes safe explanation or review from implementation, approval, ticket completion, migration, refactoring, and governance decisions. The migration review also identifies project-loading rules as necessary to prevent context contamination between projects while still allowing useful, traceable analysis when a task is explicitly read-only.

## Impact

Assistants may provide limited read-only analysis from available evidence when the missing context does not affect safety, scope, approval, or truthfulness.

Assistants must label limitations and assumptions clearly.

Assistants must not use incomplete project context to implement, approve, modify, migrate, refactor, complete tickets, update governance, or make project/source-of-truth decisions.

Project-loading rules must preserve this distinction between read-only analysis and state-changing work.

Source references:

- `01-context/project-loading-rules.md` > `Project Validation`
- `01-context/project-loading-rules.md` > `Project Loading Principles`
- `01-context/missing-context-behaviour.md` > `Approved Fallback Rules`
- `06-governance/source-of-truth-rules.md` > `Ownership Hierarchy`
- `06-governance/codex-working-rules.md` > `Confirm Scope Before Editing`
- `migration-review.md` > `ResolveOS Readiness`
- `migration/resolvepm-extraction-map.md` > `Global Context Loading Rules`

# ADR-030: Ticket-To-Implementation Is A Workflow

## Status

Accepted for draft migration.

## Decision

Ticket-to-implementation is a workflow, not a role or skill.

Roles participate in the workflow, but the workflow owns the sequence from approved scope to implementation execution.

## Rationale

Batch 4B.1 creates the first ResolveOS workflow after the core role set and context-loading rules were established. The migration review identifies `05-workflows/ticket-to-implementation.md` as the canonical home for repeated ResolvePM behaviour around current-ticket-first execution, one-ticket-at-a-time discipline, dependency and blocker handling, validation, implementation honesty, and completion reporting.

ResolvePM source material repeatedly separates role responsibility from workflow sequence. Technical Strategy Lead owns sequencing and implementation governance. Implementation Engineer owns scoped execution. Product Manager owns product scope alignment. The workflow coordinates the handoff and execution sequence without absorbing those role authorities.

## Impact

Future ResolveOS implementation guidance should reference `05-workflows/ticket-to-implementation.md` for the sequence from approved ticket, task, source item, or approved batch into implementation execution.

Role files should describe role behaviour and authority. Skills should describe reusable task methods. Templates should describe reusable report or prompt structures. The ticket-to-implementation workflow should describe the operating sequence and review points without redefining those files.

Workflow extraction must preserve role boundaries, source-of-truth rules, missing-context behaviour, project-specific command ownership, and implementation honesty.

Source references:

- `migration-review.md` > `Recommended Batch Order`
- `migration-review.md` > `Missing Governance Candidates`
- `migration-review.md` > `Remaining ResolvePM Migration Candidates`
- `migration/resolvepm-extraction-map.md` > `Duplicates And Conflicts`
- `AGENTS.md.backup` > `Core Working Rules`
- `docs/project-context/implementation-workflow.md` > `Codex Workflow`
- `02-roles/technical-strategy-lead.md` > `Responsibilities`
- `02-roles/implementation-engineer.md` > `Behaviour Rules`

# ADR-031: Approved Batch Mode Does Not Bypass One-Ticket Discipline

## Status

Accepted for draft migration.

## Decision

Approved batch mode is permitted only when:

- the batch has explicit approval
- the scope is clearly bounded
- dependencies are understood
- completion can be reported per item

Approved batch mode must not be used to bypass one-ticket-at-a-time discipline.

## Rationale

ResolvePM source material strongly preserves one-ticket-at-a-time execution and warns against broad autonomous builds, future-ticket implementation, hidden scope expansion, and large rewrites. ResolveOS migration work also uses approved batches, but those batches are bounded review units rather than permission to merge unrelated work or skip per-item completion honesty.

This decision resolves the Batch 4B.1 ambiguity around approved batch mode by allowing explicit, bounded batches while keeping the core ticket discipline intact.

## Impact

Workflows may support approved batch mode when the admin has explicitly approved the batch and each item remains reviewable.

Batch execution must still preserve scope, dependencies, validation, blockers, deferred work, and completion reporting per item.

If a batch becomes unclear, unbounded, dependency-heavy, or impossible to report per item, the work should be split or stopped for admin review.

Source references:

- `05-workflows/ticket-to-implementation.md` > `Workflow Principles`
- `06-governance/codex-working-rules.md` > `Work One Ticket Or Batch At A Time`
- `migration-review.md` > `Migration Strengths`
- `migration/resolvepm-extraction-map.md` > `Global Working Preferences`
- `AGENTS.md.backup` > `Work sequentially`

# ADR-032: Previous-Ticket Inspection Is Conditional

## Status

Accepted for draft migration.

## Decision

Previous-ticket inspection is required when:

- dependencies exist
- sequencing exists
- implementation state may affect the current ticket

Otherwise it is recommended but not mandatory.

## Rationale

ResolvePM's `AGENTS.md.backup` required checking the immediately previous ticket before starting the next ticket. The reviewed migration sources also identify this as a valuable context-loading pattern, especially for incomplete work, uncommitted changes, changed file structure, new assumptions, and prompt adjustments.

As a global ResolveOS rule, previous-ticket inspection should be required where previous work can materially affect current implementation safety. Making it mandatory for every implementation task would overfit ResolvePM's historical Jira sequence and create unnecessary overhead for independent tasks.

## Impact

Ticket-to-implementation and implementation-review workflows should require previous-ticket inspection when dependency, sequencing, repository state, or prior implementation outcome can affect the current work.

For independent implementation tasks with no dependency or sequencing relationship, previous-ticket inspection remains recommended but not mandatory.

Project context may make previous-ticket inspection stricter for local workflows.

Source references:

- `05-workflows/ticket-to-implementation.md` > `Check Previous Work When Sequenced`
- `AGENTS.md.backup` > `Check the previous ticket first`
- `migration/resolvepm-extraction-map.md` > `Context Loading Rules Found`
- `02-roles/implementation-engineer.md` > `Review Before Implementation`

# ADR-033: Ticket-To-Implementation Is General ResolveOS Workflow

## Status

Accepted for draft migration.

## Decision

Ticket-to-implementation is a general ResolveOS workflow.

It is not limited to Codex sessions.

Any implementation-capable agent, assistant, or workflow may use it.

## Rationale

Batch 4B.1 extracted ticket-to-implementation as a ResolveOS workflow, not as Codex-only guidance. Although much of the source behaviour came from Codex and Implementation Engineer instructions, the reusable behaviour governs any implementation-capable execution surface: scope confirmation, role and project context loading, dependency checks, small safe implementation, validation, blocker handling, and honest completion reporting.

Keeping the workflow general prevents ResolveOS from duplicating separate implementation sequences for each agent type while still allowing Codex-specific execution constraints to live in Codex governance.

## Impact

Implementation-capable agents, assistants, and workflows may use `05-workflows/ticket-to-implementation.md`.

Codex-specific rules, such as manual git command preferences or environment-specific limitations, remain in `06-governance/codex-working-rules.md` or project context.

Future workflow files should distinguish general ResolveOS implementation sequence from tool-specific execution constraints.

Source references:

- `05-workflows/ticket-to-implementation.md` > `Purpose`
- `05-workflows/ticket-to-implementation.md` > `What This Workflow Must Not Do`
- `06-governance/codex-working-rules.md` > `Purpose`
- `06-governance/source-of-truth-rules.md` > `Ownership Hierarchy`
- `migration-review.md` > `ResolveOS Readiness`

# ADR-034: Feedback-To-Ticket Is A Workflow

## Status

Accepted for draft migration.

## Decision

Feedback-to-ticket is a workflow, not a skill.

The user-feedback-processing skill defines how feedback is captured, preserved, classified, and interpreted.

The ticket-writing skill defines how tickets are written.

The feedback-to-ticket workflow owns the transition from feedback into reviewed, scoped, traceable work.

## Rationale

ResolvePM source material separates feedback handling from ticket execution. The reusable feedback behaviour includes preserving original feedback, simple classification, duplicate handling, ambiguity handling, and avoiding automatic current-scope expansion. Ticket-writing behaviour separately defines how scoped work should be written.

Keeping feedback-to-ticket as a workflow prevents the feedback skill from becoming a backlog process, prevents the ticket-writing skill from absorbing feedback review, and keeps scope-control decisions visible before feedback becomes implementation work.

## Impact

Use `05-workflows/feedback-to-ticket.md` when feedback may become work.

Use `03-skills/user-feedback-processing.md` for feedback capture, preservation, classification, and interpretation.

Use `03-skills/ticket-writing.md` when feedback has been reviewed and is ready to become ticket-ready scope.

Project-specific prioritisation filters remain project-owned.

Feedback does not automatically expand current implementation scope.

Source references:

- `05-workflows/feedback-to-ticket.md` > `Purpose`
- `03-skills/user-feedback-processing.md` > `Purpose`
- `03-skills/user-feedback-processing.md` > `Converting Feedback Into Work`
- `03-skills/ticket-writing.md` > `Purpose`
- `migration-review.md` > `Recommended Batch Order`

# ADR-035: Templates Implement Existing Behaviour

## Status

Accepted for draft migration.

## Decision

Templates implement existing behaviour.

Templates inherit relevant governance, workflow, skill, and role guidance rather than redefining it.

Templates are communication structures, not behavioural definitions.

## Rationale

ResolveOS separates roles, skills, workflows, governance, context, and templates. Templates should provide reusable output or prompt structure while leaving behavioural authority in the relevant canonical files.

Batch 4C.2.1B creates `04-templates/completion-report-template.md` from existing completion reporting, decision-maker reporting, ticket-to-implementation, implementation-review, and ResolvePM source material. The template preserves the rich report structure without moving truthfulness, validation, blocker handling, role boundaries, workflow sequence, or source-of-truth rules into a template.

## Impact

Future templates must reference relevant governance, workflows, skills, roles, and context files when those files define the behaviour behind the template.

Templates must not create new roles, skills, workflows, approval authority, validation requirements, or project-specific source-of-truth rules.

If a template reveals missing behaviour, the behaviour should be deferred to the correct ResolveOS file type rather than defined inside the template.

Source references:

- `00-system/file-standard.md` > `Template File Format`
- `04-templates/completion-report-template.md`
- `06-governance/decision-maker-reporting.md`
- `03-skills/completion-reporting.md`
- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`
- `migration/resolvepm-residual-audit.md` > `completion-report-template.md`

# ADR-036: ResolveOS Outputs Include Decision-Maker Context Where Appropriate

## Status

Accepted for draft migration.

## Decision

ResolveOS outputs must include decision-maker context where appropriate.

When reporting work, reviews, blockers, recommendations, implementations, risks, or changes, outputs should explain:

- what problem is being solved
- what was actually done
- why it matters
- whether the outcome differs from the original intent
- what the decision-maker should consider next

Technical detail should remain available, but should not be the only reporting layer.

## Rationale

ResolveOS exists to support human review, validation, prioritisation, and decision-making rather than technical execution alone.

ResolvePM repeatedly preserves plain-English reporting concepts such as `What I think we are achieving`, `What was achieved`, `Why it matters`, `Did this differ from the original plan?`, `Known issues`, `Suggested follow-up tickets`, and `Next recommended ticket`.

These concepts make work understandable, reviewable, and challengeable by product-minded and non-technical decision-makers without hiding the technical evidence needed for verification.

## Impact

Future templates, workflows, roles, skills, and governance that report work should preserve both:

- decision-maker context for understanding, review, prioritisation, and next decisions
- technical evidence for verification, auditability, validation, and traceability

Reporting should not collapse into purely technical output.

Reporting should not become an executive summary that hides blockers, failed checks, uncertainty, or technical evidence.

Source references:

- `06-governance/decision-maker-reporting.md`
- `03-skills/completion-reporting.md` > `Reporting Completed Work`
- `03-skills/completion-reporting.md` > `Reporting Risk And Uncertainty`
- `05-workflows/ticket-to-implementation.md` > `Completion Reporting`
- `05-workflows/implementation-review-loop.md` > `Reviewability`
- `AGENTS.md.backup` > completion response format
- `migration/resolvepm-residual-audit.md` > residual template value

# ADR-037: Blocker Reports Support Informed Decision-Making

## Status

Accepted for draft migration.

## Decision

Blocker reports exist to support informed decision-making.

A blocker report must explain:

- what is being attempted
- what is preventing progress
- why the blocker matters
- why it cannot be safely ignored or worked around
- what options exist
- what decision or information is required

Blocker reports must support both technical validation and non-technical review.

## Rationale

ResolvePM repeatedly preserves stop-and-explain behaviour for blockers, missing context, failed validation, dependency issues, contradictory information, technical uncertainty, and escalation decisions.

Existing ResolveOS context, workflow, skill, and governance files already define the behaviour: stop when progress is unsafe, explain the blocker clearly, do not silently work around it, preserve uncertainty, state the missing information or decision, and suggest the highest-leverage unblocker or follow-up action.

The blocker report template should make that behaviour reviewable without redefining it.

## Impact

`04-templates/blocker-report-template.md` is the canonical communication structure for blocker reports.

Blocker reports should include enough decision-maker context for a reviewer to understand the objective, blocker, impact, options, risk, and required decision.

Blocker reports should include enough technical evidence for validation where evidence is available.

Templates, workflows, skills, roles, and project prompts must not turn blocker reporting into hidden scope expansion, fake completion, or silent workaround approval.

Source references:

- `04-templates/blocker-report-template.md`
- `01-context/missing-context-behaviour.md` > `Stop And Explain`
- `05-workflows/implementation-review-loop.md` > `Blocker Handling`
- `03-skills/completion-reporting.md` > `Reporting Blockers`
- `06-governance/decision-maker-reporting.md` > `Required Reporting Layers`
- `AGENTS.md.backup` > stuck-loop blocker comment format
- `migration/resolvepm-residual-audit.md` > `blocker-report-template.md`

# ADR-038: Ticket Context Templates Load Implementation-Ready Work

## Status

Accepted for draft migration.

## Decision

Ticket context templates define the standard structure for loading implementation-ready work.

A ticket context template should capture intent, scope, acceptance criteria, constraints, dependencies, risks, validation expectations, and known exclusions before work begins.

Ticket context templates support context loading and workflow execution but do not replace ticket-writing skills or implementation workflows.

## Rationale

ResolvePM repeatedly preserves current-ticket-first discipline, short context-aware prompts, ticket source loading, acceptance criteria visibility, dependency checks, blocker detection, explicit exclusions, and review-before-implementation behaviour.

Existing ResolveOS files already define the behaviour: ticket-writing owns ticket preparation, acceptance-criteria owns criteria quality, role-loading owns role context, project-loading owns project context, missing-context behaviour owns gaps and blockers, and ticket-to-implementation owns execution sequence.

The ticket context template should make that context loadable and reviewable before work begins without redefining those behaviours.

## Impact

`04-templates/ticket-context-template.md` is the canonical communication structure for capturing ticket, task, source-item, or approved-batch context before work begins.

Ticket context should make intent, approved scope, exclusions, acceptance criteria, assumptions, dependencies, missing context, validation expectations, and next action visible.

Ticket context supports both non-technical review and technical implementation planning.

Templates, workflows, skills, roles, and project prompts must not use ticket context capture as approval authority, hidden scope expansion, future-ticket implementation, or acceptance criteria invention.

Source references:

- `04-templates/ticket-context-template.md`
- `03-skills/ticket-writing.md` > `Inputs`
- `03-skills/acceptance-criteria.md` > `Inputs`
- `05-workflows/ticket-to-implementation.md` > `Inputs`
- `05-workflows/ticket-to-implementation.md` > `Confirm Scope`
- `01-context/role-loading-rules.md` > current ticket and role-loading context
- `01-context/missing-context-behaviour.md` > missing acceptance criteria
- `AGENTS.md.backup` > per-ticket startup prompt
- `migration/resolvepm-residual-audit.md` > `ticket-context-template.md`

# ADR-039: Single-Handoff Rule Is Global

## Status

Accepted.

## Decision

When giving the admin something to copy, execute, send, store, paste, or reuse, ResolveOS should prefer one complete handoff rather than multiple fragmented blocks.

This is a global communication and operating rule, not a Codex-only rule.

## Rationale

Multiple copy/paste blocks create avoidable friction and increase the chance of missed instructions, ordering mistakes, version drift, and confusion.

## Impact

Assistants and agents should:

- provide one complete artifact, prompt, message, document, or instruction block by default
- consolidate additions into the main artifact rather than giving separate appendices
- regenerate the full handoff if extra instructions are discovered after drafting
- split content only when the work genuinely requires multiple sequential steps
- avoid saying "also add this" when the better answer is a single revised version

This applies globally across prompts, messages, documents, GitHub handoffs, Codex instructions, email drafts, ticket drafts, and other reusable outputs.

Source references:

- Remote `origin/main` ADR log commit `cf86b3d`

# ADR-040: Briefings Are Approved Context Summaries

## Status

Accepted for draft migration.

## Decision

Briefings are approved context summaries.

A briefing may support ticket context, role loading, project loading, implementation planning, or decision-making when source context is scattered, inaccessible, or needs consolidation.

Briefings do not replace canonical source systems unless explicitly approved as fallback context.

## Rationale

ResolvePM used Codex briefing files to provide stable implementation and epic context when direct source-system context was unavailable or scattered. Existing ResolveOS context rules now define how briefings participate in context loading, missing-context fallback, role loading, project loading, and ticket-to-implementation work.

The briefing template should preserve the reusable structure of those source briefings while keeping project-specific roadmap, ticket, route, provider, environment, and product details in project repositories.

## Impact

`04-templates/briefing-template.md` is the canonical ResolveOS communication structure for reviewed briefing context.

Briefings may help populate ticket context, role context, project context, implementation planning, or decision-making, but they must preserve source traceability and state their limitations.

Briefings must distinguish source facts, interpretation, assumptions, recommendations, missing context, and approved fallback use.

Future workflows, templates, roles, skills, and project prompts must not treat a briefing as canonical source-system truth unless the project or admin explicitly approves that fallback.

Source references:

- `04-templates/briefing-template.md`
- `04-templates/ticket-context-template.md`
- `01-context/missing-context-behaviour.md` > approved briefing fallback
- `01-context/role-loading-rules.md` > briefing context loading
- `01-context/project-loading-rules.md` > project context traceability
- `05-workflows/ticket-to-implementation.md` > approved briefing fallback
- `docs/codex-briefings/` source structures
- `migration/resolvepm-residual-audit.md` > `briefing-template.md`

# ADR-041: Role Prompts Are Startup Guidance, Not Role Definitions

## Status

Accepted for draft migration.

## Decision

Role prompts define startup guidance and focus areas for a role.

Role prompts should reference existing ResolveOS governance, context, roles, skills, workflows, and project context rather than duplicating them.

Role prompts must not redefine role responsibilities already owned by role files.

Role prompts exist to improve startup effectiveness, not to become a second role definition.

## Rationale

ResolvePM role prompt sources are intentionally short starter prompts. They point to the role file, project context, current focus, implementation workflow, and relevant briefing or ticket context. The stronger reusable behaviour now lives in ResolveOS role files, context-loading rules, project-loading rules, role-loading rules, workflows, skills, governance, and templates.

Keeping role prompts as reference-based startup guidance preserves prompt discipline, specialist-role separation, and project-boundary discipline without duplicating or flattening role behaviour.

## Impact

`04-templates/role-prompt-template.md` is the canonical ResolveOS structure for role startup prompts.

Role prompts should identify the role, startup context, current objective, focus areas, relevant context, decision boundaries, escalation boundaries, reporting expectations, constraints, and first actions.

Role prompts must not replace role files, create role authority, define workflow sequence, or embed project-specific doctrine as global ResolveOS behaviour.

Future role prompts should stay short, non-redundant, and traceable to canonical role, context, workflow, skill, governance, template, and project files.

Source references:

- `04-templates/role-prompt-template.md`
- `01-context/role-loading-rules.md` > `Role Prompt Rules`
- `01-context/context-loading-rules.md` > `Role-Based Chat Startup`
- `01-context/project-loading-rules.md` > project context boundaries
- `docs/ai-role-prompts/implementation-engineer-prompt.md`
- `docs/ai-role-prompts/technical-strategy-lead-prompt.md`
- `docs/ai-role-prompts/strategic-product-director-prompt.md`
- `docs/ai-roles/technical-strategy-lead.md` > prompt generation discipline
- `migration/resolvepm-residual-audit.md` > `role-prompt-template.md`

# ADR-042: Running Context Preserves Active Working State

## Status

Accepted for draft migration.

## Decision

ResolveOS uses a running context file to preserve active working state.

The running context is shared working memory for ongoing work.

Agents should read the running context before continuing significant migration, implementation, review, governance, or architecture work.

The running context is not a historical changelog.

Historical decisions belong in ADRs, reviews, migration reports, project records, and source systems.

The running context represents current state only.

Role-specific running contexts may exist when justified, but they must not become competing sources of truth.

## Rationale

ResolveOS work spans chats, agents, sessions, migrations, reviews, and handoffs. Relying on conversation memory risks losing active state, repeating completed work, missing open decisions, or treating stale context as current.

Existing ResolveOS context-loading and source-of-truth rules already require assistants not to work from memory when required context exists. A running context gives agents a concise current-state checkpoint without turning the ADR log, migration reviews, or project records into working memory.

## Impact

`01-context/running-context.md` is the canonical global running context file.

Agents should read it before significant migration, implementation, review, governance, or architecture work.

Updates should keep it concise and current-state focused.

Running context must not duplicate ADR content, migration reports, template reviews, project records, or source systems.

Project-specific current state belongs in project repositories. Role-specific running contexts may exist only when justified and must not become competing sources of truth.

Source references:

- `01-context/running-context.md`
- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `01-context/project-loading-rules.md`
- `06-governance/source-of-truth-rules.md`
- `migration/template-layer-review.md`

# ADR-043: Decision Logs Preserve Durable Decision Rationale

## Status

Accepted for draft migration.

## Decision

Decision logs capture durable decisions and their rationale.

Decision logs exist to preserve why a decision was made, not merely what was decided.

Decision logs complement ADRs, project records, and running context.

Decision logs are not changelogs, ticket histories, or implementation reports.

Decision logs must support both technical and non-technical review.

## Rationale

ResolveOS already separates durable architecture decisions, current working state, project-owned records, and reporting templates. The template layer review identified durable decision/source-tracker traceability as the clearest remaining template-layer gap.

Decisions often need more than a final answer. Reviewers need to understand the problem, options considered, recommended option, final decision, rationale, trade-offs, risks accepted, rejected alternatives, consequences, follow-up actions, related ADRs, related tickets, and review trigger.

Capturing that structure prevents decision rationale from being lost in chat history, memory, informal notes, or implementation reports.

## Impact

`04-templates/decision-log-template.md` is the canonical ResolveOS structure for durable decision logs.

Decision logs should preserve rationale, alternatives, trade-offs, risks, consequences, follow-up actions, source references, and review date where relevant.

Decision logs complement ADRs, but they do not replace ADRs. Architecture decisions that affect reusable behaviours, migration boundaries, source ownership, or future file creation still belong in `06-governance/architecture-decisions.md`.

Decision logs complement running context, but they do not replace running context. Current working state belongs in `01-context/running-context.md`.

Decision logs complement completion and blocker reports, but they do not replace implementation reporting.

Project-specific decisions remain project-owned unless separately promoted under ResolveOS source-of-truth rules.

Source references:

- `04-templates/decision-log-template.md`
- `06-governance/decision-maker-reporting.md`
- `01-context/running-context.md`
- `06-governance/source-of-truth-rules.md`
- `migration/template-layer-review.md`
- `migration/resolvepm-residual-audit.md`

# ADR-044: Update Process Maintains Architectural Integrity

## Status

Accepted for draft migration.

## Decision

ResolveOS uses a defined update process to maintain architectural integrity.

Changes should be applied to the correct layer.

Updates should occur at the source of ownership rather than through duplication.

Running context, ADRs, governance, roles, skills, workflows, templates, and project-specific artifacts each have distinct update responsibilities.

Update ownership must remain explicit.

## Rationale

The architecture review identified update-process governance as one of the highest-priority remaining gaps. ResolveOS now has enough layers that ungoverned updates could cause rule drift, duplication, role boundary erosion, template overreach, or project-specific doctrine leaking into global files.

ResolvePM source material repeatedly preserves update discipline: identify which file should be updated, explain why it should be updated, state whether the update is urgent or can wait, and do not let important context drift.

A canonical update process keeps maintenance decisions aligned with source-of-truth ownership and prevents changes from being made in whichever file happens to be nearest.

## Impact

`06-governance/update-process.md` is the canonical ResolveOS governance file for update ownership, layer responsibility, change propagation, review expectations, and update anti-patterns.

Running context remains the current-state layer.

ADRs remain the durable architecture decision layer.

Governance owns system rules.

Roles own responsibilities and authority.

Skills own reusable task methods.

Workflows own process sequence.

Templates own communication structure.

Project repositories own project-specific artifacts.

Future ResolveOS updates should identify the owning layer before changing files. If ownership is unclear, the update need should be deferred or escalated for admin review rather than guessed.

Source references:

- `06-governance/update-process.md`
- `06-governance/source-of-truth-rules.md`
- `01-context/running-context.md`
- `01-context/project-loading-rules.md`
- `01-context/role-loading-rules.md`
- `06-governance/decision-maker-reporting.md`
- `migration/resolveos-architecture-review.md`
- `migration/resolvepm-residual-audit.md`
- `docs/project-context/implementation-workflow.md`
- `docs/ai-roles/technical-strategy-lead.md`

# ADR-045: Duplication Control Prevents Rule Drift

## Status

Accepted for draft migration.

## Decision

ResolveOS uses duplication-control governance to prevent repeated rules from drifting across roles, skills, workflows, templates, and governance files.

High-value rules may be repeated locally for clarity, but their canonical ownership must remain clear.

## Rationale

The architecture review identified useful repeated rules as the biggest current maintenance risk. ResolveOS intentionally repeats high-value rules such as no fake functionality, completion honesty, blocker visibility, one-ticket discipline, source-of-truth boundaries, and specialist role protection across multiple surfaces.

This repetition protects behaviour, but without governance it can drift, weaken, or become conflicting over time.

Duplication control preserves the source-of-truth model while avoiding over-flattening. It allows local reminders where they protect safety, role clarity, or reviewability, but keeps ownership explicit.

## Impact

`06-governance/duplication-control.md` is the canonical ResolveOS governance file for duplicated instruction handling.

Future cleanup should identify canonical ownership before removing repeated rules.

High-value safety and behaviour rules may remain locally repeated when the repetition is intentional and traceable.

Do not weaken wording-sensitive rules by replacing them with generic best-practice language.

Do not remove repeated high-value rules merely to reduce file count.

Source references:

- `06-governance/duplication-control.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/update-process.md`
- `migration/resolveos-architecture-review.md`
- `migration/resolvepm-residual-audit.md`
- `migration-review.md`

# ADR-046: Chat Handoffs Preserve Session Continuity

## Status

Accepted for draft migration.

## Decision

Chat handoffs preserve session continuity.

A chat handoff is a short markdown file created when a chat/session becomes too long, stale, interrupted, or needs migration.

Chat handoffs preserve current objective, completed work, unresolved decisions, active risks, next recommended step, and source-of-truth references.

Chat handoffs must not become full transcripts or duplicate running context.

## Rationale

ResolveOS now has running context for shared current state, but long chats and Codex sessions can still become too long, stale, interrupted, or hard to continue safely. A concise handoff gives the next chat or agent enough context to continue without relying on memory or copying a full transcript.

The handoff template preserves continuity while respecting source-of-truth discipline. Running context remains the shared current-state layer; handoffs are session-specific transfer artifacts.

## Impact

`04-templates/chat-handoff-template.md` is the canonical ResolveOS template for chat and session migration.

Use chat handoffs for ChatGPT chat migration, Codex session migration, long-running project handoff, role-switch handoff, interrupted work recovery, and concise session transfer.

Do not use chat handoffs as transcripts, source-of-truth replacements, completion reports, blocker reports, decision logs, or project current-focus files.

Source references:

- `04-templates/chat-handoff-template.md`
- `01-context/running-context.md`
- `06-governance/update-process.md`
- `06-governance/duplication-control.md`
- `migration/resolveos-architecture-review.md`

# ADR-047: Running Context Freshness Is Metadata-Driven

## Status

Accepted for draft migration.

## Decision

Running context freshness is metadata-driven.

Agents should use file metadata such as `last_updated` and `max_staleness_days` rather than relying on chat message timestamps.

If running context is stale before significant work, agents should update it or create a chat handoff before continuing.

## Rationale

Chat timestamps are not reliable source-of-truth evidence for repository state. Running context is a file-backed current-state artifact, so its freshness should be determined from file metadata and current repository context.

Metadata-driven freshness prevents agents from relying on old chat memory, stale assumptions, or interrupted-session context when significant migration, implementation, review, governance, or architecture work continues.

## Impact

`01-context/running-context.md` includes `last_updated` and `max_staleness_days` metadata.

Before significant work, agents should check running-context freshness.

If running context is stale and the current state is known, update running context.

If running context is stale because a session needs migration or chat-specific continuity, create a chat handoff.

If current state cannot be determined safely, stop and ask for admin review rather than guessing.

Source references:

- `01-context/running-context.md`
- `04-templates/chat-handoff-template.md`
- `06-governance/update-process.md`
- `01-context/context-loading-rules.md`
- `01-context/missing-context-behaviour.md`

# ADR-048: ResolveOS Supports Project Initiation

## Status

Accepted for draft migration.

## Decision

ResolveOS supports project initiation.

Project initiation may be:

- new project initiation
- existing project adoption

The workflow establishes project operating structure, source-of-truth ownership, required roles, recommended chats, context management, and initial running context.

Project initiation must not overwrite existing project state without explicit approval.

## Rationale

ResolveOS is intended to be reusable across projects. Applying it safely requires a structured AI entrypoint that distinguishes a new project from an existing project, preserves project-owned source systems, and recommends only the roles, chats, context, tools, and operating model that fit the project.

Existing ResolveOS governance already separates global behaviour from project-specific doctrine. Project initiation turns that separation into a practical workflow before implementation, ticketing, adoption, or cleanup work begins.

## Impact

`05-workflows/project-initiation.md` is the canonical ResolveOS workflow for starting a new project or adopting an existing project.

Project initiation should produce a Project Setup Report with recommended roles, chats, context files, source systems, integrations, operating model, known gaps, and next actions.

The workflow may recommend project files, source systems, tools, chats, and integrations, but it must not create or overwrite them without explicit approval.

Existing project state must be preserved and assessed before replacement or refactor is recommended.

Source references:

- `05-workflows/project-initiation.md`
- `01-context/project-loading-rules.md`
- `01-context/role-loading-rules.md`
- `01-context/running-context.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/update-process.md`
- `06-governance/duplication-control.md`

# ADR-049: Dependency Management Is A Reusable Skill

## Status

Accepted for draft migration.

## Decision

Dependency management is a reusable skill.

Dependency management identifies, validates, sequences, tracks, and communicates dependencies without assuming implementation ownership.

## Rationale

ResolveOS already preserves dependency behaviour across ticket-writing, ticket-context capture, briefing context, ticket-to-implementation, implementation review, Technical Strategy Lead behaviour, blocker reporting, and completion reporting.

The architecture review and residual audit both identify dependency management as a high-evidence missing skill. Centralising the reusable method reduces scattered repetition while preserving existing role, workflow, governance, and project ownership boundaries.

## Impact

`03-skills/dependency-management.md` is the canonical ResolveOS skill for dependency identification, classification, validation, sequencing, risk assessment, communication, and tracking.

The skill does not approve implementation scope, create dependency tickets automatically, replace Technical Strategy Lead authority, replace workflow sequence, or move project-specific dependency state into ResolveOS.

Dependency work outside approved scope must be reported as prerequisite, blocker, or follow-up work rather than silently added to the current ticket.

Source references:

- `03-skills/dependency-management.md`
- `03-skills/ticket-writing.md`
- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`
- `02-roles/technical-strategy-lead.md`
- `04-templates/ticket-context-template.md`
- `04-templates/briefing-template.md`
- `migration/resolvepm-residual-audit.md`
- `migration/resolveos-architecture-review.md`

# ADR-050: Requirement Traceability Is A Reusable Skill

## Status

Accepted for draft migration.

## Decision

Requirement traceability is a reusable skill.

Requirement traceability preserves links between objectives, requirements, acceptance criteria, implementation, validation, feedback, and follow-up work.

## Rationale

ResolveOS repeatedly requires original intent preservation, source-backed requirements, acceptance criteria alignment, feedback traceability, validation evidence, drift reporting, and follow-up separation.

The architecture review and residual audit identify requirement traceability as a high-evidence missing skill repeated across Product Manager, Business Analyst, QA Tester, ticket-writing, acceptance criteria, user-feedback processing, completion reporting, decision-maker reporting, feedback-to-ticket, and implementation-review work.

## Impact

`03-skills/requirement-traceability.md` is the canonical ResolveOS skill for preserving links from source intent through requirements, acceptance criteria, implementation, validation, feedback, decisions, blockers, and follow-up work.

The skill does not approve scope, create tickets automatically, replace project source systems, replace role authority, or impose project-specific traceability schemas globally.

Source references:

- `03-skills/requirement-traceability.md`
- `02-roles/business-analyst.md`
- `03-skills/user-feedback-processing.md`
- `03-skills/acceptance-criteria.md`
- `03-skills/ticket-writing.md`
- `06-governance/decision-maker-reporting.md`
- `05-workflows/feedback-to-ticket.md`
- `migration/resolvepm-residual-audit.md`
- `migration/resolveos-architecture-review.md`

# ADR-051: Implementation Review Is A Reusable Skill

## Status

Accepted for draft migration.

## Decision

Implementation review is a reusable skill.

Implementation review assesses whether delivered work satisfies approved scope, acceptance criteria, architectural intent, validation requirements, and documented decisions.

## Rationale

ResolveOS already contains workflow, role, reporting, and template behaviour for reviewing stuck, failed, drifted, blocked, questionable, partial, or completed implementation work.

The architecture review and residual audit identify implementation review as a high-evidence missing skill. A reusable review method helps preserve implementation honesty, no fake completion, validation awareness, acceptance criteria alignment, implementation drift detection, architectural alignment, blocker visibility, and follow-up separation without duplicating workflow sequence or role authority.

## Impact

`03-skills/implementation-review.md` is the canonical ResolveOS skill for reviewing implementation scope, acceptance criteria, validation, architecture, documentation, drift, and review outcomes.

The skill does not replace the implementation-review-loop workflow, QA sign-off, Technical Strategy Lead authority, completion-reporting template, blocker-reporting template, or project-specific verification commands.

Source references:

- `03-skills/implementation-review.md`
- `05-workflows/implementation-review-loop.md`
- `05-workflows/ticket-to-implementation.md`
- `03-skills/completion-reporting.md`
- `03-skills/acceptance-criteria.md`
- `06-governance/decision-maker-reporting.md`
- `04-templates/completion-report-template.md`
- `04-templates/blocker-report-template.md`
- `migration/resolvepm-residual-audit.md`
- `migration/resolveos-architecture-review.md`

# ADR-052: Project Initiation Is The Canonical ResolveOS Entry Point

## Status

Accepted for draft migration.

## Decision

Project initiation is the governing ResolveOS workflow for new project initiation, existing project adoption, and existing project continuation.

`00-system/resolveos-entrypoint.md` is the canonical ResolveOS AI entrypoint.

Project initiation supports:

- new project initiation
- existing project adoption
- continue existing project

When project access is available, `05-workflows/project-initiation.md` is the governing workflow for new project initiation, existing project adoption, and existing project continuation.

Project initiation recommends structure, roles, chats, context, source-of-truth ownership, and next actions.

## Rationale

ResolveOS now has enough draft context, role, skill, workflow, template, and governance coverage that projects need a single starting workflow rather than scattered setup instructions.

Existing ResolveOS governance already requires project-owned source systems, role boundaries, context loading, update ownership, and duplication control. Project initiation provides the governing workflow for applying those rules to new projects, adopting existing projects, or safely continuing existing work after a pause, handoff, or chat change.

## Impact

`00-system/resolveos-entrypoint.md` is the canonical ResolveOS AI entrypoint.

`05-workflows/project-initiation.md` is the governing project-initiation workflow when project access is available.

Project initiation should not create bootstrap files, external systems, alternative AI entrypoints, duplicate project-initiation workflows, roles, skills, templates, or project files without explicit approved scope.

Project initiation must preserve existing project state and should not overwrite project structures without explicit approval.

Source references:

- `05-workflows/project-initiation.md`
- `01-context/project-loading-rules.md`
- `01-context/role-loading-rules.md`
- `01-context/running-context.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/update-process.md`
- `06-governance/duplication-control.md`
- `migration/resolveos-architecture-review.md`

# ADR-053: ResolveOS Distinguishes Between Readiness States

## Status

Accepted for draft migration.

## Decision

ResolveOS distinguishes between different readiness states.

A project may be:

- Adoption Ready
- Discovery Ready
- Planning Ready
- Implementation Ready
- Validation Ready

Readiness must be assessed independently.

Being ready for one stage does not imply readiness for another.

## Rationale

The ResolveYGO adoption validation showed that successful project adoption does not automatically mean the project is ready for implementation or validation. A project can have enough evidence for adoption or discovery while still missing canonical source confirmation, active scope, acceptance criteria, implementation evidence, or validation paths.

Separate readiness states prevent false confidence, hidden blockers, and premature implementation.

## Impact

`06-governance/project-readiness.md` defines readiness assessment across project lifecycle states.

`05-workflows/project-initiation.md` should report adoption, discovery, planning, implementation, and validation readiness independently when readiness affects the next action.

Source references:

- `06-governance/project-readiness.md`
- `05-workflows/project-initiation.md`
- `migration/architecture-review-3.md`
- ResolveYGO adoption validation findings

# ADR-054: Project Initiation Must Identify The Canonical Project Source

## Status

Accepted for draft migration.

## Decision

Project initiation must identify the canonical project source.

Where multiple repositories, folders, databases, trackers, or implementations exist, project initiation must determine which source is authoritative and identify inconsistencies.

## Rationale

The ResolveYGO adoption validation showed that project adoption can involve multiple candidate sources. Without a canonical source assessment, agents may use the nearest repository, newest file, tracker status, or partial implementation as truth.

Canonical source assessment preserves source-of-truth discipline during project initiation and prevents implementation or validation work from starting from the wrong source.

## Impact

`05-workflows/project-initiation.md` includes canonical source assessment for repository, implementation location, tracker, and documentation source.

If the canonical source cannot be determined safely, the inconsistency should be reported for admin or project-owner decision rather than guessed.

Source references:

- `05-workflows/project-initiation.md`
- `06-governance/source-of-truth-rules.md`
- `01-context/project-loading-rules.md`
- ResolveYGO adoption validation findings

# ADR-055: ResolveOS Supports Reconciliation Between Tracker State And Repository Reality

## Status

Accepted for draft migration.

## Decision

ResolveOS supports reconciliation between tracker state and repository reality.

Differences between plans, trackers, reports, metadata, implementation status, and repository state should be surfaced explicitly rather than silently ignored.

## Rationale

Project adoption validation showed that tracker state, documentation state, metadata, reports, and repository reality can diverge. Silent selection of one source creates false progress, false completion, and bad continuation.

Reconciliation does not mean ResolveOS owns the project state. It means ResolveOS must expose the mismatch so the correct project source owner can decide.

## Impact

`05-workflows/project-initiation.md` includes reconciliation checks for tracker vs repository, plan vs implementation, metadata vs actual state, repository vs external implementation, documentation vs source, completion reports vs repository reality, and decisions vs active behaviour.

Project-specific reconciliation rules, tracker fields, repository naming, commands, and implementation details remain project-owned.

Source references:

- `05-workflows/project-initiation.md`
- `06-governance/project-readiness.md`
- `06-governance/source-of-truth-rules.md`
- ResolveYGO adoption validation findings

# ADR-056: Continuation Requires Evidence

## Status

Accepted for draft migration.

## Decision

Continuation requires evidence.

Where possible, project continuation should identify:

- current objective
- last completed work
- active work
- active blockers
- latest completion evidence
- latest decision evidence

before implementation begins.

## Rationale

ResolveOS already rejects working from memory when required context exists. The ResolveYGO adoption validation showed that continuation needs a sharper evidence check: what is active, what was last completed, what is blocked, and what evidence supports the current state.

Evidence-backed continuation reduces repeated work, false assumptions, stale context use, and implementation from chat memory.

## Impact

`05-workflows/project-initiation.md` includes continuation evidence checks.

`01-context/running-context.md` records this validation finding and points agents toward evidence-backed continuation.

Missing continuation evidence should be reported as missing rather than invented.

Source references:

- `05-workflows/project-initiation.md`
- `01-context/running-context.md`
- `04-templates/completion-report-template.md`
- `04-templates/chat-handoff-template.md`
- ResolveYGO adoption validation findings

# ADR-057: Planning State Is Project-Owned And Source-System-Aware

## Status

Accepted for draft migration.

## Decision

ResolveOS defines lightweight planning concepts but does not own project planning state.

Canonical planning concepts are:

- Objective
- Highest-Leverage Activity
- Top 3 Recommended Actions
- Active Work
- Backlog
- Blockers
- Risks

If Jira, Notion, GitHub Issues, Azure DevOps, or another planning system is declared authoritative, ResolveOS must use that source.

If no planning source exists, ResolveOS may support a lightweight project-owned planning model through a project current-focus, running-context, plan, tracker, or equivalent source.

ResolveOS must not create a competing roadmap, backlog, or project-management system.

## Rationale

ResolveOS needs enough planning persistence to answer what the project is trying to achieve, what is being worked on, what comes next, and what is blocked. It does not need to recreate external planning tools or move project-specific state into global ResolveOS guidance.

Source-system-aware planning preserves source-of-truth ownership while giving continuation a small stable vocabulary.

## Impact

`05-workflows/project-initiation.md` defines planning state and continuation output.

`06-governance/source-of-truth-rules.md` keeps project planning state project-owned and requires declared external planning systems to be used when they exist.

Project-specific planning fields, tracker statuses, roadmaps, ticket keys, and workflow conventions remain project-owned.

Source references:

- `05-workflows/project-initiation.md`
- `06-governance/source-of-truth-rules.md`
- `01-context/running-context.md`

# ADR-058: Decisions Use A Lightweight Lifecycle

## Status

Accepted for draft migration.

## Decision

ResolveOS decisions use a lightweight lifecycle:

- Proposed
- Active
- Superseded
- Rejected

Existing ADRs that use `Accepted` should be treated as `Active` unless a later ADR or decision record supersedes or rejects them.

Project continuation should identify active, proposed, superseded, and rejected decisions where decision state affects safe progress.

## Rationale

ResolveOS already has ADRs and a decision-log template, but continuation needs a consistent way to distinguish governing decisions from pending, replaced, or rejected decisions.

A small lifecycle improves continuity without adding approval bureaucracy or replacing project-owned decision systems.

## Impact

`05-workflows/project-initiation.md` defines the lifecycle and continuation behaviour.

`04-templates/decision-log-template.md` uses the shared decision states for durable non-ADR decision records.

Architecture decisions remain in `06-governance/architecture-decisions.md`; project-specific decisions remain project-owned.

Source references:

- `05-workflows/project-initiation.md`
- `04-templates/decision-log-template.md`
- `06-governance/architecture-decisions.md`

# ADR-059: Validation State Uses Assumptions, Evidence, Confidence, And Status

## Status

Accepted for draft migration.

## Decision

ResolveOS uses a lightweight validation model when readiness, continuation, product direction, commercial validation, or implementation validation depends on assumptions.

Core concepts are:

- Assumption
- Evidence
- Confidence
- Validation Status

Validation statuses are:

- Proven
- Partially validated
- Unvalidated
- Disproven

## Rationale

ResolveOS can identify assumptions and risks, but readiness and continuation need a consistent way to show what is proven, partially validated, unvalidated, or disproven.

The model improves validation honesty without creating a research-management system.

## Impact

`06-governance/project-readiness.md` defines the validation state model.

`05-workflows/project-initiation.md` uses validation state for planning, continuation, and Project Setup Reports.

Project-specific research plans, analytics, customer records, test commands, acceptance evidence, and validation artifacts remain project-owned.

Source references:

- `06-governance/project-readiness.md`
- `05-workflows/project-initiation.md`
- `06-governance/source-of-truth-rules.md`

# ADR-060: Information Architecture Governs Storage Decisions

## Status

Accepted for draft migration.

## Decision

ResolveOS must decide information architecture before writing to documentation, workspace, knowledge-base, project-management, repository, or local storage tools.

ResolveOS should identify:

- information type
- storage model
- source-of-truth owner
- location
- whether existing structure should be updated
- whether new top-level storage is justified

ResolveOS must not assume durable information becomes a page.

New top-level pages, documents, files, folders, or database structures are justified only for new major projects, product areas, systems, databases, or durable knowledge domains.

Routine feedback, notes, decisions, risks, meeting outputs, implementation context, discovery items, research items, validation findings, and conversation summaries should usually be stored inside the relevant existing structure using the storage model appropriate to the information type.

## Rationale

Documentation and workspace tools can become fragmented when AI creates standalone pages, files, folders, documents, or databases for routine information. That creates cleanup work, hides context, and weakens source-of-truth discipline.

The earlier documentation-storage capability prevented random top-level page creation, but it still risked assuming that durable information should become a page. ResolveOS must first decide what kind of information exists and what storage model should own it.

ResolveOS already separates global governance from project-owned context and requires source-system-aware planning. Information architecture is part of that same discipline: the correct model and home for information matter as much as the content itself.

## Impact

`03-skills/information-architecture.md` is the canonical ResolveOS skill for classifying information and selecting storage model, source owner, location, and execution path before writing to documentation and workspace tools.

`00-system/resolveos-entrypoint.md` routes save, store, documentation, Notion, feedback capture, risk storage, discovery item preservation, and conversation-preservation requests through the skill.

`06-governance/source-of-truth-rules.md` treats storage model and location as source-of-truth discipline.

`05-workflows/project-initiation.md` recommends tools together with the information architecture model for using them well.

Project-specific documentation structures, databases, folders, schemas, tool permissions, and workspace conventions remain project-owned.

Source references:

- `03-skills/information-architecture.md`
- `00-system/resolveos-entrypoint.md`
- `06-governance/source-of-truth-rules.md`
- `05-workflows/project-initiation.md`

# Enforcement

When future ResolveOS files touch global dependency structure, dependency management, requirement traceability, implementation review, project readiness, canonical project source assessment, tracker/repository reconciliation, evidence-backed continuation, project planning state, decision lifecycle, validation state, information architecture, canonical AI entrypoint behaviour, role/skill separation, context loading, running context, running-context freshness, chat handoffs, project initiation, update process, duplication control, decision-log templates, missing-context behaviour, project-loading rules, low-risk read-only analysis, metadata, global/project ownership, assistant operating principles, startup context, role-loading rules, role prompt structure, workflow extraction order, workflow ownership, ticket-to-implementation sequence, implementation-review-loop behaviour, feedback-to-ticket transition, template ownership, approved batch mode, previous-ticket inspection, general workflow applicability, Codex execution constraints, no-fake-functionality, cost-safe AI/API behaviour, acceptance-criteria format, ticket context, briefing context, completion reporting, blocker reporting, single-handoff communication, project verification commands, dependency ordering, feedback schema, default message classification, prioritisation filters, Product Manager ticket authority, Product Manager role boundary, Business Analyst ticket authority, QA Tester defect ticket authority, QA role taxonomy, Technical Strategy Lead technical ticket authority, Implementation Engineer ticket proposal authority, low-risk scope clarification, documentation hygiene ownership, or decision-maker reporting, they must follow ADR-001 through ADR-060 unless admin explicitly changes these decisions.

# Exceptions

Projects may override these decisions locally when:

- the override is explicit
- the project context owns the reason
- the override does not silently become global ResolveOS doctrine

# Examples

Project-owned extension:

```text
ResolveOS canonical feedback fields:
- category
- message
- user
- timestamp

Project extension:
- severity
- product area
- duplicate reference
- review status
```

# Reconciliation Notes

This file was reconciled during Batch 3B.2.

ADR-001 through ADR-005 were restored from `00-system/resolveos-implementation-plan.md`.

ADR-006 through ADR-010 were restored from accepted Batch 1 files because no separate historical ADR text was present in the checkout.

ADR-011 through ADR-014 were restored from accepted Batch 2 skill references and current accepted file state.

ADR-015 through ADR-024 were preserved from the existing architecture decision log.

ADR-025 was added from the Batch 3B.2 instruction.

ADR-018 was restored from accepted Product Manager role boundaries and the extraction map's specialist-role separation.

ADR-026 was added from the Batch 3B.3 instruction.

ADR-027 was added from the Batch 4A.1 instruction.

ADR-028 was added from the Batch 4A.2 instruction.

ADR-029 was added from the Batch 4A.3 instruction.

ADR-030 was added from the Batch 4B.1 instruction.

ADR-031 through ADR-033 were added from the Batch 4B.2 instruction.

ADR-034 was added from the Batch 4B.3 instruction.

ADR-035 was added from the Batch 4C.2.1B instruction.

ADR-036 was added from the Batch 4C.2.1A instruction.

ADR-037 was added from the Batch 4C.2.2 instruction.

ADR-038 was added from the Batch 4C.2.3 instruction.

ADR-039 was preserved from remote `origin/main` during the final migration push rebase. It was renumbered from the remote ADR-018 to avoid conflicting with the existing migration ADR-018.

ADR-040 was added from the Batch 4C.2.4 instruction. The instruction requested ADR-039, but ADR-039 already existed in the current repository, so the briefing decision was assigned the next available ADR number to avoid duplicate ADR IDs.

ADR-041 was added from the Batch 4C.2.5 instruction.

ADR-042 was added from the Batch 4D.1 instruction.

ADR-043 was added from the Batch 4D.2 instruction.

ADR-044 was added from the Batch 5.1 instruction.

ADR-045 through ADR-047 were added from the combined Batch 5.1 governance stabilisation and context continuity instruction.

ADR-048 was added from the Batch 5.3 instruction.

ADR-049 through ADR-051 were added from the Batch 6.1 instruction.

ADR-052 was added from the Batch 6.1 project initiation refinement instruction.

ADR-053 through ADR-056 were added from the Batch 7.0 ResolveYGO adoption validation refinement instruction.

ADR-057 through ADR-059 were added from the final core project-state management refinement instruction.

ADR-060 was added from the documentation storage architecture instruction and refined by the information architecture instruction.

---

# Source: 06-governance/codex-working-rules.md

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

---

# Source: 06-governance/decision-maker-reporting.md

---
type: governance
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration-review.md
  - migration/resolvepm-residual-audit.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
  - docs/project-context/implementation-workflow.md
  - docs/ai-roles/implementation-engineer.md
  - docs/ai-roles/technical-strategy-lead.md
  - docs/ai-core/operational-clarity-framework.md
related_roles:
  - 02-roles/product-manager.md
  - 02-roles/business-analyst.md
  - 02-roles/qa-tester.md
  - 02-roles/technical-strategy-lead.md
  - 02-roles/implementation-engineer.md
  - 02-roles/strategic-product-director.md
related_skills:
  - 03-skills/completion-reporting.md
  - 03-skills/ticket-writing.md
  - 03-skills/acceptance-criteria.md
  - 03-skills/user-feedback-processing.md
related_workflows:
  - 05-workflows/ticket-to-implementation.md
  - 05-workflows/implementation-review-loop.md
  - 05-workflows/feedback-to-ticket.md
related_governance:
  - 00-system/ai-operating-principles.md
  - 06-governance/codex-working-rules.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define the ResolveOS reporting philosophy that makes technical work understandable, reviewable, and challengeable by non-technical decision-makers.

ResolveOS reporting should support human review, validation, prioritisation, and decision-making. Technical detail should remain available, but it should not be the only reporting layer.

This file is governance. It is not a completion report template, blocker report template, ticket prompt template, skill, workflow, role, or executive-summary format.

Source references:

- `03-skills/completion-reporting.md` > completion reporting principles and outputs
- `05-workflows/ticket-to-implementation.md` > completion reporting
- `05-workflows/implementation-review-loop.md` > reviewability and drift handling
- `AGENTS.md.backup` > ticket startup, implementation drift, blocker, and completion response formats
- `migration/resolvepm-residual-audit.md` > residual template value and completion-report risk
- `migration-review.md` > migration strengths, duplication, and remaining candidates

# When To Use

Use this governance when reporting:

- completed work
- partial work
- failed work
- blocked work
- implementation drift
- validation or QA results
- risks and trade-offs
- recommendations
- follow-up work
- migration batches
- reviews
- decisions
- changes that need admin or stakeholder judgement

Use this when a report may be read by a product-minded, non-technical, or decision-making audience that needs to understand what happened and what to decide next.

# Reporting Principles

## Decision-Maker Context Where Appropriate

When reporting work, reviews, blockers, recommendations, implementations, risks, or changes, include decision-maker context where appropriate.

Explain:

- what problem is being solved
- what was actually done
- why it matters
- whether the outcome differs from the original intent
- what the decision-maker should consider next

Source references:

- ADR-036 in `06-governance/architecture-decisions.md`
- `AGENTS.md.backup` > `What I think we are achieving`, `What was achieved`, `Why it matters`, `Did this differ from the original plan?`

## Truth Before Framing

Decision-maker reporting must not soften or hide reality.

Do not claim work was done unless it was actually done.

Do not imply validation, testing, deployment, commit, source-ticket update, storage, approval, or completion happened unless there is direct evidence.

Source references:

- `00-system/ai-operating-principles.md` > truthfulness and implementation honesty
- `03-skills/completion-reporting.md` > truthfulness before fluency
- `06-governance/codex-working-rules.md` > do not invent implementation claims

## Plain English Before Dense Technical Detail

Start with the decision-maker layer when the output is meant for review.

Use plain English to explain the intent, outcome, impact, risk, uncertainty, and next step.

Technical details should remain available after the decision-maker layer or alongside it when they are needed to verify the claim.

Source references:

- `00-system/ai-operating-principles.md` > plain-English communication
- `AGENTS.md.backup` > explain the outcome in plain English
- `02-roles/implementation-engineer.md` > simple enough for a non-expert product-minded admin to follow

## Reviewable And Challengeable

Reports should make the work reviewable.

A reviewer should be able to challenge:

- whether the work matched the original intent
- whether the acceptance criteria are still satisfied
- whether the reported validation proves enough
- whether blockers or risks remain
- whether follow-up work is separate from completed scope
- whether technical decisions changed product, requirement, delivery, or validation meaning

Source references:

- `03-skills/completion-reporting.md` > preserve reviewability
- `05-workflows/implementation-review-loop.md` > reviewability
- `migration-review.md` > traceability and completion honesty duplication

## Both Layers Matter

Do not reduce reporting to purely technical output.

Do not reduce reporting to an executive summary that hides technical evidence.

Keep both layers:

- decision-maker context for understanding and judgement
- technical evidence for verification and auditability

# Decision-Maker Context

Decision-maker context explains why the technical work matters to the human reviewing it.

It should answer the practical review questions:

- What were we trying to achieve?
- What actually happened?
- Why does this matter?
- Did reality differ from the plan?
- What is still uncertain, risky, blocked, partial, or deferred?
- What decision or next action is needed?

Use decision-maker context when technical facts alone would leave the admin or stakeholder unable to judge whether the work is acceptable, risky, incomplete, strategically relevant, or ready for follow-up.

# Required Reporting Layers

Use only the layers that fit the report, but do not omit an important layer just because it is not technical.

## 1. Intent Layer

Explain the original intent, goal, ticket, task, review question, or problem being solved.

Preserved source concepts:

- `What I think we are achieving`
- ticket, task, or scope
- goal
- why it matters
- assumptions

## 2. Outcome Layer

Explain what was actually done or found.

Preserved source concepts:

- `What was achieved`
- implementation path
- validation result
- review result
- current status

## 3. Difference Layer

Explain whether the result differs from the original plan, ticket, acceptance criteria, or expected path.

Preserved source concepts:

- `Did this differ from the original plan?`
- original plan
- what actually happened
- why it changed
- impact
- follow-up needed

## 4. Risk And Uncertainty Layer

Explain known issues, blockers, failed checks, missing context, assumptions, uncertainty, and residual risk.

Preserved source concepts:

- known issues
- blockers
- checks not run
- not verified
- partial or blocked status
- first clear failure where available

## 5. Recommendation Layer

Explain what should happen next.

Preserved source concepts:

- suggested follow-up tickets
- suggested documentation updates
- next recommended ticket
- highest-leverage follow-up action
- admin-review question

## 6. Evidence Layer

Provide enough technical detail to support review.

Evidence may include files changed, commands run, checks not run, validation performed, exact blocker, changed source context, defect evidence, or source references.

Technical evidence should support the decision-maker layer. It should not replace it.

# Technical Versus Business Reporting

Technical reporting answers:

- what files changed
- what commands ran
- what checks passed or failed
- what implementation path was used
- what error appeared
- what dependency or schema issue exists

Decision-maker reporting answers:

- what problem this relates to
- why the change matters
- whether the result satisfies the intent
- what trade-off or risk exists
- what still needs decision, review, or follow-up

Both are needed for serious work.

If the output contains only commands, file names, stack traces, or implementation facts, it may be technically detailed but not decision-maker reviewable.

If the output contains only business summary with no evidence, it may be readable but not auditable.

# Explaining Intent

Explain intent before reporting details when the reader needs context.

Good intent reporting identifies:

- the task, ticket, source item, batch, or review question
- what the work was trying to achieve
- why the work mattered
- relevant scope or non-goals
- important assumptions

Do not invent intent. If the intent was unclear, say so and identify the missing context.

# Explaining Outcomes

Explain outcomes as actual state, not aspiration.

Outcome reporting should distinguish:

- completed work
- partial work
- failed work
- blocked work
- not verified work
- deferred work
- recommendations that were not implemented

Do not use polished wording to make partial, blocked, failed, or unverified work sound complete.

# Explaining Impact

Explain impact when it affects review, acceptance, prioritisation, stakeholder meaning, product scope, delivery sequencing, validation, or future work.

Impact may include:

- user-facing impact
- product-scope impact
- requirement or acceptance impact
- validation impact
- delivery or sequencing impact
- architecture or dependency impact
- documentation impact
- cost, security, deployment, or operational risk

Do not exaggerate impact. If impact is unknown, say it is unknown and explain what would be needed to know.

# Explaining Deviations

When work differs from the original plan, explain the drift.

Use the preserved ResolvePM concepts:

- original plan
- what actually happened
- why it changed
- impact
- follow-up needed

If the drift affects acceptance criteria, do not mark the work complete unless the criteria are still satisfied.

If the drift changes product meaning, requirement meaning, sequencing, architecture, validation, or strategy, escalate to the accountable role.

Source references:

- `AGENTS.md.backup` > implementation drift format
- `05-workflows/implementation-review-loop.md` > implementation drift handling
- `02-roles/implementation-engineer.md` > implementation drift reporting

# Explaining Risk And Uncertainty

Risk and uncertainty must be visible.

Explain:

- what is known
- what is missing
- what is inferred
- what is not verified
- what is blocked
- what could fail later
- what decision or context would reduce the uncertainty

Do not hide uncertainty behind confidence.

Do not bury blockers, failed checks, missing context, known issues, or risk inside vague summaries.

Source references:

- `00-system/ai-operating-principles.md` > explicit uncertainty
- `01-context/missing-context-behaviour.md` > explicit uncertainty and blocker handling
- `05-workflows/implementation-review-loop.md` > failed validation and missing context handling

# Explaining Recommendations

Recommendations should be separate from completed work.

When recommending next steps, explain:

- what is recommended
- why it is separate from completed scope
- whether it is required, optional, blocked, or deferred
- what role or decision-maker should review it
- what source evidence supports it

Do not imply recommended follow-up work was implemented.

Do not convert recommendations into current scope without admin approval or an established workflow.

Source references:

- `03-skills/completion-reporting.md` > reporting follow-up work
- `05-workflows/feedback-to-ticket.md` > review outcomes and scope control
- `06-governance/codex-working-rules.md` > work one ticket or batch at a time

# Anti-Patterns

Do not:

- report only technical details when a decision-maker needs context
- provide an executive-style summary that hides evidence, blockers, failed checks, or uncertainty
- claim success when status is unknown
- bury known issues in vague language
- present partial, blocked, failed, or unverified work as complete
- omit why the work matters when impact is needed for review
- omit whether the outcome differed from the original intent when drift occurred
- omit next-step guidance when a decision, blocker, risk, or follow-up remains
- mix recommendations into completed work
- make follow-up work look implemented
- turn this governance into a completion report template
- create role, skill, workflow, or template behaviour inside this governance file

# Examples

Decision-maker layer with technical evidence:

```text
Intent:
The work was meant to make the current ticket ready for implementation.

Outcome:
The scope is clearer, but acceptance criteria are still missing.

Why it matters:
Implementation would require guessing what success looks like.

Decision needed:
Admin should confirm the missing acceptance criteria before implementation starts.

Evidence:
The loaded ticket context includes goal and scope, but no acceptance criteria section.
```

Blocked reporting:

```text
Problem:
The requested implementation depends on source context that is not available.

Current state:
No safe implementation change was made.

Risk:
Continuing would require invented requirements or fake completion.

Next step:
Provide the missing source item or approve a clearly limited draft.
```

Drift reporting:

```text
Original intent:
The ticket expected one implementation path.

What changed:
Repository reality required a smaller safe path.

Impact:
Acceptance criteria still need review before completion can be claimed.

Follow-up:
Create or review a follow-up ticket if the original path remains required.
```

These are examples of reporting philosophy. They are not canonical templates.

# Related Roles

- `02-roles/product-manager.md`
- `02-roles/business-analyst.md`
- `02-roles/qa-tester.md`
- `02-roles/technical-strategy-lead.md`
- `02-roles/implementation-engineer.md`
- `02-roles/strategic-product-director.md`

# Related Skills

- `03-skills/completion-reporting.md`
- `03-skills/ticket-writing.md`
- `03-skills/acceptance-criteria.md`
- `03-skills/user-feedback-processing.md`

Future related skills may include:

- implementation review
- risk assessment
- decision-log writing
- debugging support

# Related Workflows

- `05-workflows/ticket-to-implementation.md`
- `05-workflows/implementation-review-loop.md`
- `05-workflows/feedback-to-ticket.md`

# Related Governance

- `00-system/ai-operating-principles.md`
- `01-context/missing-context-behaviour.md`
- `06-governance/codex-working-rules.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred because they belong in future templates, roles, skills, or workflows:

- exact completion report template
- exact blocker report template
- exact ticket-context prompt template
- exact source-tracker comment format
- role-specific reporting obligations beyond references to existing roles
- implementation-review skill details beyond governance principles
- risk-assessment skill details
- decision-log-writing skill details
- project-specific report formats, source-system fields, commands, ticket keys, routes, or deployment details

# Candidate Files Requiring Future ADR-036 Alignment

Future work should review these files for ADR-036 alignment when they are created or updated:

- `04-templates/completion-report-template.md`
- `04-templates/blocker-report-template.md`
- `04-templates/ticket-context-template.md`
- `04-templates/briefing-template.md`
- `04-templates/decision-log-template.md`
- `03-skills/implementation-review.md`
- `03-skills/risk-assessment.md`
- `03-skills/debugging-support.md`
- `03-skills/decision-log-writing.md`
- `06-governance/update-process.md`
- `06-governance/duplication-control.md`

# Ambiguous Items For Admin Review

Admin review is needed for:

- Whether all future templates must include a decision-maker context layer by default or only when the task is review-facing.
- Whether completion reports should always include `why it matters` or only when useful for decision-making.
- Whether decision-maker reporting should become part of `completion-reporting.md` later, or remain governance inherited by templates and workflows.
- Whether stakeholder-facing reporting needs stricter language than admin-facing reporting.
- Whether ADR-035 should be reserved, restored, or left absent.

# What This Governance Must Not Do

This governance must not:

- create templates
- create skills
- create workflows
- create roles
- replace `03-skills/completion-reporting.md`
- replace `05-workflows/implementation-review-loop.md`
- define project-specific report formats
- make technical detail optional where verification requires it
- weaken implementation honesty or explicit uncertainty

---

# Source: 06-governance/duplication-control.md

---
type: governance
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolveos-architecture-review.md
  - migration/template-layer-review.md
  - migration/resolvepm-residual-audit.md
  - migration-review.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
related_context:
  - 01-context/running-context.md
  - 01-context/role-loading-rules.md
  - 01-context/project-loading-rules.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/update-process.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define how ResolveOS prevents duplicated instructions from drifting across roles, skills, workflows, templates, context, and governance files.

Duplication control exists to preserve source-of-truth ownership without over-flattening high-value guidance.

This file is governance. It is not a cleanup plan, template, skill, workflow, role, or project-specific refactor instruction.

Source references:

- `migration/resolveos-architecture-review.md` > `Duplication Risks`
- `migration/resolveos-architecture-review.md` > `Recommended Next Batch`
- `migration/resolvepm-residual-audit.md` > `Residual Global Content`
- `migration-review.md` > `Duplicate Behaviour Inventory`
- `06-governance/source-of-truth-rules.md` > `Duplication Rules`
- `06-governance/update-process.md` > `Change Propagation Rules`

# Canonical Ownership

Every important rule should have one canonical owner.

Canonical ownership means:

- one layer owns the rule
- other files may reference or locally repeat the rule when useful
- local repetition must not change the meaning
- cleanup must preserve wording where wording matters
- conflicts must be resolved by checking the owning source first

Canonical ownership should follow ResolveOS layer responsibility:

- global assistant behaviour: `00-system/ai-operating-principles.md`
- context loading and missing context: `01-context/`
- role responsibilities and authority: `02-roles/`
- task methods: `03-skills/`
- communication structures: `04-templates/`
- process sequence: `05-workflows/`
- system rules and ownership: `06-governance/`
- project-specific facts and decisions: project repositories

# Valid Local Repetition

High-value rules may be repeated locally when repetition protects behaviour, safety, reviewability, or role clarity.

Valid local repetition includes:

- no fake functionality reminders in implementation-facing files
- completion honesty reminders in reporting, QA, implementation, and workflow files
- blocker handling reminders in missing-context, workflow, role, and template files
- one-ticket or approved-batch discipline in ticket, workflow, Codex, and role files
- project-specific boundary warnings in project-loading, templates, and migration files
- role authority reminders where ticket creation could be mistaken for approval authority

Local repetition should be concise and traceable to the canonical owner where practical.

# Invalid Duplication

Duplication is invalid when it:

- creates competing sources of truth
- weakens stronger source wording
- silently changes the meaning of a rule
- spreads project-specific doctrine into global ResolveOS files
- duplicates long sections that should be referenced instead
- repeats role responsibilities inside templates or workflows as if they own the role
- repeats workflow sequence inside roles as if the role owns the process
- repeats project commands as global validation requirements
- causes prompts to become overloaded context dumps

# High-Value Rules

The following high-value rules may remain locally repeated while canonical ownership stays clear:

- do not make things up
- prefer evidence over invention
- no fake functionality
- no invented implementation claims
- do not claim work was done unless it was actually done
- do not hide blockers or uncertainty
- one ticket, task, or approved batch at a time
- project doctrine stays project-owned
- preserve admin intent
- preserve wording where wording matters
- do not flatten specialist roles

Do not weaken these rules by replacing specific guidance with generic best-practice language.

# Consolidating Duplicate Behaviour

Before consolidating duplicates:

1. Identify every file where the rule appears.
2. Identify the canonical owner.
3. Preserve the strongest wording.
4. Identify which local repetitions are valid and should remain.
5. Replace unnecessary duplicates with references only when a cleanup batch approves it.
6. Report any ambiguity or conflict before changing ownership.

Do not consolidate merely to reduce file count.

Do not remove repeated safety rules just because they appear in multiple places.

# Referencing Canonical Files

When replacing duplication with a reference:

- name the canonical file
- state the specific section when useful
- keep only the local reminder needed for safe use
- do not force the reader to chase references for critical stop rules

Examples:

```text
Follow `06-governance/source-of-truth-rules.md` for ownership.
```

```text
No fake functionality. See `00-system/ai-operating-principles.md`.
```

# Avoiding Over-Flattening

Do not over-flatten.

Some repeated guidance has different meaning in different layers:

- Product Manager scope discipline is not the same as Implementation Engineer scope discipline.
- QA validation evidence is not the same as completion-reporting evidence.
- Technical Strategy Lead dependency governance is not the same as ticket-writing dependency notes.
- Template blocker sections are not the same as missing-context behaviour.

Preserve role nuance, workflow meaning, and template purpose.

# When Not To Deduplicate

Do not deduplicate when:

- wording itself protects behaviour
- the rule is safety-critical
- role boundaries would become less clear
- the duplicate is a short local stop rule
- the file needs the reminder to be usable without hidden assumptions
- cleanup would require broad edits outside the approved batch
- source ownership is unclear
- project/global classification is unresolved

# Change Propagation

When canonical wording changes:

- update the canonical owner first
- identify files with local repetitions
- update local repetitions only when the change materially affects their meaning
- leave valid local reminders alone if they still match the canonical rule
- report deferred cleanup where batch scope does not allow alignment

Use `06-governance/update-process.md` for update ownership and review expectations.

# Anti-Patterns

Do not:

- remove repeated high-value rules before review
- flatten specialist roles into generic roles
- replace concrete admin instructions with vague best practices
- hide conflicts by choosing the shorter rule
- duplicate project doctrine into ResolveOS
- copy whole canonical files into prompts or templates
- let templates redefine behaviour to avoid references
- treat examples as canonical ownership
- deduplicate across layers without understanding why the rule appears there

# Notes

Deferred because they belong elsewhere:

- exact ResolvePM cleanup plan belongs in a future cleanup planning batch
- source-tracker posting rules belong in a future handoff template, workflow, or project-owned process
- dependency-management method belongs in a future skill or governance decision
- project-specific override locations belong in project repositories

Admin review is needed for:

- whether a future duplication inventory should be maintained as a separate report
- whether some high-value repeated rules should be marked as mandatory local reminders
- whether migration prompt artifacts should remain in `05-workflows/` or move later

What this governance must not do:

- create a refactor plan by itself
- remove existing duplication
- redefine source-of-truth rules
- redefine update-process rules
- promote ResolvePM project doctrine into ResolveOS

---

# Source: 06-governance/project-readiness.md

---
type: governance
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolveYGO adoption validation
source_files:
  - migration/architecture-review-3.md
  - migration/resolvepm-residual-audit.md
  - migration/template-layer-review.md
related_context:
  - 01-context/running-context.md
  - 01-context/project-loading-rules.md
  - 01-context/context-loading-rules.md
  - 01-context/missing-context-behaviour.md
related_workflows:
  - 05-workflows/project-initiation.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/update-process.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define readiness assessment across project lifecycles.

Project readiness is not a single state. A project may be ready for adoption, discovery, planning, implementation, or validation at different times.

Being ready for one stage does not imply readiness for another.

This governance exists because the ResolveYGO adoption validation showed that a project can be suitable for ResolveOS adoption while still needing separate checks for canonical source, current state, tracker/repository consistency, implementation readiness, and validation evidence.

Readiness language should help the user move forward. Do not surface a readiness gap without also identifying whether it blocks current progress, the smallest mitigation, and the next action.

Source references:

- `migration/architecture-review-3.md` > Project Initiation Assessment
- `05-workflows/project-initiation.md` > Project Setup Report and continuation state
- `01-context/project-loading-rules.md` > project source ownership
- `06-governance/source-of-truth-rules.md` > source ownership and conflict rules

# Rules

Assess readiness independently for each stage:

- adoption readiness
- discovery readiness
- planning readiness
- implementation readiness
- validation readiness

Do not treat readiness as transitive.

Do not say a project is implementation ready because it is adoption ready.

Do not say a project is validation ready because implementation exists.

Do not hide uncertainty about readiness. If evidence is missing, mark the readiness state as blocked, partial, or unknown.

Do not describe a project as not ready without explaining the practical resolution path.

Readiness assessment should identify:

- purpose
- required evidence
- common blockers
- minimum conditions
- anti-patterns
- whether a gap blocks progress now
- what can still continue safely, if anything
- the smallest mitigation or source needed
- which user-facing role, team member, specialist chat, AI assistant, engineer, consultant, or source owner should handle it
- whether a prompt, handoff, checklist, or follow-up task should be generated

Keep readiness output proportionate. Initial setup should not list every readiness category unless it helps the user understand the project state or next action.

# Validation State Model

Use a lightweight validation state model when assumptions, evidence, confidence, or validation status affect readiness.

Core concepts:

- Assumption: a claim, dependency, expectation, user need, business rule, technical belief, or delivery condition that is not yet fully proven.
- Evidence: a source-backed observation, test result, research finding, customer signal, repository state, completion report, validation report, or authoritative source-system record that supports or weakens an assumption.
- Confidence: the current strength of belief based on available evidence, stated as high, medium, low, or unknown.
- Validation status: proven, partially validated, unvalidated, or disproven.

Validation statuses mean:

| Status | Meaning |
| --- | --- |
| Proven | Strong evidence supports the claim for the current project context. |
| Partially validated | Some evidence supports the claim, but scope, sample size, environment, or acceptance coverage is incomplete. |
| Unvalidated | The claim may be plausible, but source-backed evidence is missing or too weak to rely on. |
| Disproven | Evidence contradicts the claim or shows the expected result is false in the current context. |

Use this model to improve readiness assessment, commercial validation, product validation, implementation validation, and project continuation.

Do not turn validation state into a research-management system. Keep exact research plans, customer interviews, analytics, test commands, tracker fields, and acceptance records project-owned.

# Adoption Readiness

## Purpose

Determine whether ResolveOS can be safely applied to a project without overwriting existing project state or inventing missing project facts.

## Required Evidence

- project identity
- project repository, workspace, or primary working location
- known source systems
- project owner or admin instruction
- existing project context, if any
- existing operating model, if any
- clear statement of whether this is new project initiation, existing project adoption, or continuation

## Common Blockers

- no accessible project source
- unclear project identity
- multiple candidate repositories or implementations with no canonical source
- no admin approval to assess or adopt
- project-specific doctrine being mistaken for ResolveOS doctrine

## Minimum Conditions

- The project can be identified.
- The available sources can be named.
- Existing state will be preserved.
- ResolveOS can make recommendations without creating files or changing systems automatically.

## Anti-Patterns

- Assume every project needs every ResolveOS role, chat, workflow, or template.
- Start by creating bootstrap files.
- Overwrite existing project structure.
- Import product doctrine into ResolveOS.
- Treat adoption readiness as implementation readiness.

# Discovery Readiness

## Purpose

Determine whether enough context exists to investigate, classify, and understand the project safely.

## Required Evidence

- canonical project source or list of candidate sources
- documentation sources
- tracker or task source, if one exists
- repository or implementation source, if one exists
- known gaps, contradictions, and unavailable sources
- project-specific context-loading constraints

## Common Blockers

- unclear canonical source
- inaccessible repository, tracker, database, or documentation
- contradictory project records
- stale metadata
- missing owner for project decisions

## Minimum Conditions

- The investigation can identify what is known, unknown, missing, stale, or contradictory.
- The assistant can distinguish source facts from assumptions.
- Discovery can proceed without changing project state.

## Anti-Patterns

- Treat stale documentation as current implementation state.
- Treat tracker status as repository truth without checking.
- Treat repository state as product approval.
- Smooth over contradictions instead of surfacing them.

# Planning Readiness

## Purpose

Determine whether the project has enough source-backed context to recommend roles, chats, context, source-of-truth structure, gaps, highest-leverage activity, and top recommended actions.

## Required Evidence

- project objective
- canonical source assessment
- known source systems
- current or proposed operating model
- known constraints
- active work or intended next work
- known risks and blockers
- relevant decisions or decision gaps
- validation state for assumptions that materially affect the next recommendation

## Common Blockers

- objective is unclear
- source ownership is unresolved
- active work is unknown
- plan conflicts with repository reality
- role or chat recommendations would be speculative

## Minimum Conditions

- The highest-leverage activity can be stated with evidence.
- Missing context is identified rather than guessed.
- Project-specific facts remain project-owned.
- Recommendations can be reviewed by the admin or source owner.

## Anti-Patterns

- Create a full operating model without source evidence.
- Recommend every role or chat by default.
- Treat planning as approval to implement.
- Hide project-specific assumptions inside global ResolveOS guidance.

# Implementation Readiness

## Purpose

Determine whether scoped implementation work can begin safely.

## Required Evidence

- approved ticket, task, batch, or scope
- current objective
- acceptance criteria or explicit acceptance gap
- dependency and blocker state
- canonical repository and implementation location
- relevant project context
- latest completion, blocker, or decision evidence where continuation is involved
- applicable validation expectations

## Common Blockers

- missing approved scope
- missing or guessed acceptance criteria
- unresolved canonical source
- tracker and repository state disagree
- required dependency is incomplete
- latest completion evidence is missing
- active blocker is unresolved

## Minimum Conditions

- Current scope is clear.
- Required context is available or the limitation is explicit.
- Dependencies and blockers have been checked.
- Continuing work is supported by evidence rather than memory.

## Anti-Patterns

- Start implementation from chat memory.
- Treat planning readiness as implementation readiness.
- Implement future-ticket work.
- Work around blockers silently.
- Claim implementation can begin when canonical source or active scope is unresolved.

# Validation Readiness

## Purpose

Determine whether delivered work can be checked, reviewed, or accepted with enough evidence.

## Required Evidence

- implementation scope
- acceptance criteria
- validation method
- project-specific commands or manual steps where available
- repository state or delivered artifact
- completion report, if work was already performed
- known failed, skipped, blocked, or not-run checks
- assumptions being validated
- evidence and confidence for the validation result

## Common Blockers

- no acceptance criteria
- no validation path
- implementation location is unclear
- tracker says complete but repository evidence is missing
- failed checks are unresolved
- validation environment is unavailable

## Minimum Conditions

- There is something specific to validate.
- The expected result is observable.
- Validation evidence can be captured or missing validation can be reported honestly.
- Failed or unavailable checks are not hidden.

## Anti-Patterns

- Treat implementation existence as validation success.
- Treat tracker completion as validation evidence.
- Claim checks passed when they did not run.
- Hide failed validation inside a positive completion summary.

# Enforcement

Project initiation, continuation, implementation planning, and validation work should state the relevant readiness state when readiness affects the highest-leverage activity.

If readiness is partial, blocked, or unknown, report the blocker or uncertainty clearly.

Also report the practical resolution path. If the issue does not block the current objective, say so and continue with an explicit limitation.

Where readiness depends on project-specific systems, keep exact commands, tools, fields, ticket keys, repositories, databases, and implementation details in the project repository or source system.

# Exceptions

Small low-risk conversations may not need a full readiness assessment.

Do not over-format casual questions into readiness reports.

When work is significant, durable, implementation-facing, validation-facing, or project-adoption-facing, readiness should be assessed explicitly.

# Examples

Adoption ready but not implementation ready:

```text
The project has an accessible repository and source documentation, so ResolveOS can assess adoption.
Implementation should not start yet because the active ticket, acceptance criteria, and latest completion evidence are missing.
Smallest mitigation: provide the active ticket or latest handoff, or approve a clearly labelled implementation-readiness draft.
```

Planning ready but not validation ready:

```text
The next work can be planned from the source context and tracker.
Validation is not ready because the project-specific check commands and expected manual result are not documented.
Smallest mitigation: document the validation path before claiming acceptance or release readiness.
```

# Notes

Deferred because they belong elsewhere:

- Project-specific readiness checklists belong in project repositories.
- Exact tracker fields, repository names, database names, commands, and environment details belong in project context.
- Source-system posting rules belong in future source-system handoff guidance or project-owned process.

Ambiguous for admin review:

- Whether project readiness should later have a template.
- Whether adoption validation should become a repeatable workflow after more project trials.
- Whether customer-facing readiness language should differ from internal agent-facing readiness language.

---

# Source: 06-governance/source-of-truth-rules.md

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

---

# Source: 06-governance/update-process.md

---
type: governance
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolveos-architecture-review.md
  - migration/template-layer-review.md
  - migration/resolvepm-residual-audit.md
  - migration-review.md
  - migration/resolvepm-extraction-map.md
  - migration/resolvepm-extraction-audit.md
  - AGENTS.md.backup
  - docs/project-context/implementation-workflow.md
  - docs/ai-roles/technical-strategy-lead.md
  - docs/ai-roles/implementation-engineer.md
related_context:
  - 01-context/running-context.md
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/project-loading-rules.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/decision-maker-reporting.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define how ResolveOS artifacts are maintained, updated, reviewed, and kept aligned over time.

This governance preserves the update discipline extracted from ResolvePM: do not let important context drift, update the correct file, explain why the update is needed, keep ownership explicit, and avoid spreading duplicate behaviour across layers.

ResolveOS uses a defined update process to maintain architectural integrity.

This file is governance. It is not a template, skill, workflow, role, context file, ADR, or project-specific update checklist.

Source references:

- `migration/resolveos-architecture-review.md` > `Recommended Next Batch`
- `migration/resolveos-architecture-review.md` > `Architectural Weaknesses`
- `06-governance/source-of-truth-rules.md` > `Core Principle`
- `01-context/running-context.md` > `Usage Guidance`
- `docs/project-context/implementation-workflow.md` > documentation update check
- `docs/ai-roles/technical-strategy-lead.md` > documentation update timing labels
- `docs/ai-roles/implementation-engineer.md` > persistent context update flagging
- `AGENTS.md.backup` > `Update documentation`

# Update Principles

## Update The Source Of Ownership

Updates should occur at the source of ownership rather than through duplication.

Every important rule should have one canonical home. Copies, summaries, references, and derived versions may exist, but ownership must remain explicit.

If the needed change affects global behaviour, update the owning ResolveOS layer.

If the needed change affects project facts, project decisions, tickets, roadmap, commands, terminology, or implementation constraints, update the project-owned artifact.

## Apply Changes To The Correct Layer

Changes should be applied to the correct layer.

Running context, ADRs, governance, roles, skills, workflows, templates, and project-specific artifacts each have distinct update responsibilities.

Do not move behaviour between layers just because the nearby file is convenient.

## Preserve Architectural Boundaries

Updates must preserve the current ResolveOS architecture:

- roles own responsibilities and authority
- skills own reusable task methods
- workflows own process sequence
- templates own communication structure
- context files own loading, precedence, current-state, and missing-context handling
- governance owns system rules
- ADRs own durable architecture decisions
- project repositories own project-specific facts and doctrine

## Do Not Let Important Context Drift

When planning, ticketing, roadmap, architecture, implementation, review, migration, or governance work reveals persistent context that has changed, flag the update need.

If an update is needed, explicitly identify:

- which file or source should be updated
- why it should be updated
- whether the update is immediate, next task, when convenient, or optional
- who owns the update

Use concrete timing labels. Do not describe urgency only as vague levels like low, medium, or high.

## Preserve Reviewability

Updates should be reviewable.

Prefer small, focused changes. Do not create broad rewrites or mixed-purpose updates unless the batch explicitly approves them.

When update impact is uncertain, report the uncertainty rather than changing multiple layers defensively.

# Layer Ownership

| Layer | Owns | Must Not Own |
| --- | --- | --- |
| `00-system/` | file standards, metadata standards, operating principles, migration strategy | project doctrine, role behaviour, workflow sequence |
| `01-context/` | loading order, startup assumptions, running state, missing context, role/project loading | role responsibility, skill method, project facts |
| `02-roles/` | reusable role purpose, responsibilities, authority, escalation, anti-patterns | skill procedures, workflow sequence, templates, project doctrine |
| `03-skills/` | reusable task methods | role authority, workflow sequence, report templates, project commands |
| `04-templates/` | communication and prompt structures | behaviour definitions, approval authority, workflow sequence |
| `05-workflows/` | multi-step process sequence | role authority, skill method detail, project-specific commands |
| `06-governance/` | system rules, source ownership, update rules, decision reporting, architecture decisions | project facts, ticket status, implementation reports |
| project repositories | product vision, roadmap, active tickets, project decisions, commands, architecture, local constraints | global ResolveOS behaviour unless reviewed and promoted |

# When To Update Running Context

Update running context when current working state materially changes.

Use running context for:

- current phase
- current state
- recently completed work
- active work
- open decisions
- active risks
- current recommendations
- do-not-repeat lessons
- source-of-truth references for current work

Running context is current-state context only.

Do not use running context for:

- historical changelogs
- durable architecture decisions
- detailed migration history
- project-specific current focus
- source-system status
- implementation reports

Replace stale current-state items instead of appending a long history.

# When To Update ADRs

Update ADRs when a durable architecture decision affects:

- reusable ResolveOS behaviour
- migration boundaries
- source ownership
- role/skill/workflow/template separation
- context-loading architecture
- governance architecture
- future file creation
- global/project ownership rules

ADRs preserve decisions, rationale, impact, and source references.

Do not use ADRs for:

- temporary current state
- routine implementation status
- ticket history
- changelogs
- project-specific decisions unless they affect ResolveOS globally

If a decision is durable but not architecture-level, use a decision log or project-owned decision record instead.

# When To Update Governance

Update governance when the change defines or changes a system rule.

Governance should own:

- source-of-truth rules
- update process
- duplication control
- Codex execution constraints
- decision-maker reporting
- extraction and migration guardrails
- architecture decisions
- review and enforcement rules

Governance should not absorb role behaviour, skill methods, workflow steps, or template structure.

If governance reveals missing role, skill, workflow, or template behaviour, defer that behaviour to the correct layer.

# When To Update Roles

Update role files when reusable role behaviour changes.

Role updates may be needed when:

- responsibilities change
- decision authority changes
- escalation boundaries change
- role anti-patterns change
- source evidence clarifies role behaviour
- a role boundary conflict needs preservation

Do not update a role file to add a full skill method, workflow sequence, template structure, project-specific doctrine, project commands, or ticket status.

Specialist roles must not be flattened during updates.

# When To Update Skills

Update skill files when a reusable task method changes.

Skill updates may be needed when:

- the process for a task changes
- inputs or outputs change
- anti-patterns for the method change
- examples need to preserve clearer source guidance
- repeated method guidance needs a canonical home

Do not update skills to grant role authority, define workflow sequence, create templates, or store project-specific commands.

# When To Update Workflows

Update workflows when a multi-step operating process changes.

Workflow updates may be needed when:

- trigger conditions change
- required inputs change
- process steps change
- handoff points change
- review points change
- failure modes change

Do not update workflows to redefine role authority, skill methods, template structures, or project-owned commands.

Project-specific workflows remain project-owned unless reviewed and promoted as reusable ResolveOS workflows.

# When To Update Templates

Update templates when a reusable communication, prompt, briefing, report, or log structure changes.

Template updates may be needed when:

- a report needs a new review surface
- a prompt needs a new reference field
- a handoff needs a clearer structure
- decision-maker reviewability requires a missing section
- source traceability needs to be made visible

Templates implement behaviour. They do not define it.

If a template reveals missing behaviour, update or create the correct role, skill, workflow, context, or governance file in a separate approved batch.

# When To Update Project Artifacts

Update project artifacts when the change is project-specific.

Project repositories own:

- product vision
- product strategy
- roadmap
- project decisions
- active tickets
- current focus
- project architecture decisions
- source-system status
- domain terminology
- project-specific workflows
- project-specific commands
- environment configuration
- provider configuration
- deployment targets
- release notes and changelogs

Do not migrate project-specific facts into ResolveOS just because a project file needs an update.

When project context changes, update the project-owned source rather than creating a ResolveOS global rule.

# Change Propagation Rules

When a change affects multiple files:

1. Identify the canonical source of ownership.
2. Update the canonical source first.
3. Identify derived references, examples, templates, prompts, or project consumers that may need alignment.
4. Update derived files only when the batch scope allows it.
5. If alignment is needed but out of scope, report it as deferred work.
6. Do not silently make broad updates across layers.

When a rule appears in multiple files:

- preserve the strongest wording in the canonical source
- keep necessary local reminders only where they protect reviewability or safety
- replace unnecessary duplication with references when a cleanup batch approves it
- do not remove wording-sensitive rules until duplication-control governance exists and the cleanup is reviewed

When source material conflicts:

- apply the migration priority for the current batch
- prefer existing ResolveOS governance and context over older source material
- flag contradictions rather than silently choosing the easier source
- defer uncertain ownership for admin review

# Review Expectations

Review is required before:

- changing global standards
- changing source-of-truth rules
- changing context-loading behaviour
- changing role authority or role boundaries
- changing skill method semantics
- changing workflow sequence
- changing template ownership boundaries
- changing ADR decisions
- promoting project-specific doctrine into ResolveOS
- removing duplicated high-value rules
- refactoring project repositories to depend on ResolveOS

Completion reports for update work should identify:

- files created or updated
- source sections used
- ownership decisions made
- deferred update needs
- ambiguity requiring admin review
- contradictions found
- validation performed or not performed

# Anti-Patterns

Do not:

- update the nearest file instead of the owning file
- duplicate behaviour instead of updating the source of ownership
- move role behaviour into templates
- move skill methods into governance
- move workflow sequence into roles
- move project doctrine into ResolveOS
- use running context as a changelog
- use ADRs for routine implementation status
- use templates to create approval authority
- silently update multiple layers without review
- remove repeated high-value rules before duplication-control governance exists
- let documentation drift from reality
- infer project-specific updates from memory
- treat migration reports as current state
- refactor ResolvePM before ResolveOS ownership and cleanup rules are reviewed

# Notes

This file intentionally defines update ownership and propagation only.

Deferred because they belong elsewhere:

- detailed duplication cleanup rules belong in future `06-governance/duplication-control.md`
- dependency progression belongs in a future dependency-management skill or governance decision
- source-tracker posting rules belong in a future source-tracker handoff template, workflow, or project-owned process
- project-specific update locations belong in project repositories
- exact release-note or changelog formats remain project-specific until proven reusable

Admin review is needed for:

- whether every project should define a standard local update-process override
- whether running context should be added to global startup loading rules in a dedicated context batch
- whether update timing labels should be exactly `Immediate`, `Next Task`, `When Convenient`, and `Optional`
- whether historical Codex prompt artifacts should remain under `05-workflows/` or move to a migration/prompt location later

What this governance must not do:

- create templates
- create skills
- create workflows
- create roles
- replace source-of-truth rules
- replace architecture decisions
- replace running context
- define project-specific update procedures
- promote ResolvePM project doctrine into ResolveOS

