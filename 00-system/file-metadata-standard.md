---
type: standard
scope: global
owner: ResolveOS
version: 0.1
status: draft
---

# ResolveOS Metadata Standard

## Purpose

Define the mandatory YAML metadata structure used across ResolveOS.

## Required Fields

Every markdown file must contain:

```yaml
---
type:
scope:
owner:
version:
status:
---
```

## Required Field Definitions

### type

Defines what kind of file this is.

Approved values:

- standard
- principle
- context
- role
- skill
- template
- workflow
- governance
- plan
- audit-report
- extraction-map
- codex-prompt
- strategy

### scope

Defines applicability.

Approved values:

- global
- project
- migration
- role
- skill

### owner

Normally:

```yaml
owner: ResolveOS
```

### version

Semantic versioning preferred.

Examples:

```yaml
version: 0.1
version: 1.0
version: 1.2
```

### status

Approved values:

- draft
- active
- deprecated
- archived

## Optional Fields

Use when helpful.

```yaml
source_project:
source_files:
related_roles:
related_skills:
related_context:
review_required:
last_reviewed:
```

## Migration Rules

When content is extracted from another repository:

- Preserve source references.
- Preserve source file information where practical.
- Preserve review traceability.

## Validation Rules

Files should not become active unless:

- Metadata exists.
- Metadata is valid.
- File type matches file purpose.
- Scope matches file responsibility.
