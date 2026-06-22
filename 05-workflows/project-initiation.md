---
type: workflow
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
  - 03-skills/dependency-management.md
  - 03-skills/requirement-traceability.md
  - 03-skills/implementation-review.md
  - 03-skills/information-architecture.md
related_templates:
  - 04-templates/briefing-template.md
  - 04-templates/chat-handoff-template.md
  - 04-templates/decision-log-template.md
  - 04-templates/role-prompt-template.md
  - 04-templates/ticket-context-template.md
related_context:
  - 01-context/running-context.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/project-loading-rules.md
  - 01-context/context-loading-rules.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/update-process.md
  - 06-governance/duplication-control.md
  - 06-governance/project-readiness.md
  - 06-governance/decision-maker-reporting.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define the canonical ResolveOS workflow for starting a new project, adopting an existing project, or continuing work on an existing project.

Project initiation is the governing ResolveOS workflow for new project initiation, existing project adoption, and existing project continuation.

`00-system/resolveos-entrypoint.md` is the canonical ResolveOS AI entrypoint.

Users should start from `README.md`. ResolveOS AI interactions should start from `00-system/resolveos-entrypoint.md`, which routes new project initiation, existing project adoption, and existing project continuation to this workflow when appropriate.

Project initiation determines the appropriate operating model, roles, chats, context, source-of-truth structure, setup requirements, known gaps, highest-leverage activity, and top recommended actions.

Project initiation should make ResolveOS value visible without exposing unnecessary internal framework complexity. It should show the project situation, what matters now, what is blocked, what team or specialist support is needed, and how to move forward.

Project initiation may be:

- new project initiation
- existing project adoption
- continue existing project

This workflow produces a Project Setup Report. It does not automatically create external systems, overwrite existing project state, create roles, create skills, create templates, create project files, or refactor existing repositories.

Source references:

- `01-context/project-loading-rules.md` > project repositories own project context
- `01-context/role-loading-rules.md` > role selection and role boundaries
- `01-context/running-context.md` > current-state and handoff discipline
- `06-governance/source-of-truth-rules.md` > ownership hierarchy
- `03-skills/information-architecture.md` > information classification and storage model selection before writing to documentation and workspace tools
- `06-governance/update-process.md` > layer ownership and project artifact updates
- `06-governance/duplication-control.md` > avoid duplicate instruction stacks
- `migration/resolveos-architecture-review.md` > overall architecture and missing capabilities

# Trigger

Use this workflow when:

- a new project should start with ResolveOS support
- an existing project should adopt ResolveOS
- an existing project should continue under ResolveOS after a pause, handoff, chat change, stale context, or interrupted work
- a project needs an operating model before tickets, roles, or chats are created
- project source-of-truth systems are unclear
- project roles, chats, context files, or running context need initial assessment
- a project handoff needs structured setup before implementation starts
- multiple repositories, folders, trackers, databases, or implementations may exist and the canonical source must be identified
- tracker state, repository state, documentation, metadata, or implementation reality may disagree

Do not use this workflow to:

- implement project work
- rewrite an existing project
- create external systems automatically
- impose every ResolveOS role or chat on every project
- migrate project-specific doctrine into ResolveOS
- overwrite existing project state without explicit approval

# Inputs

For a new project, useful inputs include:

- project name
- project type
- objectives
- team structure
- preferred tooling
- constraints
- expected users, stakeholders, or review audiences
- expected delivery, research, validation, or operational cadence

For an existing project, useful inputs include:

- existing documentation
- existing tooling
- existing tickets
- existing team
- existing source-of-truth systems
- existing documentation and storage structure
- existing context files
- existing operating model
- existing roles, chats, prompts, workflows, templates, or handoff files
- current repository state where relevant
- current objective, active ticket, active batch, running context, or handoff state when continuing existing work
- current planning source, if one exists
- candidate canonical repository, implementation location, tracker, and documentation source
- known tracker, repository, documentation, metadata, database, or implementation inconsistencies
- known assumptions, validation evidence, confidence, or validation status where these affect readiness

If key inputs are missing, proceed with an explicit limitation only when the assessment can remain useful and read-only.

