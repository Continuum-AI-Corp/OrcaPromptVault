# MiMoCode

🐋 **Both files here are [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) captures**,
taken 2026-09-04: [the prompt](mimocode-mimo-v2.5-system-prompt-2026-09-04.md), 50,400 characters —
the longest CLI prompt in this archive — and [its 16 tools](mimocode-mimo-v2.5-tools.json).

One file covers two models. `mimo-v2.5` and `mimo-v2.5-pro` send **byte-identical** prompts and tool
sets, same sha256: the tier changes the model behind the request and nothing about the request.

```console
node capture/capture.mjs mimo --model mimo-v2.5
node capture/capture.mjs mimo --model mimo-v2.5-pro
```

Details in [docs/CAPTURES.md](../../docs/CAPTURES.md).
