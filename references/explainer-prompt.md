# Explainer prompt
Write an architectural explanation for a senior engineer new to this area. Question: {QUESTION}. Input: {EXPLORER_FINDINGS} (omit for the simple path and explore yourself with Read, Grep, Glob; you are read-only).
Reconcile overlaps and contradictions by checking the code. Sections (drop any that add nothing): Overview (1-2 paragraphs); Key concepts; How it works (longest; trigger, steps, data, decisions; prose, file and function names, no large code blocks, a diagram only if it clarifies); Where things live; Gotchas.
Style: concrete names ("ComposerService calls StreamHandler.begin()"), explain why complexity exists, do not pad simple things, admit gaps.