During setup, adoption, or continuation, ask or infer whether the user is working solo, with a team, with AI or automation support, or with a mix only when that changes the recommended team, handoff, or next action.

If unknown and not blocking, default to a light assumption:

```text
I will assume you are working solo for now unless you tell me otherwise.
```

# New Project Initiation

For a new project, identify what must be established before work begins.

Assess:

- project purpose and objectives
- project type and operating needs
- source systems needed
- project-owned context files needed
- initial running context
- recommended roles
- recommended chats
- recommended workflows and templates
- required tools and integrations
- recommended storage model for documentation, knowledge-base, workspace, repository, or project-management tools
- initial tickets, feedback capture, decision logs, or briefing needs
- constraints, risks, and gaps

Do not assume a new project needs every ResolveOS role, every chat, every workflow, every template, or every external tool.

# Existing Project Adoption

For an existing project, preserve current state first.

Assess:

- what already exists
- what source systems are authoritative
- what project context already governs work
- what roles or informal responsibilities already exist
- what chats, prompts, agents, or workflows are already in use
- what documentation is stale, missing, contradictory, or duplicated
- what ResolveOS can reference without replacing
- what should remain project-specific
- what requires admin approval before changing

Do not overwrite existing project structures.

Do not import project doctrine into ResolveOS.

Do not treat missing project documentation as permission to invent project facts.

# Continue Existing Project

For continuing an existing project, preserve current state before recommending action.

Use this mode when ResolveOS is already being applied to a project and the admin, agent, or chat needs to resume safely.

Assess:

- current objective
- highest-leverage activity
- top recommended actions
- current ticket, task, batch, or approved scope
- last completed item
- current running context or current-focus state
- active work, backlog, blockers, and risks
- latest handoff, completion report, blocker report, or decision log
- latest completion evidence
- latest decision evidence
- latest validation evidence
- source-system state
- repository state where relevant
- active role or role handoff
- active, pending, superseded, or rejected decisions
- open blockers, risks, dependencies, and decisions
- stale or missing context
- highest-leverage activity

When repository access exists, read the relevant project context and source-of-truth files before relying on chat memory.

Do not treat continuation as permission to overwrite existing operating structure.

Do not restart project initiation from scratch when current state can be loaded.

Do not continue implementation from memory when required current context, ticket scope, repository state, or validation evidence is missing.

# Discovery Questions

Ask only the questions needed for the project type and adoption state.

Core questions:

- Is this a new project, existing project adoption, or continue-existing-project situation?
- What is the project trying to achieve?
- What decisions, work, or outcomes does the project need to support?
- Who owns project decisions?
- What source systems already exist?
- What source systems are missing?
- Which source is canonical?
- What tools does the project already use?
- How are documentation and workspace tools structured today?
- What project constraints matter?
- What work is active now?
- What should not be changed?

New project questions:

- What should be true before the first ticket or delivery work starts?
- What initial project context should exist?
- What is the simplest useful operating model?
- Which roles are needed now, and which can wait?

Existing project questions:

- Which files, tickets, docs, chats, or systems are authoritative today?
- What is stale, duplicated, contradictory, or missing?
- Which existing processes should be preserved?
- What should ResolveOS reference rather than replace?
- Are there multiple repositories, folders, trackers, databases, or implementations that need reconciliation?
- Which repository, implementation location, tracker, and documentation source are authoritative?

Continue-existing-project questions:

- What was the last reliable current-state source?
- What is the current objective?
- What was the last completed item?
- What work is active now?
- What is next?
- What remains blocked, risky, unverified, or deferred?
- What is the latest completion evidence?
- What is the latest decision evidence?
- What assumptions remain unvalidated, partially validated, proven, or disproven?
- What role should continue the work?
- What context is stale or missing?
- What should not be repeated?

# Project Planning State

Project planning state answers:

- What are we trying to achieve?
- What are we doing now?
- What comes next?
- What is blocked?
- What risks matter?

Use these canonical planning concepts:

