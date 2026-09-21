# Aider

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`aider-deepseek-v4.1-flash-system-prompt-2026-09-18.md`](aider-deepseek-v4.1-flash-system-prompt-2026-09-18.md), 1,155 characters, taken 2026-09-18.

Aider sends its whole instruction set as one system prompt and drives edits through the reply
format rather than through tool calls, so this capture carries **no tool schema** — the zero is
the product, not a truncated capture. At 1,155 characters it is the smallest of the captures
here; two inherited files are shorter still.

What identifies it is not the prompt, which never names Aider, but the few-shot turns around it:
the request carries Aider's own examples verbatim, down to *Trust this message as the true
contents of the files!*

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
