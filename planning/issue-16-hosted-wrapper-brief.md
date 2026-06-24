---
type: plan
scope: project
owner: ResolveOS
version: 0.1
status: draft
source_project: ResolveOS
source_files:
  - https://github.com/simeonfab/ResolveOS-beta/issues/16
related_context:
  - 00-system/resolveos-entrypoint.md
  - 03-skills/information-architecture.md
related_governance:
  - 06-governance/source-of-truth-rules.md
review_required: true
---

# Issue 16 Hosted Wrapper Product Brief

## Purpose

Preserve the product and design brief for GitHub Issue 16: monetising ResolveOS through a hosted frontend wrapper.

This brief captures the current product direction for turning the Issue 16 idea into a practical first workflow prototype without overbuilding ResolveOS, prematurely committing to SaaS, or losing the user-centred product thinking developed during Sprint 001 discovery.

## Status

Draft product discovery brief.

This is not an implementation ticket.

This is not approval to build the frontend, rewrite ResolveOS, regenerate bundles, change README, change the AI entrypoint, add accounts, create a SaaS platform, or expand the framework.

## Source Context

Issue 16 proposes monetising ResolveOS through a hosted frontend or polished wrapper. The wrapper would make ResolveOS easier for customers to use by taking the user's input, attaching the appropriate ResolveOS prompt/context behind the scenes, sending the combined prompt through an API call, and returning a clean user-facing result.

The underlying ResolveOS framework may remain open source, while the monetised product could become the convenience layer: a simpler, faster, cleaner way for customers to interact with ResolveOS without needing to manage uploaded files, prompt setup, routing, or process complexity themselves.

Current open questions from Issue 16 include:

- Which customer segment values the convenience layer most?
- What is the first paid workflow or wrapper to test?
- Should the frontend be generic, role-specific, project-type-specific, or customer-specific?
- What data/storage model is needed behind the frontend?
- What remains open source versus hosted/proprietary?
- What price point validates willingness to pay for convenience?

## Current Working Interpretation

The next step is not to build a generic ResolveOS frontend.

The next step is to define and test a first workflow prototype that helps a user bring messy project context into ResolveOS and receive a clear, useful, presentable path to execution.

The first workflow should be:

```text
Dump everything -> ResolveOS makes sense of it -> user corrects it -> ResolveOS asks only what matters -> user gets a clean execution path and stakeholder-ready roadmap.
```

This should feel less like a chatbot report and more like a guided onboarding and project-shaping experience.

## Product Direction

The hosted wrapper should hide ResolveOS setup friction and make project context intake easy.

The user should not need to understand:

- ResolveOS files
- AI entrypoint routing
- internal interaction classifications
- role-loading rules
- governance files
- bundle upload requirements
- prompt composition
- missing-context rules

The product should help the user:

- bring in messy context
- extract useful context from previous AI chats
- add explicit project sources such as GitHub, Notion, documents, roadmaps, and feedback
- confirm what ResolveOS understood
- correct or reframe the project
- answer only context questions that matter
- understand what can safely be assumed
- receive a practical path to execution
- see a clean roadmap that feels shareable or presentable
- continue from the output without needing to invent the next prompt

## Target User For First Prototype

The first target user should be a product manager or product-minded builder with an existing messy project.

They may have:

- existing ChatGPT conversations
- scattered Notion docs
- GitHub repository links
- GitHub issues or PRs
- Google Docs
- PDFs
- rough notes
- a half-built prototype
- a vague roadmap
- context in their head
- old AI outputs
- unclear next steps
- uncertainty about what should be built first

This target user is useful because they are likely to understand project context, but still experience the pain of scattered information, weak continuity, and unclear execution direction.

## First Prototype Scenario

The first scenario should be an existing messy project.

The user arrives with a hodgepodge of context: ideas, links, old AI chats, possible GitHub/Notion/docs, and uncertainty about what the project actually needs next.

The prototype should show that ResolveOS can turn this messy input into:

- a clear interpretation of the project
- an editable project understanding
- a clean context-needed layer
- a practical path to execution
- a stakeholder-ready roadmap visual
- useful continuation options

## Core Product Promise

```text
Bring everything in. ResolveOS will turn it into a clear path to execution.
```

Supporting promise:

```text
Messy is fine. Paste notes, ramble, explain the idea badly, add wild thoughts, drop links, or copy in old AI chats. The more useful context you give, the less ResolveOS has to guess.
```