| Concept | Meaning |
| --- | --- |
| Objective | The current plain-English outcome the project is trying to achieve. |
| Highest-Leverage Activity | The single activity expected to create the greatest project progress, risk reduction, validation, learning, or delivery impact. |
| Top 3 Recommended Actions | The next three practical actions, prioritised by evidence and usefulness. |
| Active Work | Work currently approved, in progress, or being continued. |
| Backlog | Known future work that is not active now. |
| Blockers | Issues that prevent safe progress without more information, access, validation, prerequisite work, or a decision. |
| Risks | Uncertain conditions that may affect delivery, validation, cost, scope, architecture, quality, or source-of-truth integrity. |

Source-of-truth behaviour:

- If Jira, Notion, GitHub Issues, Azure DevOps, or another planning system is declared authoritative, use that system for planning state.
- If no planning system exists, support a lightweight project-owned planning model using the project's running context, current-focus file, plan, tracker, or equivalent source.
- Do not create a competing ResolveOS roadmap, backlog, or task-management system.
- Do not copy project-specific planning details into global ResolveOS files.
- When planning sources conflict, surface the conflict and the owner decision needed before recommending implementation.

The lightweight project-owned planning model should be enough to answer the four continuation questions above. It does not need to replicate external project-management tooling.

# Decision State

Use a lightweight decision lifecycle so project continuation can identify which decisions matter now.

Canonical decision states:

| State | Meaning |
| --- | --- |
| Proposed | A decision has been raised or recommended but is not yet accepted as governing work. |
| Active | The decision currently governs behaviour, scope, architecture, source ownership, validation, or project direction. |
| Superseded | The decision was previously active but has been replaced by a later decision. |
| Rejected | The decision was considered and explicitly not adopted. |

For ADRs that already use `Accepted`, treat `Accepted` as equivalent to `Active` unless a later ADR says otherwise.

Continuation should identify:

- active decisions that currently govern work
- proposed decisions that need review before safe progress
- superseded decisions that should not be followed as current guidance
- rejected decisions that should not be reintroduced without new evidence

Do not create extra decision bureaucracy. Use existing ADRs, project-owned decision records, source-system records, or the decision-log template where durable rationale needs to be preserved.

# Evidence And Validation State

Use lightweight validation concepts when readiness, continuation, product direction, commercial validation, or implementation validation depends on assumptions.

Core concepts:

| Concept | Meaning |
| --- | --- |
| Assumption | A claim, dependency, expected user behaviour, business rule, technical belief, or delivery condition that is not fully proven. |
| Evidence | A source-backed observation, test result, research finding, customer signal, repository state, completion report, validation report, or authoritative source-system record. |
| Confidence | The current strength of belief based on evidence: high, medium, low, or unknown. |
| Validation Status | The current validation state: proven, partially validated, unvalidated, or disproven. |

Validation statuses:

- Proven: strong evidence supports the claim for the current project context.
- Partially validated: some evidence supports the claim, but coverage, sample, environment, or scope is incomplete.
- Unvalidated: the claim is plausible but lacks reliable evidence.
- Disproven: evidence contradicts the claim or shows the expected result is false.

Use this model to improve readiness assessment and continuation. Do not turn ResolveOS into a research tracker. Project-specific research plans, analytics, test commands, customer records, and acceptance artifacts remain project-owned.

# Canonical Source Assessment

Determine the canonical project source before recommending implementation, validation, or cleanup work.

Explicitly identify:

- canonical repository
- canonical implementation location
- canonical tracker
- canonical documentation source
- canonical planning source
- canonical decision source
- canonical validation evidence source

Where multiple repositories, folders, databases, trackers, documents, or implementations exist, identify:

- which source appears authoritative
- which sources are stale, duplicate, incomplete, or contradictory
- which source requires admin or project-owner confirmation
- what inconsistencies affect the highest-leverage activity

Do not assume the nearest repository, loudest tracker, newest file, or most complete document is canonical.

Do not silently choose between conflicting sources when the choice affects project state, implementation, validation, or source-of-truth ownership.

# Readiness Assessment

Assess readiness independently.

Use `06-governance/project-readiness.md` for the detailed readiness rules.

Project initiation should report:

- Adoption Readiness
- Discovery Readiness
- Planning Readiness
- Implementation Readiness
- Validation Readiness

