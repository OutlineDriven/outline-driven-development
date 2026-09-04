# Outline-Driven Development

> 바이브는 너무 얕습니다. 스펙은 너무 복잡합니다. 아웃라인이 있으라.

**스펙을 넘어서. 바이브를 넘어서.** 버전 관리된 아웃라인이 모든 에이전트 행위의 계약이 됩니다.

[![GitHub Stars](https://img.shields.io/github/stars/OutlineDriven/outline-driven-development?style=flat-square)](https://github.com/OutlineDriven/outline-driven-development/stargazers)
[![License](https://img.shields.io/badge/license-MIT-c8803c?style=flat-square)](LICENSE)
[![Last commit](https://img.shields.io/github/last-commit/OutlineDriven/outline-driven-development?style=flat-square)](https://github.com/OutlineDriven/outline-driven-development/commits/main)
[![Site](https://img.shields.io/badge/site-outlinedriven.github.io-c8803c?style=flat-square)](https://outlinedriven.github.io)

---

## 목차

- [Outline-Driven Development란?](#outline-driven-development란)
- [구현체](#구현체)
- [설치](#설치)
- [비교](#비교)
- [상태](#상태-2026-09)
- [기여](#기여)
- [라이선스](#라이선스)

---

## Outline-Driven Development란?

Outline-Driven Development는 LLM 코드 에이전트를 위한 코딩 방법론입니다. 두 가지 실패 모드 사이의 영역을 차지합니다. 바이브는 너무 얕고 재현 불가능하며, 스펙은 너무 경직되어 유지 비용이 높습니다. 진실의 단위는 버전 관리된 아웃라인이며, 그 해시가 모든 디프, 모든 테스트, 모든 다이어그램을 고정합니다.

아웃라인은 하네스에 종속되지 않습니다. 구현체는 특정 에이전트를 위한 플러그인과 확장으로 배포되며, 방법론 자체는 모든 에이전트가 사용할 수 있는 프롬프트 파일로 이 저장소에 있습니다. 전체 설계 근거와 추적 가능성 모델은 [PHILOSOPHY.md](PHILOSOPHY.md)를 참조하십시오.

---

## 구현체

[odin-claude-plugin](https://github.com/OutlineDriven/odin-claude-plugin)이 유일한 소스입니다. 28개
플러그인에 613개 스킬을 한 번만 작성하며, Claude Code, Codex, Cursor, 그리고 모든 Agent Plugins
클라이언트가 동일한 트리에서 이를 발견합니다. 에이전트별로 따로 설치하거나 관리할 저장소는 없습니다.

---

## 설치

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

Cursor에서 `OutlineDriven/odin-claude-plugin` 마켓플레이스를 추가한 뒤:

```
/plugin install odin-core
```

Cursor는 각 플러그인 루트의 Agent Plugins 매니페스트를 읽습니다.

### Devin

Devin에는 마켓플레이스 단계가 없습니다. Devin은 `.devin/skills/<skill>/SKILL.md`에서 프로젝트 스킬을
읽으며, 이 저장소는 플러그인 트리를 평탄화하여 생성한 미러로 모든 스킬을 그 경로에 담고 있습니다.
`.devin/skills/index.json`은 각 스킬이 속한 플러그인과 미러링한 릴리스를 기록합니다.
[.devin/skills/README.md](.devin/skills/README.md)를 참조하십시오.

### 플러그인 선택

위에서 설치한 `odin-core`가 기본입니다. 나머지 27개 플러그인은 선택 사항이므로, 작업하는 영역만
추가하고 나머지는 건너뛰십시오. 설치 명령은 모두 같은 형태입니다. 예를 들어
`/plugin install odin-security@odin-marketplace`입니다. 자주 쓰이는 세 가지 추가 조합입니다.

| 작업 영역 | 추가 |
|---|---|
| 일상적인 코드 변경 | `odin-code`, `odin-run` |
| 보안 검토와 강화 | `odin-security`, `odin-security-advanced` |
| 리서치와 기술 문서 작성 | `odin-research`, `odin-writing` |

플러그인별 스킬 수를 포함한 전체 영역별 표는
[odin-claude-plugin README](https://github.com/OutlineDriven/odin-claude-plugin#choose-your-plugins)에 있습니다.

### CLI 도구 설치

CLI 도구 사전 요구 사항과 상세 설정은 [INSTALL.md](INSTALL.md)를 참조하십시오.

---

## 비교

| 측면 | 바이브 코딩 | 스펙 주도 (Spec Kit) | BMad | **아웃라인 주도 개발** |
|---|---|---|---|---|
| 진실의 원천 | LLM 직관 | 스펙 문서 | 행동 스펙 | **버전 관리된 아웃라인 (해시 고정)** |
| 반복 단위 | "다시 시도" | 스펙 -> 재프롬프트 | BDD 시나리오 | **아웃라인 노드 x 디프** |
| 검증 | 육안 검사 | 스펙 준수 | 인수 테스트 | **다이어그램 우선 불변량 + AST** |
| 도구 | 일반 채팅 | GitHub Spec Kit | BMad CLI | **Claude Code, Codex, Cursor를 위한 단일 플러그인 트리** |
| 재사용 단위 | 대화 | 스펙 템플릿 | 스토리 | **스킬 / 에이전트 / 아웃라인** |
| LLM 창의성 | 제한 없음 | 스펙으로 제한 | 스토리로 제한 | **아웃라인으로 제한; 봉투 내에서 보존** |
| 적합 분야 | 일회성 스크립트 | 그린필드 기능 | 사용자 대면 흐름 | **장수 방법론 + 에이전트 작업** |

---

## 상태 (2026-09)

odin-claude-plugin 2.0.0이 유일한 구현체이며, Claude Code, Codex, Cursor, 그리고 모든 Agent Plugins
클라이언트를 위해 28개 플러그인에 613개 스킬을 제공합니다. 2026년 9월 초에 세 개의 프롬프트 파일에서
페르소나 독트린을 제거했으므로, 방법론 자체는 어떤 에이전트 정체성도 갖지 않습니다. 릴리스는 이
저장소가 아니라 구현체 저장소에서 출시됩니다.

---

## 기여

아이디어 논의나 버그 보고를 위해 이슈를 여십시오. 방법론, 프롬프트, 도구 문서를 개선하는 PR을 환영합니다.

이 저장소에서 `.devin/skills/`를 직접 수정하지 마십시오. 그 아래의 모든 파일은
[odin-claude-plugin](https://github.com/OutlineDriven/odin-claude-plugin)의
`scripts/sync-outline-skills.mjs`가 생성하며, 플러그인 트리에서 사라진 파일은 이 스크립트가 삭제합니다.
해당 저장소의 `plugins/<plugin>/skills/<slug>/`에서 스킬을 수정한 뒤 그곳에서 `just sync-outline`을
실행하십시오. 스크립트는 기본적으로 형제 디렉터리 `../outline-driven-development`에 기록하며,
`node scripts/sync-outline-skills.mjs --target <path>`로 대상을 바꾸고 `--check`로 기록 없이 드리프트만
보고할 수 있습니다.

---

## 라이선스

MIT — [LICENSE](LICENSE) 참조.
