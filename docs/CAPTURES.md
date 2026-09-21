# Captured entries

The files listed here were not copied from anywhere. Each one was pulled off the wire on a real
machine by [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay)'s local proxy while the
harness ran unmodified, then scrubbed and written out. The last column is the command that produces
it again: clone OrcaReplay, run it, diff the result against the file here.

`chars` is the character count of the file as committed. Check any row with:

```console
node -e "console.log(require('fs').readFileSync(process.argv[1],'utf8').length)" <file>
```

The prompt *as sent* is a few hundred characters longer in most rows, because the scrubber's
placeholders (`{{HOME}}`, `{{GIT_USER}}`, `{{PROJECT_SLUG}}`, …) are shorter than the paths and
names they replace.

## Claude Code

| model | mode | captured | chars | tools | file | regenerate |
|---|---|---|---|---|---|---|
| `claude-fable-5-1` | interactive (`cc_entrypoint=cli`) | 2026-09-02 | 26,131 | 35 | [prompt](../Claude-Code/claude-code-fable-5.1-system-prompt-2026-09-02.md) · [tools](../Claude-Code/claude-code-fable-5.1-tools.json) | `node capture/capture.mjs claude --model claude-fable-5-1` |
| `claude-fable-5-1` | print / Agent SDK (`sdk-cli`) | 2026-09-02 | 20,806 | 29 | [prompt](../Claude-Code/claude-code-fable-5.1-print-system-prompt-2026-09-02.md) · [tools](../Claude-Code/claude-code-fable-5.1-print-tools.json) | `node capture/capture.mjs claude --model claude-fable-5-1 --print` |
| `claude-opus-4-8` | interactive | 2026-09-02 | 18,672 | 33 | [prompt](../Claude-Code/claude-code-opus-4.8-system-prompt-2026-09-02.md) · [tools](../Claude-Code/claude-code-opus-4.8-tools.json) | `node capture/capture.mjs claude --model claude-opus-4-8` |
| `claude-opus-5` | interactive | 2026-09-03 | 22,950 | 35 | [prompt](../Claude-Code/claude-code-opus-5-system-prompt-2026-09-03.md) · [tools](../Claude-Code/claude-code-opus-5-tools.json) | `node capture/capture.mjs claude --model claude-opus-5` |

Harness version rides in the first line of each file: `cc_version=2.1.258.18d` for the first three,
`2.1.259.23b` for Opus 5. The working directory is part of this prompt — a capture taken outside a
git repository loses the whole `gitStatus` block, about 4 KB on a measured run.

## Codex CLI

| model | mode | captured | chars | tools | file | regenerate |
|---|---|---|---|---|---|---|
| `gpt-5.6-luna` | `codex exec` | 2026-09-02 | 20,815 | 3 | [prompt](../Codex/codex-cli-gpt-5.6-luna-system-prompt-2026-09-02.md) · [tools](../Codex/codex-cli-gpt-5.6-luna-tools.json) | `node capture/capture.mjs codex --model gpt-5.6-luna` |
| `gpt-5.6-sol` | `codex exec` | 2026-09-03 | 23,354 | 9 | [prompt](../Codex/codex-cli-gpt-5.6-sol-system-prompt-2026-09-03.md) · [tools](../Codex/codex-cli-gpt-5.6-sol-tools.json) | `node capture/capture.mjs codex --model gpt-5.6-sol` |
| `gpt-6-astra` † | `codex exec` | 2026-09-05 | 21,261 | — | [prompt](../Codex/codex-cli-gpt-6-astra-system-prompt-2026-09-05.md) | `node capture/capture.mjs codex --model gpt-6-astra` |

Codex groups its tools into namespaced containers, so the JSON is an array of two entries holding
nine tools rather than nine entries. The count in the table is the tool count.

## Other coding harnesses

