# Gemini CLI

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`gemini-cli-gemini-3.5-flash-system-prompt-2026-09-17.md`](gemini-cli-gemini-3.5-flash-system-prompt-2026-09-17.md), 25,050 characters, taken 2026-09-17.

Google's terminal agent, shipped as `@google/gemini-cli`, with 8 tools behind it. This folder
said a capture needed either a profile or the runbook; it was the runbook.

Gemini's own model prompts live in [../Gemini](../Gemini).

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
