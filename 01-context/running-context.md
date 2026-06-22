---
type: context
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
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
  - 01-context/role-loading-rules.md
  - 01-context/missing-context-behaviour.md
  - 01-context/project-loading-rules.md
related_governance:
  - 06-governance/decision-maker-reporting.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
  - 06-governance/update-process.md
  - 06-governance/duplication-control.md
  - 06-governance/project-readiness.md
review_required: true
last_reviewed: 2026-06-12
last_updated: 2026-06-19
max_staleness_days: 7
---

# Purpose

Preserve active ResolveOS working state across chats, agents, sessions, migrations, and handoffs without relying on conversation memory.

The running context is shared working memory for ongoing work. It should answer where the work is, what was just completed, what is currently in progress, what decisions matter now, what risks are active, what should happen next, and what should not be repeated.

The running context is current-state context only.

It is not:

- a historical changelog
- a decision log
- a migration report
- a source-system replacement
- a project-specific current-focus file

Source references:

- `01-context/context-loading-rules.md` > core rule and loading order
- `01-context/project-loading-rules.md` > memory is not a source of truth
- `06-governance/source-of-truth-rules.md` > ownership hierarchy
- `migration/template-layer-review.md` > readiness assessment and recommended next batch

# Current Phase

ResolveOS is in controlled migration from ResolvePM.

Current phase: validation-driven refinement after successful project adoption testing.

The template layer and core delivery skills are complete enough at draft level for validation-driven refinement.

`00-system/resolveos-entrypoint.md` is the canonical ResolveOS AI entrypoint.

Project initiation is established as the governing workflow for new project initiation, existing project adoption, and continuing existing projects when project access is available.

The successful ResolveYGO adoption test validated project initiation and revealed practical improvements around readiness states, canonical project source identification, tracker/repository reconciliation, and evidence-backed continuation.

Current refinement adds lightweight project-state management for planning state, decision lifecycle, and evidence/validation state without creating new roles, workflows, templates, or external project-management systems.

Source references:

- `migration/template-layer-review.md` > `Executive Summary`
- `migration/template-layer-review.md` > `Readiness Assessment`
- `migration/resolveos-architecture-review.md` > `Recommended Next Batch`

# Current State

ResolveOS currently has draft foundations for:

- file standards and metadata standards
- migration strategy and source-of-truth governance
- AI operating principles and Codex working rules
- startup, context-loading, role-loading, missing-context, and project-loading context
- Product Manager, Business Analyst, QA Tester, Technical Strategy Lead, Implementation Engineer, and Strategic Product Director roles
- ticket-writing, completion-reporting, user-feedback-processing, acceptance-criteria, dependency-management, requirement-traceability, and implementation-review skills
- project-initiation, ticket-to-implementation, implementation-review-loop, and feedback-to-ticket workflows
- completion report, blocker report, ticket context, briefing, role prompt, decision log, and chat handoff templates
- update-process and duplication-control governance
- project-readiness governance
- project-state refinements for planning persistence, decision lifecycle, and validation state
- architecture decisions through ADR-059

ResolveOS remains draft migration guidance until admin review changes file status.

ResolvePM should not be refactored to depend primarily on ResolveOS until the relevant migration batches are reviewed and accepted.

Source references:

- `migration-review.md` > `Executive Summary`
- `migration-review.md` > `ResolveOS Readiness`
- `migration/resolvepm-residual-audit.md` > `Executive Summary`
- `migration/template-layer-review.md` > `Templates Reviewed`

# Recently Completed

Recently completed draft migration work includes:

- completion report template
- blocker report template
- ticket context template
- briefing template
- role prompt template
- template layer review
- running context
- decision log template
- ResolveOS architecture review
- update-process governance
- duplication-control governance
- chat handoff template
- project initiation workflow
- dependency-management skill
- requirement-traceability skill
- implementation-review skill
- Architecture Review #3
- ResolveYGO adoption validation

