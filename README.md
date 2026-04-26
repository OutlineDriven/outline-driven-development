# Outline Driven Development: The whole new paradigm for the augumented LLM Code Agent workflows.

## `Vibe`s are too *shallow*, `Spec`s are too *complex*.
### Let there be the `outline`.

### And Indeed... Here it is!

## Prerequisites

`ast-grep` | `ripgrep` | `fd` | `eza` | `lsd` | `tokei` | `bat` | `just` | `git-branchless` | `difftastic` | `procs` | `fend` | `hck` | `hyperfine` | +`other tools` | `MCPs` (**context7**, **sequentialthinking-tools**, **actor-critic-thinking**, **shannon-thinking**, **repomix**)

### Install Various Rust-based CLI Tools with highest native optimizations through cargo

#### Install Cargo (if not installed)

<https://rustup.rs/>

#### Linux/macOS with cargo

**Install**

```bash
export RUSTFLAGS="-C target-cpu=native -C link-arg=-fuse-ld=mold -C opt-level=3 -C strip=symbols -C panic=abort -C lto=thin"

cargo install --locked cargo-binstall
cargo install ast-grep ripgrep fd-find eza lsd
cargo binstall -y bat tokei git-delta just raff-cli difftastic git-branchless zoxide procs bfs fselect tealdeer srgn nomino shellharden grex mergiraf jaq jql hck huniq lemmeknow hyperfine rargs eva fend rip2 sccache
```

#### Windows with cargo

**Install (run inside powershell)**
```powershell
$env:RUSTFLAGS="-C target-cpu=native -C opt-level=3 -C strip=symbols -C panic=abort -C lto=thin -C link-arg=/LTCG -C link-arg=/OPT:REF"

cargo install --locked cargo-binstall
cargo install ast-grep ripgrep fd-find eza lsd
cargo binstall -y bat tokei git-delta just raff-cli difftastic git-branchless zoxide procs bfs fselect tealdeer srgn nomino shellharden grex mergiraf jaq jql hck huniq lemmeknow hyperfine rargs eva fend rip2 sccache
```

## Installation

- **Gemini CLI:** <https://github.com/OutlineDriven/odin-gemini-cli-extension>
  - Quick Install:
  - ```gemini extensions install https://github.com/OutlineDriven/odin-gemini-cli-extension```
- **Claude Code:** <https://github.com/OutlineDriven/odin-claude-plugin>
  - Quick Install:
    - ```wget -O ~/.claude/CLAUDE.md https://raw.githubusercontent.com/OutlineDriven/odin-claude-plugin/refs/heads/main/CLAUDE.md && claude plugin marketplace add OutlineDriven/odin-claude-plugin && claude plugin install odin@odin-marketplace```
- **Codex CLI:** <https://github.com/OutlineDriven/odin-codex-plugin>
  - Quick Install:
    - ```git clone https://github.com/OutlineDriven/odin-codex-plugin.git && cp -r ./odin-codex-plugin/ ~/.codex/```
- **Prompt-only (*Manual Apply for IDEs/Agents like Antigravity/Windsurf/Cursor/Augument Code ...*):** [Prompt](GENERIC_PROMPT.md)
- **Compact Prompt-only (*Manual Apply for IDEs/Agents like Antigravity/Windsurf/Cursor/Augument Code ...*):** [Prompt](COMPACTED_PROMPT.md)

### Recommended MCP Extensions

#### Crucial [Automatically installed]
ast-grep | context7 | sequentialthinking-tools | actor-critic-thinking | shannon-thinking

#### Additional [Manually install if needed]
Time, Tavily, Exa, Ref-tools

## Outline-Driven Development Philosophy

> Deterministic scaffolds harness non-deterministic LLM creativity only when the outline stays the single source of truth and every downstream stage revalidates against it.

### Deterministic-with-Non-Deterministic-LLMs-by-Nature

- **Outline-as-assembly:** Human intent, compliance constraints, and architectural guardrails are compiled into a versioned outline whose hash becomes the control envelope for every agentic act.
- **LLM-as-module:** LLM calls are intentionally non-deterministic but bounded by the outline contract; disagreement between generated code and outline immediately halts or replays the step.
- **Telemetry feedback:** Execution traces, test verdicts, and rubric scores continuously feed back into the outline refinement loop to converge to a reproducible build.

**Control Envelope Checklist**

1. Canonical outline stored with content-addressable ID and time windowed approvals.
2. Every agent invocation receives a minimized delta (outline slice) plus explicit success metrics.
3. Determinism is measured: diff noise ≤ 2% between successive outline-conformant runs; higher variance triggers outline tightening before reattempting generation.

### Design-First / Best-Practices Batteries Included

- **Architecture-first:** Each outline must include interfaces, pre/postconditions, error domains, latency and memory budgets before code exists.
- **Tooling-first:** `eza`, `ast-grep`, `ripgrep`, `fd`, LangGraph, and MCP stacks are treated as mandatory batteries so that structural edits, search, and orchestration are reproducible.
- **Quality gates:** Spec → outline → implementation is instrumented with lint/test/benchmark gates plus rollback hooks.
- **Observability:** Outline nodes ship tracing IDs and contract assertions so failures are attributable to outline leaves rather than opaque LLM conversations.

### Traceability Matrix

| Diagram | Goal | Associated Invariants |
| --- | --- | --- |
| Architecture | Map outline-to-toolchain interfaces | Outline hash monotonicity |
| Data-flow | Guarantee data never bypasses verification | Contract-bound IO only |
| Concurrency | Preserve happens-before relationships | No circular waits; deadlock-free |
| Memory | Ensure ownership + persistence model | Leak-free caches, append-only audit |
| Optimization | Tie budgets to feedback loops | Regression triggers deterministic rollback |

## Recent updates (2026-04)

- **Execution default flipped:** Review-Gated Sequencing is the default for dependent tasks; Parallel only when independence is provable. Reviewer subagent inserted between every worker phase.
- **Testing charter narrowed:** A test exists only if deleting it would let a real bug reach prod. Skip config-shape/constructor-output tests *only* when a static guarantee covers them (Rust, TS-strict, Kotlin, Java, C++); keep boundary shape/type tests in dynamic languages (Python, JS, Ruby).
- **Token-Efficient Output [MANDATORY]:** ANSI/decoration suppression, discovery-then-targeted-read pattern, per-tool flag table.
- **Completion Gate [MANDATORY]:** Run repo-native verification (e.g., `pytest`+`pyright`, `cargo test`+`clippy`) before declaring task complete.
- **DOD anchor in CS anchors:** Data layout first (SoA vs AoS, alignment, padding), hot/cold split, batch homogeneity, zero-copy boundaries, no pointer-chasing in hot loops.
- **OCaml 5.2+ language profile** added: `.mli`-first, `result`+`let*`/`let+`, Eio direct-style, dune 3.x + opam 2.2+, Alcotest+QCheck.
- **Commit hygiene tightened:** never bundle unrelated changes; one concern touching N files = 1 commit, not N commits.
- **Post-Agent Verify:** read back modified files after subagent edits; line-count mismatch = critical failure → rollback.
