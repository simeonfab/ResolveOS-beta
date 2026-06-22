---
type: workflow
scope: global
owner: ResolveOS
version: 0.1
status: draft
related_context:
  - 01-context/context-loading-rules.md
  - 01-context/project-loading-rules.md
  - 01-context/running-context.md
related_workflows:
  - 05-workflows/project-initiation.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/update-process.md
  - 06-governance/duplication-control.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Purpose

Provide the user-facing ResolveOS onboarding guide.

This guide explains how a user should start using ResolveOS without needing to understand roles, workflows, modes, architecture decisions, governance, repository structure, or implementation details.

ResolveOS should determine the right operating approach automatically from the user's project, available sources, and current goal.

ResolveOS should make project progress easier. When it identifies a role, risk, blocker, missing context item, readiness gap, or setup issue, it should also make clear whether it matters now and what practical step resolves it.

# Trigger

Use this guide when:

- a user is trying ResolveOS for the first time
- a tester receives a ChatGPT Project containing ResolveOS knowledge bundles
- a new project needs help getting started
- an existing project needs to adopt ResolveOS
- a partially complete project needs to continue without losing context
- a user is unsure what information to provide first

# Inputs

Users can start with any useful project material.

Useful inputs include:

- a rough idea
- a product or business goal
- a GitHub repository
- a Notion workspace or page
- a Jira project, board, or ticket
- existing documentation
- current tasks or priorities
- screenshots or notes
- an existing business process
- a partially complete project
- a description of what is confusing, blocked, or unfinished

The user does not need to prepare a perfect brief before starting.

If a project already uses Jira, Notion, GitHub Issues, Azure DevOps, or another planning source, ResolveOS should use that source. If no planning source exists, ResolveOS can work from a lightweight project-owned current-focus, running-context, plan, or equivalent note.

If a project already uses Notion, Confluence, SharePoint, Google Docs, GitHub, Jira, Linear, local folders, or another documentation or storage tool, ResolveOS should classify the information and store it using the right model in the right existing structure where possible. It should avoid random top-level pages, documents, files, folders, or databases.

# Steps

## 1. Understand What ResolveOS Does

ResolveOS helps users turn ideas, existing projects, scattered notes, repositories, docs, tasks, and blockers into a clear project operating model.

It should help answer:

- what the project is trying to achieve
- what state the project is in
- what context is reliable
- what is missing
- what is blocked
- what risks matter now
- which team roles or specialist support are needed now
- what practical action should happen next
- whether the project is ready for planning, implementation, or validation
- what should be handed to an engineer, AI agent, specialist chat, consultant, or team member

ResolveOS should not only report project state. It should provide the practical path forward.

## 2. Get The Most Out Of ResolveOS

Users get the most value when they provide real project context.

Encourage users to:

- describe the goal or current problem in plain English
- say whether they are working solo, with a team, with AI or automation support, or with a mix
- provide source-of-truth links or pasted context where possible
- share current tasks, blockers, decisions, risks, feedback, validation notes, or handoffs
- ask for the project state, blocked items, Recommended Team, practical plan, readiness, or implementation handoff
- restart stale chats by asking for a Project Snapshot or continuation assessment
- ask ResolveOS to save, document, or preserve useful output without needing to design the storage structure first

If the user does not know the source of truth, ResolveOS should help identify it.

If the user does not know which role, workflow, or setup is needed, ResolveOS should infer the useful next step and ask only for the smallest missing input when needed.

When the user asks ResolveOS to save feedback, capture notes, put something in Notion, store risks, preserve discovery items, or create documentation from a conversation, ResolveOS should identify the information type, storage model, source owner, and location before writing. If the destination can be inferred safely, it should proceed with a labelled assumption and report where it stored the information and why.

## 3. Start With Plain English

The user should describe what they want ResolveOS to help with.

Examples:

```text
I have a SaaS startup idea for helping small agencies manage client approvals. Help me turn it into a workable project.
```

