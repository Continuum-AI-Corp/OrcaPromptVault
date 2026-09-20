# Hermes

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../../docs/CAPTURES.md)

**Both files here are [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) captures**,
taken 2026-09-04: [the prompt](hermes-nemotron-3.5-lightning-free-system-prompt-2026-09-04.md),
14,049 characters, and [its 19 tools](hermes-nemotron-3.5-lightning-free-tools.json).

About 6,300 characters of that prompt is an `<available_skills>` block listing 51 skills, all of
them Hermes' own builtins — so the catalogue belongs in the capture, and this file is the whole
prompt.

The same model, `nemotron-3.5-lightning-free`, was also captured under
[OpenCode](../OpenCode): 9,656 characters and 11 tools there against 14,049 and 19 here.
Same model, same anonymous endpoint, different instructions and a different tool surface — **the
harness is the variable**, and this pair is what isolates it.

```console
node capture/capture.mjs hermes --model nemotron-3.5-lightning-free
```

Details in [docs/CAPTURES.md](../../docs/CAPTURES.md).
