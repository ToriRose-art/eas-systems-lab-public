# Build Log — Agent Context Retrieval + Persistent Skill Context

**Date:** 2026-09-07  
**Status:** Built and bounded-test verified; additional real-host interoperability/reuse verification remains.

## What EAS worked on

Today EAS formalized and tested two technical capabilities that sit inside a broader context-engineering and AI-workflow QA practice:

1. **AST / Tree-sitter symbol-level repository retrieval** for Python repositories.
2. **Persistent skill/context extraction** for reusable agent instructions.

The goal was not to create two more storefront products. The goal was to turn existing EAS mapping, context-continuity, and QA practices into bounded technical capabilities with evidence and explicit claim boundaries.

## 1. Bounded repository context retrieval

The private implementation parses Python repositories with Tree-sitter, indexes functions, classes, and class methods, and supports exact symbol lookup so a workflow can return the requested code boundary instead of automatically returning an entire containing file.

### Current bounded proof

In the included QA example:

- Full containing file: **2,214 bytes / 58 lines**
- AST-bounded symbol: **710 bytes / 18 lines**
- Reduction in that specific test: **67.93% by bytes / 68.97% by lines**

This is a result from one controlled test case. It is **not** a universal token-reduction claim.

### What is currently demonstrated

- Python repository parsing
- Functions, classes, and class methods
- Exact symbol lookup
- Malformed-file resilience in the included test scenario
- JSON-RPC `tools/list` and `tools/call` handler behavior
- Full-file versus bounded-symbol context comparison

### What is not yet claimed

The private source includes an MCP-like JSON-RPC tool handler, but actual MCP client/host interoperability — including initialization, transport, and client discovery — still needs independent verification. EAS therefore does not treat the current proof as MCP specification conformance.

## 2. Persistent agent skill/context extraction

The second private build tests a controlled process for turning a useful agent correction or lesson into reusable structured context.

The current implementation can:

- extract one reusable skill from a trace using a deterministic local demonstration path;
- normalize the skill;
- reject duplicates by skill ID or trigger;
- present a human approval gate;
- persist an approved instruction to `AGENTS.md` and `skills.json`; and
- run deterministic verification that reads the stored instruction.

### Important boundary

The current verification proves persistence and the bundled deterministic response path. It does **not** yet prove that an independent production agent host will discover and correctly apply the persisted instruction in a fresh real-world session.

That stronger test remains separate.

## Why this matters

These builds address two related context problems:

- **Precision:** an AI coding workflow may retrieve much more repository context than it needs.
- **Continuity:** useful corrections and operating knowledge can disappear between agent sessions.

EAS is testing ways to make both problems more measurable and controllable rather than assuming that more context or a written instruction automatically produces better behavior.

## The operating rule

**BUILD → TEST → PROVE → CLAIM**

A passing local test is evidence for what that test actually demonstrates. It is not permission to silently expand the claim.

That distinction became part of today's work: working JSON-RPC tool behavior is not the same thing as verified MCP-host interoperability, and successfully writing an instruction is not the same thing as proving an independent agent will reuse it correctly.

## Public vs. private

This public build log shares the tested findings, boundaries, and reusable lessons. The production implementation and proprietary source remain private EAS IP.

Deeper implementation lessons, failure modes, and decision notes are intended for EAS Research / the paid R&D layer.

## Related EAS capabilities

- Repository and workflow mapping
- Context-continuity systems
- Agent and LLM QA/testing
- AI workflow evaluation
- Technical research and documentation
- Machine-readable discovery and proof surfaces

## Next verification

The smallest useful next proofs are:

1. Connect the retrieval tool to a real MCP-capable host/client and verify discovery + invocation + correct bounded output.
2. Run a fresh independent agent session against an approved persisted instruction and verify that it is discovered and correctly applied.

No broader performance or interoperability claim should be made until those tests exist.
