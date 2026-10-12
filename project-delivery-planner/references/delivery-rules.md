# Selecting delivery requirements and rules

Read after the project context is known. Select concerns that change decisions; do not impose this whole guide on every application.

## Size the conversation to the work

- Small local tool: establish input/output, execution environment, failure behavior, and safe rerun behavior. A short brief and a few checks may be enough.
- Shared business application: establish users/roles, important state transitions, contracts, concurrency, data sensitivity, and usable first-release boundaries.
- Jobs, imports, integrations, or monitoring: establish side effects, source of truth, identities, volume, capacity, time limits, partial success, rerun/recovery behavior, and necessary evidence accuracy.
- Existing system: establish current behavior and consumers before changing the contract; preserve existing tests and authorizations.

## Operational questions when relevant

| Concern | Establish | Example acceptance shape |
| --- | --- | --- |
| Load/performance | Expected users, concurrency, record volume, growth, target workflow duration, and measurement environment. | The agreed representative workload finishes within the user-approved target under stated conditions. |
| Availability/recovery | Tolerable downtime/data loss, restart behavior, backup owner, and recovery method. | A representative interrupted job resumes or is safely retried without duplicating a committed effect. |
| Retention/privacy | Necessary fields, retention/deletion expectations, access roles, and approved storage locations. | Restricted records cannot be accessed by an unauthorized role; unnecessary identifiers are not persisted. |
| Accessibility/usability | Main devices, user abilities, keyboard interaction, and required accessibility expectations. | The main workflow can be completed using the agreed interaction method with actionable validation feedback. |
| Integrations | Provider contract, authentication method/key names, limits, side effects, and sandbox access. | Timeout or uncertain success produces a truthful status and a safe follow-up strategy. |

An unanswered operational target is an assumption or open decision, not a fabricated number. Treat it as a blocker only when the dependent architecture or business commitment cannot safely proceed.

Use one primary decision class: BLOCKER, ASSUMPTION, or DEFERRED. Additional notes can explain missing technical evidence or a dependent commitment. For DEFERRED, specify the phase/action that makes the answer necessary; do not leave a material question with only an "open" label.

## Requirement coverage

For a multi-requirement project, keep coverage near the brief. Adapt this shape:

| Requirement | Acceptance criterion | Rule/contract | Verification | Status/evidence |
| --- | --- | --- | --- | --- |
| Import one source batch | A repeat of the same batch creates no second record. | Stable batch identity and the agreed duplicate policy. | First run, repeated run, and interrupted retry using representative input. | PLANNED until run; then record actual result. |

Check both directions: every required capability has a criterion/check; every material rule protects a stated requirement, constraint, or actual risk. A simple tool can express this in sentences rather than a table.

Do not equate "test exists" with "acceptance passed." Report the tested environment, relevant output, and exclusions. Document-only checks do not prove that application behavior works.

## Conditional engineering rules

| Area | Derive only relevant rules |
| --- | --- |
| Business application | Own presentation, use-case coordination, business decisions, persistence, and transaction boundaries clearly. Avoid layers that only forward calls. |
| Business lifecycle | Use consistent business terms and enforce required state transitions. Rich modeling is optional unless it improves correctness. |
| Persistent storage | Verify actual keys, constraints, queries/SP results, transaction scope, conflict handling, and existing consumers. Use parameterized queries at unsafe input boundaries. |
| External API | Define timeouts, retry eligibility/bounds, input/response validation, duplicate effects, and unknown-success handling. |
| Queue or scheduler | Define capacity, overlap, full behavior, accepted versus persisted work, restart/recovery, and useful failure signals. |
| Sync or monitoring | Define stable identity, tenant/company boundary, complete-run criteria, partial failure, schema drift, replay, and repair. Incomplete capture is not proof of deletion/no change. |
| Legacy changes | Observe unclear current behavior, protect required consumers, and separate behavior changes from structural cleanup when useful. |
| Operational release | Verify authorized environment, setup/configuration, relevant acceptance checks, readiness/diagnostics, recovery, and support handover. |

Use the actual declared stack. For .NET/SQL, verify database/SP contracts rather than relocating business logic automatically. For Business Central/AL, verify environment/version, companies, dependencies, and permissions; impose read-only access only when this project's purpose requires it.

## Feasibility and change handling

If time, budget, or dependency availability conflicts with scope, explain which result is at risk. Recommend a usable first release and an explicit follow-up rather than silently removing required features. An estimate should state its key assumptions; do not invent dates or costs.

On a scope change, follow affected requirements into acceptance criteria, implementation boundaries, verification, operational dependencies, and agent imports. Resolve contradictions before calling the updated plan ready. Continue independent work if only one dependent decision is blocked.

## Optional engineering references

These are sources of selected principles, not runtime dependencies or complete rules to load by default:

- [Code Complete](https://github.com/ciembor/agent-rules-books/tree/main/code-complete): requirements and construction verification.
- [Enterprise Application Architecture](https://github.com/ciembor/agent-rules-books/tree/main/patterns-of-enterprise-application-architecture) and [A Philosophy of Software Design](https://github.com/ciembor/agent-rules-books/tree/main/a-philosophy-of-software-design): responsibility ownership and proportional abstractions.
- [Release It!](https://github.com/ciembor/agent-rules-books/tree/main/release-it) and [Data-Intensive Applications](https://github.com/ciembor/agent-rules-books/tree/main/designing-data-intensive-applications): operational failures and data correctness.
- [DDD Distilled](https://github.com/ciembor/agent-rules-books/tree/main/domain-driven-design-distilled), [Legacy Code](https://github.com/ciembor/agent-rules-books/tree/main/working-effectively-with-legacy-code), and [Refactoring](https://github.com/ciembor/agent-rules-books/tree/main/refactoring): selective business modeling and safe changes.

Read a source only for a specific unresolved question. Preserve required notices if importing third-party text in a later revision.
