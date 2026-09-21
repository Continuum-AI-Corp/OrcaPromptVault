# OrcaPromptVault
<sub>**English** · [简体中文](docs/i18n/README.zh-CN.md) · [日本語](docs/i18n/README.ja.md) · [한국어](docs/i18n/README.ko.md) · [Deutsch](docs/i18n/README.de.md) · [Français](docs/i18n/README.fr.md) · [Español](docs/i18n/README.es.md) · [العربية](docs/i18n/README.ar.md)</sub>

### The open archive of how AI agents actually work.

A versioned, verifiable archive of system prompts, developer instructions, tool schemas and agent
harnesses powering today's AI products. Captured with
[OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay).

<a href="https://www.orcarouter.ai">
  <img src="docs/orcarouter.svg" alt="OrcaRouter" height="28" align="left" hspace="10">
</a>

**Built by the team behind [OrcaRouter](https://www.orcarouter.ai)** — one API key and one endpoint
for Claude, GPT, Gemini, Grok, DeepSeek, Qwen and the rest.

Find us: [All model APIs](https://www.orcarouter.ai/models) · [OrcaCode Review](https://www.orcarouter.ai/code-review) · [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) · [OrcaRouter Lite](https://github.com/Continuum-AI-Corp/OrcaRouter-Lite)

Connect: [X](https://x.com/OrcaRouter) · [Discord](https://discord.com/invite/YEubt8enRA) · [Hugging Face](https://huggingface.co/orcarouter) · [Ollama](https://ollama.com/orcarouter)

<br clear="left">

[![Artifacts](https://img.shields.io/badge/artifacts-119-blue)](#whats-inside)
[![Captured](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](docs/CAPTURES.md)
[![Tool schemas](https://img.shields.io/badge/tool%20schemas-16-brightgreen)](docs/CAPTURES.md)
[![License](https://img.shields.io/badge/license-AGPL--3.0-blue)](LICENSE)

## Why this exists

An agent's behaviour is not only in its weights. It is in the twenty-odd thousand characters of
instructions a harness assembles and sends *before* your first word, and in the thirty-five tool
definitions it sends with them. That text decides what the agent refuses, which tool it reaches for
first, how it talks to you, and what it has been told about you.

Read it and the product stops being a black box. Keep it dated and diffable and a change in
behaviour stops being folklore: you can point at the line that changed.

## What's inside

| vendor | products | artifacts | of which captured |
|---|---|---|---|
| OpenAI | [ChatGPT](ChatGPT/) 4o · 4.1 · 4.5 · 5 · o3/o4-mini · Atlas, [Codex](Codex/) CLI · cloud · desktop, [ChatKit Studio](ChatKit-Studio/) | 21 | 5 |
| Anthropic | [Claude](Claude/) Sonnet 3.5 → Opus 5 · Fable 5.1 · Design · user styles, [Claude Code](Claude-Code/) CLI + Agent SDK | 22 | 8 |
| Google | [Gemini](Gemini/) 2.5 Pro · Diffusion · Gmail assistant, [Gemini CLI](Gemini-CLI/) on 3.5 Flash | 4 | 1 |
| xAI | [Grok](Grok/) 3 · 4 · 4.1 · 4.20 · Code Fast 1 | 7 | — |
| Cursor | [Cursor](Cursor/) agent · 2.0 · Composer on Grok 4.5 | 4 | 1 |
| Moonshot | [Kimi](Kimi/) K2 · K2 Thinking | 2 | — |
| Alibaba | [Qwen Code](Qwen/) CLI | 2 | 2 |
| ZAI | [ZCode](GLM/) prompt · skills · tools | 3 | — |
| DeepSeek | [dsh](DeepSeek/) CLI | 1 | 1 |
| Meta | [Meta AI](Meta-AI/) on Muse Spark · Llama 4 in WhatsApp | 2 | — |
| independent | [OpenCode](OpenCode/) · [Devin](Devin/) · [Windsurf](Windsurf/) · [Cline](Cline/) · [Replit](Replit/) · [Manus](Manus/) · [v0](Vercel-v0/) · [Bolt](Bolt/) · [Lovable](Lovable/) · [Perplexity](Perplexity/) · [Mistral](Mistral/) · [MiniMax](MiniMax/) · [MiMoCode](MiMoCode/) · [Hermes](Hermes/) · [Kilo Code](Kilo-Code/) · [Dia](Dia/) · [Brave Leo](Brave-Leo/) · [Factory Droid](Factory-Droid/) · [Hume](Hume/) · [Cluely](Cluely/) · [Same.dev](Same-Dev/) · [MultiOn](MultiOn/) · [MiniMax Code](MiniMax-Code/) · [Crush](Crush/) · [OpenClaw](OpenClaw/) · [goose](Goose/) · [Cline capture](Cline/) · [pi](Pi/) · [HackerAI](HackerAI/) · [Aider](Aider/) | 51 | 26 |

Forty-four of these files are captures taken off the wire on our own machines — thirty-two
runs, listed
with their sizes, harness versions and the command that reproduces each one in
**[docs/CAPTURES.md](docs/CAPTURES.md)**. The other seventy-five are inherited from CL4R1T4S,
unedited, and indexed path by path in **[docs/UPSTREAM.md](docs/UPSTREAM.md)**.

## Captured, or reported

Every file here is one of two things, and the difference matters more than the contents.

**Captured** — pulled off the wire by a local proxy while the real harness ran unmodified: the
prompt the tool on this machine actually sent, scrubbed of anything identifying, filed with its
harness version, its mode, its size and the one command that produces it again. You do not have to
trust it. Run the command and diff.

**Reported** — everything a local proxy cannot see. A chat product assembles its prompt
server-side: claude.ai, ChatGPT and Gemini never send one from your machine, so their text can only
come from the model repeating it, and it arrives as a transcript rather than as bytes on a wire.
Those files are archived as received, dated where the date is known, and they carry the uncertainty
that comes with that. Treat a captured file as evidence and a reported one as testimony.

## Capture one yourself

```console
npm i -g orcareplay
git clone https://github.com/Continuum-AI-Corp/OrcaReplay
node capture/capture.mjs claude --model claude-opus-5
```

It stands up a local proxy, launches the agent unmodified, waits for the request that carries the
prompt, pulls the prompt out, replaces your home directory, username, git identity and gateway host
with placeholders, and writes one file. Then open a pull request here — see
[CONTRIBUTING.md](CONTRIBUTING.md).

Codex, OpenCode, Qwen Code, Cursor, MiMoCode, Kilo and Hermes work the same way; the
[capture notes](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/README.md) cover
the per-harness detail, including the five that have to be reached with `--tls-intercept`, because
their origin cannot be moved with an environment variable.

## What the archive already shows

Four findings you can check against the files in this repository, without taking anyone's word:

- **The harness is the variable.** One model, `nemotron-3.5-lightning-free`, on two harnesses:
  [9,656 characters and 11 tools from OpenCode](OpenCode/opencode-nemotron-3.5-lightning-free-system-prompt-2026-09-02.md),
  [14,049 and 19 from Hermes](Hermes/hermes-nemotron-3.5-lightning-free-system-prompt-2026-09-04.md).
  Same model, same free endpoint, different instructions and a different tool surface.
- **So is the model.** [OpenCode](OpenCode/) sends three different templates across seven
  models. Five free ones open with *You are opencode, an interactive CLI tool*; Muse Spark gets a
  different opening and the responses dialect; GPT-5.6-Sol gets a third template and `apply_patch`
  in place of `edit` and `write`. The prompt and the wire format are both chosen per model.
- **Interactive is not the same prompt as `-p`.** Claude Code on Fable 5.1 sends
  [26,131 characters and 35 tools](Claude-Code/claude-code-fable-5.1-system-prompt-2026-09-02.md)
  from a terminal and
  [20,806 and 29](Claude-Code/claude-code-fable-5.1-print-system-prompt-2026-09-02.md)
  from a script, where the identity line itself changes to *You are a Claude agent, built on
  Anthropic's Claude Agent SDK*. The prompt behind daily use and the one your CI job gets are two
  different prompts.
- **A tier is not a prompt.** MiMoCode sends
  [byte-identical text and tools](MiMoCode/mimocode-mimo-v2.5-system-prompt-2026-09-04.md)
  for `mimo-v2.5` and `mimo-v2.5-pro`. The tier changes the model behind the request and nothing
  about the request. And [Cursor's system prompt](Cursor/cursor-grok-4.5-high-system-prompt-2026-09-03.md)
  is 1,955 characters — composed on Cursor's servers and sent *back* in the response, with another
  19 KB of environment, rules, skills and tool namespaces riding in the user turn instead.

## Layout

```
Orca-PromptVault/
├── README.md · CONTRIBUTING.md · LICENSE
├── docs/
│   ├── CAPTURES.md          every captured entry + the command that reproduces it
│   ├── UPSTREAM.md          what came from CL4R1T4S, path by path
│   └── i18n/                this README in 7 more languages
├── ChatGPT/        Codex/ · ChatKit-Studio/          OpenAI
├── Claude/         Claude-Code/                      Anthropic
├── Gemini/         Gemini-CLI/                       Google
├── Grok/                                             xAI
├── Kimi/ · Qwen/ · GLM/ · Meta-AI/ · DeepSeek/       Moonshot · Alibaba · ZAI · Meta
├── Cursor/ · Windsurf/ · Cline/ · Kilo-Code/         editors and IDE agents
├── OpenCode/ · Hermes/ · MiMoCode/ · MiniMax/        terminal agents
├── Devin/ · Manus/ · Replit/ · Factory-Droid/        autonomous and hosted
└── …                                                 one folder per product
```

One product, one folder, at the top level. Files sit under **whoever ships the prompt**, not
whoever trained the model: an NVIDIA model driven by OpenCode is filed under `OpenCode/`, because
OpenCode wrote those instructions; Meta AI's own assistant is filed under `Meta-AI/`, because Meta
did. The vendor is a column in the table above, not a directory — a path is for finding one
product, and nesting it under a lab meant knowing the lab before you could look. One file per capture, named
`<harness>-<model>-<artifact>-<date>`, so a file pulled out on its own still says where it came
from.

## Contributing

Prompts, tool schemas, skill definitions, harness instructions — from any product, in any language.
A capture with a reproducible command is the gold standard; a dated, honest transcript is welcome
too. [CONTRIBUTING.md](CONTRIBUTING.md) has the naming rules, the provenance header and the short
list of what we will not take (anything with credentials, personal data, or text you wrote
yourself and cannot source).

Most wanted right now: DeepSeek, Gemini CLI, Kimi CLI/K2 agent, GLM coding plane, Copilot, Devin's
current build, and anything from a non-English product.

## Provenance, ethics, takedowns

These are the instructions a vendor sends to a model on behalf of a user — visible to that user by
construction, and archived here for research, interoperability and public understanding of systems
that millions of people now trust. Nothing in this repository is obtained by breaking into
anything: the captures come from a proxy on our own machines, reading our own traffic, during our
own sessions.

Nothing here contains credentials, API keys, personal data or account identifiers; every capture is
scrubbed before it is written and a capture that cannot be scrubbed is not published. Prompts remain
the property of their authors. If you own one and want it removed, open an issue and it goes.

This archive is for understanding agents, not for defeating their safety work. Pull requests whose
purpose is a jailbreak payload are declined.

## Credits

Everything here that is not an OrcaReplay capture — 75 of the 106 artifacts, four fifths of the
bytes — is inherited from [CL4R1T4S](https://github.com/elder-plinius/CL4R1T4S) by
**@elder_plinius**, whose work made the case that these documents are worth keeping at all. This
repository carries that history commit by commit, keeps the corpus under AGPL-3.0, and adds to it
rather than replacing it. Every inherited file is indexed back to its upstream path in
[docs/UPSTREAM.md](docs/UPSTREAM.md).

The *captured* half is produced by [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay),
which records any coding agent and replays the run byte-for-byte with no model called.

## License

[AGPL-3.0](LICENSE) for this repository. The archived prompts are the work of their respective
owners and are collected here under fair use for research and transparency.
