# Orca PromptVault

<sub>[English](../../README.md) · **简体中文** · [日本語](README.ja.md) · [한국어](README.ko.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · [Español](README.es.md) · [العربية](README.ar.md)</sub>

### 把 AI agent 的真实工作方式公开归档。

一份带版本、可验证的归档：收录当下各家 AI 产品背后的系统提示词、开发者指令、工具 schema 与 agent
harness。由 [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) 抓取。

<a href="https://www.orcarouter.ai">
  <img src="../orcarouter.svg" alt="OrcaRouter" height="28" align="left" hspace="10">
</a>

**由 [OrcaRouter](https://www.orcarouter.ai) 团队打造**——一把 API key、一个 endpoint，覆盖 Claude、
GPT、Gemini、Grok、DeepSeek、Qwen 等等。

相关：[全部模型 API](https://www.orcarouter.ai/models) · [OrcaCode Review](https://www.orcarouter.ai/code-review) · [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) · [OrcaRouter Lite](https://github.com/Continuum-AI-Corp/OrcaRouter-Lite)

联系：[X](https://x.com/OrcaRouter) · [Discord](https://discord.com/invite/YEubt8enRA) · [Hugging Face](https://huggingface.co/orcarouter) · [Ollama](https://ollama.com/orcarouter)

<br clear="left">

[![Artifacts](https://img.shields.io/badge/artifacts-106-blue)](#仓库内容)
[![Captured](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../CAPTURES.md)
[![Tool schemas](https://img.shields.io/badge/tool%20schemas-15-brightgreen)](../CAPTURES.md)
[![License](https://img.shields.io/badge/license-AGPL--3.0-blue)](../../LICENSE)

## 为什么做这件事

一个 agent 的行为不只写在权重里。它写在你开口之前、harness 组装好并发出去的那两万多个字符的指令里，
也写在随之发出的三十几个工具定义里。这段文字决定了它拒绝什么、先伸手去拿哪个工具、用什么口吻跟你说
话、以及它被告知了关于你的哪些事。

把这段文字读出来，产品就不再是黑箱。把它按日期存好、可以逐行 diff，行为的变化也就不再是传闻：你能指
着改动的那一行说话。

## 仓库内容

| 目录 | 收录了什么 | 文件数 | 其中抓取 |
|---|---|---|---|
| OpenAI | [ChatGPT](../../ChatGPT/) 4o · 4.1 · 4.5 · 5 · o3/o4-mini · Atlas，[Codex](../../Codex/) CLI · cloud · desktop，ChatKit Studio | 21 | 5 |
| Anthropic | [Claude](../../Claude/) Sonnet 3.5 → Opus 5 · Fable 5.1 · Design · 用户风格，[Claude Code](../../Claude-Code/) CLI 与 Agent SDK | 22 | 8 |
| Google | [Gemini](../../Gemini/) 2.5 Pro · Diffusion · Gmail 助手 | 3 | — |
| xAI | [Grok](../../Grok/) 3 · 4 · 4.1 · 4.20 · Code Fast 1 | 7 | — |
| [Cursor](../../Cursor/) | Cursor agent · Cursor 2.0 · Composer 跑 Grok 4.5 | 4 | 1 |
| Moonshot | [Kimi](../../Kimi/) K2 · K2 Thinking | 2 | — |
| Alibaba | [Qwen Code](../../Qwen/) CLI | 2 | 2 |
| ZAI | [ZCode](../../GLM/) 提示词 · skills · tools | 3 | — |
| [DeepSeek](../../DeepSeek/) | 暂无——[征集中](../../CONTRIBUTING.md#wanted) | 0 | — |
| Meta | Meta AI（Muse Spark）· WhatsApp 里的 Llama 4 | 2 | — |
| Others | OpenCode · Devin · Windsurf · Cline · Replit · Manus · v0 · Bolt · Lovable · Perplexity · Mistral · MiniMax · MiMoCode · Hermes · Kilo Code · Dia · Brave Leo · Factory Droid · Hume · Cluely · Same.dev · MultiOn | 40 | 15 |

其中 31 份是我们自己在本机从网络流量里抓下来的——共二十次抓取，体积、harness 版本，以及能把每一份重新
生成出来的那条命令，都列在 **[docs/CAPTURES.md](../CAPTURES.md)**。另外 75 份原样继承自 CL4R1T4S，
逐条路径对照见 **[docs/UPSTREAM.md](../UPSTREAM.md)**。

## 抓取，还是转述

这里的每份文件只属于两类之一，而这个区别比内容本身更重要。

**抓取（captured）**——真实 harness 原样运行时，由本地代理从流量里取下来的：这台机器上的工具实际发出
的那段提示词，抹掉一切可识别信息，连同 harness 版本、运行模式、字符数，以及能再跑一次的那条命令一起归
档。你不需要相信它。把命令跑一遍，然后 diff。

**转述（reported）**——本地代理看不见的那些。聊天类产品在服务端组装提示词：claude.ai、ChatGPT、Gemini
从不从你的机器上发出它，所以那些文字只能由模型自己复述出来，到手的是一份转录，而不是网络上的字节。这
类文件按收到的样子归档、尽可能标注日期，并带着随之而来的不确定性。抓取的当证据看，转述的当证词看。

## 自己抓一份

```console
npm i -g orcareplay
git clone https://github.com/Continuum-AI-Corp/OrcaReplay
node capture/capture.mjs claude --model claude-opus-5
```

它会起一个本地代理，原样启动 agent，等到带提示词的那个请求，把提示词取出来，把你的 home 目录、用户名、
git 身份和网关地址替换成占位符，然后写出一个文件。接着来这里提 PR——见
[CONTRIBUTING.md](../../CONTRIBUTING.md)。

Codex、OpenCode、Qwen Code、Cursor、MiMoCode、Kilo、Hermes 走的是同一条路；各 harness 的细节（包括五
个必须用 `--tls-intercept` 才能拿到的——它们的地址没法靠环境变量改掉）见
[capture 说明](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/README.md)。

## 这份归档已经能看出什么

四个结论，都能对着本仓库的文件自己核，不用信谁的一面之词：

- **harness 才是变量。** 同一个模型 `nemotron-3.5-lightning-free`，跑在两个 harness 上：
  [OpenCode 给它 9,656 个字符、11 个工具](../../OpenCode/opencode-nemotron-3.5-lightning-free-system-prompt-2026-09-02.md)，
  [Hermes 给它 14,049 个字符、19 个工具](../../Hermes/hermes-nemotron-3.5-lightning-free-system-prompt-2026-09-04.md)。
  同一个模型、同一个免费 endpoint，指令不同，工具面也不同。
- **模型同样是变量。** [OpenCode](../../OpenCode/) 在七个模型上发出三套不同的模板。五个免费模
  型收到的是 *You are opencode, an interactive CLI tool*；Muse Spark 收到的是另一套开头，而且走的是
  responses 协议；GPT-5.6-Sol 收到第三套，并且用 `apply_patch` 替掉了 `edit` 和 `write`。提示词和传输
  格式都是按模型挑的。
- **交互模式和 `-p` 不是同一段提示词。** Claude Code 在 Fable 5.1 上，从终端里发出的是
  [26,131 个字符、35 个工具](../../Claude-Code/claude-code-fable-5.1-system-prompt-2026-09-02.md)，
  从脚本里发出的是
  [20,806 个字符、29 个工具](../../Claude-Code/claude-code-fable-5.1-print-system-prompt-2026-09-02.md)，
  连身份那一句都变成了 *You are a Claude agent, built on Anthropic's Claude Agent SDK*。你天天用的那
  段提示词，和你的 CI 拿到的那段，是两段。
- **档位不等于提示词。** MiMoCode 对 `mimo-v2.5` 和 `mimo-v2.5-pro` 发的是
  [逐字节相同的文本和工具集](../../MiMoCode/mimocode-mimo-v2.5-system-prompt-2026-09-04.md)：档位
  换的是请求背后的模型，请求本身一点没变。而
  [Cursor 的系统提示词](../../Cursor/cursor-grok-4.5-high-system-prompt-2026-09-03.md)只有 1,955 个字
  符——它在 Cursor 服务端组装，再从*响应*里发回来，另有约 19 KB 的环境、规则、skills 和工具命名空间藏
  在 user 那一轮里。

## 目录结构

```
Orca-PromptVault/
├── README.md · CONTRIBUTING.md · LICENSE
├── docs/
│   ├── CAPTURES.md          每一份抓取记录 + 复现它的命令
│   ├── UPSTREAM.md          继承自 CL4R1T4S 的部分，逐条路径对照
│   └── i18n/                本 README 的另外 7 种语言
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
└── Others/         一个产品一个目录
```

文件按**谁发出这段提示词**归档，而不是按谁训练了模型。OpenCode 驱动的 NVIDIA 模型归在 OpenCode 下，因
为那段指令是 OpenCode 写的；Meta AI 自家的助手归在 Meta 下，因为那是 Meta 写的。一次抓取一个文件，命
名为 `<harness>-<model>-<artifact>-<date>`，这样文件被单独拿出去，也仍然说得清自己从哪来。

## 参与贡献

提示词、工具 schema、skill 定义、harness 指令——任何产品、任何语言都收。带可复现命令的抓取是最高标准；
诚实标注的转录同样欢迎。[CONTRIBUTING.md](../../CONTRIBUTING.md) 里有命名规则、来源标注头，以及一份很
短的不收清单（任何带凭据、个人信息的，或你自己写的、说不清出处的文字）。

当下最想要：DeepSeek、Gemini CLI、Kimi CLI / K2 agent、GLM 的编程链路、Copilot、Devin 的当前版本，以及
任何非英语产品的提示词。

## 来源、伦理与下架

这些是厂商代表用户发给模型的指令——按其本性就对该用户可见；归档在这里，是为了研究、互操作，以及让公众
理解如今数以百万计的人所信任的系统。本仓库里没有任何一份是靠攻破什么拿到的：抓取全部来自我们自己机器
上的代理，读的是我们自己的流量，跑的是我们自己的会话。

这里不含任何凭据、API key、个人数据或账号标识；每一份抓取在写盘前都会被清洗，清洗不掉的不会发布。提示
词的著作权属于其作者。如果某一份是你的、你希望撤下，提个 issue 即可。

这份归档是为了理解 agent，不是为了击穿它们的安全工作。以越狱载荷为目的的 PR 会被拒绝。

## 致谢

本仓库里凡不是 OrcaReplay 抓取的部分——106 份中的 75 份，约五分之四的体量——全部继承自
**@elder_plinius** 的 [CL4R1T4S](https://github.com/elder-plinius/CL4R1T4S)，是他的工作先证明了这些
文档值得被保存。本仓库逐个提交地承接了那段历史，沿用 AGPL-3.0，是在其上增补而不是取而代之。每一份继承文件与其上游路径的对照，见
[docs/UPSTREAM.md](../UPSTREAM.md)。

*抓取*的那一半由 [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) 产出：它能录制任意编程
agent，并在不调用任何模型的前提下逐字节重放整个过程。

## 许可

本仓库采用 [AGPL-3.0](../../LICENSE)。归档的提示词著作权归各自所有者，此处基于合理使用为研究与透明性
而收录。
