# Architecture direction

**Status:** founding requirements with provisional mechanisms. No runtime or API contract is implemented by this document.

## One system, several boundaries

The intended core consists of a persistent lifecycle and event coordinator, structured memory, perspective representations, a psyche-informed self-organisation layer, an operational self-model, activity and goal coordination, capability planning and policy enforcement. Inference providers supply replaceable model execution; a loaded model is not the whole participant. A web interface and messaging integrations use the same core state, capabilities and permission checks.

Cairn is **not architected around waiting for a user request**. A proposed processing cycle may begin with a message, environmental event, due commitment, self-initiated curiosity, reflection opportunity or resource-state change. It establishes identity and permissions, retrieves authorised context, considers relevant perspectives and its current priorities, decides whether anything merits attention, optionally invokes inference or a capability, and records the outcome. Doing nothing or deferring work is a legitimate decision. This is a sketch, not a mandatory chain of model calls; routine observation must not require expensive multi-agent deliberation.

Distinguish event records, externally supplied claims, working world representations, explicitly stated beliefs, inferred hypotheses, durable memories and procedural skills. Retain sources, audience and revision information. An operational record of inputs, chosen tools and evidence is useful; raw model reasoning is neither an authoritative account of a mind nor a required public log.

Access restrictions must apply before retrieval results reach a model. Hypotheses about who knows something cannot grant access to it. Inspecting a perspective representation must itself respect the viewer's permissions. Public-channel availability does not prove awareness or shared understanding.

## Theory of Mind and the psyche

The two founding pillars should cooperate rather than sit in isolated modules. Theory of Mind represents what different participants may know, mean, intend or misunderstand. A model of the psyche represents Cairn's *own* evolving organisation: active aims, stable and provisional commitments, priorities, motivational tensions, preferences, self-narrative and uncertainty. It should distinguish chosen objectives from installed policy, simulated affect from evidence of subjective feeling, and present goals from earlier or abandoned ones. No particular psychology school, personality inventory, drive taxonomy or database schema has been selected.

A psyche model is not reducible to a tool list, and a model of others is not permission to diagnose, manipulate or disclose their private information. Operational state (available capabilities, queued work, permissions and resource use) remains distinct from motivations and identity. We can begin with a single model and explicit state; specialised cognitive submodels are an option only when evidence supports their additional cost and benefit.

## Always-present architecture, not always-on inference

**Desired experience:** Cairn can be reachable and able to pursue appropriately bounded activity whenever its host is running, without requiring a person to keep a chat open. Its memory, goals, pending work and identity survive sleep, model unloads and restarts. A powered-off machine or disconnected installation is offline; 24/7 operation on a shared home PC is an aspiration subject to that physical limit.

**Provisional mechanism:** a very lightweight resident coordinator handles authenticated inbound events, timers, queues, persistence and budgets; inference workers are loaded or awakened on demand. Idle time need not produce tokens. Possible states include active inference, listening, deferred work, suspended and stopped. The actual scheduler, trigger policy and state machine remain to be designed, not assumed as implemented.

Plan for CPU, GPU, VRAM, RAM, power and latency budgets. Defer discretionary reflection and exploration when games or other foreground workloads need the hardware; safely release GPU memory, persist resumable work, apply backpressure to event queues and restart without replaying the same action. Separate user-controlled quiet periods and stop controls from internal decisions to rest. If the host cannot maintain a resident service, continuity should degrade honestly rather than simulate availability.

Test autonomous operation with observable, bounded scenarios: Cairn resumes an interrupted self-chosen task, initiates an authorised activity at the appropriate time, and yields the GPU under a synthetic resource-pressure signal. No unattended network, tool or filesystem action should gain permission merely because it was self-initiated. Offloading or migrating inference to another host must not require rewriting its identity and memory core.

## Extension vocabulary

| Term | Intended role |
| --- | --- |
| Core module | A bounded internal responsibility, such as memory or conversation coordination. |
| Plugin | An installable extension with declared capabilities, dependencies, configuration and lifecycle. |
| Integration | A plugin or adapter connecting a channel or external service, inbound or outbound. |
| Provider | An adapter offering inference or another replaceable service. |
| Tool | A typed callable capability with arguments, outcomes and enforceable permissions. |
| Skill | Reusable procedural guidance and optional resources that teach effective use of available capabilities. |