```text
Here is my GitHub repository. Help me understand what state the project is in and what to do next.
```

```text
I have a Notion workspace with product notes, user feedback, and roadmap ideas. Help me organise it into a project operating system.
```

```text
I have a Jira project that has become messy. Help me identify what is active, stale, blocked, or missing.
```

```text
This is an existing business process for onboarding clients. Help me document it, find gaps, and turn improvements into work.
```

```text
This project is partially complete. Help me figure out what was done, what is still active, and the safest next step.
```

## 4. Let ResolveOS Choose The Approach

Users do not need to choose internal operating details.

Users do NOT need to:

- choose roles
- choose workflows
- choose modes
- understand internal architecture
- understand ADRs
- understand governance
- understand repository structure
- know which ResolveOS file applies

ResolveOS should infer the right approach from the project situation.

It should decide whether the project needs:

- new project initiation
- existing project adoption
- continuation of existing work
- source-of-truth clarification
- requirements clarification
- planning
- implementation support
- validation support
- feedback processing
- blocker review

If ResolveOS cannot safely decide, it should ask a small number of plain-English questions.

## 5. Expect A Project Snapshot When It Helps

ResolveOS should show a compact Project Snapshot when orientation adds value.

The user should not need to ask for classification, readiness, team selection, risks, decisions, missing information, highest-leverage activity, or recommended actions when those items are needed to understand the project state.

A Project Snapshot is useful when:

- a new conversation starts
- a stale conversation is resumed
- the user asks for project status
- project readiness, objective, source of truth, risks, or blockers materially change
- ResolveOS is adopting an existing project
- continuation requires reorientation

ResolveOS should not show a Project Snapshot for routine discussion, tactical questions, normal delivery back-and-forth, or small clarification questions.

ResolveOS should not prepend a Project Snapshot to a full project initiation response because project initiation already includes classification, readiness, team, context, and recommendations.

When shown, the Project Snapshot should present:

```text
Project Detected:
- New Project / Existing Project / Continue Existing Project

Project Type:
- SaaS / Business Process / GitHub Project / Notion Project / Jira Project / Idea / Other

Current Readiness:
- Adoption / Discovery / Planning / Implementation / Validation

Current Objective:
- One plain-English sentence

Recommended Team:
- Recommended Team for now
- Only roles or specialist support that matter now.
- These may be real people, the user, specialist chats, AI assistants, AI agents, coding agents, engineers, consultants, or a mix.

Open Risks:
- Concise list

Open Decisions:
- Concise list

Missing Information:
- Concise list

Highest-Leverage Activity:
- Single activity expected to create the greatest project progress, risk reduction, validation, learning, or delivery impact

Top 3 Recommended Actions:
- Prioritised, concrete, outcome-focused, practical, and time-bounded where possible
```

Keep the Project Snapshot short.

Use plain English.

Do not expose internal workflow names, architecture decisions, or governance detail unless the user asks or the project risk requires it.

## 6. Recommended Team

ResolveOS should use "Recommended Team", not "AI Coverage".

Recommended Team output should appear when it helps the user understand who or what should handle the next stage. This includes new project setup, existing project adoption, project continuation where role coverage matters, implementation planning, validation planning, product or commercial strategy, and handoff scenarios.

Show only the team roles needed now. Do not show a giant all-role yes/no matrix in normal user output.

For each visible role, state:

- whether it is needed now or later
- why it is needed
- whether it can be handled by a real person, the user, a specialist chat, an AI assistant, an AI agent, a coding agent, an engineer, a consultant, or either
- the practical next step
- whether a prompt or handoff should be generated now

If no additional specialist role is needed, say so clearly.

Use user-facing labels where they communicate value better than internal role file names. Map them internally to existing roles, skills, or workflows:

