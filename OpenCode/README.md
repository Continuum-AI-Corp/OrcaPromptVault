# OpenCode

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**Every file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture** —
one harness, seven models, captured across 2026-09-02 and 09-03.

| model | chars | tools | prompt |
|---|---|---|---|
| `big-pickle` | 9,622 | 11 | [prompt](opencode-big-pickle-system-prompt-2026-09-02.md) |
| `ling-3.0-flash-fin-free` | 9,648 | 11 | [prompt](opencode-ling-3.0-flash-fin-free-system-prompt-2026-09-02.md) |
| `mimo-v2.5-free` | 9,630 | 11 | [prompt](opencode-mimo-v2.5-free-system-prompt-2026-09-03.md) |
| `nemotron-3-ultra-free` | 9,644 | 11 | [prompt](opencode-nemotron-3-ultra-free-system-prompt-2026-09-02.md) |
| `nemotron-3.5-lightning-free` | 9,656 | 11 | [prompt](opencode-nemotron-3.5-lightning-free-system-prompt-2026-09-02.md) |
| `muse-spark-1.2-contributor-free` | 10,250 | 11 | [prompt](opencode-muse-spark-1.2-contributor-free-system-prompt-2026-09-02.md) · [tools](opencode-muse-spark-1.2-contributor-free-tools.json) |
| `gpt-5.6-sol` | 10,334 | 9 | [prompt](opencode-gpt-5.6-sol-system-prompt-2026-09-02.md) · [tools](opencode-gpt-5.6-sol-tools.json) |

**Seven models, three prompts.** The first five differ from each other in exactly one line — *You
are powered by the model named …* — and send a byte-identical tool set, which is why they share one
[`opencode-tools.json`](opencode-tools.json). Muse Spark gets a different opening and the responses
dialect. GPT-5.6-Sol gets a third template entirely, with `apply_patch` in place of `edit` and
`write`. The prompt and the wire format are both chosen per model, and you can diff the files here
to see it.

`nemotron-3.5-lightning-free` also appears under [Hermes](../Hermes) — same model, same free
endpoint, a different harness. That pair is the cleanest comparison in the archive.

```console
node capture/capture.mjs opencode --model <id>
```

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
