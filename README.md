# Outline-Driven Development

> Vibes are too shallow. Specs are too complex. Let there be the outline.

**Beyond specs. Beyond vibes.** A versioned outline becomes the contract for every agentic act.

[![GitHub Stars](https://img.shields.io/github/stars/OutlineDriven/outline-driven-development?style=flat-square)](https://github.com/OutlineDriven/outline-driven-development/stargazers)
[![License](https://img.shields.io/badge/license-MIT-c8803c?style=flat-square)](LICENSE)
[![Last commit](https://img.shields.io/github/last-commit/OutlineDriven/outline-driven-development?style=flat-square)](https://github.com/OutlineDriven/outline-driven-development/commits/main)
[![Site](https://img.shields.io/badge/site-outlinedriven.github.io-c8803c?style=flat-square)](https://outlinedriven.github.io)

---

## Contents

- [What is Outline-Driven Development](#what-is-outline-driven-development)
- [Implementation](#implementation)
- [Install](#install)
- [Comparison](#comparison)
- [Status](#status-2026-09)
- [Contributing](#contributing)
- [License](#license)

---

## What is Outline-Driven Development

Outline-Driven Development is a coding methodology for LLM code agents. It occupies the space between two failure modes: vibes (too shallow, non-reproducible) and specs (too rigid, too expensive to maintain). The unit of truth is a versioned outline whose hash anchors every diff, every test, and every diagram.

The outline is harness-agnostic. One implementation carries it to every agent, and the methodology
itself lives here as prompt files that any agent can consume. See [PHILOSOPHY.md](PHILOSOPHY.md)
for the full design rationale and traceability model.

---

## Implementation

[odin-claude-plugin](https://github.com/OutlineDriven/odin-claude-plugin) is the single source: 613
skills in 28 plugins, authored once and discovered by Claude Code, Codex, Cursor, and any Agent
Plugins client from the same tree. There is no separate per-agent repository to install or track.

---

## Install

### Claude Code

```
/plugin marketplace add OutlineDriven/odin-claude-plugin
/plugin install odin-core@odin-marketplace
```

### Codex

```
codex plugin marketplace add OutlineDriven/odin-claude-plugin
codex plugin add odin-core@odin-marketplace
```

### Cursor

Add the `OutlineDriven/odin-claude-plugin` marketplace in Cursor, then:

```
/plugin install odin-core
```

Cursor reads the Agent Plugins manifest at each plugin root.

### Pick your plugins

`odin-core` is the base installed above. The other 27 plugins are optional, so add the domains you
work in and skip the rest. Every one installs the same way, for example
`/plugin install odin-security@odin-marketplace`. Three common additions:

| Working on | Add |
|---|---|
| Everyday code changes | `odin-code`, `odin-run` |
| Security review and hardening | `odin-security`, `odin-security-advanced` |
| Research and technical writing | `odin-research`, `odin-writing` |

The full domain-to-plugin table, with the skill count per plugin, is in the
[odin-claude-plugin README](https://github.com/OutlineDriven/odin-claude-plugin#choose-your-plugins).

### CLI Tools

See [INSTALL.md](INSTALL.md) for CLI tool prerequisites and detailed setup.

---

## Comparison

| Aspect | Vibe coding | Spec-driven (Spec Kit) | BMad | **Outline-Driven Development** |
|---|---|---|---|---|
| Source of truth | LLM intuition | Spec doc | Behavioral specs | **Versioned outline (hash-anchored)** |
| Iteration unit | "Try again" | Spec -> re-prompt | BDD scenarios | **Outline node x diff** |
| Validation | Eyeball | Spec compliance | Acceptance tests | **Diagram-first invariants + AST** |
| Tooling | Plain chat | GitHub Spec Kit | BMad CLI | **One plugin tree for Claude Code, Codex, and Cursor** |
| Reuse unit | Conversation | Spec template | Story | **Skill / agent / outline** |
| LLM creativity | Unbounded | Bounded by spec | Bounded by story | **Bounded by outline; preserved within envelope** |
| Best for | Throwaway scripts | Greenfield features | User-facing flows | **Long-lived methodologies + agentic work** |

---

## Status (2026-09)

odin-claude-plugin 2.0.0 is the single implementation, shipping 613 skills across 28 plugins for
Claude Code, Codex, Cursor, and any Agent Plugins client. The three prompt files were stripped of
persona doctrine in early September 2026, so the methodology carries no agent identity of its own.
Releases ship from the implementation repository, not from here.

---

## Contributing

Open an issue to discuss ideas or report bugs. PRs improving the methodology, prompts, or tooling documentation are welcome.

---

## License

MIT — see [LICENSE](LICENSE).
