# Adzzat-X-Tejas

Step 1:

The target repository has already been finalized. Do not suggest alternative repositories or modify the selection. Your sole responsibility is to analyze the existing repository and its currently open GitHub issues.
From those open issues, select exactly three (3) that satisfy all of the following conditions:
1. Issue Status
    * The issue must be open at the time of selection.
2. Difficulty Level
    * The issue must be exceptionally difficult, involving architectural design, system-level behavior, concurrency, performance, correctness guarantees, or deep framework internals.
    * It must represent work that would reasonably require 4+ hours of focused effort from an experienced engineer.
3. AI-Resistance
    * The issue must be hard for AI systems to solve reliably without substantial human reasoning, trade-off analysis, or deep understanding of the repository’s architecture.
4. Testability
    * The issue must be fully testable using the repository’s existing testing infrastructure (unit, integration, or end-to-end), without introducing nondeterminism or external dependencies.
5. No Existing Solution
    * There must be no proposed solution in:
        * Issue comments
        * Open or closed pull requests
    * The issue must not have an active or abandoned PR attempting to resolve it.
6. Engineering Significance
    * The issue must represent a meaningful real-world engineering problem, not a cosmetic change, refactor, documentation update, or minor bug fix.

Required Output for Each Selected Issue
For each of the three issues, provide:
* Issue reference (title + link)
* Why the issue is high-difficulty
    * Explain the architectural, systemic, or technical complexity involved.
* Why it is suitable for HighLevel task creation
    * Demonstrate how the problem is:
        * Well-bounded
        * Deterministic
        * Objectively testable under the current test setup
        * Aligned with real production engineering work
Use the provided example issue only as a difficulty and quality benchmark. Do not restate, reuse, or closely mirror that example. Each selected issue must be distinct and original.

Problem Description : 


Step 2:

Strict Task Specification (HighLevel / Venus-Aligned)
Phase 0 — Preconditions (Non-Negotiable)
* A specific GitHub repository and issue will be provided.
* You must work against a fixed commit hash (no moving targets).
* Do NOT fix the issue. This task is only about detecting, isolating, and formalizing the bug into a HighLevel-compatible task.

Phase 1 — Repository Setup & Validation
1. Clone the GitHub repository locally
    * Checkout the exact commit hash referenced by the issue.
    * Do not upgrade dependencies or refactor code.
2. Install dependencies
    * Use only the repository’s documented dependency manager.
    * No global installs.
    * No dependency upgrades.
3. Run existing tests
    * All existing tests must pass before proceeding.
    * If baseline tests fail, abort the task (repo is invalid).

Phase 2 — Bug Detection via Strict Testing
1. Create exactly ONE new unit test file
    * Location: inside the existing tests/ (or equivalent) directory
    * Follow repository testing conventions exactly.
2. Write exceptionally strict tests
    * Minimum 11 test cases, including edge cases.
    * Tests must:
        * Be deterministic
        * Use no randomness
        * Use no time-based behavior without mocking
        * Use no external network calls
    * The tests must only validate behavior, not implementation.
3. Execute the new tests
    * If all new tests pass, the issue is no longer present → STOP.
    * If any new test fails, the issue is confirmed → proceed.

Phase 3 — Task Packaging (task-1/)
If the issue is confirmed, create a folder named:
task-1/
This folder must contain exactly three files:

1️⃣ problem.md
Rules (Very Strict):
* First line: Problem title (one line only)
* Problem Description section:
    * Short
    * Precise
    * No repetition
    * No background story
    * No implementation hints
    * No “how to fix” guidance
* Describe only what is broken and the observable incorrect behavior.
End of file must include:
* GitHub repository link
* GitHub issue link
* Exact commit hash used
❌ Do NOT include:
* Test references
* Code snippets
* Suggested solutions
* Architectural hints

2️⃣ Dockerfile
* Must strictly follow Venus Docker rules
* Purpose: development + test execution only
* Allowed:
    * Base Venus image
    * Dependency installation
* Forbidden:
    * Running tests automatically
    * CI logic
    * Custom entrypoints beyond /bin/bash
Use the provided sample as a structural reference only, not copy-paste.

3️⃣ test.patch
This file must be generated exactly as follows:
Contents
The patch must include only two file diffs:
1. test.sh
    * Must support:
        * ./test.sh base → existing tests only (PASS)
        * ./test.sh new → new tests only (FAIL on baseline)
2. The single unit test file you created
Generation Rules
* Stage files manually: git add test.sh path/to/new_test_file
* 
* Generate patch: git diff --cached > task-1/test.patch
* 
❌ Do NOT include:
* Fixes to source code
* Refactors
* Formatting changes
* Dependency changes
* Extra files

Phase 4 — Quality Bar (Hard Requirements)
The task is invalid if any of the following are true:
* Fewer than 11 tests
* Tests rely on nondeterministic behavior
* Tests reference internal implementation details
* Tests fail intermittently
* Patch contains unrelated changes
* Problem description hints at a solution
* Baseline tests do not pass
* New tests do not fail on the base commit