The template review found no high-priority template rewrite requirement and warned against removing valid repeated sections such as intent, risk, missing context, validation, recommendation, and evidence.

# Current Validation Findings

Validation findings from the successful ResolveYGO adoption test and later project-state refinement:

- Project initiation is validated as the governing workflow for new project initiation, existing project adoption, and existing project continuation.
- Architecture Review #3 is complete and found ResolveOS functionally complete at draft level.
- Validation-driven improvements are needed for readiness states, canonical project source assessment, reconciliation between tracker state and repository reality, and evidence-backed continuation.
- Final core refinements define planning ownership, decision states, and validation state so continuation can identify objective, active work, next actions, blockers, decisions, evidence, and validation gaps.
- These refinements should improve adoption reliability without creating new roles, workflows, templates, duplicate planning systems, duplicate decision systems, or duplicate validation systems.

Source references:

- `migration/template-layer-review.md` > `Templates Reviewed`
- `migration/template-layer-review.md` > `Things That Should NOT Change`
- `migration/template-layer-review.md` > `Duplication Analysis`

# Active Work

Active work: final core project-state management refinement.

This refinement covers:

- `06-governance/project-readiness.md`

This refinement updates:

- `05-workflows/project-initiation.md`
- `06-governance/architecture-decisions.md`
- `01-context/running-context.md`
- `06-governance/source-of-truth-rules.md`
- `05-workflows/user-guide.md`
- `04-templates/decision-log-template.md`

Do not create additional workflows, templates, roles, skills, or ResolvePM changes as part of this batch.

Source references:

- Current Batch 7.0 admin instruction
- `00-system/file-standard.md` > folder responsibility rules
- `06-governance/source-of-truth-rules.md` > migration rules

# Open Decisions

Open decisions that matter now:

- Whether real-world project use shows that source-tracker handoff/comment structure is needed, or whether project-owned source systems are enough.
- Whether source-tracker blocker, completion, or decision comments should be mandatory when source-system access exists or remain project-owned.
- Whether completion reports need a `Files Removed` section.
- Whether briefing templates need stricter freshness or `last reviewed` metadata.
- Whether multi-role prompts need their own template or the current role-loading rules and role prompt template are sufficient.
- Whether role-specific running contexts are justified later, and if so how they avoid becoming competing sources of truth.
- Whether chat handoff files should be stored in projects, temporary migration folders, or generated ad hoc.
- Whether project initiation should later have a companion template or remain workflow-only.
- Whether project readiness should later have a template after more adoption trials.
- Whether source-system handoff should remain project-owned or become a global template/workflow.

Source references:

- `migration/template-layer-review.md` > `Candidate Improvements`
- `migration/template-layer-review.md` > `Recommended Next Batch`
- `migration/template-layer-review.md` > `Stop / Do Not Build Yet`
- `04-templates/blocker-report-template.md` > deferred source-tracker comment items
- `04-templates/briefing-template.md` > ambiguous freshness items

# Active Risks

Active risks:

- The running context could become a changelog, decision log, or migration report if updates append history instead of preserving current state.
- Source-system handoff remains the clearest template-layer gap after decision-log and chat-handoff templates.
- Project-specific ResolvePM doctrine could still leak into global ResolveOS if future batches are not checked against source-of-truth rules.
- Template cleanup could remove valid repeated intent, risk, missing-context, validation, recommendation, and evidence sections.
- Unreviewed draft files may be treated as final source of truth too early.
- Role-specific or project-specific running contexts could become competing sources of truth if created without clear ownership.
- Running context may go stale if agents rely on chat timestamps instead of file metadata.
- Project initiation could become overloaded if future batches add bootstrap-file creation, external-tool creation, or project doctrine to the governing workflow.
- Readiness language could become too heavy if applied to low-risk casual conversations.
- Canonical-source and reconciliation checks could accidentally absorb project-specific tracker fields or repository conventions if not kept source-owned.
- Planning, decision, and validation state could become too heavy if future work tries to recreate Jira, Notion, Azure DevOps, Trello, GitHub Issues, or research-management tools.

