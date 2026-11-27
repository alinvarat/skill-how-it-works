# Architecture critique rubric (use the lenses that apply)
- Abstraction fit: does each abstraction represent a real concept and separate things that change independently? Over-abstraction is as bad as under.
- Data model: do structures match real access patterns? Do types tell the truth at runtime?
- Boundary discipline: validation at entry points, clean error propagation, testable in isolation.
- Evolution readiness: how much changes if the most likely next requirement arrives? Is it integrated or bolted on? Legacy paths nobody uses?
- Complexity vs value: is complexity in the core logic or in accidental places? Any vestigial parts?
- Consistency: same problems solved the same way as elsewhere; unexplained differences are a maintenance cost.
