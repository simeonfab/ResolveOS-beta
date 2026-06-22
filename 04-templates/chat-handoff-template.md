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
