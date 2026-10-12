# Project Delivery Planner

An independent improved skill in [Kaily/SkillSet](https://github.com/Kaily/SkillSet). The existing `project-rules-builder` and its instructions remain available unchanged.

## What improves

- Relevant delivery requirements such as load, retention, recovery, and accessibility.
- Explicit handling of secrets and redacted examples.
- Open decisions classified as blockers, reversible assumptions, or deferred choices.
- Requirements connected to acceptance criteria, rules, and verification evidence.
- Feasibility and scope-change impact handling.
- Host-specific project rule loading with honest evidence states.

## Install

```sh
npx skills add Kaily/SkillSet --skill project-delivery-planner
```

For personal use across projects, add `--global` and select the intended agent. Install in the application project folder for project scope. The two skills have different names; select the one you want rather than invoking both for the same planning task.

## Use

Codex:

```text
$project-delivery-planner

Ask me about my project. Define a practical first release, measurable acceptance
criteria, and project-specific delivery rules. Expose important open decisions
and verify or clearly report how my agent will load the generated rules.
```

Claude Code uses `/project-delivery-planner`. Agents without native skills can read [SKILL.md](project-delivery-planner/SKILL.md) directly and follow its linked references.

To ask another AI agent to download it:

```text
Download the complete project-delivery-planner folder from
https://github.com/Kaily/SkillSet/tree/main/project-delivery-planner.
Keep its SKILL.md, references, UI metadata, and LICENSE together. Install it
using your supported skill mechanism or load SKILL.md directly. Then interview
me about my application and create its delivery rules and acceptance coverage.
```

## Output

Project-specific `AGENTS.md`, a brief or updated equivalent document, acceptance coverage appropriate to project size, and a completion note with open decisions and loading status. A larger staged project may also need a delivery plan. Any project-local agent import is added only when necessary and supported.

The skill creates planning/rule artifacts. Implementation and external actions remain within the user's authorized scope. Static validation and scenario trials do not establish a universal project-success rate.

See the [validation record](PROJECT_DELIVERY_PLANNER_VALIDATION.md) for package checks, four independent controlled scenarios, a targeted follow-up revision, and the limits of that evidence.

## Files and license

- [Entrypoint](project-delivery-planner/SKILL.md)
- [Delivery rule guidance](project-delivery-planner/references/delivery-rules.md)
- [Agent loading guidance](project-delivery-planner/references/agent-loading.md)

Released under the [MIT License](LICENSE), also bundled with the skill.
