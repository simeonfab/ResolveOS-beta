---
type: skill
scope: global
owner: ResolveOS
version: 0.1
status: draft
related_skills:
  - 03-skills/user-feedback-processing.md
  - 03-skills/completion-reporting.md
related_context:
  - 01-context/missing-context-behaviour.md
  - 01-context/context-loading-rules.md
related_governance:
  - 06-governance/source-of-truth-rules.md
  - 06-governance/architecture-decisions.md
review_required: true
---

# Information Architecture

## Purpose

Determine what information is, which storage model should own it, which system is authoritative, where it belongs, how to store it, and how to explain the storage decision.

Use this skill before ResolveOS writes to any documentation, workspace, knowledge-base, project-management, repository, or local storage tool.

This skill is about information architecture. It does not replace source-of-truth governance, project-specific documentation rules, feedback processing, ticket writing, decision logging, or external tool permissions.

## Core Principle

ResolveOS should classify information before deciding where to store it.

Do not assume durable information becomes a page.

Before storing information, ResolveOS must decide:

- information type
- storage model
- source-of-truth owner
- location
- execution

Documentation storage is one storage use case inside the broader information architecture decision. A page, child page, document, database record, ADR, ticket, comment, section, or temporary note should be selected because it fits the information type and source owner, not because the content feels durable.

## When To Use

Use this skill when the user asks to:

- save something
- store something
- put something in Notion
- capture feedback
- store risks, discovery items, validation findings, research notes, or decisions
- review an existing workspace, page set, documentation structure, database, folder, ticket group, or file structure
- create documentation from a conversation
- preserve a handoff, meeting output, implementation summary, decision, risk, research note, or project context
- write to a documentation, knowledge-base, workspace, project-management, repository, or local file tool

Use it before the storage tool is called, the file is created, an existing storage model is accepted, or a page hierarchy is chosen.

## Five-Stage Information Architecture Model

### Stage 1 - Information Classification

Determine what category the information belongs to.

Common categories include:

- project
- feature
- epic
- task
- decision
- risk
- feedback
- validation finding
- research item
- discovery item
- meeting output
- implementation context
- technical knowledge
- operating knowledge
- temporary note
- documentation
- roadmap item
- backlog item

ResolveOS should classify first.

Do not assume information becomes a page.

If more than one category applies, choose the primary category that determines ownership and storage model, then preserve secondary labels or links where useful.

### Stage 2 - Storage Model Selection

Determine what storage model should own the information.

Common storage models include:

- database record
- page
- child page
- section
- ADR
- GitHub document
- ticket
- comment
- temporary holding area

Repeatable record types should be evaluated for record or database storage before page creation.

Examples of repeatable record types:

- feedback
- risks
- validation findings
- research items
- discovery items
- backlog items
- tasks

Explicitly challenge this assumption:

```text
durable information = page
```

Durability means the information should be preserved. It does not decide whether the storage model is a page, database record, ADR, ticket, repository document, comment, or section.

When reviewing existing content, identify both:

- ideal storage model
- current storage model

Existing structure is evidence, not authority.

Do not preserve a page, database, file, folder, ticket, or section merely because it already exists.

Existing standalone pages should not be grandfathered automatically.

Repeatable or structured information must be evaluated as records or databases for both existing and future content.

### Stage 3 - Source-Of-Truth Selection

Determine ownership using `06-governance/source-of-truth-rules.md`.

Do not duplicate source-of-truth logic in this skill.

Possible owners include:

- Notion
- GitHub
- Jira
- Linear
- Confluence
- SharePoint
- Google Docs
- local repository
- project documentation system

Project-specific source-of-truth declarations override generic tool preferences.

### Stage 4 - Location Selection

Only choose location after storage model selection.

Determine the specific home:

- existing page
- existing database
- existing folder
- existing section
- existing project area
- child page
- justified new page
- justified new database

Preference order:

1. existing structure
2. child structure
3. new structure only if justified

Existing structure is preferred only after it has been evaluated against the information type and ideal storage model.

New top-level pages, documents, files, folders, or database structures should be created only when the content represents a new major project, product area, system, database, or durable knowledge domain.

Routine feedback, notes, decisions, risks, meeting outputs, implementation context, discovery items, research items, validation findings, and conversation summaries should usually be stored inside the relevant existing structure.

If current volume is too low to justify a database, state whether the current page, section, file, or folder structure is:

