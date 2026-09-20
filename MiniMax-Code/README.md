# MiniMax Code

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**All four files here are [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay) captures**,
taken 2026-09-20 from [`mcode`](https://github.com/MiniMax-AI/minimax-code) 0.4.12.

MiniMax Code ships **three** system prompts and picks one per surface, so all three are here:

| `--prompt-mode` | file | chars |
|---|---|--:|
| `tui` (default) | [prompt](minimax-code-deepseek-v4-flash-free-system-prompt-2026-09-20.md) | 14,652 |
| `coding` | [prompt](minimax-code-deepseek-v4-flash-free-coding-system-prompt-2026-09-20.md) | 16,032 |
| `work` | [prompt](minimax-code-deepseek-v4-flash-free-work-system-prompt-2026-09-20.md) | 17,596 |

They are three documents, not one with a flag in it: `coding` swaps the `Deliverable Files` section
for `Media Output`, and `work` adds an `Artifact Completion Contract` on top of that. All three
declare the same [18 tools](minimax-code-deepseek-v4-flash-free-tools.json) — the three captures came out byte-identical,
so they share the one file.

## The model is not the variable

Seven models across six labs — MiniMax, DeepSeek, OpenAI, Kimi, GLM, Hunyuan — on two different
gateways produced **119 identical lines each**. The only difference was one line, `- Model: <id>`,
and the tool set never moved. The prompts are Handlebars templates shipped inside the package
(`assets/agents/_v2/*/SYSTEM.md.hbs`), not fetched from a server, and none of their conditionals
branches on a model or a provider. The model in these filenames is the one that answered, not a
variant.

## What is missing from these, and why

These are the BYOK shape. The code that answers a bring-your-own-key run forces `disableMemory` and
`disableMavis`, which drops a 3,381-character `# Memory` section and a 210-character block that a
signed-in run carries. Setting `memory.enabled: true` in the config does not bring it back —
measured, byte-identical output. Capturing the fuller prompt needs a MiniMax credential, and this
capture deliberately used none.

## Regenerate

There is no `capture.mjs` profile for this harness yet, so it is not a one-liner. The route, which
is worth knowing before trying the obvious one:

- **Interception does not work here.** MCode's HTTP client is Node's `fetch`, which ignores
  `HTTP_PROXY`, so `--tls-intercept` records nothing and reports `capture.empty`.
- The provider's base URL lives in `~/.minimax/config.yaml`, not in an environment variable. Point
  it at orca's proxy for the run and put it back afterwards.
- `provider add --use` cannot activate a provider headlessly — that path throws `TEST_REQUIRED`
  unconditionally. Set `defaultModel` to `<providerId>/<modelId>` instead, where the provider id
  starts with `custom_provider:`.
- No account and no key are needed: the prompt travels in the request, and orca records it before
  the origin answers `401`.

Details in [docs/CAPTURES.md](../docs/CAPTURES.md).
