---
name: how-it-works
description: Explain how a subsystem, feature flow or codebase works at senior-onboarding depth, and optionally critique its architecture with independent Claude critics. Use on "how does X work", "walk me through", "อธิบายระบบนี้", "critique this architecture".
---

# How it works
Read-only. Two modes: **Explain** (default) and **Critique** (user asks for problems or improvements; run Explain first).

## Explain
1. Restate the question and your scope in one line. If ambiguous, guess and say so; do not ask.
2. Pick the path:
   - Simple (one module or function): one `Explore` subagent (Sonnet) explores and writes the explanation using [explainer-prompt](references/explainer-prompt.md).
   - Complex (several files or services): split into 2-4 non-overlapping angles; spawn one `Explore` subagent (Haiku or Sonnet) per angle in one message using [explorer-prompt](references/explorer-prompt.md); then one Sonnet subagent merges their findings with [explainer-prompt](references/explainer-prompt.md), re-checking code where findings conflict.
3. Present the explanation with light edits only: Overview, Key concepts, How it works (prose with file and function names; a mermaid or ASCII diagram only when it clarifies), Where things live, Gotchas. Report open questions and gaps honestly.

## Critique
1. Run Explain first.
2. Spawn three read-only critics in one message, each given the explanation, the file paths and [critique-rubric](references/critique-rubric.md), using [critic-prompt](references/critic-prompt.md): critic A on Opus, critic B on Sonnet, critic C on Sonnet with the Evolution and Complexity lenses only. Different Claude models are intentional.
3. Judge as a pragmatic lead. Sort findings into Act on, Consider, Noted, Dismissed with one line of reasoning each. Show the explanation first, then the verdict. An empty critique is a valid result.
