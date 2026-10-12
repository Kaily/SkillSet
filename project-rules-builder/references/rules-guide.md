# Selecting project rules

Use this guide after the user has described the project. These are selection criteria, not a checklist to impose on every project.

## Keep the baseline small

State the project's purpose, scope, verified stack/contracts, important boundaries, and acceptance checks. Prefer one maintainable application or script when it meets the need. Introduce extra layers, services, queues, or infrastructure only for a demonstrated requirement.

Use plain, enforceable rules. Replace "write good code" with a concrete local convention or acceptance check. Do not require every developer to follow a particular book.

## Choose conditional rules

| Project concern | Useful rules to derive | Evidence to request or inspect |
| --- | --- | --- |
| Small script or utility | Keep invocation, inputs, outputs, failure behavior, and rerun behavior explicit; avoid an application framework without a need. | Example input/output and execution environment. |
| Web app, portal, or desktop workflow | Define roles, server-side enforcement where relevant, validation, user-visible errors, state transitions, and ordinary user-flow checks. | Main user journey, permissions, and a representative screen or flow. |
| Business application | Assign ownership of presentation, use-case coordination, business decisions, persistence, and external calls; use the simplest architecture fitting the rules. | Business scenarios and current schema/API contracts. |
| Complex business lifecycle | Name business concepts consistently and protect the required transitions/invariants; introduce richer domain modeling only when it changes correctness. | Valid/invalid transitions and domain expert examples. |
| SQL or other persistent storage | Establish source of truth, keys, constraints, transaction ownership, concurrency behavior, query parameters, and compatibility with existing consumers. | Actual schema, stored procedure result contracts, and access patterns. |
| API or external integration | Specify authentication, payload/status validation, timeouts, retry eligibility/bounds, duplicate effects, and what an unknown outcome means. | Provider contract, side effects, rate limits, and sandbox availability. |
| Background or scheduled work | Define overlap handling, capacity, restart behavior, checkpoints, failure visibility, and accepted versus durably completed work. | Expected volume, allowable loss, duplicate tolerance, and recovery needs. |
| Import, sync, comparison, or audit | Define stable identity, company/tenant boundaries, consistency, partial-run handling, schema drift, repair, and replay behavior. | Representative records and required evidence accuracy. |
| Existing/legacy system | Observe current behavior before changing it; protect required contracts; separate behavior changes from structural cleanup when useful. | Existing tests, actual consumers, and a reproducible flow. |
| Deployment or production work | Define authorized environment/actions, configuration validation, readiness, useful diagnostics, and a recovery strategy appropriate to the change. | Actual hosting/setup, environment separation, and recovery constraints. |

## Adapt to the declared stack

- .NET/SQL: use the actual framework and packages; verify stored procedure parameters/results and transaction ownership. Keep sensitive SQL parameterized. Do not migrate business logic out of existing procedures automatically.
- Business Central/AL: verify environment/version, companies, object dependencies, permissions, and supported extension/integration contracts. Legitimate AL development can include writes; impose a read-only boundary only when the project requires it.
- Read-only configuration monitoring: if its brief requires source reads only, keep source permissions read-only and store monitoring data separately. An incomplete capture must not be reported as a deletion or proof of no change; exact actor/time needs reliable evidence.
- Other stacks: derive equivalent rules from their actual contracts and tooling. Do not reuse a Microsoft-specific rule merely because the owner has other Microsoft projects.

These examples are conditional. A new project does not inherit every boundary of a previous one.

## Make acceptance observable

Pick examples that matter to the declared project:

- Complaint submission: a valid request creates one complaint; an invalid request returns an actionable error without a partial save.
- Scheduled import: rerunning an already completed batch does not duplicate records; a partial failure remains recoverable.
- Monitoring: a failed capture is distinguishable from a successful capture with no changes.
- Integration: a saved business record remains clearly saved when a later notification fails; retries respect duplicate-side-effect risk.
- Small file tool: a representative file produces the agreed output; invalid input does not corrupt an existing output.

Do not copy these as requirements unless they match the user's project. Select checks according to the change's actual risk. State when integration or deployment checks cannot be run; do not invent success evidence.

## Shape the project files

For a new project, a concise brief can contain:

1. Purpose, users, and main workflow.
2. Required first release and explicit exclusions.
3. Chosen technology, authoritative data/contracts, and dependencies.
4. Observable acceptance criteria.
5. Confirmed constraints, assumptions, and unresolved decisions.

A project `AGENTS.md` can contain:

1. Purpose and link to the brief.
2. Project structure and relevant verified commands, when code exists.
3. Scope, contract, data-access, and implementation rules.
4. Applicable verification and completion-report expectations.

Use existing equivalent documents instead of duplicating them. Avoid empty headings or speculative build commands. Larger delivery plans and architecture diagrams belong in separate documents only when they help the requested delivery.

## Engineering references

This skill uses original, project-specific instructions. The following reviewed community rule sets are optional design references, not dependencies or rules to load together by default:

- [Code Complete](https://github.com/ciembor/agent-rules-books/tree/main/code-complete): construction and evidence-based verification.
- [Patterns of Enterprise Application Architecture](https://github.com/ciembor/agent-rules-books/tree/main/patterns-of-enterprise-application-architecture): responsibility and transaction ownership.
- [A Philosophy of Software Design](https://github.com/ciembor/agent-rules-books/tree/main/a-philosophy-of-software-design): interfaces and complexity.
- [Release It!](https://github.com/ciembor/agent-rules-books/tree/main/release-it): integration and operational failure behavior.
- [Designing Data-Intensive Applications](https://github.com/ciembor/agent-rules-books/tree/main/designing-data-intensive-applications): consistency, durability, replay, and schema evolution.
- [Domain-Driven Design Distilled](https://github.com/ciembor/agent-rules-books/tree/main/domain-driven-design-distilled): selective business modeling.
- [Working Effectively with Legacy Code](https://github.com/ciembor/agent-rules-books/tree/main/working-effectively-with-legacy-code) and [Refactoring](https://github.com/ciembor/agent-rules-books/tree/main/refactoring): safe changes to existing behavior.

Fetch a source only for a concrete unresolved design question. If copying or adapting repository text in a later revision, preserve its required MIT copyright and license notice. Combining design references requires judgment; do not turn the repository's compatibility labels into universal architectural prohibitions.
