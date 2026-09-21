# pi

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`pi-gpt-4o-mini-system-prompt-2026-09-17.md`](pi-gpt-4o-mini-system-prompt-2026-09-17.md), 2,610 characters, taken 2026-09-17.

A small prompt and a small tool set — 4 tools — from a harness that leans on the model rather
than on scaffolding.

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