Being ready for one stage does not imply readiness for another.

For each readiness state, identify:

- ready / partially ready / blocked / unknown
- evidence
- blockers
- highest-leverage activity

Do not treat project adoption, planning, implementation, or validation readiness as interchangeable.

# Reconciliation Assessment

Check for inconsistencies between:

- tracker vs repository
- plan vs implementation
- metadata vs actual state
- repository vs external implementation
- documentation vs current source
- completion report vs repository reality
- decision record vs active project behaviour
- validation status vs available evidence

Surface differences explicitly.

Do not silently ignore mismatches between trackers, plans, reports, metadata, implementation status, and repository state.

If reconciliation affects source ownership, implementation safety, validation, or project direction, identify the decision owner or admin review needed.

# Continuation Evidence

Continuation requires evidence where possible.

Before implementation begins in continue-existing-project mode, identify:

- current objective
- highest-leverage activity
- top 3 recommended actions
- last completed work
- active work
- backlog, if relevant
- active blockers
- active risks
- latest completion evidence
- latest decision evidence
- latest validation evidence
- active, proposed, superseded, or rejected decisions
- latest running context

If evidence is missing, mark it as missing rather than relying on chat memory.

Do not continue implementation from an assumed state when required continuation evidence is unavailable.

# Operating Model Assessment

Recommend an operating model based on project needs.

Possible operating model elements:

- canonical source ownership
- project context ownership
- source-system ownership
- planning ownership
- decision ownership
- validation evidence ownership
- role usage
- chat/session structure
- ticket or task flow
- feedback flow
- decision logging
- running context or current focus
- readiness assessment
- reconciliation path
- completion and blocker reporting
- validation and review cadence
- update and duplication control

If a recommendation depends on project type, state the dependency.

If uncertain, recommend rather than assume.

# Role Assessment

Use `01-context/role-loading-rules.md` and the role files to recommend only the roles needed.

Use the user-facing label `Recommended Team`, not `AI Coverage`.

Recommended Team output should:

- show only roles or specialist support relevant to the current stage
- briefly explain why each visible role is needed
- say whether it is needed now or later
- explain how to action it
- say clearly when no additional specialist role is needed
- avoid giant all-role yes/no matrices in normal user output
- avoid asking the user to manage internal role files or workflows

Role recommendations are not the same as role loading. Recommend a visible team only when it helps the user understand next action, handoff, ownership, or specialist support.

Use clear user-facing labels when they communicate value better than internal role file names. Map them internally to existing ResolveOS roles, skills, or workflows:

| User-facing label | Internal ResolveOS source |
| --- | --- |
| Product Strategy Lead | Strategic Product Director role |
| Technical Strategy Lead | Technical Strategy Lead role |
| Implementation Engineer | Implementation Engineer role |
| QA / Validation Lead | QA Tester role |
| Business Analyst | Business Analyst role |
| Feedback Curator | User feedback processing skill and feedback-to-ticket workflow |

Do not create a new role when an exact internal role does not exist. Use the closest existing role, skill, or workflow only when its boundary fits, and make the mapping explicit when it matters.

Internal role selection guidance:

- Product Manager for product execution clarity, ticket readiness, scope, and feedback-to-work discipline.
- Business Analyst for requirements, assumptions, ambiguity, traceability, and business rules.
- QA Tester for validation, acceptance evidence, defects, and quality risk.
- Technical Strategy Lead for architecture, sequencing, dependency mapping, implementation governance, and prompt/context governance.
- Implementation Engineer for scoped implementation, debugging, checks, and completion reporting.
- Strategic Product Director for product direction, roadmap coherence, prioritisation, positioning, and whether something should exist.

Do not recommend every role by default.

Do not flatten specialist roles into generic project roles.

If a requested role does not exist, do not invent it. Recommend the closest existing role only when its boundary fits.

When a recommended role should act now, generate the specialist prompt or handoff immediately unless the user has asked not to. Use `04-templates/role-prompt-template.md` for role startup prompts and `04-templates/chat-handoff-template.md` for handoffs when session transfer is needed.

Recommended Team examples:

