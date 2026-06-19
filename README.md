---
type: knowledge_bundle
scope: global
owner: ResolveOS
source_repository: https://github.com/simeonfab/ResolveOS
source_commit: 747d2d2ab4456ddc7a55063875241c0d2d75d3a5
generated: true
status: draft
---

# ResolveOS ChatGPT Project Setup Guide

## What ResolveOS Is

ResolveOS helps ChatGPT understand, organise, continue, and improve projects.

It gives ChatGPT a single starting point for deciding whether you are starting a new project, adopting an existing project, continuing work, asking for status, planning, reviewing, or validating work.

You do not need to learn any setup terminology. Describe what you need in plain English.

## Files To Upload

Upload these files to the ChatGPT Project knowledge area:

- `START_HERE.md`
- `01_RESOLVEOS_CORE.md`
- `02_RESOLVEOS_CONTEXT_AND_LOADING.md`
- `03_RESOLVEOS_ROLES.md`
- `04_RESOLVEOS_SKILLS_AND_WORKFLOWS.md`
- `05_RESOLVEOS_TEMPLATES.md`
- `06_RESOLVEOS_GOVERNANCE.md`

Do not upload `generate-resolveos-bundles.ps1`.

## How To Create A ChatGPT Project

1. Create a new ChatGPT Project.
2. Give it a clear project name.
3. Upload `START_HERE.md` and the six ResolveOS bundle files.
4. Paste the Project Instructions below into the project instructions field.
5. Start the first chat by describing the project or work you want help with.

## How To Paste Project Instructions

Copy the exact text in the Project Instructions section below.

Paste it into the ChatGPT Project instructions field without changing the wording.

## Project Instructions

```text
Always begin by loading and following 00-system/resolveos-entrypoint.md.

Do not bypass it.
```

## Start A New Project

Start with a short plain-English message, for example:

```text
I have an idea for a project and want help turning it into a clear plan.
```

ResolveOS should identify that this is a new project, ask only for missing essentials, and recommend the next useful action.

## Adopt An Existing Project

Provide the source you already have, for example:

```text
Here is my repo. I want ResolveOS to review what exists and help me work out what should happen next.
```

You can provide a GitHub repository, Notion workspace, Jira project, existing docs, business process, or partially complete project.

ResolveOS should preserve existing project state and use the project source of truth where available.

## Continue An Existing Project

Use a direct continuation request, for example:

```text
Continue this project. We were working on onboarding and need to know what comes next.
```

ResolveOS should use available project context before relying on memory, identify missing context if needed, and avoid pretending it knows current project state when it has not been loaded.

## Verify ResolveOS Is Working

ResolveOS is working when ChatGPT:

- starts by using `00-system/resolveos-entrypoint.md`
- classifies the type of interaction before answering
- loads the required uploaded files for that interaction
- uses your project source of truth when project-specific context is needed
- asks for missing context instead of inventing project facts
- gives clearly caveated general guidance only for low-risk questions
- stops when continuing would require unsupported project assumptions

If ChatGPT skips the entrypoint or asks you to choose setup files, check that all seven files were uploaded and that the Project Instructions text was pasted exactly.

## Source

These files are static upload snapshots from:

```text
https://github.com/simeonfab/ResolveOS
```

Source commit:

```text
747d2d2ab4456ddc7a55063875241c0d2d75d3a5
```

Uploaded ChatGPT Project files do not update automatically. Re-upload the refreshed files when ResolveOS is updated.
