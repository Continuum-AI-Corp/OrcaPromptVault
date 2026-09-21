# Cline

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`cline-gpt-4o-mini-system-prompt-2026-09-17.md`](cline-gpt-4o-mini-system-prompt-2026-09-17.md), 4,251 characters, taken 2026-09-17.

The other file here, [`cline-system-prompt.md`](cline-system-prompt.md), is inherited from
CL4R1T4S and carries no date. This one is a capture with 25 tools behind it, so the two can be
read against each other.

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