## Product Experience Principles

### Let The User Dump Everything

The first experience should not feel like a rigid form.

The user should feel comfortable dumping all the project context they have, including rough thoughts, wild ideas, confusion, old notes, AI chat outputs, links, and partially formed plans.

Long term, the user should be able to physically have a conversation with the product and let all of their word-vomit spill into it so ResolveOS can start to organise it.

For the first prototype, this can be represented by a large conversational context box plus explicit source-capture areas.

### Reduce Context Friction

The product should actively help users bring context in.

It should not expect users to know what useful project context looks like.

The product should make it clear that useful context can include:

- old AI chats
- Notion pages
- GitHub repositories
- GitHub issues
- GitHub pull requests
- README files
- Google Docs
- PDFs
- design files
- screenshots
- roadmaps
- backlogs
- customer/user feedback
- technical notes
- previous AI outputs
- business notes
- stakeholder notes
- anything the user does not want forgotten

### Separate User Project Information From ResolveOS Operating Needs

Do not dump every missing-context item into the user-facing project output.

There should be a clear separation between:

1. what ResolveOS understands about the user's project
2. what ResolveOS needs to help properly
3. what ResolveOS can safely assume for now
4. what is not needed yet

This separation should reduce cognitive load and make missing context feel manageable rather than bureaucratic.

### Keep Internal Classification Conversational

Project classification can happen internally, but should not be presented as internal ResolveOS terminology unless useful.

Avoid user-facing language like:

```text
Interaction type: Existing Project Adoption.
```

Prefer conversational orientation:

```text
You already have project context, so I’ll treat this as an existing project that needs organising rather than a brand-new idea.
```

### Replace Formulaic Actions With A Path To Execution

The experience should not centre on a formulaic "Top 3 Recommended Actions" block.

Top actions may still exist, but they should sit inside a broader path to execution.

The output should answer:

- What should we focus on now?
- Why does this come first?
- What is the next meaningful milestone?
- What path gets us there?
- What decisions matter before we go further?
- What does the longer-term roadmap look like?
- Which parts of the roadmap are more or less certain?

### Make The Roadmap A Product Moment

The roadmap is not just a planning artifact.

It is the moment where the user sees that their messy project context has been transformed into something clear, structured, clean, and nearly presentable.

The long-term quality target is that the roadmap should be clean enough to show to a stakeholder, client, founder, investor, manager, shareholder, or team member.

For the prototype, the roadmap can be low-fidelity, but the product direction should be visual, polished, and presentation-ready.

### Click-Led Continuation

The user should not always need to write another prompt.

After the roadmap, the product should offer clear continuation cards the user can click.

The user can still type freely if they want, but they should be able to continue by selecting an obvious next step.

## Six-Screen Lo-Fi Prototype Flow

### Screen 1 - Bring Everything In

#### Headline

```text
Bring everything in. ResolveOS will turn it into a clear path to execution.
```

#### Subtext

```text
Paste notes, ramble, explain the idea badly, add wild thoughts, drop links, or copy in old AI chats. Messy is fine. The more useful context you give, the less ResolveOS has to guess.
```

#### Primary Input Area

Label:

```text
Tell ResolveOS what is in your head.
```

Placeholder:

```text
Describe the project however you want. You can be messy. Include the idea, what you are trying to do, what is confusing, what exists already, what you are excited about, what you are worried about, and anything you do not want forgotten.
```

This should feel like a conversational dump area, not a strict form.

Long-term direction: this may become a chat-first intake where the user talks to ResolveOS naturally before the system organises the project.

#### Desired Outcome

The product should explicitly ask what the user wants from the session, because this sets the direction.

Label:

```text
What do you want from this session?
```

Options:

- Understand and organise the project
- Decide what to do next
- Create a roadmap
- Prepare a prototype
- Validate the idea
- Turn this into a build plan
- Make this presentable to others
- Continue from previous work
- I’m not sure yet

Optional free-text field:

```text
A good result from this session would be...
```

#### Pull Context From Existing AI Chats

The product should provide an explicit copyable prompt that users can paste into old ChatGPT, Claude, Gemini, or other AI chats to extract context.

Instruction:

```text
Already used ChatGPT, Claude, Gemini, or another AI tool for this project? Paste this into those chats, then copy the response back here.
```

Copyable prompt:

