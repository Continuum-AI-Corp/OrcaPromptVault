# Crush

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`crush-deepseek-v4.1-flash-system-prompt-2026-09-18.md`](crush-deepseek-v4.1-flash-system-prompt-2026-09-18.md), 28,839 characters, taken 2026-09-18.

Charm's terminal agent, and the largest capture in this repository after MiMoCode. Its
`<available_skills>` block lists the skills Crush can load, each with a `crush://skills/...`
location — a product URI, not a path on the machine it was captured on.

29,335 characters as sent; 28,839 here, because the capture scrubber replaced a home path and
two account uuids that an earlier version of it had missed.

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
