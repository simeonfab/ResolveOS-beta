---
type: knowledge_bundle
scope: global
owner: ResolveOS
source_repository: https://github.com/simeonfab/ResolveOS
source_commit: ed02e9ab2f37ec18f8808f63450a7dfd04c0160c
generated: true
status: draft
---

# ResolveOS ChatGPT Project Knowledge Bundles

## Purpose

These files are generated markdown snapshots of stable ResolveOS guidance for upload into ChatGPT Projects.

They consolidate reusable ResolveOS standards, context, roles, skills, workflows, templates, and governance into a small number of project-knowledge files.

`START_HERE.md` is the user entry point for private beta testers. It is short, non-technical, and should be read before interacting with the uploaded knowledge bundles.

ResolveOS should show a compact Project Snapshot when orientation adds value, such as a new conversation, stale continuation, project adoption, status request, or material change in readiness, objective, source of truth, risks, or blockers.

ResolveOS should not show a Project Snapshot on every interaction or prepend one to a full project initiation response.

ResolveOS should use declared project planning, decision, and validation sources such as Jira, Notion, GitHub Issues, Azure DevOps, project repositories, or project documentation. If no planning source exists, ResolveOS supports only a lightweight project-owned planning model and should not create a competing roadmap or project-management system.

## Files To Upload

Upload `START_HERE.md` and these six bundle files to the ChatGPT Project knowledge area:

- `START_HERE.md`
- `01_RESOLVEOS_CORE.md`
- `02_RESOLVEOS_CONTEXT_AND_LOADING.md`
- `03_RESOLVEOS_ROLES.md`
- `04_RESOLVEOS_SKILLS_AND_WORKFLOWS.md`
- `05_RESOLVEOS_TEMPLATES.md`
- `06_RESOLVEOS_GOVERNANCE.md`

Do not upload `generate-resolveos-bundles.ps1`; it is the local regeneration script.

After upload, tell testers to read `START_HERE.md` first.

## Project Instructions

Set the ChatGPT Project instructions to:

```text
Always begin by loading and following 00-system/resolveos-entrypoint.md. Do not bypass it. If required context is missing, state what is missing and stop.
```

## Canonical Source

These bundles are generated snapshots.

GitHub remains the canonical source for ResolveOS:

```text
https://github.com/simeonfab/ResolveOS
```

The source commit used for this export is:

```text
ed02e9ab2f37ec18f8808f63450a7dfd04c0160c
```

Uploaded ChatGPT Project files do not update automatically. Regenerate and re-upload them when ResolveOS source guidance changes.

Project-specific context must come from the relevant project repository, tracker, workspace, or documentation source. Project repositories and project-owned systems remain the source of truth for project facts, code, roadmap, tickets, decisions, and implementation state.

These bundles contain global ResolveOS operating guidance only. They are snapshots for ChatGPT Projects, not a replacement for the live ResolveOS repository or any project repository.

## Bundle Mapping

| Bundle | Source directories |
| --- | --- |
| `01_RESOLVEOS_CORE.md` | Stable reusable files from `00-system/` |
| `02_RESOLVEOS_CONTEXT_AND_LOADING.md` | Stable reusable files from `01-context/` |
| `03_RESOLVEOS_ROLES.md` | Files from `02-roles/` |
| `04_RESOLVEOS_SKILLS_AND_WORKFLOWS.md` | Files from `03-skills/` and stable reusable files from `05-workflows/` |
| `05_RESOLVEOS_TEMPLATES.md` | Files from `04-templates/` |
| `06_RESOLVEOS_GOVERNANCE.md` | Stable reusable files from `06-governance/` |

## Regeneration

From the ResolveOS repository root, run:

```powershell
.\exports\chatgpt-project\generate-resolveos-bundles.ps1
```

The script:

- verifies expected source directories exist
- excludes the export directory from input
- writes UTF-8 markdown bundles
- sorts source files deterministically by repository path
- preserves each included source file verbatim
- records the current ResolveOS source commit and generation date
- avoids modifying canonical ResolveOS source files

## Known Limitation

ChatGPT Project uploads are static. Uploaded bundles will not update automatically when GitHub changes.
