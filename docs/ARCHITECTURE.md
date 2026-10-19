# Architecture direction

**Status:** founding requirements with provisional mechanisms. No runtime or API contract is implemented by this document.

## One system, several boundaries

The intended core consists of conversation coordination, structured memory, perspective representations, an operational self-model, capability planning and policy enforcement. Inference providers supply model execution; they are not Cairn itself. A web interface and messaging integrations use the same core APIs and permission checks.

A proposed processing cycle is: receive an event, establish identity and visibility, retrieve authorised context, consider relevant perspectives and uncertainty, select a response or capability, enforce policy, act, and record the outcome. This is a design sketch, not a mandatory chain of separate model calls. Ordinary exchanges should not require an expensive multi-agent deliberation.

Distinguish event records, externally supplied claims, working world representations, explicitly stated beliefs, inferred hypotheses, durable memories and procedural skills. Retain sources, audience and revision information. An operational record of inputs, chosen tools and evidence is useful; raw model reasoning is neither an authoritative account of a mind nor a required public log.

Access restrictions must apply before retrieval results reach a model. Hypotheses about who knows something cannot grant access to it. Inspecting a perspective representation must itself respect the viewer's permissions. Public-channel availability does not prove awareness or shared understanding.

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

## Web-first experience

Provide a unified web home for conversation and administration. Proposed areas are conversation; overview and runtime status; memory and perspectives; models and providers; connections and integrations; extensions and tools; the skill library; activity, permissions and settings. Group and name these through design work, not a proliferation of unrelated dashboards.

The panel should make readiness, selected model, integration health, queues, permission requests and errors understandable. First-run configuration should establish an installation's identity, provider and optional connections without editing source. Sensitive settings require protected server-side handling, not plaintext echoing into browser state or diagnostic exports.

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

Python, Ollama and SQLite are provisional starting candidates, not an installed or final stack. Frontend framework, distribution method, configuration schemas, module APIs and model selection are unresolved. A single model can initially serve several cognitive roles. Specialised sub-models may be introduced if their value justifies latency and memory costs.

Slack is an intended early optional integration. Slack's [Socket Mode](https://docs.slack.dev/apis/events-api/using-socket-mode/) can support a local app without a public HTTP request endpoint. Test its actual event behaviour, external-agent interaction and permissions; connector access is not proof of unattended bot-to-bot dialogue. Socket Mode's public Marketplace restrictions also require separate distribution planning.

Use explicit participants, source-message IDs, thread context, bounded queues, duplicate suppression, response budgets, cooldowns and a stop control for multi-agent conversations. Keep cross-channel access rules intact. Start with explicit addressing rather than replying to every event.

## Evidence without changing the purpose

Use synthetic scenarios and component comparisons to check whether perspective tracking improves useful conversation and avoids information leakage. [FANToM](https://aclanthology.org/2023.emnlp-main.890/) offers examples of evaluating information-asymmetric conversation; benchmark performance alone does not establish an implemented human-like mind.

Initial design work should choose the smallest end-to-end slice that expresses this foundation: a recognisable web home, one inference adapter, core conversation, minimal durable state and a narrow perspective distinction. Do not implement the entire vision in one pass.
