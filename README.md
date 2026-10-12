# SkillSet

**Reusable AI agent skills for clear project requirements and practical delivery rules.**

Start with your project idea. Let the agent ask the important questions, define what successful delivery means, and create a rule set tailored to that project.

The current collection contains **Project Rules Builder**, a general-purpose skill for new and existing software projects. It supports different languages and frameworks through project-specific guidance rather than a fixed architecture.

[Quick start](#quick-start) · [Ask any AI agent](#ask-any-ai-agent-to-download-and-use-it) · [Installation](#installation-options) · [Expected output](#expected-output) · [Troubleshooting](#troubleshooting)

## Available skill

| Skill | Purpose | Entrypoint |
| --- | --- | --- |
| `project-rules-builder` | Understand the project through a focused conversation, then create or update its delivery rules. | [SKILL.md](project-rules-builder/SKILL.md) |

Use it when starting a project, improving an incomplete project brief, or updating rules after a meaningful scope change. For ordinary coding tasks, continue using the project's agreed rules.

## Why use it?

A project idea often leaves important decisions unstated: who will use the software, what must be delivered first, which existing systems it depends on, and how success will be verified.

Project Rules Builder makes those decisions explicit before they become implementation assumptions. It:

- Uses details you already supplied and asks only about important gaps.
- Keeps questions understandable even when you have not selected a technology stack.
- Separates confirmed requirements, assumptions, and unresolved decisions.
- Defines observable acceptance criteria for the main workflow and relevant failure cases.
- Creates rules appropriate to the project's size, data, integrations, and maintenance needs.
- Preserves useful existing instructions and authoritative database/API contracts.

The reusable skill stays the same. **Each application gets its own rules.**

## Quick start

You need an AI agent that can read files or access GitHub. The CLI method also requires Node.js/npm.

**1. Open your application project folder** in your coding agent.

**2. Install the skill** from that folder:

```sh
npx skills add Kaily/SkillSet --skill project-rules-builder
```

Select the intended agent when prompted. Project installation is the CLI's default scope; personal installation across projects is described below.

**3. Invoke it and describe your project.** In Codex:

```text
$project-rules-builder

I am starting a new project in this folder. Ask me the important questions
about its purpose, users, features, and constraints. Then define the scope,
acceptance criteria, and project-specific delivery rules.
```

In Claude Code, invoke `/project-rules-builder`. Other agents use their own skill invocation interface.

**4. Answer the questions and review the generated rules.** When you are ready to implement, ask the agent to continue using the agreed project brief and rules.

## Ask any AI agent to download and use it

For an agent with GitHub or file access, copy this message:

```text
Download the project-rules-builder skill from https://github.com/Kaily/SkillSet.
Read BOOTSTRAP.md and use its installation or manual-loading instructions.
Keep the complete skill folder, including its references and license.

Use the skill in my current application project. First ask me the important
questions about the project. Use my answers to establish scope, constraints,
and acceptance criteria, then create or update project-specific AGENTS.md rules.
```

Roman Hindi version:

```text
Pehle https://github.com/Kaily/SkillSet se project-rules-builder skill download
karo. BOOTSTRAP.md follow karke complete skill folder install ya load karo.

Phir mere project ke baare mein zaroori sawal poochho. Mere answers ke basis
par scope, constraints, acceptance criteria aur custom AGENTS.md rules banao.
Jo information main pehle de chuka hoon, woh dobara mat poochho.
```

[BOOTSTRAP.md](BOOTSTRAP.md) includes the clone command, raw-file download links, complete package requirements, and instructions for agents without native skill support.

## Installation options

### Skills CLI

Run a project installation inside the application folder. Choose an agent interactively, or select it explicitly:

```sh
# Install for Codex in the current project
npx skills add Kaily/SkillSet --skill project-rules-builder --agent codex

# Install for Claude Code in the current project
npx skills add Kaily/SkillSet --skill project-rules-builder --agent claude-code

# Install for personal use across projects; select the agent when prompted
npx skills add Kaily/SkillSet --skill project-rules-builder --global

# Inspect available skills without installing
npx skills add Kaily/SkillSet --list
```

The repository has been checked with the CLI's listing command, which discovers `project-rules-builder`. Native installation and invocation depend on the agent you select. See the [Skills CLI documentation](https://github.com/vercel-labs/skills#readme).

### Manual installation

Clone this repository into a separate download folder, or use **Code → Download ZIP** on GitHub:

```sh
git clone https://github.com/Kaily/SkillSet.git
```

Copy the **complete** `SkillSet/project-rules-builder/` folder into the location supported by your agent. Keep `SKILL.md`, `LICENSE`, `references/rules-guide.md`, and `agents/openai.yaml` together.

| Agent | Project destination | Personal destination | Invocation |
| --- | --- | --- | --- |
| Codex | `.agents/skills/project-rules-builder/` | `~/.agents/skills/project-rules-builder/` | `$project-rules-builder` |
| Claude Code | `.claude/skills/project-rules-builder/` | `~/.claude/skills/project-rules-builder/` | `/project-rules-builder` |
| Other Agent Skills-compatible agents | Use the agent's documented skill directory. | Use its documented personal skill directory. | Use its supported skill interface. |

Check the [Codex documentation](https://learn.chatgpt.com/docs/build-skills) or [Claude Code documentation](https://code.claude.com/docs/en/skills) for current discovery behavior. Preserve local customizations when replacing or updating an existing installation.

### Agents without native skill support

Keep the complete folder somewhere the agent can read. Ask it to read `project-rules-builder/SKILL.md` and follow the workflow, including the linked reference when needed.

If the agent cannot download files, provide the complete skill files through its supported attachment mechanism. Reading instructions does not add filesystem access or editing tools to a plain chat product.

## What the skill asks

The interview adapts to what is already known. Typical topics include:

| Topic | Example question |
| --- | --- |
| Purpose and users | What are you building, who will use it, and what problem does it solve? |
| First release | Which capabilities must work in the first usable version? |
| Existing systems | Is this a new application or a change to existing code, databases, or APIs? |
| Constraints | Are there required technologies, hosting limits, deadlines, or maintenance needs? |
| Data and access | Which system owns the data, and which operations are allowed? |
| Acceptance | What should a successful workflow produce, and which failures must it handle? |

Questions are asked in small rounds, in the user's language. You do not need to complete a technical questionnaire before starting.

## Expected output

| Deliverable | Contents |
| --- | --- |
| `AGENTS.md` | Project purpose, scope, relevant contracts, development boundaries, implementation conventions, and applicable verification/reporting rules. |
| `PROJECT_BRIEF.md`, when needed | Users, workflows, first-release requirements, exclusions, constraints, acceptance criteria, assumptions, and open decisions. |
| Completion note | Links to the files, selected approach, unresolved decisions, and the next concrete delivery step. |

The skill reuses an existing requirements document when it already serves the brief's purpose. It updates useful existing rules instead of replacing them blindly.

For example, a rule for a scheduled import might require that rerunning the same batch does not create duplicate records. A rule for a small file-conversion tool might require that invalid input leaves an existing output intact. These rules apply only when they match the actual project.

## Supported project types

Suitable for websites, portals, APIs, desktop apps, scripts, ERP extensions, database tools, imports, synchronization, monitoring, and external integrations. It can also help establish safer rules for maintaining legacy code.

The skill chooses guidance from the project's actual requirements. It does not require .NET, a particular database, microservices, DDD, or a fixed number of layers.

Project rules support the host agent's instruction hierarchy and existing user authorization. They do not authorize production changes, publication, messaging, or unrelated work. Implementation continues only when requested; creating rules is a separate deliverable.

## Troubleshooting

| Situation | What to do |
| --- | --- |
| The agent cannot find the skill | Check its installation directory, folder name, and `SKILL.md` metadata. Refresh or restart the agent if its documentation requires it. |
| Only `SKILL.md` was downloaded | Download the complete skill folder so the linked reference and license are available. |
| Native skill support is unavailable | Use the manual-loading instructions above. |
| The agent asks questions you already answered | Point it to your existing brief and ask it to focus on material gaps. |
| You have not chosen a technology stack | Describe the users, workflows, and constraints; let the agent recommend a suitable approach. |
| You already have project rules | Ask it to review and update them while preserving useful instructions. |
| The project scope changes | Invoke the skill again with the changed requirements and update the brief, rules, and acceptance criteria. |

## Repository structure

```text
SkillSet/
├── README.md
├── BOOTSTRAP.md
├── AGENTS.md
├── LICENSE
└── project-rules-builder/
    ├── SKILL.md
    ├── LICENSE
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── rules-guide.md
```

The root [AGENTS.md](AGENTS.md) contains instructions for maintaining this skill repository. The skill generates a separate `AGENTS.md` in your application project.

## Maintenance and references

Improve the skill using actual project experience. Keep instructions focused, preserve the interview-first workflow, and validate metadata and relative references after changes. Project-specific business information belongs in the application project, not in this public reusable skill.

The package follows the open [Agent Skills specification](https://agentskills.io/specification). Optional engineering references are listed in [rules-guide.md](project-rules-builder/references/rules-guide.md), including selected community guidance from [agent-rules-books](https://github.com/ciembor/agent-rules-books). Those sources are references rather than runtime dependencies or mandatory rules for every project.

## License

Released under the [MIT License](LICENSE). Keep the license notice with installed and distributed copies of the skill.
