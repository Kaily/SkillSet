# Bootstrap for an AI agent

Repository: https://github.com/Kaily/SkillSet

This document explains how to obtain and use the skill. It is not the application project's rule set. Respect the user's intended project, existing instructions, and the host agent's permissions.

## 1. Get the complete skill

Use your supported GitHub connector, Skills CLI, Git client, or download mechanism. For Git:

```sh
git clone https://github.com/Kaily/SkillSet.git
```

Clone into a separate, non-existing download folder chosen for the task, not over the user's application folder. A clone downloads this skill repository; it does not create the user's application or authorize modifying unrelated repositories.

Alternatively, download the repository ZIP through GitHub's Code menu. Preserve the layout of `project-rules-builder/`. It must contain:

- `SKILL.md`
- `LICENSE` (retain the license with installed and distributed copies)
- `references/rules-guide.md`
- `agents/openai.yaml` (optional UI metadata; retain it when copying the package)

The following raw URLs are a fallback for agents that can fetch only individual files. Download all four into the same relative layout:

- https://raw.githubusercontent.com/Kaily/SkillSet/main/project-rules-builder/SKILL.md
- https://raw.githubusercontent.com/Kaily/SkillSet/main/project-rules-builder/LICENSE
- https://raw.githubusercontent.com/Kaily/SkillSet/main/project-rules-builder/references/rules-guide.md
- https://raw.githubusercontent.com/Kaily/SkillSet/main/project-rules-builder/agents/openai.yaml

Use a specific verified commit instead of `main` when reproducible versions matter. Never claim a successful installation if a required file could not be downloaded.

## 2. Install or load

- If your agent supports native skills, install the complete skill folder in its documented project or personal location. Check for an existing installation and preserve local customizations.
- Codex project location: `<application-project>/.agents/skills/project-rules-builder/`.
- Claude Code project location: `<application-project>/.claude/skills/project-rules-builder/`.
- If native skills are unavailable, read `project-rules-builder/SKILL.md` directly and follow it as the user's requested workflow. Read `references/rules-guide.md` when the entrypoint calls for it.

Do not paste this repository's entire README or all external book rules into the application's `AGENTS.md`. The generated rules must come from the user's actual project context.

## 3. Start the project interview

If no meaningful brief exists, ask in the user's language:

> Tell me about your project: what do you want to build, who will use it, and what problem should it solve? Include any features or constraints you already know. It is fine if the technology is not decided yet.

If the user already supplied a brief, use it and ask only about important gaps. Follow the skill to create the appropriate rules and brief in the user's named application folder. Downloading the skill does not itself authorize implementing or publishing that application.
