# Cursor

[![captured with OrcaReplay](https://img.shields.io/badge/captured%20with-OrcaReplay-black)](../docs/CAPTURES.md)

**One of the four files here is an [OrcaReplay](https://github.com/Continuum-AI-Corp/OrcaReplay)
capture**: [`cursor-grok-4.5-high-system-prompt-2026-09-03.md`](cursor-grok-4.5-high-system-prompt-2026-09-03.md),
1,955 characters, taken 2026-09-03.

It is one of the two shortest captures in the archive — Aider, added later, is 800 characters
shorter — and in Cursor's case that is the finding. Cursor composes the prompt on
its own servers and sends it back in the **response** rather than the request, over HTTP/2 in a
protobuf-framed stream — reaching it needs `--tls-intercept` and a local orca build. Another 19 KB
of environment, rules, skills and tool namespaces travels in the user turn, and Cursor declares no
tool schemas on the wire at all: two meta-tools in prose, the rest named in an XML attribute.

```console
ORCA_BIN=packages/cli/dist/cli.js node capture/capture.mjs cursor
```

Details in [docs/CAPTURES.md](../docs/CAPTURES.md); the interception write-up is in
[CURSOR-HTTP2.md](https://github.com/Continuum-AI-Corp/OrcaReplay/blob/main/capture/CURSOR-HTTP2.md).

The `cursor-agent-*` and `cursor-2.0-*` files are inherited from CL4R1T4S
([index](../docs/UPSTREAM.md)).
