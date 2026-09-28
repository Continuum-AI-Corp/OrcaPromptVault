# Letta

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`letta-deepseek-v4.1-flash-system-prompt-2026-09-21.md`](letta-deepseek-v4.1-flash-system-prompt-2026-09-21.md), 31,583 characters, taken 2026-09-21.

This one is unusual in that the prompt doubles as the agent's memory. Letta Code opens with *You
are a Letta Code agent — a new generation of agent built for experiential learning*, and then
treats its own system prompt as editable state: memory blocks are *editable segments of the system
prompt*, identity lives in a `<self>` block projected to a `persona.md` file, and the whole thing is
stored in a git-tracked filesystem (`$MEMORY_DIR`) the agent can read and rewrite. The model is
described as interchangeable — *the model is the engine; you are the tokens* — which is the
clearest statement in this archive of a harness designing for model portability.

Two lines move between captures and nothing else does: `CONVERSATION_ID` and `System prompt last
recompiled`. Five runs, three models, byte-identical everywhere else.

Taken in local mode (`letta backend local`), so the prompt is assembled on the machine rather than
server-side, with the provider pointed at the proxy through `letta connect openai-compatible`. 19
tools ride with it.

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
