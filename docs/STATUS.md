# Current state and next discussion

**Updated:** 19 October 2026. This is a dated branch snapshot, not a live status feed.

## Verified baseline

The public `Wick-Labs/Cairn` repository was inspected with `main` at `4a5255407eb4d0a32e5d7e4e533d249771b9bf5c`. The existing MIT licence is preserved without modification.

The founding scaffold was then verified at `e8bcf08a7410c73da34c4732c14ffe8ee4ed31a3` on `docs/founding-vision`, with [PR #1](https://github.com/Wick-Labs/Cairn/pull/1) open, draft and unmerged. This starter update builds on that checkpoint. Consult the live PR and branch for the latest revision.

## Available foundation

This branch contains the README, [charter](../CHARTER.md), [contributor standards](../CONTRIBUTING.md), [agent entry point](../AGENTS.md), [architecture direction](ARCHITECTURE.md), this status record and ignore rules. Shared text conventions and concise pull request and design idea templates support contributions across environments.

The charter preserves the founding intent. Mechanisms labelled as proposals remain open; no additional architecture decision is accepted by this setup work. Contributor templates will become the repository defaults after reaching the default branch; they are currently reviewable in this draft.

## Founding clarification accepted

Cairn is explicitly **a stack for an autonomous, continuing AI participant, not an assistant product**. The two founding cognitive pillars are Theory of Mind and a model of the psyche. The latter must address evolving self-organisation, motivations and goals as well as operational capability awareness. The participant may use one model or submodels, develop a name distinct from the stack, and initiate bounded pursuits without a human prompt.

The 24/7 goal is continuity and availability *when the host is on*, not nonstop model inference. Low-cost resident scheduling, on-demand inference, resource pressure handling and safe pauses are requirements to design toward; none are implemented. The precise psyche model, scheduler and autonomy policies remain open. See the [charter](../CHARTER.md) for the canonical commitment and [architecture direction](ARCHITECTURE.md) for candidate mechanisms.

## Local deployment requirement

The agreed default is a fully local stack with local inference and memory, presented through a **localhost web interface**. A browser-based UI does not imply remote hosting. Offline core use, optional external connections and deliberate network exposure are design requirements, not implemented behaviour. The precise implementation and ports remain open.

## Not implemented or verified

There is no application, frontend, inference integration, database schema, skill interpreter, sandbox, startup wizard or messaging plugin. No runtime dependencies, build pipeline or automated application test suite exists. No installation or deployment has been verified. No framework or model has been selected.

Conversation channels or access through an external connector do not constitute a working Cairn integration. Actual agent event delivery, response triggers and bounded unattended exchanges still require implementation and verification.

## First focused discussion

Start with a short fictional conversation in which the participants are authorised to share the relevant information: Rowan mentions a Friday demonstration; Kit later reports a move to Saturday; Rowan has not acknowledged that report. What should Cairn notice, say and retain when Rowan next asks about Friday?

Use that scene to explore the following proposals, without fixing schemas or treating a discussion as an accepted decision:

1. **What has been established together?** Distinguish a report, message visibility, acknowledgement and agreement. A small record of where this conversation stands may be more useful initially than elaborate participant profiles.
2. **What changes when Cairn is corrected?** If Saturday referred to a different event, revise the working understanding and revisit advice that depended on the error. Historical context should not keep resurfacing as a competing current fact.
3. **What is Cairn carrying forward?** Consider a small, inspectable view of relevant retained information, uncertainty and accepted commitments. Show sources and recorded outcomes rather than claiming to expose hidden model reasoning.
4. **How should company and rest work?** Explore thread-scoped invitations for human and agent exchanges, explicit stopping points, and pausing inference on a shared computer. Capabilities, availability and completed actions should reflect verified state.
5. **What is the first satisfying build?** A candidate is one local web conversation that handles a correction, retains a narrow perspective distinction, survives a restart and permits inspection and correction of that state, *plus* one tiny scheduled or self-initiated activity that can wait safely while inference is asleep.

The candidate milestone is an invitation to choose, not an approved build specification. The participant's autonomy and psyche are fixed vision requirements even if their first implementation is deliberately modest. It would give the six-part cognitive picture a small practical foothold. Provider, model, frontend and storage choices should follow the chosen experience and verified constraints.

## Continue from here

Hold the founding discussion, record the few choices actually accepted, and define a bounded first implementation with observable success criteria. Consult [the architecture direction](ARCHITECTURE.md) for the wider skill and extension ambitions; those do not all need to be resolved before the first working conversation.

Verify the current remote branch, pull request and commit before resuming. Record applicable checks and the exact resulting commit in the PR or handoff. Update this snapshot instead of appending a session diary, and keep private collaboration and deployment details outside the public repository.
