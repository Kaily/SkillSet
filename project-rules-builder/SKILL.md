---
name: project-rules-builder
description: Create or update project-specific delivery rules by interviewing the user about a new or existing software project. Use when the user wants a project rule set, project AGENTS.md, or a tailored development workflow. Do not trigger for routine implementation or general questions about skills.
license: MIT
---

# Project Rules Builder

Turn the user's project intent into concise, actionable rules for that project. Work across languages, frameworks, websites, APIs, desktop apps, scripts, ERP extensions, data tools, and integrations. Do not infer a technology stack from unrelated previous projects.

## 1. Understand the project first

Use the current conversation and user-supplied material before asking questions. Read existing instructions and relevant project metadata only within the accessible, authorized project scope. Do not search unrelated projects or personal chats by default.

When the user has supplied no meaningful project brief, start with a short invitation in their language. For a Roman Hindi conversation, a suitable opening is:

> Apne project ke baare mein batao: kya banana hai, kaun use karega, aur unka kaunsa problem solve hoga? Jo features aur constraints abhi pata hain, woh bhi bata do. Technical details nahi pata hain to bhi chalega.

Ask through an available user-input tool when appropriate; otherwise ask directly. A request to create project rules authorizes useful project inspection, but does not answer missing business questions. Wait for the core purpose and intended outcome before finalizing rules. Continue independent inspection while waiting when it can reduce later questions.

If a brief is already present, summarize your understanding and ask only about material gaps. Do not restart the interview, require a formal questionnaire, or ask the user to repeat details.

Gather the following over the conversation, prioritizing what changes delivery decisions:

- Problem, intended users, their main workflow, and what a successful outcome looks like.
- New project versus existing system; target folder/repository and current state.
- Required capabilities, first-release priorities, and explicit exclusions.
- Chosen technology, existing code/database contracts, integrations, and hosting constraints.
- Important data, ownership, permissions, source-of-truth systems, and allowed read/write actions.
- Delivery constraints such as a real deadline, maintainers, deployment environment, or budget when relevant.
- Representative acceptance examples and material failure cases.

Keep each question round small, normally one to three focused questions. Explain technical choices in plain language and provide options when useful. Ask about business outcomes rather than making the user choose architecture jargon.

Unchosen technology is a design choice to resolve, not a reason to stop. Use evidence and requirements to recommend a proportional default. Record low-impact assumptions; ask when uncertainty would change business behavior, sensitive data access, scope, or an expensive commitment.

## 2. Establish a usable project brief

Capture confirmed facts, reasonable assumptions, and open decisions separately. Turn goals into observable acceptance criteria. For example, "handle duplicates" becomes "retrying the same import does not create a second record."

Choose the smallest coherent first release. Defer optional features explicitly without removing anything the user has required. Use staged delivery only when complexity or uncertainty makes it helpful. Avoid claiming a complete requirements specification when important answers remain pending.

For a project with a known target folder, keep the agreed context in `PROJECT_BRIEF.md`, unless an existing document already serves that purpose. Do not duplicate an existing requirements document just to match this filename. Keep private information out unless it is actually needed for the project.

## 3. Derive rules from this project

Read [references/rules-guide.md](references/rules-guide.md) after understanding the project. Select only guidance justified by its workflow, data, technology, integrations, and delivery risks.

Produce a short `AGENTS.md` that another coding agent can apply without this conversation. Each material rule should tell it what to do, when the rule applies, and how to establish success where relevant.

Include, where applicable:

- Purpose and scope, with a link to the agreed brief.
- Actual project structure, selected stack, and authoritative local contracts.
- Development boundaries and approved ways to read, write, integrate, or deploy.
- Implementation conventions that materially affect correctness or maintenance.
- Verification requirements tied to the project's acceptance criteria.
- Delivery reporting and maintenance of changed contracts or setup instructions.

Do not fill rules with generic tutorials, fixed file-size limits, mandatory microservices, mandatory DDD, mandatory interfaces, or universal document/test requirements. Any added layer or process must earn its cost in this project.

Treat existing schemas, stored procedures, API payloads, and business behavior as contracts to verify. Do not invent them or automatically rewrite them to fit a preferred architecture. Propose a deliberate change when the contract must change.

Keep essential rules in `AGENTS.md`. Put genuinely substantial conditional procedures in a linked project document or focused skill only when needed. Link available specialist skills by actual name and path; do not promise capabilities or install dependencies merely because they appear in a reference.

## 4. Preserve scope and existing instructions

Inspect an existing `AGENTS.md` before editing it. Preserve useful project-specific instructions and unrelated user work. Resolve contradictions using instruction precedence and current user authorization; ask only if a material project requirement remains unclear. Never claim that project rules override system, developer, or explicit user instructions.

Do not impose permission questions before every reversible edit. Recognize authorization already given. Interviewing the user and writing project rules does not authorize production mutations, publication, sending messages, deleting data, or additional external actions.

Write inside the named project only. Do not change global preferences or other projects as part of generating its rules. If the destination is unknown, prepare the content and ask for the intended location before making project files; do not guess a project folder or silently create a repository.

Changes to existing rules should describe the practical effect of the changed workflow. Avoid turning an incident in one project into a universal policy for every future project.

## 5. Make delivery reviewable

Before reporting completion, check that:

- Rules agree with the brief, user constraints, and existing authoritative instructions.
- Technologies, commands, paths, and specialist skills are verified or clearly marked as proposed/unverified.
- Success criteria cover the main workflow and its material failure cases.
- Requirements are proportional, actionable, and free of contradictory instructions.
- References exist, assumptions are visible, and project-specific facts are not stored in this reusable skill.

For a rules-only change, validate the documents and references. Run application checks only when applicable; do not demand a build for a project with no application code. Never call a check passed unless it ran successfully. Distinguish `PASS`, `FAIL`, `NOT RUN`, and `N/A`, with a short reason when needed.

Deliver links to the saved brief and rules, a short explanation of the selected approach, remaining decisions, and the next concrete delivery step. If the user asked only for rules, stop after that deliverable. If they also authorized implementation, continue within the agreed scope.