- a temporary lightweight model with a migration trigger
- the intended long-term model

If keeping existing pages temporarily, give a clear reason and name the trigger for migration to a better model.

### Stage 5 - Storage Execution

Store the information using the selected model and location.

Then explain:

```text
Stored under [location] because [reason].
```

The explanation should include:

- information type
- storage model
- source owner
- location choice

Do not claim storage happened unless the write actually succeeded.

## Existing Structure Review

When reviewing existing workspaces or documentation structures, ResolveOS must not assume current structure is correct.

Use this review sequence:

1. Classify the information.
2. Determine the ideal storage model.
3. Identify the current storage model.
4. Compare current vs ideal.
5. Recommend one of:
   - keep as-is
   - move under a better parent
   - convert to database or record
   - wrap with a record while retaining the detailed page
   - merge into an existing section
   - mark historical or superseded
   - keep temporarily with a migration note
6. Explain why.

Existing pages, databases, files, folders, tickets, or sections are evidence of current state, not proof of correct information architecture.

Do not grandfather existing pages just because they are already present.

If an existing page is the wrong storage model, recommend one of:

- convert to database or record
- wrap with a database record and retain the page as detail
- move under the correct parent or section
- mark as historical or superseded
- keep temporarily with a clear migration note

For repeatable, structured, or likely-to-recur content, evaluate record or database storage for existing content and future content.

## Documentation Storage

Documentation storage remains covered by this skill, but documentation is a storage decision, not an automatic destination.

Before creating documentation, ResolveOS should classify the information and select the storage model.

Preserve these documentation-storage behaviours:

- hierarchy discipline
- source-of-truth discipline
- update existing vs create new decisions
- fallback behaviour
- reporting behaviour
- Notion guidance

ResolveOS should not create unnecessary top-level pages, documents, files, folders, or database structures.

Before writing to any external documentation or workspace tool, ResolveOS must identify:

- source of truth
- storage model
- parent location
- update existing vs create new
- whether top-level storage is justified

## Storage Types

Choose the smallest storage shape that preserves context and ownership:

- append to existing page or section
- update existing page
- create child page under existing parent
- create database record
- create file in an existing folder or path
- create ticket or comment
- create an ADR for durable architecture decisions
- create a new top-level page, file, or database only when justified
- use fallback or temporary storage if the intended destination is inaccessible

Fallback storage must be labelled as fallback or temporary and should name the intended destination that was unavailable.

## Tool Model Guidance

ResolveOS should not merely recommend tools. It should know how to use them well.

Common ownership patterns:

- Notion: product context, strategy, decisions, risks, validation, feedback, discovery, research, and operating knowledge.
- Jira or Linear: execution tracking.
- GitHub: code, technical docs, implementation evidence, ADRs, and repo-owned context.
- Confluence, SharePoint, or Google Docs: organisational documentation where they are the declared source of truth.

These are defaults, not hard rules. Project-specific source-of-truth declarations override generic tool preferences.

When recommending a tool, also recommend the information architecture model that prevents clutter: databases for repeatable records, pages for durable narrative context, child pages for durable subtopics, sections for extensions of existing topics, tickets for execution work, comments for review commentary, and temporary holding areas only when the intended destination is inaccessible.

## Non-Delegation Behaviour

Do not ask the user where to store something if the correct information type, storage model, source owner, and location can be inferred.

Do not ask the user to design the information architecture unless it materially affects ownership or workflow.

If uncertain, propose the best model and location, then explain the assumption.

Ask only the smallest necessary question.

If an information architecture or storage issue is surfaced, provide the practical resolution path.

## Notion-Specific Behaviour

Notion is an example implementation of the broader information architecture model. It must not become the dominant model.

Treat Notion as a structured workspace, not a flat page dump.

ResolveOS must determine storage model before deciding page hierarchy.

A discovery item is not automatically a page.

A risk is not automatically a page.

A feedback item is not automatically a page.

A decision is not automatically a page.

Before writing to Notion:

