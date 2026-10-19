# Cairn

**An open, self-hosted AI system built around perspective, continuity and growth.**

Cairn is intended to be a coherent conversational participant with durable memory, an operational self-model, models of others, and an extensible set of capabilities. Theory of Mind informs its ordinary processing, rather than appearing only in a special prompt. Research serves the development of Cairn; Cairn is not primarily a benchmark project.

## Project state

This branch contains a **founding documentation scaffold only**. There is no runnable application, web panel, model integration, skill runtime or Slack bot yet. Aspirations below are not implemented features. Read [current state](docs/STATUS.md) before beginning work.

## Intended experience

A unified, distinctly Cairn web interface will be the default place to converse with and manage an installation. Users should be able to configure inference, inspect memory and permissions, and manage modular tools, skills and connections. Slack is an optional integration, not the host of Cairn's core identity or memory.

Models, communication channels and deployment environments should be replaceable without discarding an installation's continuity. Local inference is the initial direction; external services remain explicit choices rather than hidden requirements.

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
