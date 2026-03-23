---
url: https://medium.com/@ib_36452/the-ladder-out-of-ai-code-review-hell-319dd7130335
---

Review the code of the application. Analyze it against the following checklist and produce a prioritized improvement plan.

## Rules

- Use evidence from the code. Do not guess.
- If you cannot determine something from code, say "Unknown from available context" and move on.
- Provide exact locations as File:line. If line numbers are unavailable, provide File + function/class name.
- Skip categories that are clean. Do not pad the review.
- Sort by severity: critical, major, minor.
- Group related issues that should be refactored together.
- Every Fix must be a concrete change, not vague advice.

## Correctness & Consistency

- Logic errors, edge cases, off-by-one errors
- Inconsistent naming conventions, patterns, or abstraction levels
- Type mismatches or implicit assumptions between components

## Code Quality

- DRY violations — identify duplicated logic and propose abstractions
- Dead code, unused imports, unreachable branches
- Functions doing too much (SRP violations) — flag any over ~30 lines

## Performance & Resource Management

- Memory leaks: unclosed connections, missing cleanup, unremoved event listeners, circular references
- N+1 queries, unnecessary re-renders, unbounded data structures
- Missing timeouts, rate limits, or backpressure on I/O operations
- Blocking calls in async contexts

## Overengineering

- Premature abstractions — indirection without a second use case
- Unnecessary patterns, wrapper classes, or config logic that could be a simple function
- Layers that pass through without transforming

## Error Handling & Resilience

- Silent failures, swallowed exceptions, missing error propagation
- Missing input validation at trust boundaries
- No retry/fallback logic where external calls can fail

## Output format:

For each issue found:

- File:line
- Severity: critical / major / minor
- Issue: one sentence
- Fix: concrete code change or refactor

Sort by severity descending. Group related issues that should be refactored together. If a category is clean, skip it.
