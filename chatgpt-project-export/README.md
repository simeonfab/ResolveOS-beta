---
type: export_entrypoint
scope: global
owner: ResolveOS
version: 1.0.0
status: public-beta
generated: true
source_repository: https://github.com/simeonfab/ResolveOS
source_commit: fcde866ede5144d996a0e4bd2c34ccbcf010c524
---

# ResolveOS Offline / Upload Fallback

Use these files only when the AI tool cannot read the GitHub repo directly.

GitHub-aware usage should use the root `README.md` and the full file set in the repository instead.

## What This Folder Contains

This folder contains summarized export bundles for ChatGPT Projects or other upload-file workflows.

Upload this folder's README plus the six bundle files:

- `README.md`
- `01_RESOLVEOS_CORE.md`
- `02_RESOLVEOS_CONTEXT_AND_LOADING.md`
- `03_RESOLVEOS_ROLES.md`
- `04_RESOLVEOS_SKILLS_AND_WORKFLOWS.md`
- `05_RESOLVEOS_TEMPLATES.md`
- `06_RESOLVEOS_GOVERNANCE.md`

These are summarized export bundles. They are a fallback for tools that cannot read the full repository.

## Project Instructions

Paste this exact text into the ChatGPT Project instructions field:

```text
Always begin by loading and following 00-system/resolveos-entrypoint.md.

Do not bypass it.
```

## Starting

After uploading the files and setting the instructions, start with a plain-English message:

```text
I want to use ResolveOS for this project. Here is what I have and what I want help with: ...
```

ResolveOS should identify whether your project is new, existing, or already in progress. It should ask only for missing essentials and recommend practical next actions.

## Updating Uploaded Files

Uploaded ChatGPT Project files do not auto-update.

After a new ResolveOS-beta release, re-upload this folder's README and the six bundle files if you use offline/upload mode.