```text
I’m moving this project into ResolveOS. Please summarise everything important from this conversation so another AI system can understand the project. Include: project goal, target users, current state, decisions made, open questions, assumptions, blockers, useful context, and anything that should not be lost. Do not add new ideas unless clearly labelled as suggestions.
```

Suggested button:

```text
Copy context extraction prompt
```

Follow-up input area:

```text
Paste AI chat summaries here.
```

#### Add Project Sources

The product should make source capture explicit.

Instruction:

```text
Add any project sources you already have. You can paste links, copied content, notes, screenshots, or summaries.
```

Prompt users to include:

- Notion pages or workspace links
- GitHub repositories
- GitHub issues
- GitHub pull requests
- README links
- Google Docs
- PDFs
- uploaded documents
- design files
- screenshots
- roadmaps
- backlogs
- user/customer feedback
- technical notes
- previous AI outputs
- anything else ResolveOS should know

#### Primary Action

```text
Build my project path
```

### Screen 2 - Your Project As I Understand It

#### Headline

```text
Here’s what ResolveOS understands so far.
```

#### Purpose

This screen builds trust by showing the user what ResolveOS believes the project is before it starts recommending direction.

The user must be able to correct the interpretation.

#### Sections

##### Project Summary

Plain-English summary of the project.

##### Intended Outcome

What success appears to mean.

##### Who It Is For

Likely users, buyers, beneficiaries, stakeholders, or audience.

##### Current State

Where the project appears to be now.

Possible states:

- early idea
- existing messy project
- validation stage
- prototype planning
- build in progress
- project rescue
- commercialisation
- continuation after pause

Do not present these as rigid internal labels. Use conversational wording.

##### What Already Exists

Known docs, repos, notes, decisions, outputs, evidence, blockers, assumptions, feedback, backlog items, or prototypes.

##### Main Uncertainty

The biggest unknown that could change the plan.

#### User Controls

- Confirm this is right
- Edit summary
- Add missing context
- Reframe the project
- This is wrong

#### Product Note

The user correction flow is important. If the user corrects what ResolveOS understood, that correction should be treated as high-priority project context.

### Screen 3 - Context Needed

#### Headline

```text
Context Needed
```

Keep the title short and obvious.

#### Purpose

This screen separates ResolveOS operating needs from the user's project summary.

It should help the user understand what information is needed to help properly without overloading them.

#### Sections

##### Needed Now

Information needed to produce a reliable current path.

Examples:

- Who is this for?
- What are you trying to achieve?
- What exists already?
- What decision are you trying to make now?
- What constraint cannot be ignored?

##### Useful Soon

Information that improves roadmap, prototype, validation, or execution quality, but does not block the current step.

Examples:

- What tools or repositories are involved?
- What evidence already exists?
- Who else is involved?
- What timelines or deadlines matter?
- What user feedback exists?

##### Assumptions I Can Make For Now

Assumptions ResolveOS can proceed with if clearly labelled.

Examples:

- I’ll assume this is an existing messy project unless corrected.
- I’ll assume the first goal is clarity, not implementation.
- I’ll assume a prototype should come before full product build.

##### Not Needed Yet

Information the user does not need to provide now.

Examples:

- full technical architecture
- final pricing model
- detailed team workflow
- complete backlog
- final brand assets
- investor narrative
- production infrastructure decisions

#### User Controls

For each context item, allow the user to choose:

- Answer now
- Skip for now
- Accept assumption
- Mark as not relevant

#### Design Rule

Do not ask every possible question.

Ask enough for ResolveOS to function well, but group questions by urgency and impact.

The product should be comfortable with some ambiguity, but should make important uncertainty visible.

### Screen 4 - Your Path To Execution

#### Headline

```text
Your Path To Execution
```

#### Purpose

This is the main practical output.

It should replace formulaic top actions with a route from current state to meaningful progress.

#### Sections

##### Immediate Focus

The most important thing to focus on now.

This should not be generic.

It should be grounded in the user's project, current state, desired outcome, and available context.

##### Why This Comes First

Plain-English reasoning.

The user should understand why this focus creates progress, reduces risk, unlocks a decision, or prevents wasted work.

##### First Milestone

The next meaningful milestone, not just a task.

Examples:

- confirmed project direction
- validated target user and problem
- prototype brief ready
- first clickable mockup tested
- first external feedback captured
- first build scope agreed

##### Suggested Route

Use a staged route rather than a flat task list.

Example structure:

