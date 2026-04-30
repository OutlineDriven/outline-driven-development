# Outline-Driven Development — Philosophy

> Deterministic scaffolds harness non-deterministic LLM creativity only when the outline stays the single source of truth and every downstream stage revalidates against it.

## Deterministic with Non-Deterministic LLMs

- **Outline-as-assembly:** Human intent, compliance constraints, and architectural guardrails are compiled into a versioned outline whose hash becomes the control envelope for every agentic act.
- **LLM-as-module:** LLM calls are intentionally non-deterministic but bounded by the outline contract; disagreement between generated code and outline immediately halts or replays the step.
- **Telemetry feedback:** Execution traces, test verdicts, and rubric scores continuously feed back into the outline refinement loop to converge to a reproducible build.

**Control Envelope Checklist**

1. Canonical outline stored with content-addressable ID and time-windowed approvals.
2. Every agent invocation receives a minimized delta (outline slice) plus explicit success metrics.
3. Determinism is measured: diff noise <= 2% between successive outline-conformant runs; higher variance triggers outline tightening before reattempting generation.

## Design-First / Batteries Included

- **Architecture-first:** Each outline must include interfaces, pre/postconditions, error domains, latency and memory budgets before code exists.
- **Tooling-first:** Structural edits, search, and orchestration must be reproducible through explicit tooling (e.g., AST-aware search, grammar-scoped transforms, MCP servers). Tool choices are implementation detail; reproducibility is the invariant.
- **Quality gates:** Spec -> outline -> implementation is instrumented with lint/test/benchmark gates plus rollback hooks.
- **Observability:** Outline nodes ship tracing IDs and contract assertions so failures are attributable to outline leaves rather than opaque LLM conversations.

## Traceability Matrix

| Diagram | Goal | Associated Invariants |
|---|---|---|
| Architecture | Map outline-to-toolchain interfaces | Outline versions are strictly ordered; no rollback to a prior version without an explicit revert entry |
| Data-flow | Guarantee data never bypasses verification | Contract-bound IO only |
| Concurrency | Preserve happens-before relationships | No circular waits; deadlock-free |
| Memory | Ensure ownership + persistence model | Leak-free caches, append-only audit |
| Optimization | Tie budgets to feedback loops | Regression triggers deterministic rollback |
