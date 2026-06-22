---
type: governance
scope: global
owner: ResolveOS
version: 0.1
status: draft
---

# Extraction Migration Guardrails

## Purpose

Define mandatory guardrails for extracting existing ResolvePM guidance into ResolveOS without losing important user-specific working rules, role behaviours, ticket-writing rules, feedback-handling rules, or assistant constraints.

These rules apply to any migration from project-specific files into ResolveOS.

## Core Rule

Do not skim.

Extraction work must prioritise accuracy and preservation over speed. It is acceptable to work in batches. It is not acceptable to skim, over-summarise, flatten, or rush content simply to complete migration faster.

## Mandatory Guardrails

### 1. Preserve Detail

Do not flatten rich role guidance into generic role descriptions.

If a role contains detailed operating rules, decision patterns, constraints, or working style instructions, preserve that detail unless it is clearly obsolete or duplicated.

This applies especially to complex roles such as Technical Strategy Lead, Product Manager, Architect, Engineer, QA, Delivery, and Research roles.

### 2. Do Not Over-Generalise

Do not make ResolvePM-specific doctrine global ResolveOS doctrine.

Only promote content to ResolveOS when it is genuinely reusable across projects.

If content is specific to the ResolvePM product, roadmap, user experience, implementation choices, UI behaviour, or product strategy, it should remain in ResolvePM.

### 3. Keep Files Purpose-Specific

Each file should be specific about what it governs.

Files must not creep into unrelated areas.

Examples:

- A role file should describe role behaviour, responsibilities, boundaries, inputs, outputs, and decision style.
- A skill file should describe a reusable task method.
- A context file should describe context loading, context precedence, or working assumptions.
- A project file should describe project-specific context.
- A governance file should describe rules for maintaining the system.

If a file starts collecting unrelated rules, split the content rather than allowing scope creep.

### 4. Preserve Admin Working Rules

Do not refer to the user by personal name inside reusable global files.

Use `admin` where the file needs to refer to the human owner/operator of the system.

Do not drop rules just because they previously referenced the user directly. Convert them carefully into admin-facing language.

### 5. Preserve Assistant Anti-Patterns

Do not drop rules about what assistants or agents must not do.

The following kinds of rules are high-value and must be preserved carefully:

- No fake functionality.
- No invented implementation claims.
- No direct commits where review is required.
- No silent scope expansion.
- No implementation drift.
- No overconfident claims without evidence.
- No vague completion summaries.
- No skipping blockers.
- No ignoring missing context.
- No replacing specific user instructions with generic best practices.

### 6. Preserve Ticket-Writing Rules

Ticket-writing rules are high-value global material unless they are explicitly project-specific.

Do not summarise them so aggressively that practical writing guidance is lost.

Preserve rules covering:

- Ticket structure.
- Acceptance criteria.
- Implementation notes.
- Production validation.
- Smoke test expectations.
- Blocking issues.
- One-ticket-at-a-time workflow.
- Completion reports.
- Clarity on what is and is not implemented.

### 7. Preserve Feedback-Handling Rules

Feedback-handling rules are high-value global material unless they are explicitly tied to one product.

Preserve rules covering:

- How feedback should be captured.
- How feedback should be cleaned.
- How feedback should be classified.
- When feedback becomes a ticket.
- When feedback remains raw input.
- How duplicates should be handled.
- How not to over-format product feedback.

### 8. Preserve Prompt and Context-Loading Discipline

Rules about prompt structure and context loading must be preserved carefully.

This includes:

- What files must be loaded before work starts.
- What happens if required context is missing.
- Which context overrides which.
- How role files should reference project context.
- How current focus and briefing files should be used.
- How agents should avoid working from memory when files are required.

### 9. Preserve Cost-Safe AI/API Rules

Cost-control and AI/API usage rules must be preserved.

This includes:

- Avoid unnecessary API calls.
- Avoid expensive loops.
- Avoid fake AI behaviour.
- Be explicit about what is simulated versus implemented.
- Use simple deterministic logic where AI is not needed.

### 10. Batch Rather Than Rush

If content is too large to migrate safely in one pass, split the work into smaller batches.

Each batch should have:

- Clear source files.
- Clear target files.
- Clear extraction logic.
- A reviewable diff.
- A summary of what was preserved, changed, deferred, or left untouched.

## Review Requirement

Before implementation changes are made, produce or review an extraction map showing:

- Source file.
- Source section or rule.
- Classification.
- Proposed destination.
- Whether wording should be preserved.
- Whether the content is global, project-specific, duplicate, obsolete, or unclear.

Do not proceed with broad rewrites until risky or unclear classifications have been resolved.

## High-Risk Items From ResolvePM Audit

The following risks must be explicitly managed:

1. Losing richer historical guidance in `AGENTS.md.backup`.
2. Flattening Technical Strategy Lead into generic Architect or Product Manager roles.
3. Accidentally promoting ResolvePM product doctrine into ResolveOS global doctrine.
4. Dropping admin-specific rules around plain-English communication.
5. Dropping admin-specific rules around no direct commits.
6. Dropping admin-specific rules around implementation drift.
7. Dropping admin-specific rules around blocker handling.
8. Dropping admin-specific rules around short prompts and prompt/context-loading discipline.

## Duplication Opportunities From ResolvePM Audit

The following duplicated or repeated rules should be consolidated intentionally:

1. No fake functionality.
2. One-ticket-at-a-time workflow.
3. Cost-safe AI/API rules.
4. Completion report format.
5. Blocker behaviour.
6. Prompt/context-loading discipline.

Consolidation must preserve useful detail rather than reducing repeated rules to vague principles.