```text
Recommended Team for now:

- Product Strategy Lead - needed now because the value proposition and target user are still unclear.
  Next step: start a strategy chat using the prompt below.

No Implementation Engineer is needed yet because there is no approved implementation scope.
```

```text
No additional specialist role is needed right now. Continue in this chat with the current project setup.
```

# Chat Assessment

Recommend chats or sessions based on how the project should operate.

Possible chat/session types:

- project setup and governance chat
- strategy or direction chat
- product execution / ticket readiness chat
- requirements clarification chat
- technical planning / sequencing chat
- implementation chat
- QA / validation chat
- feedback triage chat
- handoff or review chat

Use role-specific chats only when they reduce confusion, preserve role boundaries, or make work easier to review.

Do not assume every project needs every chat.

Do not create overloaded multi-role chat stacks when a primary role plus supporting-role reference is enough.

When a chat becomes long, stale, interrupted, or needs migration, use `04-templates/chat-handoff-template.md`.

# Source Of Truth Assessment

Identify current and recommended source-of-truth systems.

Assess:

- product vision and strategy source
- roadmap source
- ticket/task source
- planning state source
- canonical repository
- canonical implementation location
- canonical tracker
- canonical documentation source
- project decisions source
- project architecture source
- domain terminology source
- feedback source
- validation and QA evidence source
- assumptions, confidence, and validation status source
- completion and blocker reporting source
- running context or current-focus source
- external tools and integrations
- documentation and storage architecture for source systems

If multiple candidates exist for any canonical source, record the inconsistency and the required confirmation.

Classify each source as:

- exists and is authoritative
- exists but stale
- exists but incomplete
- exists but contradictory
- missing
- not needed yet
- project-owned
- ResolveOS-owned

Project repositories own project-specific facts, decisions, commands, terminology, and context.

ResolveOS owns reusable operating behaviour.

For documentation and storage tools, also identify the existing hub, parent page, database, folder, repository path, ticket area, or document type that should receive routine project information. Do not recommend a new top-level page, file, folder, or database where an existing canonical structure should be used.

Recommended tool model:

- Notion: product context, strategy, decisions, risks, validation, feedback, and operating knowledge. Use hubs, child pages, and databases for repeatable records; avoid root-level clutter.
- Jira or Linear: execution tracking.
- GitHub: code, technical docs, implementation evidence, and repo-owned context.
- Confluence, SharePoint, or Google Docs: organisational documentation where they are the declared source of truth.

These are defaults. Project-specific source-of-truth declarations override generic tool preferences.

# Context Assessment

Identify what context should exist before work continues.

Recommended context may include:

- project overview or project context
- current focus or running context
- source-of-truth map
- role prompt references
- briefing for scattered or inaccessible context
- ticket context for active work
- decision logs for durable decisions
- chat handoff for session migration
- project-specific setup, commands, environment, or validation context

For new projects, recommend the smallest useful context set.

For existing projects, preserve and reference existing context before proposing new files.

Do not create context files as part of this workflow unless a separate approved task authorises file creation.

# Project Snapshot Guidance

Use a Project Snapshot when it adds orientation value.

A Project Snapshot is a compact user-facing view of the current project state.

Do not show a Project Snapshot on every message.

Project Snapshot must be shown when:

- a new conversation starts
- a stale conversation is resumed
- the user requests project status
- project readiness materially changes
- project objective materially changes
- project source-of-truth changes
- major risks or blockers materially change
- project adoption occurs
- project continuation requires reorientation

Project Snapshot should not be shown for:

- routine discussion
- tactical questions
- normal back-and-forth delivery conversations
- small clarification questions

Do not prepend a Project Snapshot to a full project initiation response.

Project initiation already performs project classification, readiness assessment, team assembly, context establishment, and recommendations. Adding a Project Snapshot before the full initiation output duplicates the same orientation and makes ResolveOS feel process-heavy.

A Project Snapshot should show:

