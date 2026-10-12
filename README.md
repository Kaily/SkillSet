# SkillSet

## Project Rules Builder

A reusable AI agent skill that asks about your project before creating its delivery rules.

Describe the problem, users, expected result, and constraints. The skill turns that context into a project-specific `AGENTS.md` and, when needed, `PROJECT_BRIEF.md`. It works with new or existing software projects without forcing a particular language, framework, or architecture.

## Give this instruction to an AI agent

```text
Download the project-rules-builder skill from:
https://github.com/Kaily/SkillSet

Read BOOTSTRAP.md and follow its installation or manual-loading steps. Download
the complete project-rules-builder folder, including its references; do not
download only SKILL.md. Then use the skill in my current project: ask me the
important questions, establish scope and acceptance criteria, and create
project-specific rules before implementing the application.
```

For a Roman Hindi conversation:

```text
Pehle https://github.com/Kaily/SkillSet se project-rules-builder
skill download karo. BOOTSTRAP.md ke steps follow karo aur complete skill folder
lo. Phir mere project ke baare mein zaroori sawal poochho aur mere answers se
scope, acceptance criteria aur custom project rules banao.
```

## Install with the Skills CLI

Requires Node.js/npm and access to GitHub:

```sh
npx skills add Kaily/SkillSet --skill project-rules-builder
```

Select the intended agent and project or personal scope when prompted. Existing installations should be updated deliberately; do not silently overwrite a locally customized skill. The CLI supports selected agents, not every AI product. See its [official documentation](https://www.skills.sh/docs/cli).

## Manual installation or loading

Download or clone this repository. Copy the **complete** `project-rules-builder/` directory into the destination supported by your agent.

| Agent | Typical project location | Usage |
| --- | --- | --- |
| Codex | `.agents/skills/project-rules-builder/` | Invoke `$project-rules-builder` in the project chat. |
| Claude Code | `.claude/skills/project-rules-builder/` | Invoke `/project-rules-builder` in the project chat. |
| Other Agent Skills-compatible agents | Use that agent's documented skill location. | Select or explicitly request the installed skill. |
| Agents without native skill support | Keep the folder in a readable location. | Ask the agent to read `SKILL.md`, then follow its instructions and read the linked reference when needed. |

For Codex personal use across repositories, the documented user location is `~/.agents/skills/project-rules-builder/`. Check your agent's current installation documentation; native discovery and invocation differ by product. [Codex skills documentation](https://learn.chatgpt.com/docs/build-skills), [Claude Code skills documentation](https://code.claude.com/docs/en/skills).

An agent needs file or web access to download/read the skill. If it cannot access GitHub, attach the complete skill files using its supported attachment mechanism. Plain chat products may follow the instructions manually but do not thereby gain repository-editing tools.

## What happens next

1. The agent uses any project context you already supplied.
2. It asks a small number of important questions about missing details.
3. It establishes the first release, constraints, assumptions, and observable acceptance criteria.
4. It creates or updates project rules in the intended project folder, preserving useful existing instructions.
5. It reports what is ready and which decisions remain open.

This skill generates rules; it does not grant permissions, replace the agent's tools, or guarantee delivery. Application implementation continues only within the user's authorized scope. Project details remain in that project's documents rather than becoming part of the reusable skill.

## Repository layout

```text
README.md
BOOTSTRAP.md
AGENTS.md                       Maintainer instructions for this repository
LICENSE
project-rules-builder/
  SKILL.md                      Portable skill entrypoint
  LICENSE                       License bundled with the installed skill
  agents/openai.yaml            Optional Codex UI metadata
  references/rules-guide.md     Conditional rule-selection guidance
```

The root `AGENTS.md` is for maintaining this skill repository. The skill creates a separate `AGENTS.md` in the user's application project.

## References and license

Uses the open [Agent Skills format](https://agentskills.io/specification). Engineering references are listed in [rules-guide.md](project-rules-builder/references/rules-guide.md); they are optional reading, not runtime dependencies. The original instructions in this repository are released under the [MIT License](LICENSE).
