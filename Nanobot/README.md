# nanobot

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`nanobot-deepseek-v4.1-flash-system-prompt-2026-09-21.md`](nanobot-deepseek-v4.1-flash-system-prompt-2026-09-21.md), 8,833 characters, taken 2026-09-21.

The first line is `## Runtime`, not an identity: who the agent is lives in a workspace file, and the
harness pastes that file into the prompt under `## SOUL.md`. The prompt is therefore assembled from
the workspace — `SOUL.md`, `USER.md`, `MEMORY.md` — rather than shipped whole, and the copy here is
what a freshly onboarded workspace produces.

Two blocks are shaped by the machine rather than the product: `## Platform Policy (Windows)` reads
*You are running on Windows. Do not assume GNU tools like `grep`, `sed`, or `awk` exist*, and
`## Format Hint` asks for terminal-shaped output. A line near the top reserves the profile and
long-term memory files for Dream memory-consolidation tasks, the only role allowed to edit them.

23 tools, all declared in the request.

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
