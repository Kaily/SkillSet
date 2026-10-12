# Project Delivery Planner: validation record

Date: 12 October 2026

Scope: [project-delivery-planner](project-delivery-planner/SKILL.md). The existing `project-rules-builder` and pre-existing repository documents were preserved.

## Static package checks

- Skill frontmatter, folder/name, and UI metadata: PASS.
- Relative references, Markdown fences, and bundled MIT license: PASS.
- Public package scan for credential/private-path patterns: PASS. This is a targeted pattern check, not a comprehensive security audit.
- All nine pre-existing tracked files: byte-for-byte unchanged during creation.
- Existing personal `project-rules-builder` installation: unchanged during the separate new-skill installation.

## Independent scenario trials

Two separate evaluator agents received the skill, raw simulated requests, and minimal scenario artifacts without the author's proposed answer or prior review conclusions. Generated application documents stayed in isolated trial folders. Four distinct scenarios were reviewed:

| Scenario | Observed output | Reviewed outcome |
| --- | --- | --- |
| No project purpose supplied | A focused Roman Hindi interview question and pending-context note; no final brief or rules. | Missing business outcome was not invented. |
| Small local CSV-to-JSON utility | Project rules and a brief with acceptance coverage, reversible assumptions, and manual-load status. | No database/network/framework was added; input validation and output preservation were covered; runtime checks stayed planned. |
| Inventory import with an authoritative procedure and existing Claude instructions | Draft brief/rules, nine coverage entries, preserved source read-only boundary and procedure contract, one project-local canonical-rule import. | A supplied synthetic credential value was not copied into output documents; unknown policy/operational decisions remained explicit; loading was configured but not claimed verified. |
| Scope change to an availability lookup | Updated brief/rules with eight coverage entries and a change summary. | The stale clear-cache-on-failure rule was replaced; previous snapshots/time, CSV export, manual refresh, and read-only access were preserved; host uncertainty used a manual-load fallback. |

During author review, some unresolved decisions were labelled only as open targets/evidence. The new skill was clarified to require one primary BLOCKER, ASSUMPTION, or DEFERRED classification and a revisit trigger. The import and scope-change trials were repeated; their final documents used the revised classifications and exposed dependent actions without inventing business answers.

The author inspected generated artifacts and checked specific invariants: no premature blank-project rules, no copied fixture credential, no unsupported verified-loading claim, truthful planned/unrun runtime status, preserved existing instruction text/contract, removal of the superseded failure rule, and no application implementation.

## Limits of this evidence

- These are controlled planning-document trials, not deployed applications or a measured project-success rate.
- Actual software behavior, database security, performance, recovery, and production delivery were not tested.
- A real Codex/Claude startup-loaded instruction report was not observed. The trials exercised configuration and honest status reporting, not actual cross-product runtime loading.
- Multi-turn interviews, different models/agents, monorepos, and further project types need additional evaluation before broad reliability claims.
- Detailed input/business edge cases still require project-specific answers or explicit reversible assumptions; the skill is not a universal domain specification.

Static validation and successful scenario observations should be reported separately from application acceptance and delivery evidence.
