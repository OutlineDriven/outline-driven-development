# Outline Driven Development: The whole new paradigm for the augumented LLM Code Agent workflows.

## `Vibe`s are too *shallow*, `Spec`s are too *complex*.
### Let there be the `outline`.

### And Indeed... Here it is!

- **Gemini CLI:** https://github.com/OutlineDriven/odin-gemini-cli-extension
- **Claude Code:** https://github.com/OutlineDriven/odin-claude-plugin
- **Codex CLI:** https://github.com/OutlineDriven/odin-codex-plugin

## Prerequisites

`lsd` | `ast-grep` | `ripgrep` | `fd` | MCPs

### Install Various Rust-based CLI Tools with cargo

#### Linux/macOS with cargo

**Install**

```bash
export RUSTFLAGS="-C target-cpu=native -C opt-level=3 -C codegen-units=1 -C strip=symbols"

cargo install lsd
cargo install ast-grep
cargo install ripgrep
cargo install fd-find
```

#### Windows with cargo

**Install (run inside powershell)**
```powershell
$env:RUSTFLAGS="-C target-cpu=native -C opt-level=3 -C codegen-units=1 -C strip=symbols -C link-arg=/LTCG -C link-arg=/OPT:REF"

cargo install lsd
cargo install ast-grep
cargo install ripgrep
cargo install fd-find
```

#### Uninstall

```
cargo uninstall ast-grep ripgrep fd-find
```

### MCPs

#### Crucial
```bash
claude mcp add -s user ast-grep -- uvx --from git+https://github.com/ast-grep/ast-grep-mcp ast-grep-server
claude mcp add -s user context7 npx @upstash/context7-mcp@latest
claude mcp add -s user deepwiki -- npx -y mcp-deepwiki@latest
claude mcp add -s user time uvx mcp-server-time
claude mcp add -s user sequentialthinking-tools npx mcp-sequentialthinking-tools
claude mcp add -s user actor-critic-thinking -- npx -y mcp-server-actor-critic-thinking
claude mcp add -s user shannon-thinking -- npx -y server-shannon-thinking@latest
```

#### Additional
Tavily, Exa, Ref-tools, Consult-ll