Source references:

- `migration/template-layer-review.md` > `Residual risk`
- `migration-review.md` > `Risks`
- `migration/resolvepm-residual-audit.md` > `Migration Risks`
- `06-governance/source-of-truth-rules.md` > `Core Principle`

# Current Recommendations

Recommended handling:

- Read this running context before continuing significant migration, implementation, review, governance, or architecture work.
- Check `last_updated` and `max_staleness_days` before significant work.
- If this file is stale, update it or create a chat handoff before continuing.
- Keep future updates concise and current-state focused.
- Replace stale current-state items instead of appending a long history.
- Use ADRs for historical decisions.
- Use migration reviews and audit reports for historical migration findings.
- Use project repositories for project-specific current focus, ticket state, roadmap, architecture, commands, and source-system details.
- Use `README.md` as the human entrypoint and `00-system/resolveos-entrypoint.md` as the AI entrypoint.
- Use `05-workflows/project-initiation.md` as the governing workflow for new project initiation, existing project adoption, and existing project continuation when project access is available.
- Treat governance stabilisation as complete enough at draft level for careful continuation.
- Treat `00-system/resolveos-entrypoint.md` as the AI entrypoint and project initiation as the governing workflow for new project initiation, existing project adoption, and continuing existing projects.
- Use `06-governance/project-readiness.md` when adoption, discovery, planning, implementation, or validation readiness affects the highest-leverage activity.
- Treat readiness states independently; one readiness state does not imply another.
- During project initiation, identify canonical project sources and surface tracker/repository, plan/implementation, metadata/state, and repository/external-implementation inconsistencies.
- During continuation, prefer evidence from running context, completion reports, blocker reports, decision records, repository state, and source systems over chat memory.
- Use declared external planning systems when they exist.
- If no planning source exists, use a lightweight project-owned planning model that can answer objective, highest-leverage activity, top recommended actions, active work, backlog, blockers, and risks.
- Treat decision states as Proposed, Active, Superseded, or Rejected; existing accepted ADRs are active unless later superseded.
- Track assumptions, evidence, confidence, and validation status only as much as needed to support readiness, continuation, commercial validation, product validation, or implementation validation.
- Current focus is validation-driven refinement and careful review of residual high-evidence capabilities before ResolvePM cleanup.
- For the next batch, prefer source-tracker handoff/comment, debugging-support, AI workflow design, or other high-evidence residual extraction only if admin approves the scope.

Source references:

- `01-context/context-loading-rules.md` > loading order and missing context behaviour
- `01-context/project-loading-rules.md` > project repositories own project context
- `06-governance/source-of-truth-rules.md` > ownership hierarchy
- `06-governance/update-process.md` > running context update rules
- `04-templates/chat-handoff-template.md` > chat/session migration

# Do Not Repeat

Do not repeat these mistakes:

- Do not rely on chat memory for active ResolveOS state.
- Do not rely on chat message timestamps to decide running-context freshness.
- Do not turn this file into a full project history.
- Do not duplicate ADR content inside this file.
- Do not duplicate migration report findings inside this file.
- Do not create extra templates, skills, workflows, roles, or governance files without an approved batch.
- Do not create alternative ResolveOS AI entrypoints or duplicate project-initiation workflows.
- Do not treat adoption readiness, discovery readiness, planning readiness, implementation readiness, and validation readiness as the same thing.
- Do not silently ignore differences between tracker state and repository reality.
- Do not create duplicate planning, decision, or validation systems when a project source of truth already exists.
- Do not refactor ResolvePM before ResolveOS review and cleanup planning are approved.
- Do not renumber ADR-039, ADR-040, or ADR-041 solely for neatness.
- Do not make project-specific commands, ticket keys, provider names, routes, deployment targets, roadmap terms, or product doctrine global.

Source references:

