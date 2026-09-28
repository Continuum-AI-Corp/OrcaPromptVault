# OpenHands

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`openhands-deepseek-v4.1-flash-system-prompt-2026-09-24.md`](openhands-deepseek-v4.1-flash-system-prompt-2026-09-24.md), 36,806 characters, taken 2026-09-24.

The longest prompt in this folder set, and one of the most sparsely tooled: 36 KB of instructions
behind **7** tools. It opens *You are OpenHands agent, a helpful AI assistant that can interact with
a computer to solve tasks* and then segments itself with XML-ish blocks — `<ROLE>`, `<MEMORY>`,
`<SECURITY>`, `<SECURITY_RISK_ASSESSMENT>`, `<VERSION_CONTROL>`, `<PULL_REQUESTS>`,
`<PROBLEM_SOLVING_WORKFLOW>`, `<SKILLS>`, `<TROUBLESHOOTING>`. The `<MEMORY>` block points the agent
at `AGENTS.md` under the repository root as its persistent memory.

One line moves between captures: `The current date and time is: …`. Five runs across three models
are otherwise byte-identical.

Captured headless inside WSL — no Docker needed for the CLI, contrary to the runtime the web GUI
expects. One trap worth recording: the model id has to carry a provider prefix (`openai/…`). Without
it LiteLLM refuses to resolve a provider, and the CLI **exits 0 having sent nothing**, which reads
like a successful run unless you are watching the proxy.

None of these harnesses has a `capture.mjs` profile yet, so this one was taken the way the
[capture runbook](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CAPTURE-RUNBOOK.md)
describes: run the agent under `orca record` with its provider base URL moved to the proxy, and
read the system prompt out of the request it sends.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
