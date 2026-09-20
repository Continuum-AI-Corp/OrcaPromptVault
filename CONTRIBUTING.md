# Contributing

One artifact per pull request, filed in the right folder, named by the rule below, with its
provenance stated. That is the whole process.

## What belongs here

System prompts, developer instructions, tool and function schemas, skill definitions, harness
scaffolding, injected context blocks — from any AI product, in any language. Chat assistants,
coding agents, browser assistants, voice agents, IDE plugins.

What does not: anything carrying credentials, API keys, personal data, account or session
identifiers; prompts you wrote yourself; paraphrases, summaries or "cleaned up" versions; and
jailbreak payloads dressed as archive entries. If you cannot say where a text came from, it is not
an archive entry.

## The two kinds of entry

**Captured** is the gold standard: the prompt as the harness sent it, recorded by a local proxy,
with a command anyone can re-run.

```console
npm i -g orcareplay
git clone https://github.com/Continuum-AI-Corp/OrcaReplay
cd OrcaReplay
node capture/capture.mjs claude --model claude-opus-5
node capture/capture.mjs codex  --model gpt-5.6-sol
node capture/capture.mjs opencode          # a free model, so this one costs nothing
```

The script stands up the proxy, launches the agent unmodified, waits for the request that carries
the prompt, pulls it out, scrubs the machine out of it and writes one file. Copy that file here,
copy `capture/<name>/<name>-tools.json` beside it if the harness declares tool schemas, and add a
row to [docs/CAPTURES.md](docs/CAPTURES.md) with the size, the tool count and the regenerate
command. Do not commit the request body or the `trace/` folder — they carry session and account
ids.

Per-harness detail, including the harnesses that must be reached with `--tls-intercept`, is in
[OrcaReplay's capture notes](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/README.md).

**Reported** is everything a proxy cannot see — a product that assembles its prompt server-side can
only be quoted, not captured. Those are welcome, and they carry a header so a reader knows what
they are holding:

```markdown
<!--
source: reported — ChatGPT web, model picker on GPT-5.2
obtained: 2026-09-14, asked the model to repeat its instructions verbatim
verbatim: yes, single response, no edits beyond removing my own name
-->
```

Say `verbatim: no` if you stitched several responses together or a section is a reconstruction.
An honest partial beats a confident fake, and a reader who knows which is which can use both.

## Naming and placement

Files go under **whoever ships the prompt**, not whoever trained the model: an NVIDIA model driven
by OpenCode is OpenCode's prompt and is filed under `OpenCode/`; Meta AI's assistant is
Meta's and is filed under `Meta/`.

```
<Product>/<harness>-<model>-<artifact>-<YYYY-MM-DD>.md
```

- lowercase, hyphen-separated, dots kept in version numbers — `claude-code-opus-4.8-…`
- `<harness>-` only where it disambiguates: a file in `Claude/` is the model's own prompt,
  a file in `Claude-Code/` is the CLI's
- `<artifact>` is `system-prompt`, `tools`, `skills`, `commands`, `functions`, …
- date is the capture or extraction date, ISO, and is omitted only when it is genuinely unknown —
  do not invent one
- text artifacts are `.md`, schemas are `.json`, whatever the source file was called
- one file per capture: two captures that came out byte-identical may share one file, noted in
  `docs/CAPTURES.md`

A product with no folder yet gets one, at the top level, named after the product rather than the
lab: `MiniMax-Code/`, not `MiniMax/Code/`. A lab that ships two products gets two folders —
`Claude/` is the model's own prompt and `Claude-Code/` is the CLI's, and neither has to be found
through the other.

## Before you open the pull request

- [ ] The text is verbatim. No reflowing, no fixing typos, no trimming the boring parts.
- [ ] No home directory, username, real name, email, org name, repo path, machine name, IP,
      session id or uuid. The capture scrubber replaces these with `{{HOME}}`, `{{USER}}`,
      `{{GIT_USER}}`, `{{EMAIL}}`, `{{UUID}}` and friends; do the same by hand for a reported entry.
- [ ] No credentials, tokens or keys. Not even expired ones.
- [ ] LF line endings (`.gitattributes` enforces this; do not fight it).
- [ ] The PR description says the product, the version or model, the date, and how you got it.

## Wanted

DeepSeek (app and coder), Gemini CLI, Kimi CLI and the K2 agent, GLM's coding plane, GitHub
Copilot, Devin's current build, Amp, Trae, Zed's agent, Junie, and anything from a product that is
not in English — this archive is thin outside the English-speaking market and that is a gap worth
closing.

New captures of products already here are wanted too. A prompt from six months ago is history, not
a duplicate: file it beside the old one with its own date and the diff becomes the interesting
part.

## Takedowns

If you own a prompt archived here and want it gone, open an issue saying which file. It will be
removed, without argument.