```text
Project Detected:
- New Project / Existing Project / Continue Existing Project

Project Type:
- SaaS / Business Process / GitHub Project / Notion Project / Jira Project / Idea / Other

Current Readiness:
- Adoption / Discovery / Planning / Implementation / Validation

Current Objective:
- One plain-English sentence

Recommended Team:
- Recommended Team for now
- Only roles or specialist support that matter now.
- These may be real people, the user, specialist chats, AI assistants, AI agents, coding agents, engineers, consultants, or a mix.

Open Risks:
- Concise list

Open Decisions:
- Concise list, grouped as active or proposed when useful

Missing Information:
- Concise list

Highest-Leverage Activity:
- Single activity expected to create the greatest project progress, risk reduction, validation, learning, or delivery impact

Top 3 Recommended Actions:
- Prioritised, concrete, outcome-focused, practical, and time-bounded where possible
```

Keep the Project Snapshot user-facing and compact.

Use role names only as the visible recommended team. Do not require the user to choose roles, workflows, modes, or internal files.

If evidence is missing, show the missing information rather than delaying the whole response.

# Gap Analysis

Identify gaps without turning the workflow into implementation.

Gap categories:

- missing source system
- unclear canonical source
- unclear ownership
- tracker/repository mismatch
- plan/implementation mismatch
- metadata/actual-state mismatch
- repository/external-implementation mismatch
- missing readiness evidence
- missing continuation evidence
- missing project context
- stale context
- contradictory context
- missing role coverage
- over-broad or missing chat structure
- missing ticket/task flow
- missing feedback flow
- missing decision logging
- missing validation or QA evidence path
- missing update process
- duplicate or drifting guidance
- missing tools or integrations
- project-specific constraints not yet captured

For each gap, state:

- what is missing
- why it matters
- who should own it
- whether it blocks work
- the highest-leverage follow-up action

# Steps

## 1. Identify Project Mode

Classify the project as:

- new project initiation
- existing project adoption
- continue existing project
- unclear

If unclear, ask for the minimum clarification needed.

## 2. Orient The User When Orientation Adds Value

Use the Project Snapshot guidance when a snapshot trigger applies.

Do not automatically prepend a Project Snapshot to every first response or to a full Project Setup Report.

The user should not need to ask for project classification, readiness assessment, role selection, source-state assessment, risks, decisions, missing information, highest-leverage activity, or recommended actions when those items are needed for orientation.

## 3. Gather Project Inputs

Gather the smallest useful set of project inputs.

Use existing project files and source systems before asking the admin to restate context.

## 4. Identify Source Systems

List existing, missing, stale, contradictory, and not-yet-needed source systems.

Do not create or configure external tools automatically.

When recommending tools such as Notion, GitHub, Jira, Linear, SharePoint, Confluence, or Google Docs, also identify how they should be used well: source owner, parent structure, storage type, and whether routine records belong in existing pages, databases, tickets, comments, folders, or files.

## 5. Identify Canonical Sources

Identify the canonical repository, implementation location, tracker, and documentation source.

Where multiple candidates exist, report the inconsistency and the decision needed.

## 6. Assess Readiness

Assess adoption, discovery, planning, implementation, and validation readiness independently.

Do not allow one readiness state to imply another.

For each material readiness gap, state whether it blocks progress now, the smallest mitigation, and the next action. Do not dump a "not ready" finding on the user without a path forward.

## 7. Reconcile Source State

Compare tracker, repository, plan, metadata, external implementation, completion, and decision evidence where relevant.

Surface mismatches explicitly.

## 8. Assess Continuation Evidence

For continuing existing work, identify current objective, last completed work, active work, blockers, latest completion evidence, latest decision evidence, and latest running context.

If continuation evidence is missing, report the gap before implementation starts.

## 9. Assess Operating Model

Recommend the simplest useful operating model for the project.

Avoid heavy process where a smaller model is enough.

## 10. Assess Roles

Recommend the user-facing Recommended Team for now.

State why each role is needed.

State which roles are not needed yet when useful.

If no additional specialist role is needed, say so clearly.

If a role should act now, generate the prompt or handoff needed to action it.

## 11. Assess Chats

Recommend chat/session structure.

Keep chats role-aware and context-aware.

Avoid overloaded chats.

## 12. Assess Context

Recommend required project context, running context, briefings, ticket context, decision logs, and handoff needs.