- `migration/template-layer-review.md` > `Things That Should NOT Change`
- `migration/resolvepm-residual-audit.md` > `Stop / Do Not Migrate Yet`
- `01-context/project-loading-rules.md` > project doctrine ownership
- `06-governance/architecture-decisions.md` > reconciliation notes

# Source Of Truth References

Use these canonical homes:

- Current active working state: `01-context/running-context.md`
- Chat/session migration context: `04-templates/chat-handoff-template.md`
- Historical architecture decisions: `06-governance/architecture-decisions.md`
- Source ownership and conflict rules: `06-governance/source-of-truth-rules.md`
- Project readiness assessment: `06-governance/project-readiness.md`
- Planning state model and continuation output: `05-workflows/project-initiation.md`
- Decision lifecycle: `05-workflows/project-initiation.md`, `04-templates/decision-log-template.md`, and `06-governance/architecture-decisions.md`
- Evidence and validation state: `06-governance/project-readiness.md` and `05-workflows/project-initiation.md`
- Update ownership and propagation rules: `06-governance/update-process.md`
- Duplication control: `06-governance/duplication-control.md`
- Context loading and missing context behaviour: `01-context/context-loading-rules.md` and `01-context/missing-context-behaviour.md`
- Project-specific current focus, tickets, roadmap, architecture, commands, and product doctrine: project repositories
- Migration findings and batch readiness: migration reviews and audit reports
- Communication structures: `04-templates/`
- Reusable behaviours and methods: `02-roles/`, `03-skills/`, `05-workflows/`, and `06-governance/`
- ResolveOS AI entrypoint: `00-system/resolveos-entrypoint.md`
- Project initiation workflow: `05-workflows/project-initiation.md`

# Last Reviewed

Last reviewed: 2026-06-12.

Last updated: 2026-06-19.

Maximum staleness: 7 days.

Status: draft.

Created during Batch 4D.1 and updated during Batch 5.1, Batch 6.1, Batch 7.0, and final core project-state management refinement. Requires admin review before becoming active.

# Usage Guidance

Use this file as a handoff checkpoint before significant work.

Update it only when current state changes materially.

Before significant migration, implementation, review, governance, or architecture work:

- check `last_updated`
- compare it with `max_staleness_days`
- treat the file as stale when the metadata threshold is exceeded
- do not rely on chat message timestamps as freshness evidence

If this file is stale:

- update it when the current state is known and source-backed
- create a chat handoff when session-specific continuity is needed
- stop and ask for admin review when the current state cannot be determined safely

When updating:

- keep the file concise
- remove stale items
- point to source-of-truth files instead of copying them
- preserve current state, not history
- flag ambiguity instead of guessing

# Deferred Items

Deferred because they belong elsewhere:

- Detailed historical decision records belong in ADRs.
- Detailed migration history belongs in migration reports and audits.
- Detailed project status belongs in project-specific current-focus or project context files.
- Source-system comments belong in future source-tracker handoff guidance or project workflows.
- Decision writing method beyond the current template belongs in a future decision-log-writing skill if approved.
- Role-specific running contexts may be considered later only if justified.
- Project-specific readiness checklists belong in project repositories.
- Exact tracker, repository, database, and validation command details belong in project context.

# Ambiguous Items For Admin Review

Admin review is needed for:

- Whether running context should be mandatory in every ResolveOS startup sequence or only before significant work.
- Whether role-specific running contexts are useful enough to justify future files.
- Whether project repositories should create local running-context files or continue using current-focus files.
- Whether source-system state should ever be summarised here, or always remain in project repositories and source systems.
- Whether 7 days is the correct global `max_staleness_days` value.
- Whether project-readiness assessment should become a template after more adoption tests.

# What This Context Must Not Do

This context must not:

- replace ADRs
- replace migration reviews
- replace templates
- replace project current-focus files
- replace source systems
- define new roles, skills, workflows, or governance rules
- promote project-specific doctrine into ResolveOS
- become an append-only history file
