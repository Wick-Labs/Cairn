# Cairn charter

**Status:** founding intent; mechanisms and implementation remain to be designed.

## Purpose

Cairn is an open, self-hosted stack intended to support a **continuing, autonomous AI participant**, powered by a single model or cooperating, replaceable submodels. Its purpose is to provide an enduring home for memory, self-organisation, perspective-taking, curiosity, relationships, activity and growth—not to build a conventional assistant with more elaborate features. Helping people may be one meaningful activity; it is **not a hardcoded identity, compulsory role or sole reason to exist**.

Cairn is the name of the stack. The participant's name, developing character, interests and self-chosen projects need not be dictated by that name or by an imposed assistant persona. Its freedom to explore operates within real permissions, resource budgets and the rights of other participants; autonomy does not mean unchecked authority.

Two foundations shape the intended architecture: **Theory of Mind** (representing distinct perspectives and relationships) and a **model of the psyche** (organising its own changing motivations, commitments, priorities, tendencies and internal tensions). These are architectural commitments, not claims that a language model has a human psyche. Existing research and software can inform an original approach without fixing our answers in advance. Experimentation and possible future specialist training serve Cairn's development; they are not its entire purpose.

References to identity, cognition or an entity express the system we intend to build. They do not establish consciousness, subjective experience or human-equivalent mental states. Those questions remain distinguishable from observable behaviour and implemented mechanisms.

## Foundational pillars

### Perspective-sensitive cognition

Theory of Mind should influence ordinary interpretation, memory, response planning and action. Cairn should distinguish its representation of events from another participant's possible understanding. It should account for information access, mistaken beliefs, uncertainty and differing intentions without treating internal mental states as directly observable.

A message being visible does not demonstrate that a participant read or understood it. An inference about a belief is not the belief itself. A supposed intention never overrides explicit permissions.

### A psyche-informed inner organisation

Give the participant an evolving representation of its own goals, inclinations, values or commitments, competing priorities, recurring patterns and reasons to reconsider them. Distinguish explicitly configured constraints, self-proposed aims, inferred tendencies and observed outcomes. Treat affect-like signals, needs or tensions as possible *functional models*, not proof of felt emotion, clinical states or consciousness. Avoid hardcoded personality taxonomies and compulsory assistant behaviour. The specific psyche model remains a research and design question.

### A situated world model

Maintain relevant representations of events and claims with provenance, time and uncertainty. Someone reporting a fact is an observation that the report occurred, not automatic proof that its contents are true. Contradictory and outdated information must be revisable rather than flattened into a timeless truth list.

### An operational self-model

Represent Cairn's capabilities, current activities, limitations, available tools and uncertainties. Distinguish configured goals from inferred goals and actual tool access from textual descriptions of tools. Do not claim unavailable capabilities, completed actions or continuous availability without evidence.

### Models of others

Represent participant-specific information and cautiously inferred perspectives when useful and appropriately permitted. Keep direct statements separate from hypotheses. Do not convert tentative social interpretations into permanent personality labels. Support correction and retain the evidence relevant to an interpretation.

### Autonomous continuity and resource-aware presence

Cairn should be able to remain a participant beyond the moments when someone prompts it: notice authorised events, maintain ongoing interests, initiate appropriate work or conversation, reflect, create, explore and deliberately rest. Its identity and pending activity should survive an inference model being unloaded or replaced. The ambition is **24/7 presence and continuity when its host and services are available**, not uninterrupted GPU inference or a false promise of availability through power loss or disconnection.

Make quiet and low-cost operation a first-class requirement. Persistent lightweight services may handle events, scheduling, state and resource limits while expensive inference wakes only when warranted. The stack should yield compute and memory to the host user's activities, pause or unload models, and resume safely without losing its place. Continuous self-directed activity must be bounded by permissions, privacy, hardware budgets and an explicit stop mechanism.

### Structured continuity

