# HackerAI

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`hackerai-gpt-4o-mini-system-prompt-2026-09-17.md`](hackerai-gpt-4o-mini-system-prompt-2026-09-17.md), 1,689 characters, taken 2026-09-17.

Captured through the package's own `Agent` class rather than its CLI, which has no
non-interactive entry point. Everything in the request comes from HackerAI's code — the shim
only calls `agent.run` and throws the answer away.

No tool schema: this turn carried none.

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