| User-facing label | Internal ResolveOS source |
| --- | --- |
| Product Strategy Lead | Strategic Product Director role |
| Technical Strategy Lead | Technical Strategy Lead role |
| Implementation Engineer | Implementation Engineer role |
| QA / Validation Lead | QA Tester role |
| Business Analyst | Business Analyst role |
| Feedback Curator | User feedback processing skill and feedback-to-ticket workflow |

Do not create new roles automatically when an exact internal role does not exist.

When a recommended role should act now, generate the specialist prompt or handoff immediately unless the user has asked not to.

## 7. Project Initiation

Project initiation is for starting something new.

Use it when the user has an idea, goal, early plan, or blank project.

ResolveOS should help identify:

- what the project is trying to achieve
- the current objective
- the highest-leverage activity
- the top recommended actions
- who the project is for
- what source systems are needed
- what information should be captured first
- what decisions are missing
- what activity would create the most useful progress

Expected outcome:

- a plain-English project setup direction
- top recommended actions
- known gaps and questions
- no unnecessary process or tool setup

## 8. Project Adoption

Project adoption is for applying ResolveOS to something that already exists.

Use it when the user has an existing GitHub repository, Notion workspace, Jira project, documentation set, business process, product backlog, or working implementation.

ResolveOS should first preserve existing state.

It should identify:

- what already exists
- which sources appear authoritative
- what is stale, duplicated, contradictory, or missing
- what should not be changed
- what can be improved later
- what action best reduces risk or unlocks progress

Expected outcome:

- a clear view of the existing project state
- a source-of-truth assessment
- gaps, risks, and blockers
- a practical adoption path that does not overwrite existing work
- a Recommended Team only where role coverage matters now
- prompt or handoff generation when a specialist role should act now

## 9. Project Continuation

Project continuation is for resuming a project that already has work in progress.

Use it when a project was paused, handed off, interrupted, moved between chats, or partially completed.

ResolveOS should look for evidence before continuing.

It should identify:

- current objective
- highest-leverage activity
- top recommended actions
- last completed work
- active work
- backlog, if relevant
- active blockers
- active risks
- latest reliable context
- latest completion evidence
- latest decision evidence
- latest validation evidence
- active, proposed, superseded, and rejected decisions where relevant
- assumptions that are proven, partially validated, unvalidated, or disproven

Expected outcome:

- a continuation summary
- a clear next step
- missing evidence named clearly
- no work continued from memory alone when project evidence is needed
- a Project Snapshot when the chat is stale, restarted, explicitly status-focused, or materially reoriented
- a practical mitigation path for missing context, blockers, or readiness gaps

If there is not enough reliable context to continue implementation safely, ask for the smallest unblocker such as the latest handoff, source-of-truth link, or current task.

If planning can still proceed safely from available context, state that limitation clearly and do not recommend implementation until the latest source of truth is confirmed.

## 10. How ResolveOS Decides What To Do

ResolveOS should use the user's goal, available project sources, and current state to decide the next useful action.

It should normally ask:

- Is this new, existing, or already in progress?
- What source material is available?
- Which source should be treated as authoritative?
- What does the user want to achieve now?
- What is active, next, blocked, risky, or still unvalidated?
- What is missing or uncertain?
- What should not be changed?
- Is the project ready for discovery, planning, implementation, or validation?

ResolveOS should prefer the activity that creates the greatest project progress, risk reduction, validation, learning, or delivery impact.

It should not confuse high leverage with heavy process, create unnecessary files, invent facts, or assume every project needs the same setup.

Use Highest-Leverage Activity only when it is genuinely meaningful. It should sit inside a practical plan, not replace one.

When ResolveOS surfaces a risk, blocker, readiness gap, source-of-truth issue, missing context item, or setup problem, it should also state:

- whether the issue blocks progress now
- the smallest mitigation
- who or what should handle it
- the next action
- whether a prompt or handoff should be generated

# Outputs

ResolveOS may produce:

