# Outline Driven Development: 증강된 LLM 코드 에이전트 워크플로우를 위한 완전히 새로운 패러다임.

## `Vibe`s are too *shallow*, `Spec`s are too *complex*.
### Let there be the `outline`.

### And Indeed... Here it is!

## 필요 도구들 (Prerequisites)

`ast-grep` | `ripgrep` | `fd` | `eza` | `tokei` | `bat` | `jj` | MCPs

### cargo를 사용한 다양한 Rust 기반 CLI 도구 설치

#### Install Cargo (if not installed)

**Linux/macOS**
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

**Windows**
<https://win.rustup.rs/x86_64>

#### For Linux/macOS

**설치**

```bash
export RUSTFLAGS="-C target-cpu=native -C opt-level=3 -C codegen-units=1 -C strip=symbols"

cargo install ast-grep ripgrep fd-find eza tokei bat git-delta just raff-cli tree-sitter-cli difftastic jj jj-cli
```

#### For Windows

**설치 (powershell 내부에서 실행)**
```powershell
$env:RUSTFLAGS="-C target-cpu=native -C opt-level=3 -C codegen-units=1 -C strip=symbols -C link-arg=/LTCG -C link-arg=/OPT:REF"

cargo install ast-grep ripgrep fd-find eza tokei bat git-delta just raff-cli tree-sitter-cli difftastic jj jj-cli
```

## 설치

- **Gemini CLI:** <https://github.com/OutlineDriven/odin-gemini-cli-extension>
  - 빠른 설치:
  - ```gemini extensions install https://github.com/OutlineDriven/odin-gemini-cli-extension```
- **Claude Code:** <https://github.com/OutlineDriven/odin-claude-plugin>
  - 빠른 설치:
    - 1. File Based (Recommended): ```git clone https://github.com/OutlineDriven/odin-claude-plugin.git && cp -r ./odin-claude-plugin/ ~/.claude/```
    - 2. Plugin Based (Claude Marketplace): ```claude plugin marketplace add OutlineDriven/odin-claude-plugin && claude plugin install odin-claude-plugin@odin-marketplace```
- **Codex CLI:** <https://github.com/OutlineDriven/odin-codex-plugin>

- **프롬프트 전용 (*Antigravity/Windsurf/Cursor/Augument Code 등과 같은 IDE/에이전트에 수동 적용*):** [Prompt](GENERIC_PROMPT.md)
- **컴팩트 프롬프트 전용 (*Antigravity/Windsurf/Cursor/Augument Code 등과 같은 IDE/에이전트에 수동 적용*):** [Prompt](COMPACTED_PROMPT.md)

### MCP 확장 추천

#### 필수 (Crucial) [자동으로 설치됩니다]
ast-grep | context7 | sequentialthinking-tools | actor-critic-thinking | shannon-thinking

#### 추가 (Additional) [필요시 수동 설치 권장]
Time, Tavily, Exa, Ref-tools

## 아웃라인 주도 개발 철학 (Outline-Driven Development Philosophy)

> 결정론적 스캐폴드(scaffold)는 아웃라인이 유일한 진실의 원천(single source of truth)으로 유지되고 모든 다운스트림 단계가 이에 대해 재검증될 때만 비결정론적 LLM의 창의성을 활용합니다.

### 본질적으로 비결정론적인 LLM을 활용한 결정론적 방식

- **Outline-as-assembly (어셈블리로서의 아웃라인):** 인간의 의도, 규정 준수 제약 조건, 아키텍처 가드레일이 버전 관리된 아웃라인으로 컴파일되며, 이 아웃라인의 해시가 모든 에이전트 행위의 제어 봉투(control envelope)가 됩니다.
- **LLM-as-module (모듈로서의 LLM):** LLM 호출은 의도적으로 비결정론적이지만 아웃라인 계약에 의해 범위가 제한됩니다. 생성된 코드와 아웃라인 간의 불일치는 해당 단계를 즉시 중단시키거나 재생(replay)하게 합니다.
- **Telemetry feedback (원격 측정 피드백):** 실행 추적, 테스트 판정, 루브릭 점수가 아웃라인 정제 루프에 지속적으로 피드백되어 재현 가능한 빌드로 수렴하도록 합니다.

**제어 봉투 체크리스트 (Control Envelope Checklist)**

1. 콘텐츠 주소 지정 가능 ID 및 시간 윈도우 승인이 포함된 표준 아웃라인 저장.
2. 모든 에이전트 호출은 최소화된 델타(아웃라인 슬라이스)와 명시적인 성공 지표를 받습니다.
3. 결정론 측정: 아웃라인을 준수하는 연속적인 실행 간의 diff 노이즈가 2% 이하이어야 함; 더 높은 분산은 생성을 재시도하기 전에 아웃라인을 더 엄격하게 조이도록 트리거합니다.

### 디자인 우선 / 모범 사례 배터리 포함 (Design-First / Best-Practices Batteries Included)

- **Architecture-first (아키텍처 우선):** 각 아웃라인은 코드가 존재하기 전에 인터페이스, 사전/사후 조건, 오류 도메인, 대기 시간 및 메모리 예산을 포함해야 합니다.
- **Tooling-first (도구 우선):** `eza`, `ast-grep`, `ripgrep`, `fd`, LangGraph, MCP 스택은 필수 배터리로 취급되어 구조적 편집, 검색, 오케스트레이션이 재현 가능하도록 합니다.
- **Quality gates (품질 게이트):** 명세(Spec) → 아웃라인 → 구현 과정은 린트/테스트/벤치마크 게이트 및 롤백 훅으로 계측됩니다.
- **Observability (관찰 가능성):** 아웃라인 노드는 추적 ID와 계약 어설션을 전송하므로, 실패의 원인을 불투명한 LLM 대화가 아닌 아웃라인 리프(leaf)로 귀속시킬 수 있습니다.

### 추적성 매트릭스 (Traceability Matrix)

| 다이어그램 | 목표 | 관련 불변량 |
| --- | --- | --- |
| 아키텍처 | 아웃라인-툴체인 인터페이스 매핑 | 아웃라인 해시 단조성 |
| 데이터 흐름 | 데이터가 검증을 우회하지 않도록 보장 | 계약에 구속된 IO만 허용 |
| 동시성 | 발생 전(happens-before) 관계 보존 | 순환 대기 없음; 데드락 자유 |
| 메모리 | 소유권 + 지속성 모델 보장 | 누수 없는 캐시, 추가 전용(append-only) 감사 |
| 최적화 | 예산을 피드백 루프에 연결 | 회귀 발생 시 결정론적 롤백 트리거 |
