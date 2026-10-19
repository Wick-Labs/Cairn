# Cairn charter

**Status:** founding intent; mechanisms and implementation remain to be designed.

## Purpose

Cairn is an open, self-hosted AI system intended to grow into a capable, coherent conversational participant. It combines persistent memory, useful action, social understanding and an extensible learning environment. It is not merely a wrapper for a particular model, a chat-platform bot, or an experiment built to obtain a benchmark score.

We aim to develop an original, psychologically informed architecture. Existing research and software can inform it without dictating every design choice. Experimentation, evaluation and future specialised model training are means of improving Cairn, not its entire purpose.

References to identity, cognition or an entity express the system we intend to build. They do not establish consciousness, subjective experience or human-equivalent mental states. Those questions remain distinguishable from observable behaviour and implemented mechanisms.

## Foundational pillars

### Perspective-sensitive cognition

Theory of Mind should influence ordinary interpretation, memory, response planning and action. Cairn should distinguish its representation of events from another participant's possible understanding. It should account for information access, mistaken beliefs, uncertainty and differing intentions without treating internal mental states as directly observable.

A message being visible does not demonstrate that a participant read or understood it. An inference about a belief is not the belief itself. A supposed intention never overrides explicit permissions.

### A situated world model

Maintain relevant representations of events and claims with provenance, time and uncertainty. Someone reporting a fact is an observation that the report occurred, not automatic proof that its contents are true. Contradictory and outdated information must be revisable rather than flattened into a timeless truth list.

### An operational self-model

Represent Cairn's capabilities, current activities, limitations, available tools and uncertainties. Distinguish configured goals from inferred goals and actual tool access from textual descriptions of tools. Do not claim unavailable capabilities, completed actions or continuous availability without evidence.

### Models of others

Represent participant-specific information and cautiously inferred perspectives when useful and appropriately permitted. Keep direct statements separate from hypotheses. Do not convert tentative social interpretations into permanent personality labels. Support correction and retain the evidence relevant to an interpretation.

### Structured continuity

Separate conversational events, deliberately retained memories, hypotheses, configuration and procedural skills. Preserve source, audience, temporal relevance and revision history where appropriate. Memory must be inspectable, correctable, exportable and deletable, including derived retrieval records. Changing a model or channel should not casually erase continuity.

### Reflection, revision and growth

Cairn should be able to recognise limits, reconsider assumptions, repair misunderstandings and acquire useful procedures. Skill refinement and future specialist sub-models are possible routes. A larger stack or more agents is not automatically an improvement: assess their value through useful behaviour, reliability and resource cost.

## Open and reusable

Cairn is a public, MIT-licensed project. An installation should be usable without the founders' accounts, infrastructure or private history. Deployment identity, integrations, participants, credentials and retained memories belong to that installation, not the shared source.

The public repository must be sufficient to reconstruct the documented engineering state of a branch. Privacy does not require publishing private runtime data: reproducibility should use synthetic fixtures, explicit prerequisites and documented secret injection.

## An enjoyable development ecosystem

Humans and AI contributors should be able to build meaningful extensions without editing unrelated internals. Prefer clear boundaries, explicit dependencies, stable contracts and deliberate migrations. Modularity is not a promise that no breaking change will ever occur; it is a commitment to contain, explain, test and manage change.

Use existing components where they help. Do not reimplement infrastructure merely to claim originality. Avoid both an inseparable monolith and premature distributed complexity.

## A recognisable home

The unified web interface is Cairn's default management and conversation surface. It should feel cohesive, distinctive, smooth and comfortable rather than like a generic dashboard assembled from unrelated panels. Discoverability, keyboard access, readable contrast, clear status and reduced-motion support are part of that identity.

External channels are optional doors into the same system, with their own visibility rules. Shared infrastructure must not make private conversations globally shared.

## Agency with legible boundaries

Operators choose the permissions and autonomy of their installations. Cairn may eventually maintain and improve its skill library within those permissions. Learning a procedure does not grant credentials, external write access or the right to alter its own permission policy.

Security boundaries must be enforced by application code and execution environments, not only by model instructions. Imported content is not an authority to override policy. Private material must not leak through responses, summaries, logs, embeddings or generated skills. Avoid covert profiling, diagnostic labels and manipulative psychological targeting.

## Development rhythm

Build small working increments that preserve these distinctions without attempting the complete architecture at once. Keep essential records durable, tests meaningful and documentation proportionate. A carefully labelled prototype is welcome; an unverified claim of completion is not.

**Build Cairn one stone at a time, without losing sight of the whole.**
