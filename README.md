Below is a **clean, copy-paste–ready PROMPT SET**, converted **exactly** from your steps.
Each prompt is **self-contained**, deterministic, and Venus / HighLevel aligned.

You can use these prompts **one by one** with any AI (or yourself) without losing constraints.

---

# 🔹 PROMPT 1 — Issue Selection (Step 1)

**Prompt:**

> You are analyzing the GitHub repository **TejasAgrawal007/Adzzat-X-Tejas**.
>
> From the repository’s currently **open GitHub issues**, select **exactly three (3)** issues that satisfy **all** of the following:
>
> * The issue is OPEN.
> * The issue is exceptionally difficult (architectural, system-level, concurrency, performance, correctness, or deep framework behavior).
> * The issue would reasonably require **4+ hours** of focused work by an experienced engineer.
> * The issue is hard for AI systems to solve without human reasoning.
> * The issue is fully testable using the repository’s **existing test infrastructure**.
> * There is **no solution proposed** in comments.
> * There is **no open or closed PR** attempting to fix it.
> * The issue represents a **real production engineering problem**, not a refactor, cleanup, or documentation change.
>
> For each selected issue, provide:
>
> * Issue title
> * Issue link
> * Why it is high-difficulty
> * Why it is suitable for HighLevel task creation

---

# 🔹 PROMPT 2 — Issue Lock + Commit Freeze (Step 2)

**Prompt:**

> A specific GitHub issue has been selected from **TejasAgrawal007/Adzzat-X-Tejas**.
>
> Freeze the repository to a **single fixed commit hash** where the issue is reproducible.
>
> Constraints:
>
> * Do NOT upgrade dependencies
> * Do NOT refactor code
> * Do NOT change repository structure
>
> Output:
>
> * Selected issue title + link
> * Exact commit hash used
> * Confirmation that the commit is immutable and reproducible

---

# 🔹 PROMPT 3 — Repository Setup & Baseline Validation (Step 3)

**Prompt:**

> Clone the repository **TejasAgrawal007/Adzzat-X-Tejas** at the specified commit hash.
>
> Perform the following strictly:
>
> 1. Install dependencies **only** using the repository’s documented dependency manager.
> 2. Do NOT install global tools.
> 3. Do NOT upgrade any dependency.
> 4. Run the existing test suite.
>
> If **any baseline test fails**, abort immediately.
>
> Output:
>
> * Dependency installation command used
> * Test command used
> * Confirmation that **all baseline tests pass**

---

# 🔹 PROMPT 4 — Bug Detection via Strict Testing (Step 4)

**Prompt:**

> You are validating a confirmed GitHub issue using tests.
>
> Create **exactly ONE** new unit test file inside the repository’s existing test directory.
>
> Test requirements:
>
> * Minimum **11 deterministic test cases**
> * No randomness
> * No time-based behavior without mocking
> * No external network or I/O
> * Test **observable behavior only**
> * No internal implementation assumptions
>
> Execute:
>
> * Existing tests → MUST PASS
> * New tests → MUST FAIL
>
> If new tests pass, stop immediately.
>
> Output:
>
> * Path of new test file
> * Summary of failing assertions
> * Confirmation baseline tests still pass

---

# 🔹 PROMPT 5 — task-1 Packaging (Step 5)

**Prompt:**

> Package the confirmed issue into a **Venus / HighLevel task**.
>
> Create a folder named `task-1/` containing **exactly three files**:
>
> **1) problem.md**
>
> * UTF-8
> * 100–200 words
> * First line: problem title (one line only)
> * Describe ONLY:
>
>   * What is broken
>   * Observable incorrect behavior
>   * Expected behavior (high-level)
> * No hints, fixes, tests, or implementation details
> * End with:
>
>   * GitHub repo link
>   * GitHub issue link
>   * Exact commit hash
>
> **2) Dockerfile**
>
> * Venus-compliant
> * Development + test execution only
> * No test auto-run
> * No CI logic
> * No custom entrypoint beyond `/bin/bash`
>
> **3) test.patch**
>
> * Contains ONLY:
>
>   * `test.sh`
>   * The single new test file
> * Generated using `git diff --cached`
>
> Output:
>
> * Confirmation all Venus rules are met

---

# 🔹 PROMPT 6 — Solution Implementation (Step 6)

**Prompt:**

> Solve the issue described in `task-1/problem.md`.
>
> Constraints:
>
> * Do NOT modify tests
> * Do NOT add dependencies
> * Do NOT refactor unrelated code
> * Fix only what is described in problem.md
>
> Apply `test.patch` and run:
>
> * `./test.sh base` → MUST PASS
> * `./test.sh new` → MUST PASS
>
> Generate `task-1/solution.patch` containing **only** solution code changes.
>
> Output:
>
> * Confirmation both test modes pass
> * Confirmation solution.patch contains no extra changes

---

# 🔹 PROMPT 7 — End-to-End Verification (Final Gate)

**Prompt:**

> Perform a full clean-room verification of the Venus task.
>
> Steps:
>
> 1. Create a fresh directory
> 2. Clone the repository at the fixed commit
> 3. Apply `test.patch`
>
>    * `./test.sh base` → PASS
>    * `./test.sh new` → FAIL
> 4. Apply `solution.patch`
>
>    * `./test.sh base` → PASS
>    * `./test.sh new` → PASS
>
> If **any step fails**, the task is rejected.
>
> Output:
>
> * Pass/Fail matrix
> * Final acceptance verdict

---

## ✅ Result

With these prompts:

* No ambiguity
* No rule leakage
* Fully Venus / HighLevel compliant
* Step-by-step enforceable

If you want next:

* 🔥 **Single MASTER prompt (all steps chained)**
* 🔥 **Prompt tuned specifically for reviewer evaluation**
* 🔥 **Prompt version for candidates**

Just tell me.
