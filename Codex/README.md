# Codex

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../../docs/CAPTURES.md)

**Five of the eleven files here are [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay)
captures**, taken from `codex exec` on our own machine.

| model | mode | chars | tools | files |
|---|---|---|---|---|
| `gpt-5.6-sol` | `codex exec` | 23,354 | 9 | [prompt](codex-cli-gpt-5.6-sol-system-prompt-2026-09-03.md) · [tools](codex-cli-gpt-5.6-sol-tools.json) |
| `gpt-5.6-luna` | `codex exec` | 20,815 | 3 | [prompt](codex-cli-gpt-5.6-luna-system-prompt-2026-09-02.md) · [tools](codex-cli-gpt-5.6-luna-tools.json) |
| `gpt-6-astra` | `codex exec` | 21,261 | — | [prompt](codex-cli-gpt-6-astra-system-prompt-2026-09-05.md) |

Reproduce with `node capture/capture.mjs codex --model <id>` — details in
[docs/CAPTURES.md](../../docs/CAPTURES.md).

The `codex-cloud-*` and `codex-desktop-*` files are inherited from CL4R1T4S
([index](../../docs/UPSTREAM.md)), and putting them next to the captures is the point of keeping
both: the desktop build ships a 298 KB prompt and **148 tools**, where the CLI on the same model
sends 23,354 characters and nine. Same product name, two different machines' worth of instructions.
