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
