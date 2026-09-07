# Bounded Context Retrieval + Persistent Agent Context

**EAS Build Note — September 7, 2026**

Elite Adaptive Solutions has been testing two related problems in AI-assisted development:

1. How can an agent retrieve the specific repository context it needs without automatically returning an entire containing file?
2. How can useful corrections and reusable instructions survive beyond the session in which they were learned?

These experiments extend existing EAS work in context continuity, repository mapping, AI workflow QA, and evidence-backed technical systems.

## Experiment 1: Bounded Repository Context Retrieval

EAS built and tested a Python repository indexing and retrieval workflow using Tree-sitter.

The current implementation can identify and retrieve:

- Python functions
- Python classes
- Class methods
- Exact symbol names
- Qualified method names

Instead of returning an entire containing file, the retrieval process can return the code bounded to the requested symbol.

### Measured QA Example

In the current controlled test:

| Retrieval method | Bytes returned | Lines returned |
|---|---:|---:|
| Full containing file | 2,214 | 58 |
| Bounded symbol retrieval | 710 | 18 |
| Reduction | 67.93% | 68.97% |

These numbers describe **this specific QA example**.

They are not presented as a universal token, context, cost, or performance reduction claim.

## What Has Been Demonstrated

The current build demonstrates:

- Python repository parsing using Tree-sitter
- Function, class, and method indexing
- Exact symbol retrieval
- Bounded source-code return
- JSON-RPC tool listing and invocation
- Malformed-file resilience within the included test scenario
- A reproducible before/after context comparison

## What Has Not Yet Been Demonstrated

The current evidence does not establish:

- universal context or token reduction
- multi-language support
- cross-file semantic resolution
- dependency or call-graph resolution
- production-scale monorepo performance
- verified interoperability with an independent MCP client/host

The implementation contains an MCP-like JSON-RPC tool interface, but EAS is not claiming MCP specification conformance until independent client/host interoperability is verified.

---

## Experiment 2: Persistent Agent Context

The second experiment addresses a different context problem:

**What happens to useful corrections and reusable instructions after an AI development session ends?**

EAS built a bounded workflow that can:

1. identify a reusable instruction from an agent trace,
2. normalize the instruction,
3. reject duplicates,
4. place the proposed instruction behind a human approval step,
5. persist an approved instruction into structured reusable context,
6. verify deterministic retrieval of that stored instruction.

The current implementation uses `AGENTS.md` and structured JSON as persistence targets.

## Why Human Approval Matters

Not every observation made during an agent session should become a permanent rule.

A correction can be:

- specific to one situation,
- incorrect,
- outdated,
- duplicated,
- overly broad,
- or inappropriate for future sessions.

Persistence therefore needs a decision boundary between:

**something happened**

and

**future agents should use this as an instruction.**

The current EAS experiment includes that approval boundary.

## Current Proof Boundary

The present verification demonstrates persistence and deterministic retrieval through the included test workflow.

It does **not yet demonstrate that an independent production agent host will read the persisted instruction and correctly apply it in a new real-world session.**

That is a separate verification step.

---

# The Larger Context Problem

These experiments address two sides of the same issue.

**Persistent context asks:**

> What knowledge should survive?

**Bounded repository retrieval asks:**

> What exact context should the agent receive when it needs to work?

EAS treats both as context-engineering and quality-assurance problems rather than assuming that storing more information or loading more code automatically produces a better agent workflow.

## EAS Testing Principle

**BUILD → TEST → PROVE → CLAIM**

A successful implementation test is not automatically proof of every larger claim surrounding a technology.

EAS records what was demonstrated, what remains unknown, and what additional verification would be required before expanding a claim.

## Related Research

Additional implementation observations, failure modes, testing decisions, and lessons from these experiments are documented through EAS Research and the EAS Context R&D Feed.

The underlying proprietary implementation remains private.

---

**Elite Adaptive Solutions**

Practical AI systems, context continuity, repository context engineering, QA evaluation, and proof-driven workflow development.
