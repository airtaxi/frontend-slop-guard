# AI 슬롭 UI를 미리 방지하세요.

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

🌐 [English](README.md) | 한국어

Frontend Slop Guard는 AI가 만든 인터페이스가 슬롭 UI가 되지 않도록 막는 에이전트 스킬입니다. AI 디자인에서 흔히 나타나는 열 가지 신호를 구체적인 규칙으로 정리하여, 프런트엔드를 작성하거나 검토할 때 그대로 적용할 수 있습니다.

실행에 사용하는 산출물은 순수한 마크다운 파일인 `SKILL.md` 하나이므로, 스킬 형식의 지침을 읽는 하네스라면 어디에서든 사용할 수 있습니다.

## 주요 기능

- UI를 출시하기 전에 열 가지 슬롭 신호를 걸러냅니다. 그라디언트 남용부터 과장된 태그라인까지 포함합니다.
- 신호마다 자체 점검을 제공하고, 출시 전 점검 목록과 리뷰 모드를 함께 담았습니다.
- `SKILL.md`를 읽는 하네스라면 마크다운 파일 하나로 그대로 사용할 수 있습니다.
- 신호별 예시 이미지 16장과 요약 표를 포함합니다.

## 잡아내는 슬롭 신호

| # | 신호 | 한 줄 규칙 |
| --- | --- | --- |
| 1 | 그라디언트 남용 | 화면마다 한 곳, 초점 한 곳에만 그라디언트를 사용합니다. |
| 2 | 무의미한 색상 남용 | 70-30-10 비율을 지키고, 색상은 의미를 전달할 때만 사용합니다. |
| 3 | 맥동하는 배지와 중복 배지 | 값이 바뀔 수 있을 때만 상태 배지를 표시합니다. |
| 4 | fingernail card | 카드 왼쪽의 얇은 강조 막대를 없애고 배경 톤, 테두리, 글꼴로 강조합니다. |
| 5 | 이모지 남용 | 하나의 아이콘 세트로 통일하고, 이모지는 내용 전달에만 사용합니다. |
| 6 | 정렬 오류 | 모든 요소를 그리드나 기준선에 맞춥니다. |
| 7 | 기본 폰트와 `//` 장식 | 상황에 맞는 폰트를 고르고, 고정폭 폰트는 실제 코드에만 사용합니다. |
| 8 | 대화 맥락에서 비롯된 불필요한 문구 | 사용자의 판단에 도움이 되는 내용만 씁니다. |
| 9 | 유리 효과와 획일적인 브루탈리즘 | 하나의 디자인 언어를 정하고, 겹치거나 떠 있는 표면에만 유리 효과를 씁니다. |
| 10 | 일반적인 태그라인과 과장 | 금지한 태그라인과 습관적인 부제목을 없앱니다. |

## 적용 범위

HTML, CSS, SCSS, JS, TS, JSX, TSX, Vue, Svelte, Astro, Tailwind를 비롯한 웹 프런트엔드 작업에 적용합니다. WinUI XAML, WPF, MAUI, React Native, Flutter처럼 데스크톱과 모바일 화면의 시각 스타일을 다루는 작업에도 적용합니다. 기존 UI를 검토하거나 리팩터링할 때에도 같은 규칙을 사용합니다.

## 설치

### 직접 설치

하네스가 읽는 스킬 디렉터리에 저장소를 복제한 뒤, 세션을 다시 시작하거나 스킬을 다시 불러옵니다.

```bash
git clone https://github.com/airtaxi/frontend-slop-guard.git <skills-dir>/frontend-slop-guard
```

주요 설치 위치는 다음과 같습니다.

- OpenCode, Claude Code(맥과 리눅스): `~/.config/opencode/skills/`, `~/.claude/skills/`
- OpenCode(윈도): `C:/Users/<you>/.config/opencode/skills/`

### Skills CLI

```bash
npx skills add airtaxi/frontend-slop-guard --global
```

## 저장소 구조

```
SKILL.md                 규칙, 자체 점검, 점검 목록을 담은 스킬 본문
agents/openai.yaml       메타데이터를 읽는 하네스를 위한 에이전트 정보
references/examples.md   예시 이미지마다 한 행으로 정리한 설명
references/images/       슬롭 신호별 예시 이미지 16장
references/source-*.md   출처 표기를 위해 보존한 원문 글
```

## 출처

열 가지 신호는 hereticpleb(Pranav Desai)가 2026년 9월 27일에 발행한 "10 tells of a slop ui"에서 가져왔습니다. 원문은 https://hereticpleb.vercel.app/blog/10-tells-of-slop 에 있습니다. 원문 텍스트와 이미지는 출처를 밝혀 `references/` 아래에 보존했습니다.

## 라이선스

MIT 라이선스로 배포합니다. 자세한 내용은 [LICENSE](LICENSE)를 확인해 주세요.

## 작성자

[Howon Lee (airtaxi)](https://github.com/airtaxi)가 만들었습니다.
