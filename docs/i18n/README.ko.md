# Orca PromptVault

<sub>[English](../../README.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · **한국어** · [Deutsch](README.de.md) · [Français](README.fr.md) · [Español](README.es.md) · [العربية](README.ar.md)</sub>

### AI 에이전트가 실제로 어떻게 동작하는지에 대한 공개 아카이브.

오늘날의 AI 제품을 움직이는 시스템 프롬프트, 개발자 지시문, 도구 스키마, 에이전트 하네스를 버전과 함께
검증 가능한 형태로 모았습니다. 수집에는
[OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay)를 사용합니다.

<a href="https://www.orcarouter.ai">
  <img src="../orcarouter.svg" alt="OrcaRouter" height="28" align="left" hspace="10">
</a>

**[OrcaRouter](https://www.orcarouter.ai) 팀이 만듭니다** — API 키 하나, 엔드포인트 하나로 Claude,
GPT, Gemini, Grok, DeepSeek, Qwen까지.

관련: [전체 모델 API](https://www.orcarouter.ai/models) · [OrcaCode Review](https://www.orcarouter.ai/code-review) · [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) · [OrcaRouter Lite](https://github.com/Continuum-AI-Corp/OrcaRouter-Lite)

연결: [X](https://x.com/OrcaRouter) · [Discord](https://discord.com/invite/YEubt8enRA) · [Hugging Face](https://huggingface.co/orcarouter) · [Ollama](https://ollama.com/orcarouter)

<br clear="left">

[![Artifacts](https://img.shields.io/badge/artifacts-106-blue)](#무엇이-들어-있나)
[![Captured](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../CAPTURES.md)
[![Tool schemas](https://img.shields.io/badge/tool%20schemas-15-brightgreen)](../CAPTURES.md)
[![License](https://img.shields.io/badge/license-AGPL--3.0-blue)](../../LICENSE)

## 왜 필요한가

에이전트의 행동은 가중치에만 들어 있지 않습니다. 사용자가 첫 마디를 꺼내기 *전에* 하네스가 조립해 보내
는 2만 자 남짓의 지시문, 그리고 함께 실려 가는 서른다섯 개의 도구 정의에도 들어 있습니다. 그 문장이 무
엇을 거절할지, 어떤 도구에 먼저 손을 뻗을지, 어떤 말투로 이야기할지, 사용자에 대해 무엇을 전달받았는지
를 결정합니다.

그 문장을 읽는 순간 제품은 블랙박스이기를 그만둡니다. 날짜를 붙여 diff할 수 있게 보관하면, 행동의 변화
는 더 이상 소문이 아니라 바뀐 줄을 가리킬 수 있는 사실이 됩니다.

## 무엇이 들어 있나

| 디렉터리 | 내용 | 개수 | 그중 포착 |
|---|---|---|---|
| [OpenAI](../../OpenAI/) | [ChatGPT](../../ChatGPT/) 4o · 4.1 · 4.5 · 5 · o3/o4-mini · Atlas, [Codex](../../Codex/) CLI · cloud · desktop, ChatKit Studio | 21 | 5 |
| [Anthropic](../../Anthropic/) | [Claude](../../Claude/) Sonnet 3.5 → Opus 5 · Fable 5.1 · Design · 사용자 스타일, [Claude Code](../../Claude-Code/) CLI와 Agent SDK | 22 | 8 |
| [Google](../../Google/) | [Gemini](../../Gemini/) 2.5 Pro · Diffusion · Gmail 어시스턴트 | 3 | — |
| [xAI](../../xAI/) | [Grok](../../Grok/) 3 · 4 · 4.1 · 4.20 · Code Fast 1 | 7 | — |
| [Cursor](../../Cursor/) | Cursor agent · Cursor 2.0 · Grok 4.5 위의 Composer | 4 | 1 |
| [Moonshot](../../Moonshot/) | [Kimi](../../Kimi/) K2 · K2 Thinking | 2 | — |
| [Alibaba](../../Alibaba/) | [Qwen Code](../../Qwen/) CLI | 2 | 2 |
| [ZAI](../../ZAI/) | [ZCode](../../GLM/) 프롬프트 · skills · tools | 3 | — |
| [DeepSeek](../../DeepSeek/) | 아직 없음 — [모집 중](../../CONTRIBUTING.md#wanted) | 0 | — |
| [Meta](../../Meta/) | Meta AI(Muse Spark) · WhatsApp의 Llama 4 | 2 | — |
| [Others](../../Others/) | OpenCode · Devin · Windsurf · Cline · Replit · Manus · v0 · Bolt · Lovable · Perplexity · Mistral · MiniMax · MiMoCode · Hermes · Kilo Code · Dia · Brave Leo · Factory Droid · Hume · Cluely · Same.dev · MultiOn | 40 | 15 |

이 중 31개 파일은 우리 기계에서 직접 통신을 열어 받아낸 것입니다 — 스무 번의 포착이고, 크기와 하네스
버전, 각각을 다시 만들어 내는 명령은 **[docs/CAPTURES.md](../CAPTURES.md)**에 있습니다. 나머지 75개는
CL4R1T4S에서 손대지 않고 이어받았으며, 경로 대조표는 **[docs/UPSTREAM.md](../UPSTREAM.md)**에
있습니다.

## 포착된 것, 전해 들은 것

여기 있는 파일은 둘 중 하나이며, 그 차이가 내용보다 중요합니다.

**포착(captured)** — 진짜 하네스를 손대지 않고 실행한 상태에서 로컬 프록시가 통신에서 꺼낸 것. 그 기계
의 도구가 실제로 보낸 프롬프트를, 식별 가능한 정보를 지운 뒤 하네스 버전·모드·글자 수·재현 명령과 함께
보관합니다. 믿을 필요 없습니다. 명령을 실행하고 diff하세요.

**전언(reported)** — 로컬 프록시가 볼 수 없는 것. 채팅 제품은 서버 쪽에서 프롬프트를 조립합니다.
claude.ai, ChatGPT, Gemini는 그 문장을 사용자의 기계에서 보내지 않으므로, 모델이 스스로 되뇌는 방식으로
만 얻을 수 있고, 전선 위의 바이트가 아니라 전사(轉寫)로 도착합니다. 이런 파일은 받은 그대로, 아는 범위
의 날짜와 함께, 그에 따르는 불확실성을 안은 채 보관합니다. 포착은 증거로, 전언은 증언으로 다루세요.

## 직접 포착해 보기

```console
npm i -g orcareplay
git clone https://github.com/Continuum-AI-Corp/OrcaReplay
node capture/capture.mjs claude --model claude-opus-5
```

로컬 프록시를 띄우고, 에이전트를 그대로 실행하고, 프롬프트가 실린 요청을 기다렸다가 꺼내고, 홈 디렉터
리·사용자 이름·git 신원·게이트웨이 주소를 자리표시자로 바꾼 뒤 파일 하나를 씁니다. 그다음 여기로 Pull
Request를 보내면 됩니다 — [CONTRIBUTING.md](../../CONTRIBUTING.md) 참고.

Codex, OpenCode, Qwen Code, Cursor, MiMoCode, Kilo, Hermes도 같은 방식입니다. 하네스별 세부 사항(환경 변수로는 주소를
바꿀 수 없어 `--tls-intercept`로 접근하는 다섯 가지 포함)은
[capture 문서](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/README.md)에 있습니다.

## 이 아카이브가 이미 보여 주는 것

네 가지 모두 이 저장소의 파일로 직접 확인할 수 있습니다.

- **변수는 하네스 쪽이다.** 같은 모델 `nemotron-3.5-lightning-free`를 두 하네스에서:
  [OpenCode는 9,656자 · 11개 도구](../../OpenCode/opencode-nemotron-3.5-lightning-free-system-prompt-2026-09-02.md),
  [Hermes는 14,049자 · 19개 도구](../../Hermes/hermes-nemotron-3.5-lightning-free-system-prompt-2026-09-04.md).
  같은 모델, 같은 무료 엔드포인트, 다른 지시문과 다른 도구 표면.
- **모델도 변수다.** [OpenCode](../../OpenCode/)는 일곱 모델에 세 가지 템플릿을 나눠 보냅니다.
  무료 모델 다섯은 *You are opencode, an interactive CLI tool*로 시작하고, Muse Spark는 다른 도입부에
  responses 방언을 쓰며, GPT-5.6-Sol은 세 번째 템플릿에 `edit`과 `write` 대신 `apply_patch`를 받습니다.
  프롬프트도 전송 형식도 모델마다 고릅니다.
- **대화형과 `-p`는 다른 프롬프트다.** Claude Code는 Fable 5.1에서 터미널이라면
  [26,131자 · 35개 도구](../../Claude-Code/claude-code-fable-5.1-system-prompt-2026-09-02.md)를,
  스크립트라면
  [20,806자 · 29개 도구](../../Claude-Code/claude-code-fable-5.1-print-system-prompt-2026-09-02.md)를
  보내며, 자기소개 문장부터 *You are a Claude agent, built on Anthropic's Claude Agent SDK*로 바뀝니다.
  매일 쓰는 프롬프트와 CI가 받는 프롬프트는 서로 다른 프롬프트입니다.
- **등급은 프롬프트가 아니다.** MiMoCode는 `mimo-v2.5`와 `mimo-v2.5-pro`에
  [바이트 단위로 동일한 텍스트와 도구](../../MiMoCode/mimocode-mimo-v2.5-system-prompt-2026-09-04.md)를
  보냅니다. 등급이 바꾸는 것은 요청 뒤의 모델뿐입니다. 한편
  [Cursor의 시스템 프롬프트](../../Cursor/cursor-grok-4.5-high-system-prompt-2026-09-03.md)는 1,955자
  입니다 — 서버에서 조립돼 *응답*으로 돌아오고, 환경·규칙·skills·도구 네임스페이스 약 19 KB는 user 턴
  쪽에 실립니다.

## 구조

```
Orca-PromptVault/
├── README.md · CONTRIBUTING.md · LICENSE
├── docs/
│   ├── CAPTURES.md          포착된 전체 목록 + 재현 명령
│   ├── UPSTREAM.md          CL4R1T4S에서 온 파일의 경로 대조
│   └── i18n/                이 README의 다른 7개 언어
├── OpenAI/         ChatGPT/ · Codex/
├── Anthropic/      Claude/ · Claude-Code/
├── Google/         Gemini/ · Gemini-CLI/
├── xAI/            Grok/
├── Cursor/
├── Moonshot/       Kimi/
├── Alibaba/        Qwen/
├── ZAI/            GLM/
├── DeepSeek/
├── Meta/
└── Others/         제품마다 디렉터리 하나
```

파일은 **그 프롬프트를 보내는 쪽** 아래에 둡니다. 모델을 학습시킨 쪽이 아닙니다. OpenCode가 구동하는
NVIDIA 모델은 OpenCode 아래에 — 그 지시문을 쓴 것은 OpenCode이기 때문입니다. Meta AI의 어시스턴트는
Meta 아래에. 포착 하나에 파일 하나, 이름은 `<harness>-<model>-<artifact>-<date>`. 파일만 따로 떼어 내도
어디서 왔는지 말해 줍니다.

## 기여

프롬프트, 도구 스키마, skill 정의, 하네스 지시문 — 어떤 제품이든, 어떤 언어든 환영합니다. 재현 명령이
있는 포착이 최선이고, 날짜와 경위를 정직하게 적은 전사도 환영합니다. 명명 규칙, 출처 헤더, 받지 않는
것(자격 증명이나 개인 정보가 든 것, 직접 쓴 뒤 출처를 댈 수 없는 글)의 목록은
[CONTRIBUTING.md](../../CONTRIBUTING.md)에 있습니다.

지금 가장 원하는 것: DeepSeek, Gemini CLI, Kimi CLI / K2 에이전트, GLM 코딩 계열, Copilot, Devin의 현행
빌드, 그리고 영어권 밖 제품이라면 무엇이든.

## 출처, 윤리, 삭제 요청

이것들은 벤더가 사용자를 대신해 모델에 보내는 지시문입니다. 그 성격상 해당 사용자에게는 보이는 것이고,
연구와 상호운용성, 그리고 이제 수백만 명이 신뢰하는 시스템에 대한 공적 이해를 위해 여기 보관합니다. 무
언가를 뚫어서 얻은 것은 하나도 없습니다. 포착은 모두 우리 기계 위의 프록시가, 우리 트래픽을, 우리 세션
중에 읽은 것입니다.

자격 증명, API 키, 개인 정보, 계정 식별자는 들어 있지 않습니다. 모든 포착은 기록 전에 세척되며, 세척할
수 없는 것은 공개하지 않습니다. 프롬프트의 권리는 작성자에게 있습니다. 본인 것을 내리고 싶다면 이슈를
열어 주세요.

이 아카이브는 에이전트를 이해하기 위한 것이지 그 안전장치를 무너뜨리기 위한 것이 아닙니다. 탈옥 페이로
드를 목적으로 한 Pull Request는 받지 않습니다.

## 크레딧

OrcaReplay 포착이 아닌 것은 전부 — 106건 중 75건, 바이트로는 약 5분의 4 — **@elder_plinius**의
[CL4R1T4S](https://github.com/elder-plinius/CL4R1T4S)에서 이어받았습니다. 이 문서들이 보관할 가치가 있
다는 것을 처음 보여 준 작업입니다. 이 저장소는 그 역사를 커밋 단위로 물려받아 AGPL-3.0을 유지하며,
대체하는 것이 아니라 보태고 있습니다. 이어받은 파일과 상류 경로의 대조는
[docs/UPSTREAM.md](../UPSTREAM.md)에 있습니다.

*포착* 쪽은 [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay)가 만들어 냅니다. 어떤 코딩 에
이전트든 기록하고, 모델을 한 번도 호출하지 않은 채 바이트 단위로 재생합니다.

## 라이선스

이 저장소는 [AGPL-3.0](../../LICENSE). 보관된 프롬프트는 각 권리자의 것이며, 연구와 투명성을 위해 공정
이용의 범위에서 수집했습니다.
