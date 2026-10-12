# Maintaining this skill repository

This repository distributes `project-rules-builder`. It is not a target application project.

- The canonical distributable skill is `project-rules-builder/SKILL.md`, with its relative reference and UI metadata files.
- Keep the entrypoint portable across agents. Agent-specific installation and invocation guidance belongs in README.md or BOOTSTRAP.md.
- Preserve the interview-first workflow: use supplied context, ask only material missing questions, and derive proportional project-specific rules.
- Do not introduce compulsory frameworks, blanket approvals, fixed file-size limits, or a universal architecture.
- Keep private project names, business data, credentials, machine paths, and conversation history out of the distributable files.
- Do not alter a user's separately installed personal skill merely by maintaining this repository. Sync it only when requested or authorized by the current task.
- After edits, check skill frontmatter/name, UI metadata, required files, relative links, and installation instructions. Describe static checks accurately; do not claim behavioral or integration validation without evidence.
- Keep the MIT license notice with distributed copies. When importing third-party text, preserve its applicable notices.
- Update download URLs when repository owner, name, branch, or layout changes. Do not publish placeholder URLs as a working installation.
