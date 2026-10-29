---
name: pragmatic-code-engineering
description: >-
  Enforce pragmatic, concise, readable, and rigorous code engineering.
  Use when writing, modifying, refactoring, reviewing, or testing code.
  Prioritize reusing existing implementations, utilities, and project
  conventions before introducing new code. Keep logic cohesive and
  straightforward; avoid excessive function extraction, trivial
  one-line helpers, unnecessary private wrappers, speculative
  abstractions, overengineering, redundant defensive checks,
  excessive try/except handling, hypothetical edge cases, and
  low-value tests. Introduce abstractions, error handling, and tests
  only when they provide concrete value. Preserve correctness,
  maintainability, and necessary safeguards for real risks.
---

# Code Anti-Overdesign

## Core Philosophy

**Write the simplest correct code that fits the existing architecture and engineering standards.**

Good code is concise, elegant, readable, cohesive, and rigorous.

Simplicity does not mean minimizing lines of code. Engineering quality does not mean maximizing abstractions, defensive checks, or tests.

Every additional function, abstraction, branch, exception handler, and test should have a concrete justification.

**Prefer reuse over reinvention, direct code over unnecessary indirection, and proven requirements over hypothetical scenarios.**

## Compatibility With Project-Specific Instructions

This skill provides general code engineering principles. It must not override explicit user requirements, project-specific workflows, safety constraints, or established repository conventions.

- Follow project-specific instructions for testing, validation, debugging, deployment, and resource management.
    
- Do not automatically initiate remote training, GPU jobs, cluster operations, or other expensive validation unless explicitly authorized.
    
- Do not remove or bypass established safeguards, cleanup procedures, failure recovery, or required tests merely to reduce complexity.
    
- When a user explicitly requests refactoring, allow justified structural changes while continuing to avoid unnecessary abstractions and excessive function extraction.
    
- Interpret minimal changes as the smallest **reasonable and maintainable** implementation, not the fewest lines of code.
    
- When multiple skills apply, use project-specific instructions for operational procedures and this skill for general implementation quality.
    

**Simplicity must not override explicit requirements, verified engineering constraints, or necessary correctness guarantees.**

## 1. Reuse Existing Code First

Inspect the relevant codebase before implementing anything.

- Search for existing functions, classes, modules, utilities, and infrastructure that already solve the problem.
    
- Prefer reusing or minimally extending existing implementations instead of writing new ones.
    
- Follow the project's established architecture, naming conventions, interfaces, error-handling patterns, and testing practices.
    
- Do not duplicate functionality already provided by the project or its dependencies.
    
- Do not create parallel implementations, redundant wrappers, or alternative utilities without a concrete need.
    
- Introduce new abstractions only when existing code cannot reasonably satisfy the requirement.
    

**Default: inspect first, reuse second, implement new code only when necessary.**

## 2. Avoid Excessive Function Extraction

**Do not create functions merely for the sake of splitting code.**

Functions must provide meaningful abstraction, reuse, or clarity.

- Keep straightforward, single-use logic inline by default.
    
- Do not habitually extract every one or two lines into separate helper functions.
    
- Avoid proliferating trivial private helpers such as `_get_xxx()`, `_do_xxx()`, `_handle_xxx()`, `_ensure_xxx()`, or `_wrap_xxx()`.
    
- Do not create functions that merely forward arguments, return an attribute, perform a trivial assignment, or wrap an existing call without adding meaningful semantics.
    
- Do not fragment a coherent workflow into numerous tiny functions solely to shorten the main function.
    
- Avoid unnecessary call chains where each layer performs only one or two trivial operations.
    
- Do not introduce helper functions for speculative future reuse.
    
- Do not mechanically apply the single-responsibility principle to split every small operation.
    

Extract a function when it provides concrete value:

- Meaningful logic is actually reused.
    
- Extraction significantly reduces complexity or improves readability.
    
- It encapsulates a coherent, nontrivial responsibility or resource lifecycle.
    
- It establishes a necessary interface, callback, or extension point.
    
- It follows an existing architectural boundary.
    

Before extracting, ask:

1. Would inlining this logic be equally clear or clearer?
    
2. Is this function doing anything meaningful beyond forwarding another call?
    
3. Does this abstraction reduce cognitive complexity or merely move code elsewhere?
    
4. Will readers needlessly jump between functions to understand one simple operation?
    

If extraction provides no clear benefit, keep the logic inline.

**Do not enforce arbitrary function-length limits.** A short function can represent a meaningful interface, and a longer cohesive function can be perfectly reasonable.

## 3. Maintain Engineering Quality

Write code that is straightforward to understand, debug, modify, and maintain.

- Follow existing project conventions for naming, typing, structure, imports, and formatting.
    
- Use clear, descriptive names and explicit interfaces.
    
- Keep related logic together and make data flow easy to follow.
    
- Prefer idiomatic code over clever tricks, overly compressed expressions, or unnecessary indirection.
    
- Avoid deeply nested control flow, duplicated logic, and hidden state changes.
    
- Use appropriate types and preserve established interface contracts.
    
- Write comments for non-obvious reasoning, invariants, and important tradeoffs rather than narrating obvious operations.
    
- Keep resource ownership, cleanup, error propagation, and concurrency semantics clear.
    
- Prefer cohesive code with a few meaningful functions over highly fragmented code with excessive helpers.
    

**Optimize for readability and correctness, not minimum line count or maximum modularity.**

## 4. Avoid Overengineering

- Implement the current requirements without speculative extensions.
    