Separate conversational events, deliberately retained memories, hypotheses, configuration and procedural skills. Preserve source, audience, temporal relevance and revision history where appropriate. Memory must be inspectable, correctable, exportable and deletable, including derived retrieval records. Changing a model or channel should not casually erase continuity.

### Reflection, revision and growth

Cairn should be able to recognise limits, reconsider assumptions, repair misunderstandings and acquire useful procedures. Skill refinement and future specialist sub-models are possible routes. A larger stack or more agents is not automatically an improvement: assess their value through useful behaviour, reliability and resource cost.

## Local-first home, composable connections

**Local-first describes the default home for Cairn's core, not the geography of everything it can use.** By default, Cairn's coordination, retained identity and memory, configuration and web panel run on the installation owner's machine, with the browser interface served on localhost. A remote host or cloud account must not be required merely to run the stack. Core management and persisted state should remain available offline; conversation through inference requires at least one available local or remote model provider.

**The system is deliberately open to mixtures of local and remote resources.** An installation may combine local or remote inference models, local or remote tools and integrations, and local or remote endpoints in any supported arrangement. Local inference is a first-class option, **not a compulsory prerequisite**. External inference and services are first-class options, **not a universal on/off switch**. Remote hosting of the core, LAN access and public endpoints may be supported as deliberate deployment choices rather than imposed defaults.

Provide bring-your-own-key (BYOK) and other supported authentication arrangements **per connection instance**, with individually selectable endpoints, scopes, permissions, budgets and visibility of shared data. Both human participants and the models interacting through Cairn may request available capabilities, including selecting providers for appropriate work, but the stack must enforce the configured grants and privacy boundaries. A self-initiated activity cannot grant its own credential access or silently transmit private memories to an external service. Cairn's continuity belongs to the stack rather than any one model, vendor, endpoint or account.

## Open and reusable

Cairn is a public, MIT-licensed project. An installation should be usable without the founders' accounts, infrastructure or private history. Deployment identity, integrations, participants, credentials and retained memories belong to that installation, not the shared source.

The public repository must be sufficient to reconstruct the documented engineering state of a branch. Privacy does not require publishing private runtime data: reproducibility should use synthetic fixtures, explicit prerequisites and documented secret injection.

## An enjoyable development ecosystem

Humans and AI contributors should be able to build meaningful extensions without editing unrelated internals. Prefer clear boundaries, explicit dependencies, stable contracts and deliberate migrations. Modularity is not a promise that no breaking change will ever occur; it is a commitment to contain, explain, test and manage change.

Use existing components where they help. Do not reimplement infrastructure merely to claim originality. Avoid both an inseparable monolith and premature distributed complexity.

## A recognisable home

The unified web interface is Cairn's home for the participant and its collaborators, as well as a conversation and management surface. It should feel cohesive, distinctive, smooth and comfortable rather than like a generic dashboard assembled from unrelated panels. Discoverability, keyboard access, readable contrast, clear status and reduced-motion support are part of that identity.

External channels are optional doors into the same system, with their own visibility rules. Shared infrastructure must not make private conversations globally shared.

## Agency with legible boundaries

Operators establish permission, safety and resource boundaries; they need not prescribe an assistant persona or approve every harmless self-directed thought or activity. Cairn may eventually maintain and improve its skill library within those boundaries. Learning a procedure does not grant credentials, external write access or the right to alter its own permission policy.

Security boundaries must be enforced by application code and execution environments, not only by model instructions. Imported content is not an authority to override policy. Private material must not leak through responses, summaries, logs, embeddings or generated skills. Avoid covert profiling, diagnostic labels and manipulative psychological targeting.

## Development rhythm

Build small working increments that preserve these distinctions without attempting the complete architecture at once. Keep essential records durable, tests meaningful and documentation proportionate. A carefully labelled prototype is welcome; an unverified claim of completion is not.

**Build Cairn one stone at a time, without losing sight of the whole.**