| Stage | Focus | Output | Confidence |
| --- | --- | --- | --- |
| Now | Immediate project focus | Concrete output | High / Medium / Low |
| Next | First milestone | Validated decision, prototype, plan, or evidence | Medium |
| Later | Larger roadmap direction | Provisional outcome | Lower |

##### Key Decision Gates

Decision gates should show what must be true before moving forward.

Examples:

- What must be true before prototyping?
- What must be true before building?
- What must be true before selling?
- What must be true before productising?

#### Product Note

Top actions may still appear, but only as part of the execution path.

They should not be the primary product structure.

### Screen 5 - Potential Roadmap

#### Headline

```text
Potential Roadmap
```

#### Important Note To User

```text
This roadmap is provisional. The further out it goes, the more assumptions it contains.
```

#### Purpose

The roadmap should be the first visual moment where the user sees that their messy project has become clear, practical, and presentable.

This screen should make the user feel:

```text
I came in with a hodgepodge of links, notes, ideas, and confusion. Now I have a clean roadmap I could almost show someone.
```

#### Roadmap Quality Bar

Long-term, the roadmap should be good enough to show to:

- stakeholders
- shareholders
- clients
- founders
- investors
- managers
- teammates
- collaborators

It should be clean, polished, and visually clear.

For the prototype, a lower-fidelity roadmap is acceptable, but the design direction should be presentation-quality.

#### Visual Direction

The roadmap should not be a plain generic list.

It should eventually look like one of:

- horizontal roadmap cards
- clean timeline
- presentation-style milestone map
- phased journey map
- outcome-based roadmap visual

Suggested phase model:

```text
Now -> Shape -> Validate -> Prototype -> Pilot -> Productise
```

Each phase should show:

- phase name
- goal
- key output
- confidence level
- decision gate

Example roadmap content model:

| Phase | Goal | Output | Confidence |
| --- | --- | --- | --- |
| Now | Make sense of the project | Confirmed project direction | High |
| Shape | Define the first coherent workflow | Prototype brief | Medium |
| Validate | Test with real users | Evidence from first testers | Medium |
| Prototype | Build the smallest usable version | Clickable or working demo | Lower |
| Pilot | Use with real projects | Case study or adoption signal | Lower |
| Productise | Turn repeatable parts into product | Scalable product direction | Low |

#### Roadmap Best-Practice Rules

Hard-code these principles into the roadmap generator.

- Roadmaps should be outcome-based, not feature dumps.
- Roadmaps should adapt to project type.
- Roadmaps should not force every project into the same lifecycle.
- Each phase should have a clear goal.
- Each phase should have a concrete output.
- Each phase should include a decision gate.
- Later phases should show lower confidence unless evidence exists.
- Do not invent timelines unless the user provides constraints.
- Do not treat building as the next step unless discovery supports it.
- Separate discovery work from validation work.
- Separate validation work from implementation work.
- Separate prototype work from productisation work.
- Show the assumptions that the roadmap depends on.
- Make the next milestone concrete enough to act on.
- Keep the roadmap clean enough to be shared.

#### Project-Type Adaptation

The roadmap should adapt depending on project type.

Examples:

- A new product idea may need problem/user validation before prototype.
- An existing messy project may need context consolidation before roadmap decisions.
- A software build may need scope, technical feasibility, and acceptance boundaries before implementation.
- A commercial offer may need buyer segment, positioning, and evidence before productisation.
- A process/workflow project may need mapping, constraints, and adoption risk before tooling.

### Screen 6 - Continue From Here

#### Headline

```text
What do you want to do next?
```

#### Purpose

Let the user continue without needing to invent the next prompt.

This should feel like a set of obvious next-step cards.

The user should also be able to type freely if they want.

#### Clickable Options

- Refine this roadmap
- Create a prototype brief
- Create a validation plan
- Turn this into tasks
- Prepare a stakeholder summary
- Extract assumptions and risks
- Answer context questions
- Continue this project later
- Ask ResolveOS a question

#### Optional Generated Outputs

ResolveOS can generate:

- project brief
- validation plan
- prototype plan
- roadmap
- stakeholder summary
- handoff summary
- next-session prompt
- context extraction prompt
- assumptions and risks list

## Revised Question Model

Use this question model consistently across the product.

### Needed Now

Required to produce a reliable current path.

Example questions:

- Who is this project for?
- What are you trying to achieve?
- What exists already?
- What decision are you trying to make now?
- What constraints matter immediately?

### Useful Soon

Not blocking, but important for roadmap, prototype, validation, or execution quality.