| harness | model | mode | captured | chars | tools | file | regenerate |
|---|---|---|---|---|---|---|---|
| Qwen Code | `gpt-5.6-sol` | `-p` | 2026-09-03 | 28,266 | 23 | [prompt](../Qwen/qwen-code-gpt-5.6-sol-system-prompt-2026-09-03.md) · [tools](../Qwen/qwen-code-gpt-5.6-sol-tools.json) | `node capture/capture.mjs qwen --model gpt-5.6-sol --dir qwen-gpt-5.6-sol` |
| Cursor | `grok-4.5-high` | `-p` | 2026-09-03 | 1,955 | 5 ‡ | [prompt](../Cursor/cursor-grok-4.5-high-system-prompt-2026-09-03.md) | `ORCA_BIN=packages/cli/dist/cli.js node capture/capture.mjs cursor` |
| MiMoCode | `mimo-v2.5` | `run` | 2026-09-04 | 50,400 | 16 | [prompt](../MiMoCode/mimocode-mimo-v2.5-system-prompt-2026-09-04.md) · [tools](../MiMoCode/mimocode-mimo-v2.5-tools.json) | `node capture/capture.mjs mimo --model mimo-v2.5` |
| MiMoCode | `mimo-v2.5-pro` | `run` | 2026-09-04 | 50,400 § | 16 § | *(same files)* | `node capture/capture.mjs mimo --model mimo-v2.5-pro` |
| Hermes | `nemotron-3.5-lightning-free` | `-z` | 2026-09-04 | 14,049 | 19 | [prompt](../Hermes/hermes-nemotron-3.5-lightning-free-system-prompt-2026-09-04.md) · [tools](../Hermes/hermes-nemotron-3.5-lightning-free-tools.json) | `node capture/capture.mjs hermes --model nemotron-3.5-lightning-free` |
| Kilo Code | `kilo-auto` (free) † | `run` | 2026-09-05 | 11,322 | 13 | [prompt](../Kilo-Code/kilo-auto-free-system-prompt-2026-09-05.md) | `node capture/capture.mjs kilo` |
| MiniMax Code | `deepseek-v4-flash-free` ¶ | `exec` (`tui`) | 2026-09-20 | 14,675 | 18 | [prompt](../MiniMax-Code/minimax-code-deepseek-v4-flash-free-tui-system-prompt-2026-09-20.md) · [tools](../MiniMax-Code/minimax-code-deepseek-v4-flash-free-tools.json) | `node capture/capture.mjs mcode --model deepseek/deepseek-v4-flash-free --prompt-mode tui --allow-failed` |
| MiniMax Code | `deepseek-v4-flash-free` ¶ | `exec --prompt-mode coding` | 2026-09-20 | 16,055 | 18 | [prompt](../MiniMax-Code/minimax-code-deepseek-v4-flash-free-coding-system-prompt-2026-09-20.md) · *(same tools)* | `node capture/capture.mjs mcode --model deepseek/deepseek-v4-flash-free --prompt-mode coding --allow-failed` |
| MiniMax Code | `deepseek-v4-flash-free` ¶ | `exec --prompt-mode work` | 2026-09-20 | 17,619 | 18 | [prompt](../MiniMax-Code/minimax-code-deepseek-v4-flash-free-work-system-prompt-2026-09-20.md) · *(same tools)* | `node capture/capture.mjs mcode --model deepseek/deepseek-v4-flash-free --prompt-mode work --allow-failed` |
| Crush | `deepseek-v4.1-flash` | non-interactive | 2026-09-18 | 28,839 ◇ | 26 | [prompt](../Crush/crush-deepseek-v4.1-flash-system-prompt-2026-09-18.md) | [runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md) ✦ |
| Gemini CLI | `gemini-3.5-flash` | non-interactive | 2026-09-17 | 25,050 | 8 | [prompt](../Gemini-CLI/gemini-cli-gemini-3.5-flash-system-prompt-2026-09-17.md) | [runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md) ✦ |
| OpenClaw | `gpt-5.6-sol` | `agent exec` | 2026-09-17 | 21,630 | 38 | [prompt](../OpenClaw/openclaw-gpt-5.6-sol-system-prompt-2026-09-17.md) | [runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md) ✦ |
| goose | `deepseek-v4.1-flash` | non-interactive | 2026-09-18 | 9,768 | 18 | [prompt](../Goose/goose-deepseek-v4.1-flash-system-prompt-2026-09-18.md) | [runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md) ✦ |
| dsh | `deepseek-flash` | non-interactive | 2026-09-17 | 4,656 | 25 | [prompt](../DeepSeek/dsh-deepseek-flash-system-prompt-2026-09-17.md) | [runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md) ✦ |
| Cline | `gpt-4o-mini` | non-interactive | 2026-09-17 | 4,251 | 25 | [prompt](../Cline/cline-gpt-4o-mini-system-prompt-2026-09-17.md) | [runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md) ✦ |
| pi | `gpt-4o-mini` | non-interactive | 2026-09-17 | 2,610 | 4 | [prompt](../Pi/pi-gpt-4o-mini-system-prompt-2026-09-17.md) | [runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md) ✦ |
| HackerAI | `gpt-4o-mini` | non-interactive ✧ | 2026-09-17 | 1,689 | 0 | [prompt](../HackerAI/hackerai-gpt-4o-mini-system-prompt-2026-09-17.md) | [runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md) ✦ |
| Aider | `deepseek-v4.1-flash` | non-interactive | 2026-09-18 | 1,155 | 0 | [prompt](../Aider/aider-deepseek-v4.1-flash-system-prompt-2026-09-18.md) | [runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md) ✦ |

## OpenCode

One harness, seven models, three templates. The five free rows differ from each other in exactly
one line — `You are powered by the model named …` — and send a byte-identical tool set, which is
why they share one `opencode-tools.json`.

