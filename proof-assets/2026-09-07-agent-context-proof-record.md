# Proof Record — Agent Context Retrieval + Persistence

**Date:** 2026-09-07  
**Evidence policy:** BUILD → TEST → PROVE → CLAIM

## Proof A — AST-bounded Python symbol retrieval

| Field | Evidence |
|---|---|
| Test | Compare full containing Python file with exact AST-bounded symbol retrieval |
| Baseline | 2,214 bytes / 58 lines |
| Bounded retrieval | 710 bytes / 18 lines |
| Measured result | 67.93% fewer bytes / 68.97% fewer lines in this specific test |
| Current status | PASS for bounded test scenario |
| Supported claim | EAS has demonstrated exact symbol-level retrieval for Python functions, classes, and class methods and measured a ~68% context reduction in the recorded test case. |
| Unsupported expansion | Universal token reduction, production-scale monorepo performance, multi-language support, cross-file semantic resolution, or verified MCP specification conformance. |

### Current technical boundary

The private implementation includes an MCP-like JSON-RPC handler with `tools/list` and `tools/call`. The included tests verify those handler paths. A real MCP-capable client/host initialization, transport, discovery, and invocation test remains pending.

## Proof B — Persistent skill/context extraction

| Field | Evidence |
|---|---|
| Test | Extract → normalize → deduplicate → approve → persist → deterministic verification |
| Persistence targets | `AGENTS.md` and `skills.json` |
| Human control | Approval gate before persistence |
| Current status | PASS for deterministic persistence verification |
| Supported claim | EAS has demonstrated a bounded workflow that persists an approved reusable instruction and verifies the stored instruction through the included deterministic path. |
| Unsupported expansion | Independent production-agent reuse, universal behavior improvement, or autonomous learning across arbitrary hosts. |

### Current technical boundary

The bundled `call_llm` path is a local demonstration stub. The next stronger proof is a fresh independent agent host/session reading and correctly applying the persisted instruction.

## Why publish the boundary?

Evidence is more useful when a buyer, developer, researcher, or automated system can distinguish:

- what was tested;
- what passed;
- what remains unknown;
- what the evidence supports; and
- what should not yet be claimed.

This record intentionally publishes the proof without publishing the proprietary implementation.
