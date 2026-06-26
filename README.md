# Open Source Flywheel

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Methodology](https://img.shields.io/badge/type-methodology-purple.svg)](#)
[![Validated](https://img.shields.io/badge/validated-3%20cases-brightgreen.svg)](#validated-cases)

> **TL;DR:** Don't just release your tool. Find a high-star community with a gap it fills, submit a PR, let their review process harden your code, then launch standalone. Community review is free quality assurance — 4 rounds of bot review found 9 real bugs in a 200-line script.

---

## Why This Exists

Most open source guides tell you *how to contribute* to existing projects. They don't tell you *how to turn your personal tools* into contributions that actually get merged and used.

This methodology fills that gap. It was validated across three cases in June 2026 and is itself open to iteration.

---

## Pre-Flight

Before starting, answer three questions:

- [ ] Is the tool **original**? (Not a thin wrapper. Attribution ≠ originality.)
- [ ] Can it be **generalized**? (No personal paths, secrets, or machine-specific assumptions.)
- [ ] Is it **under 500 lines**? (Smaller reviews faster. If larger, extract the core.)

No on any → write a blog post instead. This method needs something to work with.

---

## The Four Steps

### 1. EXTRACT — Make it standalone

Strip everything personal. Reduce to minimum dependencies (stdlib preferred). Write usage in a 3-line comment at the top.

**Gate:**
- [ ] A stranger can run this with zero knowledge of your setup
- [ ] No personal paths, secrets, or user-specific configuration remains
- [ ] README or docstring is clear enough for you to understand in 6 months

---

### 2. FIND — Locate the right community

Not any repo. The one where your tool is **complementary**, not redundant. Search:

```
github.com/search: "claude code" hooks path:skills stars:>1000
github.com/search: "quality gate" OR "stop hook" repo:owner/name
```

Evaluate each candidate:

| Criterion | Threshold | Why |
|-----------|-----------|-----|
| Stars | >1,000 | Enough users for meaningful review |
| Last commit | <30 days | Maintainer is active |
| **Has review bots** | **CodeRabbit, Greptile, or CI checks** | **Automated hardening — free QA** |
| Gap exists | Your function NOT in their features | Complements, not competes |
| Accepts PRs | Recent external PRs merged | Actually open |

**⚠️ BOT CHECK — Critical.** Before submitting, check `.github/workflows/` for CI and look at recent PRs for bot activity (CodeRabbit, Greptile, etc.). Repos without automated review depend entirely on maintainer availability. Your PR may sit for weeks or be rejected for issues a bot would catch instantly.

**How to verify:**
```
# Check for CI workflows
github.com/owner/repo/actions

# Look at closed PRs — any bot comments?
github.com/owner/repo/pulls?q=is:pr+is:closed

# Browse .github/workflows/
github.com/owner/repo/tree/main/.github/workflows
```

**Gate:**
- [ ] Searched at least 3 different communities
- [ ] Gap confirmed (no existing issue/PR covers it)
- [ ] No open duplicate PRs
- [ ] **Verified bot/CI presence — if none, warned user**

**Skip if:** last commit >90 days, 50+ stale PRs, 3+ features overlap, **or no automated review**.

**⚠️ If no bots found:** Tell the user clearly — "This repo has no automated review. Your PR will wait on a human maintainer who may take days or weeks. Proceed only if you're OK with that."

---

### 3. HARDEN — Let review find your bugs

Read CONTRIBUTING.md. Match their format exactly. Single commit. PR description: what, why complementary, what gap.

Expect multiple rounds. Bots find structural bugs (minutes). Humans find architectural issues (days to weeks).

| Review source | What they catch | Response time |
|---------------|----------------|---------------|
| Automated bots | Structural bugs, edge cases, compatibility | Minutes |
| Human maintainer | Architecture, naming, scope | Days-weeks |
| Community | Real-world usage patterns | Ongoing |

**Gate:**
- [ ] All bot reviews resolved (PASS/APPROVED)
- [ ] All discovered bugs applied back to your local copy
- [ ] PR is mergeable

**If PR is ignored 2+ weeks:** Comment politely. 4 weeks no response → proceed to launch with bot review alone.
**If rejected:** Fix, resubmit. Feedback is valuable even when unwelcome.
**If community inactive:** Extract bot review value, launch standalone.

---

### 4. LAUNCH — Standalone repo

Push the hardened code (not the original). Include: what, why, install, configure, examples. License compatible with community repo. Link back to original PR.

**Checklist:**
- [ ] Code is reviewed version, not pre-PR original
- [ ] README: what, why, install, configure, examples
- [ ] Topics set (5-8 keywords)
- [ ] Attribution section for patterns adapted from other projects
- [ ] No personal data

---

## When NOT to Use

| Situation | Alternative |
|-----------|-------------|
| Thin wrapper around others' work | Credit, don't repackage |
| Too personal to generalize | Dotfiles + blog post |
| >500 lines, tightly coupled | Extract 200-line core, submit that |
| No active community fits | Self-publish with extra docs |
| Contains proprietary logic | Don't open source |
| **Target repo has no automated review** | **Warn user, let them decide** |

---

## Attribution Standards

- **Code dependencies:** Link upstream, state what it provides
- **Format inspiration:** "Inspired by [repo]'s [pattern]" in README
- **Review feedback:** Thank reviewers by name
- **Borrowed methodology:** `agent-skills` invented Rationalizations + Red Flags format — credited

---

## Validated Cases

### ✅ delivery-gate
```
EXTRACT: CLAUDE.md five-library rules → 200-line stop hook
FIND:    ECC (100K★) — code quality checks exist, thinking quality missing
         ✅ Has CodeRabbit + Greptile bots
HARDEN:  PR #2365, 4 rounds, 9 bugs (stdin pass-through, Python 3.8 crash, os.walk, ...)
LAUNCH:  github.com/YuhaoLin2005/delivery-gate
```

### ✅ self-audit
```
EXTRACT: Consistency/Completeness/Groundedness/Honesty framework
FIND:    anthropics/skills (154K★) — document skills, no output quality gate
         ⚠️ No bots, warned user
HARDEN:  Originality confirmed via web search → PR #1360
LAUNCH:  Cross-linked to agent-skills session-quality-gate
```

### ⚠️ session-quality-gate
```
EXTRACT: Four-dimension self-audit + learning capture + disk check
FIND:    agent-skills (66K★) — REVIEW/SHIP phases, no learning capture
         ⚠️ No bots, warned user
STATUS:  PR #331 pending human review
LESSON:  Repos without bots = slower, riskier. But valid if format matches.
```

### ❌ RapidOCR wrapper
```
DECISION: Not submitted. Thin wrapper around RapidAI's work.
LESSON:  Fails originality check. Credit the source, don't repackage.
```

---

## FAQ

**Q: What if my PR is rejected?**
A: Read the reason. Fix what they asked. Resubmit. A rejection with feedback is better than no review at all.

**Q: What if there's no community for my tool?**
A: Either the tool is too niche (keep it private), or you haven't searched broadly enough. Try adjacent ecosystems.

**Q: How do I know if my tool is "original enough"?**
A: If you wouldn't feel comfortable presenting it as your own work in a job interview, it's not original. Attribution helps, but doesn't make a wrapper original.

**Q: Why not just self-publish directly?**
A: You can. But community review catches bugs you'll never find alone. Our 200-line script had 9 real bugs — 8 of them were found by bots, not humans.

---

## See Also

- [opensource.guide](https://opensource.guide) — Canonical open source contribution guide (complementary, not competing)
- [delivery-gate](https://github.com/YuhaoLin2005/delivery-gate) — First validated case
- [agent-skills CONTRIBUTING.md](https://github.com/addyosmani/agent-skills) — Gold standard for skill PRs