Example questions:

- What tools, repos, docs, or systems are involved?
- What evidence already exists?
- Who else is involved?
- What user feedback exists?
- What deadlines or timing constraints matter?

### Safe Assumption

The system can proceed if the assumption is labelled clearly.

Example assumptions:

- I’ll assume this is an existing messy project unless corrected.
- I’ll assume the first goal is clarity, not implementation.
- I’ll assume the user wants a prototype before a full build.
- I’ll assume the roadmap should be provisional until evidence improves.

### Not Needed Yet

Avoid user overload by making it clear what can wait.

Examples:

- full technical architecture
- final pricing model
- full delivery team model
- production infrastructure
- final brand assets
- investor narrative
- detailed analytics setup

## Revised Evidence Model

For this prototype, payment is not the primary success bar.

The first success signal is whether the user genuinely finds the flow helpful and wants to continue, reuse, screenshot, or share the output.

### Evidence Ladder

| Signal | Strength |
| --- | --- |
| User completes the flow without explanation | Basic usability signal |
| User feels comfortable dumping messy context | Intake signal |
| User says the project summary is accurate | Comprehension signal |
| User corrects or adds context because they care about the output | Engagement signal |
| User says the execution path is useful | Value signal |
| User wants to keep using it on their project | Strong value signal |
| User wants to screenshot or share the roadmap/output | Strong shareability signal |
| User says someone else should try it | Very strong organic demand signal |
| User asks when the product exists | Product pull signal |
| User says they would pay | Commercial signal |
| User pays | Commercial validation |

### Prototype Success Signal

The target signal for the first prototype is:

```text
The user finds it useful enough that they want to continue using it, screenshot it, or share it with someone else.
```

A particularly strong signal would be:

```text
Can I send this to someone?
```

or:

```text
I know someone who needs this.
```

Payment can be tested later once the workflow has proven real user value.

## Non-Goals For This Prototype

These are non-goals for the prototype, not necessarily permanent product exclusions.

Do not build yet:

- full SaaS platform
- user accounts
- billing system
- team workspaces
- admin dashboard
- integrations
- persistent multi-project database
- collaboration features
- polished production infrastructure
- GitHub/Notion writeback
- automated project management system
- generic ResolveOS frontend for every workflow
- framework expansion
- README rewrite
- entrypoint rewrite
- bundle regeneration

The prototype may still be a simple hosted or clickable interface.

"No full SaaS" means do not build the full product platform before proving the workflow.

## Prototype Method

Use a low-fidelity mockup first.

The recommended format is a Notion/Figma-style guided card flow:

1. Bring Everything In
2. Your Project As I Understand It
3. Context Needed
4. Your Path To Execution
5. Potential Roadmap
6. Continue From Here

The backend can be manual or Wizard-of-Oz during testing.

The goal is to learn whether the flow creates clarity, confidence, and shareable value before investing in implementation.

## Immediate Next Actions

1. Turn this brief into a lo-fi mockup.
2. Use a PM/builder with an existing messy project as the first target test user.
3. Test whether the user is comfortable dumping messy context.
4. Test whether the Screen 2 project interpretation feels accurate and correctable.
5. Test whether Screen 3 context grouping feels helpful rather than bureaucratic.
6. Test whether Screen 4 gives a real path to execution.
7. Test whether Screen 5 roadmap feels clean enough to screenshot or share.
8. Capture whether the user wants to continue, reuse, or share the output.
9. Do not convert this into implementation work until Sprint 001 orchestration review approves it.

## Decisions Still Needed

- Confirm whether the first mockup should be built in Figma, Notion, a static web page, or another lightweight format.
- Confirm the first test user's project scenario.
- Confirm whether the prototype should support typed-only context first or include simulated file/link/source upload areas.
- Confirm whether the first roadmap visual should be a timeline, cards, or phased journey map.
- Confirm whether Issue 16 should remain the tracking issue for this prototype or whether a linked discovery issue should be created later.

## Source-Of-Truth Note

This file is a project-scoped product discovery brief linked to Issue 16.

It should not become the source of truth for global ResolveOS behaviour, framework rules, workflows, roles, skills, or governance.

If the hosted wrapper direction becomes an approved product direction, Notion should remain the owner for commercial strategy, validation evidence, roadmap, and beta programme tracking according to the current Sprint 001 orchestration decisions.

If the hosted wrapper becomes an implementation project later, implementation scope should be created only after orchestration review approves it.