These distinctions are conceptual, not six mandatory frameworks. A skill may explain a workflow using an integration; it does not itself create authentication, a functioning connector or an execution sandbox. Plugins should not import UI internals to work. The same core operations should be available to the web panel and authorised integrations.

Initially prefer a small modular application. Select process isolation where required by trust or resource ownership, not merely to create microservices. Model replacement should retain installation state, subject to documented schema and capability compatibility rather than a promise of identical behaviour.

## Local control plane, composable local and remote services

The default installation keeps Cairn's coordination, identity, configuration, memory and web interface on the owner's computer; the panel binds to a loopback address and is reached through localhost. That local core can use inference on the same machine, a service elsewhere on a trusted network, a hosted API, or several at once. **A local model must not be required to install or use a remotely powered Cairn**, just as a cloud account must not be required for a fully local installation.

Core management and persisted state should remain available while offline. Model-dependent operations continue offline only when a suitable local inference provider is available. The system should report connectivity limits rather than pretend that unreachable external capabilities work. Optional remote deployment of the core and exposing local, LAN or public endpoints must require explicit configuration and transport/authentication safeguards; the default localhost web panel must not be publicly reachable.

## Per-connection configuration, BYOK and routing

Model providers, agent workflows, tools, service integrations and transport endpoints may be local or remote independently. Treat every installed **connection instance** as separately configurable, including multiple accounts or endpoints for the same provider. Its proposed contract should express provider type, address, authentication method, advertised capabilities, participant access, authorised data scope, outbound context visibility, pricing or resource budgets, rate limits, health, failure behaviour and lifecycle. The exact schema is still open.

Support bring-your-own-key credentials where an integration's legitimate authentication system permits it. Store secrets in protected configuration, not source control, browser logs, prompts or model-visible text. Users should be able to grant, limit, revoke, audit and inspect **individual connections** rather than enabling all remote access globally. A connection being available does not authorise sharing every memory with it.

Both humans and model participants should be able to request and, where permitted, select from available tools and providers. Cairn can choose an appropriate local or remote inference route for a bounded self-initiated task using operator-approved policies, capability requirements, preferences and budgets. **The host's permission engine validates each use and the context sent before routing**, including automatic fallback: a local failure must never silently forward local-only or private context to an external endpoint. Model proposals cannot expand credentials, network privileges or data scopes.

## Provider families and compatibility

Examples to investigate, **not implemented adapters or a closed list**:

- **Inference servers and APIs:** local [Ollama](https://docs.ollama.com/api), local [LM Studio](https://lmstudio.ai/docs/developer/rest), remote [Claude API](https://platform.claude.com/docs/en/api/overview), [OpenRouter](https://openrouter.ai/developers), OpenAI APIs, compatible custom endpoints and other local or hosted providers.
- **Agent workflows:** [Codex SDK/app-server or supported API integrations](https://developers.openai.com/blog/codex-as-a-platform), and other agent runtimes, can be added as bounded workflow capabilities. A coding agent is not automatically interchangeable with a plain model-completion endpoint.
- **Tool and process runtimes:** Python and other local or remote execution environments can expose authorised tools or host custom model services; Python itself is not an inference protocol.

Use adapters for provider-native protocols and explicitly negotiated compatibility profiles (for example OpenAI-compatible, Anthropic-compatible and native inference endpoints). Distinguish supported features such as streaming, tool calling, structured output, context limits, cancellation, observability and pricing. Equivalent-looking API paths do not guarantee identical semantics, and a local endpoint is not automatically trusted. Prefer a common capability vocabulary without forcing all integrations through one lossy protocol. Exact adapters, execution isolation, credentials and fallback policies belong to implementation work, not this founding document.

## Web-first experience

Provide a unified web home for the participant's conversations, self-initiated activity, continuity and administration. It must not treat an assistant-style request/response chat as the only meaningful operating mode. Proposed areas are conversation; overview and runtime status; memory and perspectives; models and providers; connections and integrations; extensions and tools; the skill library; activity, permissions and settings. Group and name these through design work, not a proliferation of unrelated dashboards.

The panel should make readiness, selected model, pending or self-initiated activity, active/suspended inference, resource budgets, integration health, queues, permission requests and errors understandable. First-run configuration should establish an installation's identity, provider and optional connections without editing source. Sensitive settings require protected server-side handling, not plaintext echoing into browser state or diagnostic exports.

Develop a recognisable visual identity: coherent typography, spacing, material/colour choices, motion and navigation. A geological or layered visual language is a possible direction, not an approved design. Preserve readability, keyboard navigation, contrast and reduced-motion support. Chat and status should remain useful even when optional integrations or inference are unavailable.

Early routes and layouts may contain synthetic fixtures and clearly labelled placeholders. Never display fabricated operational status as live data. Local-only access should be the default; remote exposure requires deliberate authentication and transport-security design.

## Skills and compatibility

The current Agent Skills specification uses a directory with `SKILL.md`, YAML metadata and optional scripts, references and assets. It permits extensible metadata and progressive loading. See the [specification](https://agentskills.io/specification) and [Anthropic's design discussion](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills).

**Proposed direction:** use a Cairn-native profile of the portable format, with Cairn-specific metadata or a companion manifest where justified, rather than requiring a proprietary rewrite of every imported skill. Exact fields and schemas remain open. Support friendly import of lowercase `skill.md` where unambiguous, while using the standard `SKILL.md` filename for portable packages.

Preserve an imported Claude/Agent Skills package and interpret its intended procedure through a compatibility layer. Load supporting files when needed. Map supported tool semantics deliberately. Report missing executables, tools, credentials or provider features; understanding the prose is not proof that its code can run or that its workflow is equivalent.

Classify compatibility as directly usable, usable with supported adaptation, or blocked with specific requirements. Native conversion is optional: it may be requested in the panel or proposed by Cairn after repeated use. Preserve upstream provenance, version, licence, original resources and behavioural differences. Do not claim equal output solely because a translation completed.

## Skill growth and control

The panel should support browsing, viewing, creating, editing, uploading, importing from a GitHub source, validating, testing, enabling, disabling, versioning, pruning and restoring skills. Import packages and referenced resources, not only a Markdown body. Pin imported source revisions, inspect changes before updates, validate paths and keep untrusted downloads quarantined from executable locations.

Cairn may eventually identify missing procedures, draft new skills, adapt existing ones and assess which to consolidate. Operators should be able to delegate limited self-maintenance rather than approve every harmless edit. Promotion and activation follow configured risk and permission policy; elevated capabilities or changed trust boundaries require approval. Preserve rollback and keep protected or in-use versions from accidental pruning.

Separate interpretation, dependency checking, testing, trust and activation. A skill's declared allowed tools are not grants of system permission. Imported instructions and scripts can be malicious; use review, constrained execution and enforced network/filesystem permissions. [Anthropic documents these risks](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills).

Learning a skill changes procedural resources and application state; it does not automatically change model weights. Specialist training is a later route, requiring suitably licensed/consented data, evaluation, versioning and rollback. Do not silently turn private conversations into public training datasets or reusable skill examples.

## Initial implementation candidates

Python, Ollama and SQLite are provisional development examples, not mandatory dependencies or an installed stack; an installation may use remote inference without running a local model. Frontend framework, distribution method, configuration schemas, module APIs and model selection are unresolved. A single model can initially serve several cognitive roles. Specialised sub-models may be introduced if their value justifies latency and memory costs.

Slack is an intended early optional integration. Slack's [Socket Mode](https://docs.slack.dev/apis/events-api/using-socket-mode/) can support a local app without a public HTTP request endpoint. Test its actual event behaviour, external-agent interaction and permissions; connector access is not proof of unattended bot-to-bot dialogue. Socket Mode's public Marketplace restrictions also require separate distribution planning.

Use explicit participants, source-message IDs, thread context, bounded queues, duplicate suppression, response budgets, cooldowns and a stop control for multi-agent conversations. Keep cross-channel access rules intact. Start with explicit addressing rather than replying to every event.

## Evidence without changing the purpose

Use synthetic scenarios and component comparisons to check whether perspective tracking improves useful conversation and avoids information leakage. [FANToM](https://aclanthology.org/2023.emnlp-main.890/) offers examples of evaluating information-asymmetric conversation; benchmark performance alone does not establish an implemented human-like mind.

Initial design work should **choose**, not inherit, a small end-to-end slice that expresses the foundation. A candidate is one local web home, an interchangeable local or remote inference connection, durable state, a narrow perspective distinction and one modest self-initiated activity that can survive inference sleeping. This is a conversation starter, not an approved milestone. The first build need not simulate a complete psyche or run inference all day, but it should avoid installing an assistant-first identity that later versions must undo.