Core Principle (Must Be Followed)
Everything tested must be described. Everything described must be testable. Nothing extra. Nothing missing.


Step 3:

While writing problem.md and creating test cases to validate the bug/behavior, you must strictly follow the rules below:
📄 Problem.md Quality Rules
* The problem description must contain only necessary information.
* The description must:
    * Clearly state what is broken
    * Describe observable incorrect behavior
    * Define expected behavior at a high level
* Keep it short, precise, and non-repetitive.
❌ Do NOT include:
* Implementation hints
* Debugging clues
* Suggested fixes
* Pseudocode
* Test references
* Architectural advice
The problem description must be understandable without reading the tests, yet fully validated by them.

🧪 Test Case Quality Rules
* Tests must validate only the behavior described in problem.md.
* Every test assertion must map directly to a statement in the problem description.
* No test may:
    * Assume undocumented behavior
    * Test internal implementation details
    * Introduce new requirements not stated in problem.md
Tests must be:
* Deterministic
* Reproducible
* Strict
* Edge-case heavy (minimum 11 test + edge cases)

🔁 Problem ↔ Test Alignment (Zero-Tolerance Rule)
* 100% alignment is mandatory:
    * Everything described in problem.md must be tested.
    * Nothing tested may be missing from problem.md.
If:
* A behavior is tested but not described → ❌ INVALID
* A behavior is described but not tested → ❌ INVALID

📚 Reference Sample Usage
A sample task from another Venus submission has been provided.
* Study the sample only to understand structure, tone, and strictness.
* Do NOT:
    * Reuse wording
    * Mirror problem phrasing
    * Copy test logic
* The new task must be original, independent, and issue-specific.

   🔧 Solution Implementation & Verification Phase (Strict)
After completing task creation (task-1/problem.md, Dockerfile, test.patch), proceed with solution implementation as follows:

Phase 5 — Solve the Issue (Controlled Scope)
1. Solve the problem in the target repository
    * Apply fixes strictly within the repository’s existing architecture.
    * Do NOT:
        * Add new dependencies
        * Refactor unrelated code
        * Modify tests or tooling
        * Change behavior not described in problem.md
2. Copy test.patch into the repository
    * Apply the patch exactly as generated in task-1/test.patch.
3. Run test validation
    * Execute:    ./test.sh base
    * ./test.sh new
    *   
    * Both must pass.
    * If either fails, the solution is invalid.

Phase 6 — Create solution.patch
1. Generate solution patch
    * Create solution.patch inside task-1/.
    * The patch must:
        * Contain only the code changes required to fix the issue
        * Exclude tests, Dockerfile, scripts, or unrelated files
2. Patch generation rule    git add <only-solution-files>
3. git diff --cached > task-1/solution.patch
4.   
❌ Do NOT include:
* Formatting-only changes
* Debug logs
* Commented-out code
* Cleanup unrelated to the bug

Phase 7 — End-to-End Verification (Mandatory)
To confirm correctness, perform the entire flow from scratch:
Validation Steps
1. Create a fresh directory:    mkdir test-project && cd test-project
2.   
3. Clone the repository again (same commit hash).
4. Apply test.patch only.
    * Run:    ./test.sh base   # MUST PASS
    * ./test.sh new    # MUST FAIL
    *   
5. Apply solution.patch.
6. Re-run tests:    ./test.sh base   # MUST PASS
7. ./test.sh new    # MUST PASS
8.   

✅ Acceptance Criteria (Zero Tolerance)
The solution is considered valid only if:
* Baseline tests pass before and after the solution
* New tests fail before applying solution.patch
* New tests pass after applying solution.patch
* solution.patch contains only solution changes
* No existing functionality is broken
* All behavior fixed is explicitly described in problem.md
If any step fails → solution is rejecte





Problem description have appropriate length (target: 100-200 words)

Problem description matches the selected category

Problem description should be valid UTF-8

Problem is not plagiarized

Test patch sanity checks

Test patch applies correctly

Problem description sanity checks (AI, up to 1 min)

Problem and tests are good quality (AI, up to 1 min)

Problem description contains only necessary information (AI, up to 2 min)

Problem and tests are aligned (AI, up to 1 min)


Phantom Lineage Termination in Cardinality-Expanding Projections


“You are an automated test-driven programming problem validator. First, generate an original UTF-8 problem description of 100–200 words that strictly matches the given category, is non-plagiarized, clear, unambiguous, and contains only necessary information; internally verify word count, originality, category match, and clarity. Then create a flawed base implementation and a base test suite such that all base tests pass on the base implementation while the implementation does not fully satisfy the problem. Perform test-patch sanity checks to ensure tests compile and run. Next, generate a clean patch (diff) that applies to the base code and fixes all missing logic without changing tests. After that, generate a new hidden test suite that fully reflects the problem and includes edge cases so that before the patch base tests pass but new tests fail, and after the patch both base and new tests pass. Finally, run AI quality gates including problem description sanity, problem–test alignment, test quality, no ambiguity, no leakage, and originality, and output in this order: problem description, base implementation, base tests, solution patch, new tests, and a validation pass/fail matrix.”



