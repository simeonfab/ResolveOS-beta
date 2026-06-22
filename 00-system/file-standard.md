---
type: standard
scope: global
owner: ResolveOS
version: 0.1
status: draft
---

# ResolveOS File Standard

## Purpose

Define the mandatory structure and formatting rules for all ResolveOS markdown files and for project files that consume ResolveOS.

This standard exists to keep roles, skills, context files, templates, workflows, and governance files consistent, reviewable, reusable, and easy for agents or Codex to understand.

## Universal Rules

Every markdown file must answer five questions:

1. Why does this file exist?
2. When should it be used?
3. What inputs does it consume?
4. What outputs does it produce?
5. What must it not do?

If a file cannot answer these questions, it should be restructured, split, or removed.

## Required YAML Frontmatter

Every markdown file must begin with YAML frontmatter.

Minimum required fields:

```yaml
---
type:
scope:
owner:
version:
status:
---
```

Standard example:

```yaml
---
type: role
scope: global
owner: ResolveOS
version: 1.0
status: active
---
```

## Recommended Metadata Fields

Use additional fields when helpful:

```yaml
source_project:
source_files:
related_roles:
related_skills:
related_context:
review_required:
last_reviewed:
```

## Approved File Types

Use one of these values for `type` unless a new type is intentionally added:

- `standard`
- `principle`
- `context`
- `role`
- `skill`
- `template`
- `workflow`
- `governance`
- `plan`
- `audit-report`
- `extraction-map`
- `codex-prompt`

## Approved Scopes

Use one of these values for `scope`:

- `global`
- `project`
- `migration`
- `role`
- `skill`

## Approved Statuses

Use one of these values for `status`:

- `draft`
- `active`
- `deprecated`
- `archived`

## Naming Rules

File names must:

- Use lowercase.
- Use hyphens between words.
- Be descriptive.
- Avoid vague names like `notes.md`, `misc.md`, `new.md`, or `draft.md`.
- Match the file's actual purpose.

Examples:

```text
technical-strategy-lead.md
user-feedback-processing.md
context-loading-rules.md
source-of-truth-rules.md
```

## Folder Responsibility Rules

Each folder has a clear responsibility.

```text
00-system/      Standards, principles, metadata, naming, global/project separation.
01-context/     Context loading, startup behaviour, precedence, missing context handling.
02-roles/       Reusable role behaviours and responsibilities.
03-skills/      Reusable methods for doing specific tasks.
04-templates/   Reusable document or prompt structures.
05-workflows/   Multi-step operating processes.
06-governance/  Source of truth, migration, duplication, review, and Codex rules.
```

Do not allow files to creep outside their purpose.

If a file contains unrelated material, split it.

## Role File Format

Role files must follow this structure unless there is a clear reason to extend it:

```markdown
# Purpose

# When To Use This Role

# Responsibilities

# Decision Authority

# Inputs

# Outputs

# Behaviour Rules

# Escalation Rules

# Anti-Patterns

# Related Skills

# Related Context
```

Role files must describe reusable role behaviour.

Role files must not contain project-specific tickets, roadmap detail, feature decisions, or implementation tasks.

High-risk or specialist roles must not be flattened into generic roles without explicit admin review.

## Skill File Format

Skill files must follow this structure unless there is a clear reason to extend it:

```markdown
# Purpose

# When To Use

# Inputs

# Process

# Outputs

# Examples

# Anti-Patterns

# Related Roles

# Related Context
```

Skill files must describe reusable task methods.

A skill may be used by multiple roles.

## Context File Format

Context files must follow this structure unless there is a clear reason to extend it:

```markdown
# Purpose

# Loading Order

# Required Inputs

# Precedence Rules

# Missing Context Behaviour

# Notes
```

Context files must define how information should be loaded, prioritised, or handled.

## Governance File Format

Governance files must follow this structure unless there is a clear reason to extend it:

```markdown
# Purpose

# Rules

# Enforcement

# Exceptions

# Examples
```

Governance files must define system rules, not project content.

## Template File Format

Template files must follow this structure unless there is a clear reason to extend it:

```markdown
# Purpose

# Template

# Usage Guidance

# Example
```

Templates should be reusable and should avoid embedding project-specific assumptions unless the template is explicitly project-scoped.

## Workflow File Format

Workflow files must follow this structure unless there is a clear reason to extend it:

```markdown
# Purpose

# Trigger

# Inputs

# Steps

# Outputs

# Review Points

# Failure Modes
```

Workflows should describe multi-step processes.

## Content Preservation Rules

When migrating from existing project files:

- Preserve specific admin instructions over generic best-practice wording.
- Preserve wording where wording matters.
- Do not flatten specialist roles.
- Do not over-summarise.
- Do not silently merge conflicting rules.
- Do not promote project-specific doctrine into global ResolveOS files.
- Use `admin` rather than personal names in reusable global files.

## Formatting Rules

Use:

- Clear headings.
- Short paragraphs.
- Bullets for rules or lists.
- Tables where comparison or mapping is needed.
- Code fences for file structures, examples, YAML, or prompts.

Avoid:

- Long unstructured prose.
- Mixed-purpose sections.
- Duplicate headings with different meanings.
- Ambiguous instructions.
- Vague statements like "use best practice" without saying what that means.

## Review Rules

A file should be reviewed before becoming `active` if it:

- Defines global behaviour.
- Changes context loading.
- Changes source-of-truth rules.
- Migrates content from project files.
- Creates or modifies a high-risk role.
- Consolidates duplicate instructions.

## Completion Requirement

A file is complete enough for review when:

1. It has valid frontmatter.
2. Its purpose is clear.
3. Its scope is clear.
4. It follows the correct format for its file type.
5. It identifies related files where relevant.
6. It avoids unrelated content.
7. It preserves important source guidance where applicable.
