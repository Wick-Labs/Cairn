# Current state and next discussion

**Updated:** 19 October 2026. This is a dated repository snapshot, not a live status feed. Verify the current branch and Git history before making changes.

## What exists

Cairn has an initial **documentation-only foundation**: a [README](../README.md), [charter](../CHARTER.md), [architecture direction](ARCHITECTURE.md), [contributor standards](../CONTRIBUTING.md), [agent entry point](../AGENTS.md), source-control conventions, lightweight contribution templates and the existing MIT licence. The founding changes were prepared and reviewed through [PR #1](https://github.com/Wick-Labs/Cairn/pull/1); consult its live status rather than assuming a particular branch or merge state.

There is **no running Cairn application**: no inference integration, web UI, database schema, memory engine, psyche implementation, scheduler, Slack bot, Skills runtime, deployment or test suite. No framework, model, provider, port or public API has been selected. No application tests, CI or local installation have been verified.

## Agreed founding direction

Cairn is an open stack for a **continuing, autonomous AI participant**, not a hardcoded assistant. Theory of Mind and a model of the psyche are foundational design concerns, alongside inspectable continuity, self-directed activity within configured boundaries, a distinct web home, and freedom to use one model or cooperating submodels. Nothing in this direction establishes consciousness or human-equivalent subjective states.

**Local-first is the default home, not a local-only restriction.** The core, identity, memory and web interface default to the user's own machine, with browser access through localhost. Inference, tools, integrations and endpoints may each be local or remote, in any supported mixture. A local model is not mandatory for remote-powered use, and an appropriately configured local system need not depend on cloud accounts. BYOK and independently configured, authorised connections—with distinct data scopes, credentials and budgets—are requirements.

The 24/7 ambition is a continuing presence **when the host and services are available**, not nonstop GPU inference. Resource-aware quiet operation, safe model unloads and resumable activity are requirements to explore; their implementations have not been chosen.

For canonical intent, see the [charter](../CHARTER.md). Mechanisms and integration vocabulary are deliberately provisional in the [architecture direction](ARCHITECTURE.md).

## Design questions still open

We have not selected a psyche model, memory representation, lifecycle scheduler, resource policy, inference framework, provider adapters, plugin contracts, trust isolation, web design or first implementation milestone. The initial build should not silently convert our shared vision into a request-and-response assistant architecture.

## Where the next conversation begins

A useful fictional scene: Rowan mentioned a Friday demonstration. Kit later reported that it moved to Saturday, but Rowan has not acknowledged the report. What should Cairn notice, ask, remember and revise when Rowan asks about Friday? What changes if Kit's report was provisional or mistaken? This helps us explore perspective, provenance, correction and continuity.

Alongside that, consider **one small self-initiated interest or task**: how would Cairn decide to revisit it later, wait quietly when the host is busy, and resume after inference is unloaded? Decide together what experience would be satisfying enough to build first; do not treat either example as an approved specification.

## Continuing development

Maintain one source of truth for each decision and distinguish accepted principles, proposed mechanisms and verified implementation. Keep personal conversations, credentials and installation state out of this public repository. Publish recoverable checkpoints and describe checks that actually ran; avoid creating empty infrastructure merely to signal progress.
