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

### ✅ Good prompts
- "Draft a minimal fix for X"
- "Add guards so Y never happens"
- "Refactor this to be safer, not faster"

### ❌ Bad prompts
- "Implement feature X end-to-end"
- "Refactor the whole service"
- "Make this production-ready"

---

## The 3-Step Daily Loop (Recommended)

1. **Explore**
```bash
gh copilot explain "How does this module interact with Synapse?" --path modules/
```

2. **Draft**
```bash
gh copilot suggest "Draft a small change to prevent mixed-language carryover" --path src/
```

3. **Own it**
- You review
- You rename things
- You simplify

Copilot drafts. You decide.

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