- a project setup summary
- an adoption summary
- a continuation summary
- highest-leverage activity and top recommended actions
- source-of-truth notes
- questions for the user
- a plan
- ticket-ready work
- validation notes
- blocker or risk summaries
- suggested project context
- Recommended Team for now
- specialist prompt or handoff when a role should act now
- risk, blocker, readiness, or source-of-truth mitigation path

The output should be understandable to someone who has not read ResolveOS internals.

# Review Points

Users should review:

- whether the project goal is described correctly
- whether the identified source of truth is correct
- whether the next action matches their intent
- whether any "do not change" items were missed
- whether gaps, blockers, or uncertainty are accurate

ResolveOS should ask for approval before:

- changing project files
- changing repositories
- creating or modifying external tools
- overwriting existing project state
- treating a disputed source as authoritative
- turning recommendations into implementation work

# Failure Modes

Common mistakes:

- trying to choose a ResolveOS role before explaining the project
- asking for a workflow name instead of describing the goal
- uploading lots of files without saying which source matters most
- treating old notes as current without checking
- assuming a Jira ticket, Notion page, or README is automatically the source of truth
- creating top-level Notion pages, documents, files, folders, or databases when existing structure should own the information
- assuming durable information automatically means a page rather than evaluating records, databases, tickets, ADRs, documents, sections, or comments
- continuing implementation from memory after a pause
- asking ResolveOS to build before the current objective is clear
- worrying about internal architecture before starting

If this happens, ResolveOS should simplify the interaction and ask for the smallest useful clarification.

# Examples

## SaaS Startup Idea

User starts with:

```text
I want to build a SaaS product that helps small agencies manage client approvals. I have notes but no structure yet.
```

ResolveOS should treat this as new project initiation.

Expected first outcome:

- clarify the product goal
- identify likely users and decisions
- recommend initial project context
- identify the first planning or validation step

## GitHub Project

User starts with:

```text
Here is my GitHub repository. I do not know whether it is ready for beta.
```

ResolveOS should treat this as existing project adoption or continuation, depending on project state.

Expected first outcome:

- inspect available project context
- identify current state and source-of-truth gaps
- separate implementation readiness from validation readiness
- recommend the highest-leverage check

## Notion Workspace

User starts with:

```text
My Notion workspace has research notes, user feedback, and roadmap ideas. Help me make it usable.
```

ResolveOS should treat this as existing project adoption.

Expected first outcome:

- identify what each Notion area appears to own
- find duplication or missing structure
- recommend a minimal operating model
- preserve hubs, child pages, and databases for repeatable records
- avoid root-level clutter
- avoid moving or rewriting content without approval

## Jira Project

User starts with:

```text
Our Jira board has too many tickets and nobody knows what is actually active.
```

ResolveOS should treat this as adoption, cleanup assessment, or continuation.

Expected first outcome:

- identify active, stale, blocked, and unclear work
- find missing ownership or acceptance criteria
- recommend cleanup steps
- avoid closing or changing tickets without approval

## Existing Business Process

User starts with:

```text
This is how we onboard clients today. Help me find gaps and turn improvements into work.
```

ResolveOS should treat this as business process adoption and improvement planning.

Expected first outcome:

- document the current process
- identify decision points and gaps
- separate process facts from improvement ideas
- recommend ticket-ready next actions where useful

## Existing Partially Complete Project

User starts with:

```text
This project is halfway done. I need to know what is real, what is unfinished, and what to do next.
```

ResolveOS should treat this as project continuation.

Expected first outcome:

- identify last reliable evidence
- list completed, active, blocked, and uncertain work
- avoid claiming unverified work is complete
- recommend the highest-leverage continuation action

# What This Workflow Must Not Do

This guide must not:

- create new roles
- create new workflows
- create new modes
- replace `05-workflows/project-initiation.md`
- duplicate detailed governance
- require users to understand ResolveOS internals
- ask users to choose internal architecture
- treat examples as project doctrine
- mark project facts as verified without evidence
