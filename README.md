---
type: public_entrypoint
scope: global
owner: ResolveOS
version: 1.0.0
status: public-beta
---

# ResolveOS

ResolveOS helps you turn ideas, messy project context, existing work, and blocked projects into a clear plan of action.

It helps an AI assistant work out what state your project is in, what matters now, what is missing, what is blocked, which specialist support is useful, and what should happen next.

Use this README as the main human entrypoint for ResolveOS-beta.

## AI Entrypoint

For GitHub-aware AI tools, use this exact instruction:

```text
Use this repository as the ResolveOS source:
https://github.com/simeonfab/ResolveOS-beta

Always begin by reading and following:
00-system/resolveos-entrypoint.md

Do not bypass it.

If the entrypoint cannot be accessed, loaded, or followed, stop and report the limitation instead of proceeding from memory or making assumptions.

Follow any additional files referenced by the entrypoint.
```

The repository root is the default GitHub-aware usage path. The folder `chatgpt-project-export/` is only for fallback, offline, or upload-file use.

## When To Use ResolveOS

Use ResolveOS when you want help to:

- start a new project from an idea, goal, or rough notes
- continue a paused, stale, interrupted, or partially complete project
- adopt or review an existing repository, workspace, backlog, process, or documentation set
- identify the current objective, source of truth, risks, blockers, and next actions
- turn feedback, notes, requirements, or decisions into useful project structure
- get practical prompts, handoffs, implementation briefs, validation steps, or status summaries

ResolveOS should reduce the amount of project-management work pushed back onto you. It should ask for missing essentials when needed, but it should not dump framework decisions, file choices, or unnecessary admin back onto the user.

## Choose A Usage Mode

### 1. Default: Point An AI Tool At This Repository

Use this mode when your AI tool can read GitHub repositories or repository files directly.

Give the AI tool this repository and the instruction below:

```text
Use this repository as the ResolveOS source:
https://github.com/simeonfab/ResolveOS-beta

Always begin by reading and following:
00-system/resolveos-entrypoint.md

Do not bypass it.

If the entrypoint cannot be accessed, loaded, or followed, stop and report the limitation instead of proceeding from memory or making assumptions.

Follow any additional files referenced by the entrypoint.
```

This is the preferred mode. It uses the full ResolveOS file set in this repository, including:

- `00-system/`
- `01-context/`
- `02-roles/`
- `03-skills/`
- `04-templates/`
- `05-workflows/`
- `06-governance/`

GitHub-aware tools can read the repository directly and can use the latest repository state when instructed.

### 2. Fallback: Offline Or Upload-File Use

Use this mode only when your AI tool cannot read this GitHub repository directly.

See `chatgpt-project-export/README.md` for offline/upload fallback instructions.

The export folder contains summarized ChatGPT Project bundle files. Uploaded ChatGPT Project files do not auto-update. After a new release, re-upload the export folder README and bundle files if you use the upload-file mode.

## Start A New Project

Tell the AI what you want to build or achieve:

```text
I want to use ResolveOS for a new project. Here is the idea and what I want help with: ...
```

ResolveOS should classify the project, identify the objective, surface missing essentials, assess readiness, recommend the most useful next activity, and generate any needed prompt or handoff.

## Continue An Existing Project

Give the AI the current source of truth if you have it, such as a repository, Notion page, Jira board, current-focus note, handoff, or project documentation:

```text
Continue this project from the latest reliable context. Show where we are, what is blocked, and the practical plan forward.
```

ResolveOS should preserve the current project state before recommending changes. It should not restart from memory when reliable project context exists.

## Adopt Or Review An Existing Project

Use this when you already have a project and want ResolveOS to understand it:

```text
Here is my repository, workspace, backlog, or documentation. Help me understand what exists, what source of truth should be used, what is blocked, and what should happen next.
```

ResolveOS should inspect the existing structure, identify what appears authoritative, avoid inventing duplicate systems, and recommend the smallest useful next step.

## Get The Most Value

Give ResolveOS real project context where possible:

- repository links or files
- product goals, roadmap notes, tickets, or backlog items
- Notion, Jira, GitHub Issues, Azure DevOps, or other source-of-truth links
- current blockers, decisions, feedback, risks, validation notes, or handoffs
- what you want to achieve now

If you do not know the source of truth, say that. ResolveOS should help identify it.

ResolveOS should use your existing project structure and source-of-truth systems. It should not create random top-level docs, pages, folders, databases, or duplicate planning systems. When storing information, it should identify the information type, owner, existing location, and reason before writing.

## Recommended Team And Roles

ResolveOS may recommend a team for the current stage.

The team can be real people, you, specialist chats, AI assistants, coding agents, consultants, or a mix.

ResolveOS should recommend only the roles needed now, briefly explain why each role matters, and generate the controlling prompt or handoff when a specialist should act. If no specialist role is needed, it should say so.

User-facing role labels may be simpler than internal file names. For example, Product Strategy Lead, Technical Strategy Lead, Implementation Engineer, QA / Validation Lead, Business Analyst, and Feedback Curator map to existing ResolveOS roles, skills, or workflows. They do not create new roles.

## If The AI Is Not Following ResolveOS

If the AI skips setup, ignores the repository, asks you to choose internal files, or gives generic advice, paste this:

```text
Use this repository as the ResolveOS source:
https://github.com/simeonfab/ResolveOS-beta

Always begin by reading and following:
00-system/resolveos-entrypoint.md

Do not bypass it.

If the entrypoint cannot be accessed, loaded, or followed, stop and report the limitation instead of proceeding from memory or making assumptions.

Follow any additional files referenced by the entrypoint.
```

Then ask it to restart from the entrypoint and classify the interaction before answering.

## Testing ResolveOS On ResolveOS

ResolveOS can be used to manage ResolveOS work, including this public beta.

Use normal repository safety controls for self-testing:

- work on branches
- open pull requests for review
- do not commit directly to `main`
- do not auto-merge
- require human approval before merging

## Versions And Releases

Initial public beta version: `v1.0.0`.

For stable testing, use the latest release: `https://github.com/simeonfab/ResolveOS-beta/releases/latest`.

The `main` branch may contain the latest beta/current state.

GitHub-aware tools can read the repository directly and can use the latest repository state when instructed. ChatGPT Projects or other tools using uploaded files do not auto-update; re-upload the files in `chatgpt-project-export/` after a new release.

ResolveOS-beta package version is `v1.0.0`. Some internal framework files may still carry `version: 0.1`, `status: draft`, or `review_required: true` metadata to describe internal document maturity. That metadata does not mean the public beta package is unreleased; it means the reusable framework is usable for beta testing and still under validation.

Internal `source_files` metadata and inline extraction notes are historical provenance from the ResolveOS migration process. They are not loading instructions for GitHub-aware tools. Runtime loading is governed by `00-system/resolveos-entrypoint.md` and the files it references.
