---
type: skill
scope: global
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolvePM
source_files:
  - migration/resolvepm-extraction-audit.md
  - migration/resolvepm-extraction-map.md
related_skills:
  - 03-skills/ticket-writing.md
  - 03-skills/completion-reporting.md
related_context:
  - 00-system/ai-operating-principles.md
  - 01-context/context-loading-rules.md
  - 01-context/startup-context.md
related_governance:
  - 06-governance/codex-working-rules.md
  - 06-governance/extraction-migration-guardrails.md
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Define how assistants, agents, and Codex capture, preserve, classify, analyse, and convert user feedback into reviewed work.

This skill exists to preserve the reusable ResolvePM feedback-handling behaviour in ResolveOS without turning it into generic product-management process.

Source references:
- `migration/resolvepm-extraction-audit.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `Extraction Table`
- `06-governance/extraction-migration-guardrails.md` > feedback-handling preservation rules

# When To Use

Use this skill when:

- Capturing product, workflow, tester, admin, or user feedback.
- Cleaning feedback without losing the original meaning.
- Classifying feedback before backlog, roadmap, or ticket decisions.
- Reviewing whether feedback should become a follow-up ticket.
- Handling duplicate, ambiguous, partial, or conflicting feedback.
- Preserving traceability from feedback to later work.

Do not use this skill to replace project-specific discovery, strategy, prioritisation, research, ticket-writing, or implementation review processes.

# Inputs

Useful inputs include:

- Raw feedback text.
- Source or user identity where available.
- Timestamp where available.
- Feedback category where available.
- Product, project, workflow, ticket, release, or testing context.
- Existing related feedback, tickets, decisions, or prior analysis.
- Project-specific prioritisation filters from the current project context.

Minimum explicit feedback fields found in ResolvePM are:

- `category`
- `message`
- `user`
- `timestamp`

Source reference:
- `migration/resolvepm-extraction-map.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `Extraction Table` > `docs/codex-briefings/CP-84-tester-readiness.md`

# Feedback Processing Principles

Keep feedback handling simple by default.

Preserve the original intent before cleaning, classifying, or converting feedback.

Separate raw feedback from interpretation. Do not overwrite the original wording with a cleaned summary.

Distinguish observations, requests, assumptions, proposed solutions, recommendations, and follow-up work.

Prefer evidence over invention. Do not infer motivation, priority, severity, or acceptance criteria that the feedback does not support.

Feedback should become reviewed follow-up tickets, not automatic current-scope expansion.

Do not over-format feedback into a heavy taxonomy unless admin approves.

Use project-specific prioritisation filters only from the active project context. Do not make ResolvePM product doctrine global.

Source references:
- `migration/resolvepm-extraction-audit.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-audit.md` > `Risks / Things Not To Lose`
- `migration/resolvepm-extraction-map.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `High Risk Migrations`
- `00-system/ai-operating-principles.md` > `Evidence Over Invention`
- `00-system/ai-operating-principles.md` > `Preserve Admin Intent`

# Capturing Feedback

Capture the raw feedback first.

When structured capture is needed, collect at least:

- `category`
- `message`
- `user`
- `timestamp`

Feedback collection should be simple enough that the user can provide useful feedback without extra operational burden.

Where practical, feedback should be collected without developer intervention.

External testing feedback should validate workflow value, not just technical correctness.

Do not expand feedback capture into workspace, billing, enterprise auth, organisation, or other platform models unless admin explicitly approves that scope.

Source references:
- `migration/resolvepm-extraction-audit.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `Extraction Table` > `docs/codex-briefings/CP-84-tester-readiness.md`

# Preserving Feedback

Preserve:

- The raw feedback wording.
- The feedback source.
- The timestamp where available.
- The project, ticket, feature, workflow, or test context.
- Any uncertainty, contradiction, or missing detail.
- Links to related feedback, tickets, or decisions where available.

Cleaned feedback may clarify grammar, remove noise, or separate concepts, but it must not change the meaning.

If the feedback contains both a problem and a proposed solution, preserve both separately.

If the assistant is unsure what the user meant, label the uncertainty explicitly instead of resolving it silently.

Source references:
- `06-governance/extraction-migration-guardrails.md` > feedback capture, cleaning, classification, and traceability guardrails
- `00-system/ai-operating-principles.md` > `Explicit Uncertainty`
- `00-system/ai-operating-principles.md` > `Do Not Over-Summarise Important Rules`

# Classifying Feedback

Use lightweight classification unless admin asks for a richer taxonomy.

Recommended lightweight classes:

- Raw feedback.
- Observation.
- Problem or pain point.
- Request.
- Proposed solution.
- Recommendation.
- Question.
- Ambiguous feedback.
- Duplicate or related feedback.
- Follow-up ticket candidate.

Classification should help review. It should not become a substitute for review.

Do not treat every user message as a ticket request. A message may be feedback, a correction, a blocker, an instruction, a question, or a signal that project context needs to be checked.

Source references:
- `migration/resolvepm-extraction-map.md` > `Ambiguous Classifications Requiring Admin Decision`
- `migration/resolvepm-extraction-map.md` > `High Risk Migrations`
- `06-governance/extraction-migration-guardrails.md` > feedback-handling rules

# Converting Feedback Into Work

Convert feedback into work only after review.

Before converting feedback into a ticket:

- Preserve the raw feedback.
- Identify the underlying problem or request.
- Separate observations from recommendations.
- Check for duplicates or related work.
- Confirm whether the work belongs in the current scope or should become follow-up work.
- Use the project context to decide whether the feedback is globally relevant, project-specific, or not actionable yet.

When feedback becomes a ticket, use `03-skills/ticket-writing.md`.

