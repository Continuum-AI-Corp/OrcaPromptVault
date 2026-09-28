# Continue

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`continue-deepseek-v4.1-flash-system-prompt-2026-09-24.md`](continue-deepseek-v4.1-flash-system-prompt-2026-09-24.md), 1,260 characters, taken 2026-09-24.

At 1,260 characters this is the shortest prompt in the archive, and most of it is not instructions
at all — it is the environment. The agent gets two sentences of direction (*You are an agent in the
Continue CLI*), a `<env>` block naming the working directory, whether it is a git repo, the platform
and the date, a `gitStatus` context block, and a `commitSignature` block that asks for
*Generated with [Continue](https://continue.dev)* in every commit. The rest of Continue's behavior
lives in its hub configuration rather than in the prompt, which is why ten tools arrive behind a
prompt this small.

The capture was taken outside a git repository, so the `gitStatus` block carries its
*Not a git repository* form — the prompt notes this context is a start-of-conversation snapshot and
does not update during the conversation.

Ten tools; five runs across three models came out byte-identical.

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