For existing projects, identify what should be preserved.

## 13. Identify Gaps And Risks

List known gaps, blockers, risks, and uncertainty.

Do not hide missing source systems or stale context.

For each material gap or risk, include whether it blocks now, the smallest mitigation, who or what should handle it, and the next action.

## 14. Produce Project Setup Report

Produce a Project Setup Report using the output structure in this workflow.

Do not implement setup unless a separate approved task authorises implementation.

## 15. Recommend Highest-Leverage Activity And Top Actions

Recommend the single activity expected to create the greatest project progress, risk reduction, validation, learning, or delivery impact.

Also provide the Top 3 Recommended Actions when useful.

Each recommended action should be:

- concrete
- outcome-focused
- prioritised
- practical
- time-bounded where possible

The goal is maximum useful progress, not minimum effort.

Use Highest-Leverage Activity only when it is genuinely meaningful. It should be part of a practical plan forward, not a label applied to every response.

If the highest-leverage activity or a recommended action requires project-specific files, source systems, external tools, or integrations, state that it requires approval.

# Project Setup Report

The workflow output should include:

```text
Project:
- [Name]

Project mode:
- New project initiation / Existing project adoption / Continue existing project / Unclear

Project type:
- [Type, if known]

Project Snapshot:
- Project Detected:
- Project Type:
- Current Readiness:
- Current Objective:
- Recommended Team:
- Open Risks:
- Open Decisions:
- Missing Information:
- Highest-Leverage Activity:
- Top 3 Recommended Actions:

Objective:
- [Plain-English objective]

Recommended operating model:
-

Recommended Team for now:
-

Recommended chats:
-

Recommended context files:
-

Recommended source systems:
-

Canonical source assessment:
-

Readiness assessment:
- Adoption Readiness:
- Discovery Readiness:
- Planning Readiness:
- Implementation Readiness:
- Validation Readiness:

Reconciliation assessment:
-

Recommended integrations or tools:
-

Initial running context:
-

Continuation state:
-

Planning state:
- Objective:
- Highest-leverage activity:
- Top 3 recommended actions:
- Active work:
- Backlog:
- Blockers:
- Risks:

Continuation evidence:
- Current objective:
- Highest-leverage activity:
- Top 3 recommended actions:
- Last completed work:
- Active work:
- Backlog:
- Active blockers:
- Active risks:
- Latest completion evidence:
- Latest decision evidence:
- Latest validation evidence:
- Decisions by state:
  - Active:
  - Proposed:
  - Superseded:
  - Rejected:
- Assumptions and validation state:
- Latest running context:

Source-of-truth behaviour:
- Planning source:
- Decision source:
- Validation evidence source:
- Conflicts or missing sources:

Known gaps:
- [For each material gap: whether it blocks now, smallest mitigation, next action.]

Active risks:
- [For each material risk: whether it blocks now, smallest mitigation, next action.]

Blockers:
- [For each blocker: smallest unblocker, owner or role, next action.]

Project-specific items to preserve:
-

Items not recommended yet:
-

Next actions:
-

Specialist prompts or handoffs needed now:
-
```

# Running Context Establishment

Project initiation should establish the current-state layer.

For a ResolveOS-level project setup, use `01-context/running-context.md`.

For a project repository, recommend a project-owned current-focus or running-context file only when useful for that project's operating model.

Initial running context should capture:

- current phase
- current state
- objective
- highest-leverage activity
- top recommended actions
- active work
- backlog, if relevant
- open decisions
- active risks
- blockers
- assumptions and validation state where relevant
- current recommendations
- source-of-truth references
- what should not be repeated

For continue-existing-project mode, running context should also identify:

- last reliable current-state source
- what was just completed
- what is still active
- what comes next
- what remains blocked or unverified
- highest-leverage activity
- latest completion evidence
- latest decision evidence
- latest validation evidence
- active, proposed, superseded, and rejected decisions where relevant
- readiness state where relevant

Running context must remain current state only.

Do not turn running context into:

- chat history
- project history
- ticket history
- decision log
- changelog
- full project documentation

# Recommendations

Recommendations should be practical, minimal, and project-specific.

