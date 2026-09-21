# Qwen Code

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**Both files here are [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) captures**:
[the prompt](qwen-code-gpt-5.6-sol-system-prompt-2026-09-03.md) Qwen Code sent on 2026-09-03 —
28,266 characters — and [the 23 tool definitions](qwen-code-gpt-5.6-sol-tools.json) that went with
it.

The model behind it is `gpt-5.6-sol`, which is the reason this file is filed under Alibaba: the
harness writes the prompt, not the model. Qwen Code drives whatever you point it at, and what it
says is its own.

```console
node capture/capture.mjs qwen --model gpt-5.6-sol --dir qwen-gpt-5.6-sol
```

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
