# Orca PromptVault

<sub>[English](../../README.md) · [简体中文](README.zh-CN.md) · **日本語** · [한국어](README.ko.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · [Español](README.es.md) · [العربية](README.ar.md)</sub>

### AI エージェントが実際どう動いているかの、公開アーカイブ。

いまの AI プロダクトを動かしているシステムプロンプト、開発者向け指示、ツールスキーマ、エージェント
ハーネスを、バージョン付きで検証可能な形にまとめたアーカイブ。取得には
[OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) を使っています。

<a href="https://www.orcarouter.ai">
  <img src="../orcarouter.svg" alt="OrcaRouter" height="28" align="left" hspace="10">
</a>

**[OrcaRouter](https://www.orcarouter.ai) のチームが作っています**——API キー 1 本、エンドポイント 1 つ
で Claude、GPT、Gemini、Grok、DeepSeek、Qwen ほかに届きます。

関連: [全モデルの API](https://www.orcarouter.ai/models) · [OrcaCode Review](https://www.orcarouter.ai/code-review) · [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) · [OrcaRouter Lite](https://github.com/Continuum-AI-Corp/OrcaRouter-Lite)

つながる: [X](https://x.com/OrcaRouter) · [Discord](https://discord.com/invite/YEubt8enRA) · [Hugging Face](https://huggingface.co/orcarouter) · [Ollama](https://ollama.com/orcarouter)

<br clear="left">

[![Artifacts](https://img.shields.io/badge/artifacts-106-blue)](#中身)
[![Captured](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../CAPTURES.md)
[![Tool schemas](https://img.shields.io/badge/tool%20schemas-15-brightgreen)](../CAPTURES.md)
[![License](https://img.shields.io/badge/license-AGPL--3.0-blue)](../../LICENSE)

## なぜ作るのか

エージェントの振る舞いは重みだけで決まりません。あなたが最初の一言を打つ*前*にハーネスが組み立てて送
り出す 2 万字あまりの指示と、それと一緒に送られる 35 個のツール定義にも書かれています。その文章が、何
を拒むか、どのツールに最初に手を伸ばすか、どんな口調で話すか、あなたについて何を知らされているかを決
めています。

それを読めば、プロダクトはブラックボックスではなくなります。日付を付けて差分が取れる形で残しておけば、
振る舞いの変化はうわさ話ではなくなり、変わった行を指させるようになります。

## 中身

| ディレクトリ | 収録物 | 件数 | うち取得 |
|---|---|---|---|
| [OpenAI](../../OpenAI/) | [ChatGPT](../../ChatGPT/) 4o · 4.1 · 4.5 · 5 · o3/o4-mini · Atlas、[Codex](../../Codex/) CLI · cloud · desktop、ChatKit Studio | 21 | 5 |
| [Anthropic](../../Anthropic/) | [Claude](../../Claude/) Sonnet 3.5 → Opus 5 · Fable 5.1 · Design · ユーザースタイル、[Claude Code](../../Claude-Code/) CLI と Agent SDK | 22 | 8 |
| [Google](../../Google/) | [Gemini](../../Gemini/) 2.5 Pro · Diffusion · Gmail アシスタント | 3 | — |
| [xAI](../../xAI/) | [Grok](../../Grok/) 3 · 4 · 4.1 · 4.20 · Code Fast 1 | 7 | — |
| [Cursor](../../Cursor/) | Cursor agent · Cursor 2.0 · Grok 4.5 上の Composer | 4 | 1 |
| [Moonshot](../../Moonshot/) | [Kimi](../../Kimi/) K2 · K2 Thinking | 2 | — |
| [Alibaba](../../Alibaba/) | [Qwen Code](../../Qwen/) CLI | 2 | 2 |
| [ZAI](../../ZAI/) | [ZCode](../../GLM/) プロンプト · skills · tools | 3 | — |
| [DeepSeek](../../DeepSeek/) | まだなし——[募集中](../../CONTRIBUTING.md#wanted) | 0 | — |
| [Meta](../../Meta/) | Meta AI（Muse Spark）· WhatsApp の Llama 4 | 2 | — |
| [Others](../../Others/) | OpenCode · Devin · Windsurf · Cline · Replit · Manus · v0 · Bolt · Lovable · Perplexity · Mistral · MiniMax · MiMoCode · Hermes · Kilo Code · Dia · Brave Leo · Factory Droid · Hume · Cluely · Same.dev · MultiOn | 40 | 15 |

このうち 31 ファイルは、自分たちのマシンで通信そのものから取得したものです（20 回の取得）。サイズ、
ハーネスのバージョン、各件を再生成するコマンドは **[docs/CAPTURES.md](../CAPTURES.md)** に。残る 75
ファイルは CL4R1T4S からそのまま引き継いだもので、パスの対照表が
**[docs/UPSTREAM.md](../UPSTREAM.md)** にあります。

## 取得したもの、報告されたもの

ここにあるファイルは 2 種類のどちらかで、その違いは中身より重要です。

**取得（captured）**——本物のハーネスを無改造で動かしたまま、ローカルプロキシが通信から取り出したもの。
そのマシンのツールが実際に送ったプロンプトを、識別につながる情報を除去したうえで、ハーネスのバージョ
ン・モード・文字数・再取得コマンドとともに保存しています。信じる必要はありません。コマンドを実行して
差分を取ってください。

**報告（reported）**——ローカルプロキシでは見えないもの。チャット製品はサーバー側でプロンプトを組み立
てます。claude.ai も ChatGPT も Gemini も、あなたのマシンからそれを送ることはありません。つまりその文
章はモデル自身に復唱させる以外に手に入らず、通信上のバイト列ではなく書き起こしとして届きます。これら
は受け取ったままの形で、分かる範囲の日付とともに保存し、そこに伴う不確かさも一緒に引き受けています。
取得は証拠、報告は証言として扱ってください。

## 自分で取得する

```console
npm i -g orcareplay
git clone https://github.com/Continuum-AI-Corp/OrcaReplay
node capture/capture.mjs claude --model claude-opus-5
```

ローカルプロキシを立て、エージェントを無改造で起動し、プロンプトを含むリクエストを待ち、そこから取り
出し、ホームディレクトリ・ユーザー名・git の身元・ゲートウェイをプレースホルダに置き換えて、1 ファイル
書き出します。あとはここに Pull Request を——[CONTRIBUTING.md](../../CONTRIBUTING.md) を参照。

Codex、OpenCode、Qwen Code、Cursor、MiMoCode、Kilo、Hermes も同じ道筋です。ハーネスごとの詳細（環境変数では宛先を
動かせず `--tls-intercept` で届かせる 5 つを含む）は
[capture のドキュメント](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/README.md)
にあります。

## このアーカイブから既に分かること

いずれもこのリポジトリのファイルで自分で確かめられます。

- **変数はハーネスのほう。** 同じモデル `nemotron-3.5-lightning-free` を 2 つのハーネスで:
  [OpenCode は 9,656 文字・11 ツール](../../OpenCode/opencode-nemotron-3.5-lightning-free-system-prompt-2026-09-02.md)、
  [Hermes は 14,049 文字・19 ツール](../../Hermes/hermes-nemotron-3.5-lightning-free-system-prompt-2026-09-04.md)。
  同じモデル、同じ無料エンドポイント、違う指示、違うツール面。
- **モデルもまた変数。** [OpenCode](../../OpenCode/) は 7 モデルに 3 種類のテンプレートを送り分
  けます。無料モデル 5 つは *You are opencode, an interactive CLI tool* で始まり、Muse Spark は別の書
  き出しで responses 方言、GPT-5.6-Sol は 3 つめのテンプレートで `edit` と `write` の代わりに
  `apply_patch` を持ちます。プロンプトもワイヤ形式もモデルごとに選ばれています。
- **対話モードと `-p` は別のプロンプト。** Claude Code は Fable 5.1 で、端末からなら
  [26,131 文字・35 ツール](../../Claude-Code/claude-code-fable-5.1-system-prompt-2026-09-02.md)、
  スクリプトからなら
  [20,806 文字・29 ツール](../../Claude-Code/claude-code-fable-5.1-print-system-prompt-2026-09-02.md)
  を送り、冒頭の自己紹介まで *You are a Claude agent, built on Anthropic's Claude Agent SDK* に変わり
  ます。日々使うプロンプトと CI が受け取るプロンプトは別物です。
- **ティアはプロンプトを変えない。** MiMoCode は `mimo-v2.5` と `mimo-v2.5-pro` に
  [バイト単位で同一のテキストとツール](../../MiMoCode/mimocode-mimo-v2.5-system-prompt-2026-09-04.md)
  を送ります。ティアが変えるのはリクエストの先にいるモデルだけです。一方
  [Cursor のシステムプロンプト](../../Cursor/cursor-grok-4.5-high-system-prompt-2026-09-03.md) は
  1,955 文字——サーバー側で組み立てられ、*レスポンス*として返ってきます。環境・ルール・skills・ツール
  名前空間の約 19 KB は user ターンのほうに乗っています。

## レイアウト

```
Orca-PromptVault/
├── README.md · CONTRIBUTING.md · LICENSE
├── docs/
│   ├── CAPTURES.md          取得した全件 + 再現コマンド
│   ├── UPSTREAM.md          CL4R1T4S 由来のファイルとパス対照
│   └── i18n/                この README の他 7 言語版
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
└── Others/         プロダクトごとに 1 ディレクトリ
```

ファイルは**そのプロンプトを送っている側**の下に置きます。モデルを訓練した側ではありません。OpenCode
が動かす NVIDIA のモデルは OpenCode の下——その指示を書いたのは OpenCode だからです。Meta AI のアシス
タントは Meta の下。1 回の取得につき 1 ファイル、名前は
`<harness>-<model>-<artifact>-<date>`。ファイル単体で持ち出しても出所が分かります。

## 貢献

プロンプト、ツールスキーマ、skill 定義、ハーネスの指示——どのプロダクトでも、どの言語でも歓迎です。再現
コマンド付きの取得が最上ですが、日付と入手経路を正直に書いた書き起こしも歓迎します。命名規則、来歴ヘッ
ダ、受け付けないもの（認証情報や個人情報を含むもの、自分で書いて出所を示せないもの）の一覧は
[CONTRIBUTING.md](../../CONTRIBUTING.md) に。

いま特に欲しいもの: DeepSeek、Gemini CLI、Kimi CLI / K2 エージェント、GLM のコーディング系、Copilot、
Devin の現行ビルド、そして英語圏以外のプロダクト全般。

## 来歴・倫理・削除依頼

これらはベンダーがユーザーの代わりにモデルへ送っている指示です。その性質上そのユーザーには見えるもの
であり、研究、相互運用性、そしていま何百万人もが信頼しているシステムを公に理解するためにここへ保存し
ています。何かを破って手に入れたものは一つもありません。取得はすべて自分たちのマシン上のプロキシで、
自分たちの通信を、自分たちのセッション中に読んだものです。

認証情報、API キー、個人データ、アカウント識別子は含まれていません。取得は書き出し前に必ず洗浄され、
洗浄しきれないものは公開しません。プロンプトの権利は作者にあります。自分のものを消したい場合は issue
を立ててください。

このアーカイブはエージェントを理解するためのもので、その安全対策を破るためのものではありません。脱獄
ペイロードを目的とした Pull Request は受け付けません。

## クレジット

OrcaReplay の取得でないものはすべて——106 件のうち 75 件、バイト数にして約 5 分の 4——**@elder_plinius**
の [CL4R1T4S](https://github.com/elder-plinius/CL4R1T4S) を引き継いだものです。これらの文書を残す価値
があると最初に示したのは彼らの仕事でした。本リポジトリはその履歴をコミット単位で受け継ぎ、AGPL-3.0 の
まま、置き換えるのではなく積み増しています。引き継いだファイルと上流パスの対照は
[docs/UPSTREAM.md](../UPSTREAM.md) に。

*取得*側は [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) が生み出しています。任意のコー
ディングエージェントを記録し、モデルを一切呼ばずにバイト単位で再生できるツールです。

## ライセンス

本リポジトリは [AGPL-3.0](../../LICENSE)。保存されたプロンプトは各権利者のものであり、研究と透明性の
ためにフェアユースの範囲で収録しています。
