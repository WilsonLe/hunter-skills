---
name: github-copilot-cli
 description: Efficient daily use of GitHub Copilot CLI for senior engineers. Use when planning, prompting, reviewing, or chaining Copilot CLI commands (gh copilot) to explore codebases, draft changes, debug issues, or accelerate workflows without losing architectural intent.
---

# GitHub Copilot CLI – Efficient Workflow

## Mental Model
Treat Copilot CLI as a **team of elite specialists** coordinated by you:
- One Copilot instance can act as **frontend engineer**
- One as **backend engineer**
- One as **tester / QA**
- One as **infrastructure or refactor specialist**

Copilot is excellent at coding *and* architecture when given clear roles. You act as the **CTO / conductor**:
- Define goals and constraints
- Let Copilot instances propose solutions
- Observe trade‑offs and conflicts
- Escalate decisions or risks to yourself explicitly

---

## Core Commands You Should Actually Use

### 1. Ask questions about a codebase
```bash
gh copilot explain "What does this service do?" --path src/
```
Use when orienting yourself or reloading context after a break.

---

### 2. Generate a focused change (most common)
```bash
gh copilot suggest "Add logging when translation fallback is used" --path services/translation
```
**Best practice:**
- Phrase the request as a **delta**, not a feature
- Always point it at a **specific directory**

---

### 3. Debug with constraints
```bash
gh copilot suggest "Why might this function return null under load?" --path src/choreo
```
Follow up manually by reading the code it points to.

---

### 4. Tests first, code second
```bash
gh copilot suggest "Write failing tests for punctuation correction on voice transcription" --path tests/
```
Then iterate toward the fix yourself.

---

## Prompting Patterns That Work

### ✅ Good prompts (role-aware)
- "As a backend engineer, draft a minimal fix for X"
- "As a tester, add guards so Y never happens"
- "As infra, refactor this to be safer, not faster"

### ❌ Bad prompts
- "Implement feature X end-to-end"
- "Refactor the whole service"
- "Make this production-ready"

---

## Multi‑Copilot Orchestration Loop (Recommended)

1. **Decompose (CTO)**
   - State the goal and constraints
   - Split into FE / BE / QA / Infra concerns

2. **Propose (Copilot roles)**
```bash
gh copilot suggest "As a backend engineer, propose a minimal fix for mixed-language carryover" --path src/

gh copilot suggest "As a tester, write failing tests for mixed-language carryover" --path tests/
```

3. **Cross‑check (Copilot vs Copilot)**
   - Compare proposals
   - Look for disagreement or assumptions

4. **Escalate (to you)**
   - Surface trade‑offs
   - Highlight risk
   - Ask for decision

5. **Finalize (with you)**
   - Apply changes
   - Clean up naming
   - Merge intentionally

---

## When NOT to Use Copilot CLI

- Architectural decisions
- Cross-repo coordination
- Security-sensitive logic
- Complex state machines

Use it **inside** the solution, not **for** the solution.

---

## Golden Rule
If you wouldn’t delegate the task to a junior engineer **unsupervised**, don’t delegate it to Copilot CLI either.

Use it to go faster — not to think less.
