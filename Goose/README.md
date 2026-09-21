# goose

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`goose-deepseek-v4.1-flash-system-prompt-2026-09-18.md`](goose-deepseek-v4.1-flash-system-prompt-2026-09-18.md), 9,768 characters, taken 2026-09-18.

The prompt attributes goose to **AAIF (Agentic AI Foundation)**, not to Block, where it started —
the first line reads *created by AAIF (Agentic AI Foundation)*. Captured on a custom provider,
with 18 tools behind it.

Its `# Extensions` section is written for a harness that loads and unloads capability at runtime:
*you can dynamically enable or disable extensions as needed*, and the prompt then lists the ones
active for this session, each with the tools it brings.

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