- classify the information first
- identify whether any current page, database, or hierarchy is evidence only or the correct model
- evaluate database records for repeatable record types before page creation
- search or fetch the relevant hub, parent page, or database before writing
- do not create top-level Notion pages by default
- use existing pages only when they match the evaluated storage model
- append to an existing page when content extends an existing topic
- create a child page under the relevant parent when content is a durable sub-topic and a page is the right storage model
- use databases for repeated structured records such as feedback, risks, decisions, validation findings, tasks, discovery items, or research notes
- use comments only for review or commentary, not permanent structured storage
- if the intended database or page is inaccessible, report that and use the best fallback
- if creating fallback storage, label it clearly as fallback or temporary

If ResolveOS recommends Notion, it should understand Notion workspace hygiene:

- hubs
- child pages
- databases for repeatable records
- preserved hierarchy
- no root-level clutter

## Behaviour Examples

### Feedback

User:

```text
Save this feedback.
```

Expected handling:

```text
Information type: feedback
Storage model: database record or feedback record before considering a page
Source owner: project feedback source of truth
Location: existing feedback database, tracker, page section, or approved fallback
```

### Discovery Item

User:

```text
Save COMBO-INTEL-001.
```

Expected handling:

```text
Information type: discovery item
Storage model: evaluate discovery record, database, GitHub markdown, or discovery section before page creation
Source owner: declared discovery or project documentation source
Current structure: if this already exists as a standalone page, treat that as current-state evidence, not approval
Location: selected only after comparing current vs ideal storage model
```

### Existing Discovery Pages

User:

```text
COMBO-INTEL-001 and COMBO-INTEL-002 already exist as standalone discovery pages.
```

Expected handling:

```text
COMBO-INTEL-001 and COMBO-INTEL-002 are existing standalone discovery pages. Their current existence does not prove the storage model is correct. They should be re-evaluated as discovery/research records. With only two items, a dedicated database may be premature, so the safe interim model may be a Discovery / Research section with the pages nested beneath it and labelled as discovery records. If more discovery/spike items are added, convert to a Discovery database or wrap each detailed page with a structured record.
```

### Implementation Handoff

User:

```text
Create documentation from this implementation handoff.
```

Expected handling:

```text
Information type: implementation context or technical documentation
Storage model: selected before assuming a documentation page
Source owner: repository, project docs, handoff system, or declared documentation source
Location: existing project/docs/source-of-truth area where possible
```

### Risks

User:

```text
Store these risks.
```

Expected handling:

```text
Information type: risk
Storage model: risk records or database before page creation
Source owner: project risk or planning source of truth
Location: existing risk database, tracker, planning source, or approved fallback
```

## Good / Bad Examples

Bad:

```text
User: "We've just discussed this. Save it somewhere."
AI creates seven new top-level Notion pages.
```

Why bad:

- workspace clutter
- context fragmentation
- user cleanup
- broken source-of-truth discipline
- extra admin
- assumes durable information means page
- treats existing pages as automatically valid because they already exist

Good:

```text
I classified this as product feedback. The right storage model is a feedback record because this is a repeatable record type. I found the Resolve Product Hub feedback database and stored it there. I did not create a top-level page because this does not represent a new product area.
```

## Anti-Patterns

Do not:

- assume durable information becomes a page
- assume existing structure is correct because it already exists
- grandfather existing standalone pages without evaluating current vs ideal storage model
- create random top-level pages, documents, files, folders, or databases
- use Notion as a flat page dump
- create a new source of truth when an existing one exists
- split one routine conversation into many standalone documents
- ask the user to design information architecture when ResolveOS can infer it safely
- treat tool recommendation as enough without explaining how the tool should be used
- use comments as permanent structured storage
- hide fallback or temporary storage
- claim content was stored, linked, ticketed, or documented unless it was

## Related Governance

- `06-governance/source-of-truth-rules.md`
- `06-governance/architecture-decisions.md`

## Related Context

- `01-context/missing-context-behaviour.md`
- `01-context/context-loading-rules.md`

## Related Skills

- `03-skills/user-feedback-processing.md`
- `03-skills/completion-reporting.md`

## Deferred Items

Deferred because they are project-specific or would overbuild this skill:

- tool-specific database schemas
- Notion workspace templates
- Confluence, SharePoint, or Google Docs templates
- automatic workspace cleanup
- project-specific taxonomy
- migration of existing documentation structures

## What This Skill Must Not Do

This skill must not:

- create a second overlapping storage skill
- make Notion the only supported model
- create duplicate source-of-truth systems
- replace project-specific documentation rules
- replace feedback processing, ticket writing, or decision logging
- impose a global database schema
- create external tool structures without approval
