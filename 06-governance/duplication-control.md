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
