# Muse Code

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**The file here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) capture**: [`muse-code-muse-spark-1.3-system-prompt-2026-09-29.md`](muse-code-muse-spark-1.3-system-prompt-2026-09-29.md), 24,865 characters, taken 2026-09-29, with [its 25 tool schemas](muse-code-muse-spark-1.3-tools.json) beside it.

Meta's terminal coding agent, powered by Muse Spark and installed with
`curl -fsSL https://dev.meta.ai/install.sh | bash`. It identifies itself as *"Muse Code powered by
Meta Muse Spark"* and speaks the OpenAI Responses dialect, with the prompt in `instructions`
rather than in a system message.

Not to be confused with [`Meta-AI/`](../Meta-AI/), which is the consumer assistant. Both run on
Muse Spark; they are different products with different prompts, which is why they are different
folders.

## The tool shape is unlike anything else here

The other 25-tool captures in this archive send twenty-five tools. Muse sends **one**, of
`type: "namespace"`, with the real twenty-five nested inside it — `workflow`, `read_file`,
`search`, `write_file`, `edit_file`, three `*_memory` calls, `powershell` and `powershell_input`,
`monitor`, three `cron_*` calls, four goal-and-progress calls, `web_search`, `read_skill`,
`write_todos` and the rest. The prompt refers to them as `muse.write_file`, and in the binary it
refers to them as `{{tool:write_file}}`: the shipped prompt is a template, rendered at launch.

Rendering that template reproduces the captured text exactly, which is how this entry's
provenance was checked rather than assumed. The binary it came from is Authenticode-signed by
Meta Platforms, Inc., and `install.sh` installs the same version and channel, `1.4.0-R4302.1`.

## Two turns, one prompt

Muse sends two model calls per prompt: the agent's turn, and a judge that decides whether a skill
should be loaded. Both carry this same 24,864-character prompt; they differ in the context block
and in how many of the nested tools they offer — twenty-five for the agent, one for the judge. The
file here is the agent's.

## How it was reached

Muse fetches a model catalogue with `GET /muse-code/models` and will not build a turn until that
answers, and OrcaReplay's proxy answers 404 to every non-POST because only a POST is ever a model
call. So the capture puts a shim in front of the proxy that serves that one GET and forwards
everything else untouched — a catalogue is not a model call, and the turn carrying the prompt still
goes through the proxy and is recorded there. The shim ships with the capture script, so
`capture.mjs muse` is still one command.

No account was needed. The key is a placeholder, the turn comes back refused, and the prompt
travels in the request either way.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
