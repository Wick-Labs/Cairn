# Development principles and standards

These standards apply to human and AI contributors. They are intended to make Cairn understandable, portable and enjoyable to develop, not to create paperwork for its own sake.

## Begin from a verified branch

Read [README.md](README.md), [the charter](CHARTER.md), [current state](docs/STATUS.md) and the relevant parts of [the architecture direction](docs/ARCHITECTURE.md). Establish the remote, branch and commit before changing anything. Check for existing work and reconcile differences; never discard newer local work simply because a remote exists.

The selected branch's committed source, tests, dependency records and documentation define its engineering state. A chat transcript, an agent's memory or a disposable workspace is not a required dependency. Contradictions between code and documentation are defects to reconcile, not a reason to invent state.

There is currently no runtime to install and no application test command. Do not invent either. When implementation begins, publish supported environments, pinned dependencies, setup and startup commands, configuration precedence, migrations and a synthetic smoke test in the same change as the functionality.

## Build across explicit boundaries

Define each component's responsibilities, inputs, outputs, failure modes and owned data. Use versioned public contracts where extensions depend on them. Register capabilities through documented interfaces; do not reach into another module's private tables or source files.

Keep presentation and messaging adapters independent from core conversation, memory and permission logic. Give extensions lifecycle management, compatibility declarations and isolated failure behaviour. A plugin running in-process is not a security sandbox; document its trust requirements. Use execution isolation for untrusted code.

Changes to contracts or data formats require compatibility tests and a migration or deprecation plan. Keep initial machinery small; do not create empty frameworks for every imagined future feature.

## Write readable source and useful documentation

Prefer clear names and simple control flow. Document public APIs and meaningful contracts: types, units, invariants, ownership, concurrency, side effects, permissions and expected failures. Comments should explain intent and non-obvious constraints rather than narrate obvious syntax. Update misleading comments in the same change as behaviour.

Give users a practical route from a fresh checkout to a working result. Give developers component boundaries, extension examples and reproducible tests. Keep one canonical home for each fact and link to it. Record significant accepted decisions with alternatives and reasons; do not write decision records for every minor edit.

## Test claims at the right level

As components are implemented, include unit and contract tests, synthetic integration fixtures, and targeted end-to-end checks. Test permission boundaries, memory provenance and visibility, failure recovery, duplicate messages, skill compatibility, and migration behaviour where relevant.

Basic development tests should not require a paid inference provider, a live messaging workspace, private credentials or a powerful GPU. Use fake providers and deterministic fixtures. Label real-model and external-service tests separately with prerequisites and costs.

Describe what each check actually demonstrates. A UI mock is not a connected service; a parser test is not safe skill execution; a model's impressive response is not proof of a cognitive mechanism. Missing test execution is not a passing result.

## Treat this as a public repository

Use synthetic identities and data throughout examples, screenshots, tests and documentation. Do not commit personal chats, private memories, health or client information, account or channel configuration, credentials, real environment files or runtime databases. Contributor attribution is not application configuration.

Use documented local configuration, environment variables or a suitable secret store. `.env` is a convenience, not encryption. Never echo secrets into logs or expose them through the web UI after entry. Provide a placeholder-only example when the configuration schema exists. Review staged files, PR descriptions, CI output and generated assets for leaks; `.gitignore` is not a security guarantee.

Do not assume imported models, skills or assets inherit the project's MIT licence. Preserve their source, applicable notices and distribution constraints.

## Collaborate without hidden workspaces

Use scoped branches and reconcile against the latest remote state. When delegating, provide branch and commit, relevant contracts, owned files, expected output, privacy constraints and stop conditions. Use separate branches or worktrees for overlapping work and designate one integrator. Merge only after reviewing differences and rerunning applicable checks; do not let workers race on shared files.

Before ending or handing over a meaningful work session, push a coherent checkpoint and verify the remote branch. Update the concise status record with implemented scope, open work, evidence, limitations and the next useful action. Identify the exact checkpoint commit in the handoff. Preserve non-secret reproduction assets in version control or a durable referenced location, not only a temporary download link.

A checkpoint may be incomplete but must be recoverable and honestly labelled. Do not reset completed work or leave the only explanation of a blocker in an unavailable chat. Do not duplicate the entire session transcript into documentation.

## Changing the foundations

Distinguish agreed requirements from implementation proposals. Changes to the charter, permission model or public extension contracts need explicit review. Agents, including any future Cairn contributor, follow the same branch, test and review standards; generated code or self-authored skills do not receive privileged trust.
