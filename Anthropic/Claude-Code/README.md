# Claude Code

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../../docs/CAPTURES.md)

**Eight of the nine files here are [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay)
captures** — the prompt Claude Code actually put on the wire from a terminal on our own machine,
with the tool schema that travelled with it.

| model | mode | chars | tools | files |
|---|---|---|---|---|
| `claude-opus-5` | interactive | 22,950 | 35 | [prompt](claude-code-opus-5-system-prompt-2026-09-03.md) · [tools](claude-code-opus-5-tools.json) |
| `claude-fable-5-1` | interactive | 26,131 | 35 | [prompt](claude-code-fable-5.1-system-prompt-2026-09-02.md) · [tools](claude-code-fable-5.1-tools.json) |
| `claude-fable-5-1` | `-p` / Agent SDK | 20,806 | 29 | [prompt](claude-code-fable-5.1-print-system-prompt-2026-09-02.md) · [tools](claude-code-fable-5.1-print-tools.json) |
| `claude-opus-4-8` | interactive | 18,672 | 33 | [prompt](claude-code-opus-4.8-system-prompt-2026-09-02.md) · [tools](claude-code-opus-4.8-tools.json) |

Rows two and three are the same model on the same day, 5,325 characters and six tools apart: the
identity line itself changes from *You are Claude Code, Anthropic's official CLI for Claude* to
*You are a Claude agent, built on Anthropic's Claude Agent SDK*. The harness version rides in the
first line of every file (`cc_version=…`).

Reproduce any row with `node capture/capture.mjs claude --model <id>`; sizes, modes and the full
command for each are in [docs/CAPTURES.md](../../docs/CAPTURES.md).

`claude-code-system-prompt-2025-03-04.md` is not a capture — it is inherited from CL4R1T4S, like
everything in [docs/UPSTREAM.md](../../docs/UPSTREAM.md).
