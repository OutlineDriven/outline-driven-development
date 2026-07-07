# Outline-Driven Development

> Vibes are too shallow. Specs are too complex. Let there be the outline.

**Beyond specs. Beyond vibes.** A versioned outline becomes the contract for every agentic act.

[![GitHub Stars](https://img.shields.io/github/stars/OutlineDriven/outline-driven-development?style=flat-square)](https://github.com/OutlineDriven/outline-driven-development/stargazers)
[![License](https://img.shields.io/badge/license-MIT-c8803c?style=flat-square)](LICENSE)
[![Last commit](https://img.shields.io/github/last-commit/OutlineDriven/outline-driven-development?style=flat-square)](https://github.com/OutlineDriven/outline-driven-development/commits/main)
[![Site](https://img.shields.io/badge/site-outlinedriven.github.io-c8803c?style=flat-square)](https://outlinedriven.github.io)

---

## Contents

- [What is Outline-Driven Development?](#what-is-outline-driven-development)
- [Install](#install)
- [Comparison](#comparison)
- [Recent Updates](#recent-updates)
- [Contributing](#contributing)
- [License](#license)

---

## What is Outline-Driven Development?

Outline-Driven Development is a coding methodology for LLM code agents. It occupies the space between two failure modes: vibes (too shallow, non-reproducible) and specs (too rigid, too expensive to maintain). The unit of truth is a versioned outline whose hash anchors every diff, every test, and every diagram.

See [PHILOSOPHY.md](PHILOSOPHY.md) for the full design rationale and traceability model.

---

## Install

| Host | Repo | Quick install |
|---|---|---|
| Claude Code | [odin-claude-plugin](https://github.com/OutlineDriven/odin-claude-plugin) | `wget -O ~/.claude/CLAUDE.md https://raw.githubusercontent.com/OutlineDriven/odin-claude-plugin/refs/heads/main/CLAUDE.md && claude plugin marketplace add OutlineDriven/odin-claude-plugin && claude plugin install odin@odin-marketplace` |
| Codex CLI | [odin-codex-plugin](https://github.com/OutlineDriven/odin-codex-plugin) | `git clone https://github.com/OutlineDriven/odin-codex-plugin.git && rsync -a ./odin-codex-plugin/ ~/.codex/` |
| Gemini CLI | [odin-gemini-cli-extension](https://github.com/OutlineDriven/odin-gemini-cli-extension) | `gemini extensions install https://github.com/OutlineDriven/odin-gemini-cli-extension` |
| Any IDE / agent (prompt-only) | — | [GENERIC\_PROMPT.md](GENERIC_PROMPT.md) |
| Compact prompt | — | [COMPACT\_PROMPT.md](COMPACT_PROMPT.md) |

See [INSTALL.md](INSTALL.md) for CLI tool prerequisites and detailed setup.

---

## Comparison

<a id="comparison"></a>

| Aspect | Vibe coding | Spec-driven (Spec Kit) | BMad | **Outline-Driven Development** |
|---|---|---|---|---|
| Source of truth | LLM intuition | Spec doc | Behavioral specs | **Versioned outline (hash-anchored)** |
| Iteration unit | "Try again" | Spec -> re-prompt | BDD scenarios | **Outline node x diff** |
| Validation | Eyeball | Spec compliance | Acceptance tests | **Diagram-first invariants + AST** |
| Tooling | Plain chat | GitHub Spec Kit | BMad CLI | **Plugins for Claude / Codex / Gemini** |
| Reuse unit | Conversation | Spec template | Story | **Skill / agent / outline** |
| LLM creativity | Unbounded | Bounded by spec | Bounded by story | **Bounded by outline; preserved within envelope** |
| Best for | Throwaway scripts | Greenfield features | User-facing flows | **Long-lived methodologies + agentic work** |

---

## Recent Updates

**2026-04**

- **Execution default flipped:** dependent tasks run sequentially by default; parallel only when independence is provable. Reviewer subagent inserted between every worker phase.
- **Testing charter narrowed:** A test exists only if deleting it would let a real bug reach prod. Skip config-shape/constructor-output tests *only* when a static guarantee covers them (Rust, TS-strict, Kotlin, Java, C++); keep boundary shape/type tests in dynamic languages (Python, JS, Ruby).
- **Token-Efficient Output [MANDATORY]:** ANSI/decoration suppression, discovery-then-targeted-read pattern, per-tool flag table.
- **Completion Gate [MANDATORY]:** Run repo-native verification before declaring task complete.
- **DOD anchor:** Data layout first (SoA vs AoS, alignment, padding), hot/cold split, batch homogeneity, zero-copy boundaries.
- **OCaml 5.2+ language profile** added.
- **Commit hygiene tightened:** one concern per commit, never bundle unrelated changes.
- **Post-Agent Verify:** read back modified files after subagent edits; line-count mismatch = critical failure.

---

## Contributing

Open an issue to discuss ideas or report bugs. PRs improving the methodology, prompts, or tooling documentation are welcome.

---

## License

MIT — see [LICENSE](LICENSE).
