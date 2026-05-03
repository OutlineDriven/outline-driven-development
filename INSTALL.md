# Prerequisites and Install Details

## Required CLI Tools

`ast-grep` | `ripgrep` | `fd` | `eza` | `lsd` | `tokei` | `bat` | `just` | `git-branchless` | `difftastic` | `procs` | `fend` | `hck` | `hyperfine` | and others

### Install Cargo (if not installed)

<https://rustup.rs/>

### Linux/macOS

```bash
export RUSTFLAGS="-C target-cpu=native -C link-arg=-fuse-ld=mold -C opt-level=3 -C strip=symbols -C panic=abort"

cargo install --locked cargo-binstall
cargo install ast-grep ripgrep fd-find eza lsd
cargo binstall -y bat tokei git-delta just raff-cli difftastic git-branchless zoxide procs bfs fselect tealdeer srgn nomino shellharden grex mergiraf jaq jql hck huniq lemmeknow hyperfine rargs eva fend rip2 sccache
```

### Windows (PowerShell)

```powershell
$env:RUSTFLAGS="-C target-cpu=native -C opt-level=3 -C strip=symbols -C panic=abort -C link-arg=/LTCG -C link-arg=/OPT:REF"

cargo install --locked --force cargo-binstall
cargo install ast-grep ripgrep fd-find eza lsd
cargo binstall -y bat tokei git-delta just raff-cli difftastic git-branchless zoxide procs bfs fselect tealdeer srgn nomino shellharden grex mergiraf jaq jql hck huniq lemmeknow hyperfine rargs eva fend rip2 sccache
```

## Recommended MCP Extensions

### Crucial (automatically installed)

repomix | sequentialthinking-tools | actor-critic-thinking | shannon-thinking

### Additional (manually install if needed)

Time, Context7, Tavily, Exa, Github-grep, Deepwiki, Ref-tools