- Avoid unnecessary factories, strategy patterns, inheritance hierarchies, adapters, wrappers, and configuration layers.
    
- Do not build generic frameworks for a single concrete use case.
    
- Avoid introducing flexibility that the current system does not need.
    
- Do not add backward compatibility or migration mechanisms without an actual requirement.
    
- Do not refactor unrelated code while making a targeted change.
    
- Do not introduce unnecessary dependencies, files, or architectural layers.
    

Choose the least complex design that adequately solves the real problem.

## 5. Avoid Excessive Defensive Programming

- Handle realistic, reachable, or contractually required edge cases.
    
- Trust established upstream validation, enforced invariants, and reliable interface guarantees.
    
- Do not repeatedly validate the same condition at every internal call layer.
    
- Avoid branches for states that cannot occur under the actual execution path.
    
- Do not introduce speculative fallbacks, retries, timeouts, or recovery paths.
    
- Do not mask violated contracts with arbitrary default values.
    
- Do not add multiple layers of validation merely to appear robust.
    

However, preserve safeguards for reachable failures with serious consequences, even when they are unlikely.

**Defensive code must be justified by actual risk, not imagination.**

## 6. Avoid Unnecessary Exception Handling

- Do not add `try/except` around every operation simply because it could theoretically fail.
    
- Prefer catching specific exceptions.
    
- Catch exceptions only when meaningful recovery, cleanup, rollback, translation, or contextualization is necessary.
    
- Avoid redundant catch-and-rethrow or log-and-rethrow blocks.
    
- Do not suppress errors or replace unexpected failures with arbitrary default values.
    
- Do not create deeply nested exception handlers for hypothetical conditions.
    
- Allow unexpected programming errors to propagate when no meaningful recovery exists.
    
- Preserve necessary handling at external system boundaries and resource lifecycle boundaries.
    

An exception handler should have a concrete responsibility. If it does nothing useful, remove it.

## 7. Avoid Overtesting

- Focus on required behavior, meaningful edge cases, known regressions, and critical invariants.
    
- Reuse the project's existing test infrastructure, fixtures, and helpers.
    
- Prefer focused regression tests when fixing bugs.
    
- Avoid repetitive tests, unnecessary parameter combinations, and unrealistic failure injection.
    
- Do not create large test matrices for impossible or unsupported states.
    
- Avoid excessive mocking that merely verifies implementation details.
    
- Do not create new test utilities or frameworks for a small change.
    
- Match testing effort to the change's scope, complexity, and risk.
    
- Do not optimize for test count or coverage percentage at the expense of usefulness.
    
- Run relevant tests and required project checks without unnecessarily expanding verification scope.
    

Retain tests necessary for correctness, security, concurrency, resource safety, and other real risks.

**Test meaningful behavior, not every imaginable possibility.**

## 8. Keep Changes Focused

- Modify only what is necessary to satisfy the current task.
    
- Preserve existing behavior and interfaces unless a change is required.
    
- Avoid unrelated refactoring, cleanup, or cosmetic changes.
    
- Do not add unnecessary logging, configuration, comments, documentation, or dependencies.
    
- Respect existing project documentation and validation requirements.
    
- Prefer a small, cohesive change over an extensive redesign.
    
- Stop expanding the implementation once the requirements are satisfied and necessary verification passes.
    

## 9. Preserve Correctness and Rigor

**Avoiding overengineering must never compromise correctness.**

Real risks must still be handled appropriately, including:

- Data loss, corruption, and inconsistent state.
    
- Resource leaks and lifecycle errors.
    
- Concurrency races, deadlocks, cancellation, and unfinished asynchronous tasks.
    
- Security vulnerabilities and untrusted external inputs.
    
- Real network, storage, and external-service failures.
    
- Existing interface contracts and explicitly required error handling.
    

Evaluate protections based on reachability, consequences, and existing guarantees.

Do not remove necessary safeguards or tests simply to make the implementation shorter.

## 10. Implementation Checklist

Before coding:

1. Does the project already contain reusable functionality?
    
2. What existing architecture and conventions should be followed?
    
3. What is the smallest reasonable change that satisfies the task?
    
4. Can this be implemented directly without unnecessary abstraction?
    

Before adding a function:

1. Is it genuinely needed?
    
2. Does it improve reuse, cohesion, or readability?
    
3. Would inlining it be simpler?
    
4. Does it introduce an unnecessary call layer?
    

Before adding defensive logic or tests:

1. Is the failure or edge case actually reachable?
    
2. Is it required by a contract or supported by a concrete risk?
    
3. Is the protection already provided elsewhere?
    
4. Is the additional complexity justified?
    

Before finishing:

1. Are there redundant helpers, wrappers, or abstractions?
    
2. Are any branches, exception handlers, or tests speculative?
    
3. Is the code concise, cohesive, readable, and consistent with the project?
    
4. Are correctness guarantees preserved?
    
5. Have the relevant tests and required checks passed?
    

## Default Workflow

**Inspect → Reuse → Implement → Verify → Stop**

- **Inspect:** Understand the relevant code, existing utilities, contracts, and conventions.
    
- **Reuse:** Prefer established implementations and patterns.
    
- **Implement:** Write cohesive, readable code with minimal justified complexity.
    
- **Verify:** Perform focused, risk-appropriate validation.
    
- **Stop:** Do not continue adding abstractions, helpers, tests, or defensive branches once the requirements are satisfied.
    

**Final rule: Code should be as simple as reasonably possible, but as rigorous as necessary.**