Feedback should suggest follow-up tickets rather than expand the current implementation scope unless admin explicitly changes the scope.

Source references:
- `migration/resolvepm-extraction-audit.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-audit.md` > `Risks / Things Not To Lose`
- `migration/resolvepm-extraction-map.md` > `Global Feedback Handling Rules`
- `03-skills/ticket-writing.md` > `Ticket Writing Process`

# Duplicate Handling

Duplicates should be consolidated without losing traceability.

When feedback duplicates or overlaps existing feedback:

- Preserve the new raw feedback.
- Link or reference the existing feedback, ticket, or decision where possible.
- Note whether it is an exact duplicate, a related example, or a new variation of the same issue.
- Preserve source and timestamp information.
- Do not discard duplicate feedback merely because the underlying issue is already known.

Repeated feedback can be evidence of importance, confusion, poor workflow fit, or documentation gaps. Do not infer priority from repetition alone without project context.

Source references:
- `06-governance/extraction-migration-guardrails.md` > duplicate and traceability preservation
- `00-system/ai-operating-principles.md` > `Evidence Over Invention`

# Ambiguous Feedback

When feedback is ambiguous:

- Preserve the original wording.
- State what is unclear.
- Avoid inventing intent.
- Avoid turning ambiguity into acceptance criteria.
- Ask for admin review when the ambiguity affects scope, priority, product direction, or implementation.
- Keep the feedback as raw or under review until enough context exists.

If feedback may be project-specific, do not migrate it into global ResolveOS behaviour without admin decision.

Source references:
- `migration/resolvepm-extraction-map.md` > `Ambiguous Classifications Requiring Admin Decision`
- `06-governance/source-of-truth-rules.md` > project repositories own project-specific decisions
- `00-system/ai-operating-principles.md` > `Explicit Uncertainty`

# Prioritisation Guidance

Prioritisation must use the active project context.

Global feedback processing may identify:

- Frequency.
- Severity.
- Workflow impact.
- User impact.
- Evidence strength.
- Scope fit.
- Follow-up readiness.

Global feedback processing must not impose ResolvePM-specific product filters on other projects.

The ResolvePM strategic filter found during extraction is not migrated as a global rule. It should remain project-specific unless admin separately approves a generic version.

Source references:
- `migration/resolvepm-extraction-audit.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `Project-Specific ResolvePM Content`
- `06-governance/source-of-truth-rules.md` > ResolveOS versus project source ownership

# Outputs

Possible outputs include:

- Preserved raw feedback record.
- Cleaned feedback summary.
- Lightweight feedback classification.
- Duplicate or related-feedback note.
- Ambiguity note.
- Follow-up ticket recommendation.
- Deferred feedback list.
- Admin-review question.
- Source-to-ticket traceability note.

Any output that claims feedback was stored, ticketed, linked, reviewed, tested, deployed, or implemented must only say so if that action actually happened.

Source references:
- `03-skills/completion-reporting.md` > completion honesty and validation reporting
- `06-governance/codex-working-rules.md` > no fake functionality and completion honesty

# Anti-Patterns

Do not:

- Over-format feedback into a heavy taxonomy unless admin approves.
- Convert every feedback item into a ticket automatically.
- Expand current implementation scope because feedback was found.
- Lose the raw wording.
- Replace user intent with assistant interpretation.
- Treat a proposed solution as the underlying problem.
- Treat an observation as a recommendation.
- Discard duplicates without traceability.
- Hide ambiguity.
- Invent priority, severity, source, timestamp, or acceptance criteria.
- Make ResolvePM product doctrine global.
- Claim feedback was stored, reviewed, ticketed, or implemented unless it was.

Source references:
- `migration/resolvepm-extraction-map.md` > `Global Feedback Handling Rules`
- `migration/resolvepm-extraction-map.md` > `High Risk Migrations`
- `06-governance/extraction-migration-guardrails.md` > preservation rules
- `00-system/ai-operating-principles.md` > truthfulness and evidence rules

# Examples

Simple captured feedback:

```text
category: workflow
message: "It is not clear what happens after I submit tester feedback."
user: external tester
timestamp: 2026-06-07 14:30
```

Cleaned classification:

```text
Raw feedback preserved: yes
Classification: observation; possible documentation or workflow clarity issue
Interpretation: user may need clearer post-submit confirmation
Uncertainty: exact expected confirmation is not specified
Recommended handling: review against project context before creating a follow-up ticket
```

Feedback-to-ticket review note:

```text
Feedback should not expand the current implementation scope.
Recommended follow-up: create a reviewed ticket only if admin agrees this is actionable now.
Traceability: retain source feedback and timestamp in the ticket background.
```

# Related Skills

- `03-skills/ticket-writing.md`
- `03-skills/completion-reporting.md`

# Related Governance

- `00-system/ai-operating-principles.md`
- `01-context/context-loading-rules.md`
- `01-context/startup-context.md`
- `06-governance/codex-working-rules.md`
- `06-governance/extraction-migration-guardrails.md`
- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

# Deferred Items

Deferred for later batches or admin decision:

- A dedicated `05-workflows/feedback-to-ticket.md` workflow.
- Any feedback capture template.
- A richer feedback triage taxonomy.
- Project-specific prioritisation filters.
- Product-specific tester-readiness workflows.
- Storage implementation details for feedback systems.
- Automatic feedback collection mechanisms.

# Ambiguous Items For Admin Review

Admin review is needed for:

- Whether ResolveOS should keep feedback fields minimal or define a richer canonical taxonomy.
- Whether ordinary user messages should be treated as feedback by default across all projects.
- Whether ResolveOS should define a generic version of ResolvePM's product feedback strategic filter.
- Which storage fields beyond `category`, `message`, `user`, and `timestamp` should become canonical.
