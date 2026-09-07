# Agent Context QA Checklist

A public, implementation-neutral checklist for testing context retrieval and persistence claims.

## A. Repository context retrieval

- [ ] Define the exact repository question or symbol requested.
- [ ] Record the baseline context that would otherwise be returned.
- [ ] Retrieve the bounded context.
- [ ] Confirm the returned boundary contains the requested symbol.
- [ ] Record bytes, lines, and/or tokens using the same measurement method for both samples.
- [ ] Calculate the measured difference.
- [ ] Record repository language and symbol type.
- [ ] Record malformed/edge-case behavior where relevant.
- [ ] Separate local handler tests from real host/client interoperability tests.
- [ ] Phrase performance results as test-specific unless broader evidence exists.

## B. Persistent agent context

- [ ] Identify the correction, decision, convention, or reusable lesson.
- [ ] Convert it into a clear reusable instruction.
- [ ] Normalize the record into the chosen schema.
- [ ] Check for duplicate IDs, triggers, or substantially equivalent instructions.
- [ ] Require human approval when the instruction can materially affect future agent behavior.
- [ ] Persist the approved instruction to the intended context source.
- [ ] Verify that the stored record can be read back correctly.
- [ ] Start a fresh independent session/host when testing real reuse.
- [ ] Confirm the new agent discovers the instruction.
- [ ] Confirm the agent applies it correctly in the relevant situation.
- [ ] Record PASS / FAIL / UNKNOWN rather than inferring success.

## C. Claim boundary

Before publishing a claim, answer:

1. **What exactly did we test?**
2. **What passed?**
3. **What evidence exists?**
4. **What remains untested?**
5. **Does the sentence we want to publish say more than the evidence demonstrates?**

If #5 is yes, narrow the claim.

**EAS operating rule:** BUILD → TEST → PROVE → CLAIM.
