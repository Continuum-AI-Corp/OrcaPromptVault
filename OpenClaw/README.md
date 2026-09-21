# OpenClaw

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`openclaw-gpt-5.6-sol-system-prompt-2026-09-17.md`](openclaw-gpt-5.6-sol-system-prompt-2026-09-17.md), 21,630 characters, taken 2026-09-17.

**38 tools**, the largest tool surface captured here. The prompt opens with an HTML comment,
`<!-- openclaw:attempt:STABLE -->`, rather than an identity sentence — the harness labels the
attempt tier in the prompt itself.

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