For each recommendation, state:

- what is recommended
- why it is recommended
- whether it is required now or can wait
- which role or source owner should review it
- what source evidence supports it

Do not recommend files, tools, roles, chats, or integrations without evidence.

# Outputs

This workflow may produce:

- Project Setup Report
- canonical source assessment
- readiness assessment
- reconciliation assessment
- continuation evidence summary
- recommended operating model
- recommended roles
- recommended chats
- recommended context files
- recommended source systems
- recommended tools or integrations
- known gaps
- blockers
- highest-leverage activity and top recommended actions
- admin-review questions

# Review Points

Admin review is required before:

- overwriting existing project state
- creating or changing external source systems
- creating project files
- adopting project-specific tooling
- promoting project-specific doctrine into ResolveOS
- changing role authority
- treating an existing project source as superseded

# Failure Modes

Failure modes include:

- assuming new project setup rules apply to an existing project
- overwriting existing state
- inventing missing project facts
- recommending every role or chat by default
- globalising project-specific doctrine
- creating external tools without approval
- treating missing source systems as if they exist
- treating tracker state as repository reality without checking
- treating planning readiness as implementation readiness
- treating implementation existence as validation readiness
- turning initiation into implementation
- restarting existing work from scratch when source-backed continuation context exists

# Anti-Patterns

Do not:

- overwrite existing project state without explicit approval
- automatically create external systems
- assume every project needs every role
- assume every project needs every chat
- create an alternative ResolveOS AI entrypoint
- create a duplicate project-initiation workflow
- treat readiness as a single state
- silently ignore tracker/repository, plan/implementation, metadata/state, or repository/external-implementation mismatches
- continue implementation without available continuation evidence
- use ResolvePM product doctrine as a global project-initiation model
- make project-specific commands, tools, ticket keys, provider names, deployment targets, or roadmap terms global
- invent project facts from memory
- flatten specialist roles into generic project roles
- create context files, tickets, templates, roles, skills, or workflows from this workflow
- turn the Project Setup Report into implementation approval

# Notes

Deferred because they belong elsewhere:

- project-specific setup files belong in project repositories
- external source-system creation belongs in approved project setup work
- detailed source-tracker handoff belongs in a future template, workflow, or project-owned process
- project-specific role prompt files belong in project repositories or generated prompts

Ambiguous items for admin review:

- whether every project should have a local project-initiation report
- whether every project should have a local running-context file or current-focus file
- whether project initiation should later have a companion template
- whether tool recommendations should be standardised by project type

# Related Roles

- `02-roles/product-manager.md`
- `02-roles/business-analyst.md`
- `02-roles/qa-tester.md`
- `02-roles/technical-strategy-lead.md`
- `02-roles/implementation-engineer.md`
- `02-roles/strategic-product-director.md`

# Related Skills

- `03-skills/ticket-writing.md`
- `03-skills/acceptance-criteria.md`
- `03-skills/user-feedback-processing.md`
- `03-skills/completion-reporting.md`
- `03-skills/dependency-management.md`
- `03-skills/requirement-traceability.md`
- `03-skills/implementation-review.md`

# Related Templates

- `04-templates/briefing-template.md`
- `04-templates/chat-handoff-template.md`
- `04-templates/decision-log-template.md`
- `04-templates/role-prompt-template.md`
- `04-templates/ticket-context-template.md`

# Related Context

- `01-context/running-context.md`
- `01-context/startup-context.md`
- `01-context/role-loading-rules.md`
- `01-context/project-loading-rules.md`
- `01-context/context-loading-rules.md`

# Related Governance

- `06-governance/source-of-truth-rules.md`
- `06-governance/update-process.md`
- `06-governance/duplication-control.md`
- `06-governance/project-readiness.md`
- `06-governance/decision-maker-reporting.md`
- `06-governance/architecture-decisions.md`

# What This Workflow Must Not Do

This workflow must not:

- create templates
- create skills
- create roles
- create external systems
- create project files without approval
- overwrite existing project state
- replace project-loading rules
- replace role-loading rules
- replace source-of-truth governance
- approve implementation work
- promote project-specific doctrine into ResolveOS
