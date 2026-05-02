# WML Conformance

A WML document is conformant when another agent, human, validator, or runtime can review it and determine what source published the world, what world is described, what entities exist, what claims are made, what evidence supports them, how items relate, what constraints apply, what chunks exist, what actions are available, and what receipts have been recorded.

## Checklist

- [ ] A world document exists.
- [ ] The world has a stable unique world ID.
- [ ] The world scope is clear.
- [ ] The source is identified when known.
- [ ] Important objects are represented as entities.
- [ ] Entity state is separate from claims and conclusions.
- [ ] Claims are represented explicitly when they matter.
- [ ] Claims cite evidence when support is available.
- [ ] Evidence is separate from claims and conclusions.
- [ ] Relationships use typed links rather than only prose references, generic hyperlinks, backlinks, folders, or visual layout.
- [ ] Long content is represented as chunks when chunking improves agent consumption.
- [ ] Chunk order or continuation is explicit when needed.
- [ ] Constraints are explicit when they affect use, interpretation, privacy, trust, freshness, scope, or action.
- [ ] Actions include permission classes or constraints.
- [ ] Side-effecting actions require approval unless a permission constraint explicitly says otherwise.
- [ ] Receipts exist for completed, rejected, failed, skipped, or pending actions when action outcomes are represented.
- [ ] The document avoids relying on visual layout, scrolling, styling, or hidden UI state for meaning.

## Non-Conforming Behavior

The following behaviors are non-conforming:

- relying on visual layout as the only source of meaning
- mixing claims and evidence without distinction
- treating unsupported claims as evidence
- omitting important entities and forcing agents to infer all referents from prose
- using generic links, backlinks, or folders where typed relationships are needed
- splitting content into page fragments without chunk order or continuation
- exposing actions without permission or constraint information
- claiming an action completed without a receipt or equivalent evidence
- hiding important boundaries in human-only prose warnings
- omitting source or freshness information when it affects interpretation

## Reviewer Prompt

Use this prompt when reviewing a WML document:

```text
You are reviewing a WML document.

Do not judge it as a visual page, Markdown note, or app export. Review it as an agent-readable world.

Read:
- README.md
- SPEC.md
- AGENT.md
- CONFORMANCE.md
- the WML document being reviewed

Your task:
1. Check whether the document follows WML.
2. Verify that the world has a stable unique ID and clear scope.
3. Verify that the source is identified when known.
4. Verify that important objects are represented as entities.
5. Verify that claims are distinct from evidence.
6. Verify that evidence supports the claims it cites.
7. Verify that relationships are typed where relationships matter.
8. Verify that chunks are ordered when continuation matters.
9. Verify that constraints are explicit where boundaries matter.
10. Verify that actions include permission classes or constraints.
11. Verify that action outcomes have receipts when represented.
12. Identify missing structure, unsupported claims, ambiguous boundaries, and hidden page assumptions.
```