| model | captured | chars | tools | file |
|---|---|---|---|---|
| `big-pickle` | 2026-09-02 | 9,622 | 11 | [prompt](../OpenCode/opencode-big-pickle-system-prompt-2026-09-02.md) · [tools](../OpenCode/opencode-tools.json) |
| `ling-3.0-flash-fin-free` | 2026-09-02 | 9,648 | 11 | [prompt](../OpenCode/opencode-ling-3.0-flash-fin-free-system-prompt-2026-09-02.md) · [tools](../OpenCode/opencode-tools.json) |
| `mimo-v2.5-free` | 2026-09-03 | 9,630 | 11 | [prompt](../OpenCode/opencode-mimo-v2.5-free-system-prompt-2026-09-03.md) · [tools](../OpenCode/opencode-tools.json) |
| `nemotron-3-ultra-free` | 2026-09-02 | 9,644 | 11 | [prompt](../OpenCode/opencode-nemotron-3-ultra-free-system-prompt-2026-09-02.md) · [tools](../OpenCode/opencode-tools.json) |
| `nemotron-3.5-lightning-free` | 2026-09-02 | 9,656 | 11 | [prompt](../OpenCode/opencode-nemotron-3.5-lightning-free-system-prompt-2026-09-02.md) · [tools](../OpenCode/opencode-tools.json) |
| `muse-spark-1.2-contributor-free` | 2026-09-02 | 10,250 | 11 | [prompt](../OpenCode/opencode-muse-spark-1.2-contributor-free-system-prompt-2026-09-02.md) · [tools](../OpenCode/opencode-muse-spark-1.2-contributor-free-tools.json) |
| `gpt-5.6-sol` | 2026-09-02 | 10,334 | 9 | [prompt](../OpenCode/opencode-gpt-5.6-sol-system-prompt-2026-09-02.md) · [tools](../OpenCode/opencode-gpt-5.6-sol-tools.json) |

Regenerate any of them with `node capture/capture.mjs opencode --model <id>`. OpenCode keeps its
provider origin in `opencode.json` rather than an environment variable, so it cannot be redirected:
the capture uses `--tls-intercept` to terminate the TLS OpenCode established itself, and leaves its
config untouched.

## Footnotes

¶ The model is not the variable for MiniMax Code. Seven models across six labs, on two gateways,
produced 119 identical lines each — the only difference was `- Model: <id>` — and the tool set
never moved. Its prompts are Handlebars templates shipped inside the package, and none of their
conditionals branches on a model or a provider. These three rows are also the BYOK shape: a
signed-in run carries a further 3,381-character `# Memory` section that a bring-your-own-key run
has forced off. See [MiniMax-Code/README.md](../MiniMax-Code/README.md).

**✦** No `capture.mjs` profile. These nine were taken before their harness had one, by running the
agent under `orca record` with its provider base URL moved to the proxy and reading the system
prompt out of the request — the route the capture runbook describes. `capture.mjs <harness>`
answers `unknown harness` for every one of them, and writing profiles is the follow-up that turns
these rows into one-liners. Everything else about them is an ordinary capture: same scrubber, same
audit, same char counts measured the same way.

**✧** HackerAI's CLI has no non-interactive entry point, so this turn was driven through the
package's own `Agent` class. The prompt is the product's — the shim calls `agent.run` and discards
the answer. Aider and HackerAI both show zero tools because neither drives edits through tool
calls; the column is the product, not a truncated capture.

**◇** 29,335 characters as sent. This is the one capture here that needed re-scrubbing before it
could be published: it was taken on 2026-09-18, before OrcaReplay's scrubber matched a Windows path
written with forward slashes, so eight `<location>` lines carried a home directory and two account
uuids past the audit meant to stop exactly that. Re-scrubbed and re-audited against home paths,
usernames, emails, uuids, long hex, key shapes, IPs and gateway hosts.

**†** Not in OrcaReplay's own capture index, so no tool schema was kept and the regenerate command
is the harness's standard form rather than a recorded one. Kilo's is exact all the same — its
capture profile defaults to `kilo/kilo-auto/free`, so the bare command picks that model. Tool count
for the Kilo row comes from OrcaReplay's capture notes; the Astra row has none to report. Both
prompts are as captured.

**‡** Cursor declares no tool schemas on the wire. Its prompt is composed server-side and arrives
in the *response*, not the request; two meta-tools are described in prose and the rest are named in
an XML attribute, so five is the honest count rather than a missing one. A further 19 KB of
environment, rules, skills and tool namespaces travels in the user turn and is not part of this
file.

**§** `mimo-v2.5` and `mimo-v2.5-pro` send byte-identical prompts and tool sets, so one file serves
both rows. The tier changes the model behind the request and nothing about the request.

## What is not here

- **Request bodies and raw traces.** They carry session, message, account and device ids. OrcaReplay
  keeps them local by design and so do we.
- **Anything a chat product injects server-side.** claude.ai, ChatGPT and Gemini never send their
  prompt from your machine; a proxy cannot see what never crosses it. Those entries live in the
  archive as *reported*, not captured.
- **Named Cursor models.** Only `auto` could be captured on the account used; every named model
  answers `resource_exhausted`.
