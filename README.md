# Cairn

**An open, self-hosted home for an autonomous AI participant—grounded in Theory of Mind and a model of the psyche.**

Cairn is a stack for a continuing participant, powered by one model or cooperating submodels, with durable identity and memory, its own evolving priorities, models of others, reflective learning and self-initiated activity. It is **not an assistant product**: helping a person may be one chosen activity, not an imposed purpose or personality. Its conversational participant can develop a name and character distinct from the Cairn stack.

The vision is resource-aware presence when the host is available, not nonstop GPU inference. Expensive models should be able to sleep or unload while lightweight services retain continuity, listen for permitted events and resume worthwhile work. The psyche and Theory-of-Mind concepts are design commitments, not evidence of consciousness or human-like subjective experience.

## Project state

This branch contains a **founding documentation scaffold only**. There is no runnable application, web panel, model integration, skill runtime or Slack bot yet. Aspirations below are not implemented features. Read [current state](docs/STATUS.md) before beginning work.

## Local-first home, mix-and-match capabilities

Cairn's default core runs on the installation owner's computer, with its browser panel reached through **localhost**. The web interface is not evidence of cloud hosting. Memory, identity, configuration and basic management should work offline once installed, and local inference should allow fully offline conversation where an appropriate local model is available.

**The stack must also support remote inference, remote integrations and remote endpoints as first-class, optional resources.** A local model is not required if the user chooses remote inference. Local and remote providers, connections, tools and endpoints can be combined per installation—and selected for permitted activities by humans or by Cairn's participating models. Bring-your-own-key (BYOK), per-integration credentials, scopes, data-sharing controls and resource/cost budgets are foundational requirements, not one global network access toggle. A hosted core or remote web interface is a separate optional deployment choice.

## Intended experience

A unified, distinctly Cairn web interface will be the participant's home for conversation, visible self-directed activity and installation management. Users should be able to configure inference, inspect memory and permissions, and manage modular tools, skills and connections. Slack is an optional integration, not the host of Cairn's core identity or memory.

Models, communication channels and deployment environments should be replaceable without discarding an installation's continuity. Its core must be able to initiate authorised work without first receiving a chat prompt. Inference may run locally or remotely through independently configured providers. No one runtime, vendor or cloud account is a prerequisite for Cairn's core.

## Start here

- [Charter](CHARTER.md): purpose, identity and guiding principles.
- [Architecture direction](docs/ARCHITECTURE.md): boundaries, interface ambitions, Skills and open choices.
- [Development standards](CONTRIBUTING.md): reproducibility, documentation, tests and collaboration.
- [Agent entry point](AGENTS.md): concise instructions for machine contributors.
- [Current state](docs/STATUS.md): verified scope, unresolved decisions and next work.

The repository at the selected branch and commit is the shared engineering record. No private chat, personal memory, vendor-specific workspace or founder configuration is required to understand this scaffold.

## Public code, private installations

Cairn must not ship personal identities, conversations, credentials, psychological profiles or deployment-specific accounts. Configuration and runtime data belong outside source control. Examples and tests must use synthetic data. Do not submit secrets or private logs in public issues or pull requests.

## Licence

The project uses the existing [MIT licence](LICENSE). Separately acquired models, skills, dependencies and datasets retain their own licences and notices; importing them does not relicense them as Cairn source.
