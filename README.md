# Adzzat-X-Tejas
**Haan bhai, bilkul — step by step isse 100% Venus / HighLevel ke saath align kar sakte hain.**
Main neeche **exact execution plan** de raha hoon. Tum bas har step ka output share karte jaana, main validate + correct karta jaunga. No guesswork.

---

## 🔁 Overall Plan (High-Level)

Hum **5 clear phases** me kaam karenge.
Har phase ke end pe **PASS / FAIL gate** hoga.

---

## ✅ STEP 1 — Issue Selection (MOST IMPORTANT)

**Tumhe ye dena hoga:**

1. Repository (already fixed ✅):
   `TejasAgrawal007/Adzzat-X-Tejas`
2. **Exactly 3 OPEN GitHub issues**

   * Issue link
   * Confirm they are **OPEN**
   * No PR linked
   * No solution in comments

### 🔍 Main kaam (tum):

* GitHub → Issues tab
* 3 issues choose karo jo:

  * Architectural / system-level ho
  * 4+ hours engineer effort lage
  * Testable ho

📤 **Tum mujhe bhejo:**

```
Issue 1: <title + link>
Issue 2: <title + link>
Issue 3: <title + link>
```

➡️ **Gate:**
❌ Agar issue weak / cosmetic hua → reject
✅ Agar strong hua → Step 2

---

## ✅ STEP 2 — One Issue Lock + Commit Freeze

Ab un 3 me se **1 issue pick** karenge (main help karunga).

### Tum karoge:

```bash
git clone https://github.com/TejasAgrawal007/Adzzat-X-Tejas
cd Adzzat-X-Tejas
git checkout <COMMIT_HASH>
```

📤 Tum bhejo:

* Selected issue link
* Exact commit hash (`git rev-parse HEAD`)

➡️ **Gate:**
❌ Moving branch / no hash → INVALID
✅ Fixed commit → Step 3

---

## ✅ STEP 3 — Baseline Validation (Non-Negotiable)

```bash
# documented way only
npm test   # or pytest / pnpm / etc (repo jo use karta ho)
```

📤 Tum bhejo:

* Command used
* Output summary

➡️ **Gate:**
❌ Baseline tests fail → STOP (repo invalid)
✅ All tests pass → Step 4

---

## ✅ STEP 4 — Bug Detection via Tests

### Rules (STRICT):

* **Exactly 1 new test file**
* **Minimum 11 tests**
* Deterministic
* No randomness / network / time

### Tum karoge:

1. New test likho (behavior only)
2. Run:

```bash
./test.sh base   # PASS
./test.sh new    # FAIL
```

📤 Tum bhejo:

* Test file
* Failing output (new)
* Passing output (base)

➡️ **Gate:**
❌ New tests pass → issue not real → STOP
✅ New tests fail → CONFIRMED → Step 5

---

## ✅ STEP 5 — task-1/ Packaging (Venus Core)

Create:

```
task-1/
 ├─ problem.md
 ├─ Dockerfile
 └─ test.patch
```

### problem.md (VERY STRICT)

* 100–200 words
* What is broken
* Observable behavior only
* No hints, no fixes

### test.patch

Only:

* `test.sh`
* new test file

➡️ **Gate:**
❌ Extra files / hints → INVALID
✅ Clean → Step 6

---

## ✅ STEP 6 — Solution Phase (LAST)

1. Fix bug (no refactor)
2. Generate:

```
task-1/solution.patch
```

3. Full replay test:

```bash
./test.sh base   # PASS
./test.sh new    # PASS
```

➡️ **Gate:**
❌ Any failure → REJECT
✅ All green → ✔️ **FULLY ALIGNED**

---

## 🧠 My Role (Clear)

* ❌ Main repo / issue suggest nahi karunga
* ✅ Main:

  * Issue quality judge karunga
  * Tests & problem.md alignment check karunga
  * Venus rules violation pakadunga
  * Final PASS/FAIL stamp dunga

---

## 🚀 Next Action (Start Here)

👉 **Abhi sirf STEP 1 karo**
Send me:

```
Issue 1 link
Issue 2 link
Issue 3 link
```


