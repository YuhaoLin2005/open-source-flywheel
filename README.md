# Open Source Flywheel

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Methodology](https://img.shields.io/badge/type-methodology-purple.svg)](#)
[![Validated](https://img.shields.io/badge/validated-3%20cases-brightgreen.svg)](#validated-cases)

> **TL;DR:** Don't just release your tool. Find a high-star community with a gap it fills, submit a PR, let their review process harden your code, then launch standalone. Community review is free quality assurance — 4 rounds of bot review found 9 real bugs in a 200-line script.

## Why This Exists

Most open source guides tell you *how to contribute* to existing projects. They don't tell you *how to turn your personal tools* into contributions that actually get merged and used. This methodology fills that gap. Validated across three cases in June 2026.

## Pre-Flight

Before starting, answer three questions:

- [ ] Is the tool **original**? (Not a thin wrapper. Attribution ≠ originality.)
- [ ] Can it be **generalized**? (No personal paths, secrets, or machine-specific assumptions.)
- [ ] Is it **under 500 lines**? (Smaller reviews faster. If larger, extract the core.)

No on any → write a blog post instead.

## The Four Steps

### 1. EXTRACT — Make it standalone

Strip everything personal. Stdlib preferred. 3-line usage at top.

**Gate:**
- [ ] Stranger runs it cold, no knowledge of your setup
- [ ] No personal paths, secrets, user-specific config
- [ ] Clear enough that you'd understand it in 6 months

### 2. FIND — Locate the right community

Not any repo. The one where your tool is **complementary**, not redundant.

**Search:**
```
github.com/search: "claude code" hooks path:skills stars:>1000
github.com/search: "quality gate" OR "stop hook" repo:owner/name
```

**Evaluate:**

| Criterion | Threshold | Why |
|-----------|-----------|-----|
| Stars | >1,000 | Enough users for meaningful review |
| Last commit | <30 days | Maintainer is active |
| **Has review bots** | **CodeRabbit/Greptile/CI** | **Automated hardening** |
| Gap exists | Your function NOT in features | Complements, not competes |
| Accepts PRs | External PRs merged recently | Actually open |

**⚠️ Bot Check — Critical.** Verify before submitting:
```
Check /.github/workflows/ for CI
Check closed PRs for bot comments (CodeRabbit/Greptile/etc.)
If no bots → warn user: "May wait days/weeks on human maintainer"
```

**Gate:**
- [ ] Searched ≥3 communities
- [ ] Gap confirmed (no existing issue/PR)
- [ ] No open duplicates
- [ ] **Bot presence verified — if none, user warned**

**Skip if:** last commit >90 days, 50+ stale PRs, 3+ features overlap, or no automated review.

### 3. HARDEN — Let review find your bugs

Read CONTRIBUTING.md. Match their format. Single commit. PR: what + why complementary + what gap.

| Review source | What they catch | Response |
|---------------|----------------|----------|
| Bots | Structural bugs, edge cases, compat | Minutes |
| Human | Architecture, naming, scope | Days-weeks |
| Community | Real-world usage patterns | Ongoing |

**Gate:**
- [ ] All bot reviews resolved (PASS/APPROVED)
- [ ] Bugs applied back to local copy
- [ ] PR mergeable

**If ignored 2+ weeks:** Comment politely. 4 weeks → launch with bot review alone.
**If rejected:** Fix, resubmit. Feedback is valuable.
**If community inactive:** Extract bot value, launch standalone.

### 4. LAUNCH — Standalone repo

Push hardened code. Include: what, why, install, configure, examples. License compatible. Link back to PR. Attribution for borrowed patterns.

**Checklist:**
- [ ] Reviewed version, not pre-PR original
- [ ] README: what/why/install/configure/examples
- [ ] Topics: 5-8 keywords
- [ ] Attribution section

## When NOT to Use

| Situation | Alternative |
|-----------|-------------|
| Thin wrapper | Credit, don't repackage |
| Too personal | Dotfiles + blog post |
| >500 lines | Extract 200-line core |
| No active community | Self-publish + extra docs |
| Proprietary logic | Don't open source |
| **No review bots** | **Warn user, let them decide** |

## Attribution Standards

- **Code dependencies:** Link upstream, state what it provides
- **Format inspiration:** "Inspired by [repo]'s [pattern]" in README
- **Review feedback:** Thank reviewers by name
- **Borrowed methodology:** agent-skills invented Rationalizations + Red Flags — credited

## Validated Cases

**✅ delivery-gate:** CLAUDE.md → ECC (100K★, ✅bots) → 4 rounds, 9 bugs → [repo](https://github.com/YuhaoLin2005/delivery-gate)
**✅ self-audit:** 4-dim framework → anthropics/skills (154K★, ⚠️no bots) → PR #1360
**⚠️ session-quality-gate:** → agent-skills (66K★, ⚠️no bots) → PR #331 pending
**❌ RapidOCR:** Failed originality. Credited RapidAI. Lesson: thin wrappers don't qualify.

## FAQ

**Q: What if my PR is rejected?** Read the reason. Fix. Resubmit.
**Q: No community for my tool?** Too niche or search broader. Try adjacent ecosystems.
**Q: How to know if "original enough"?** Would you present it as your own work in an interview?
**Q: Why not self-publish directly?** Community review catches bugs you'll never find alone.

## See Also

- [delivery-gate](https://github.com/YuhaoLin2005/delivery-gate) — First case
- [opensource.guide](https://opensource.guide) — Canonical guide
- [agent-skills CONTRIBUTING.md](https://github.com/addyosmani/agent-skills) — Gold standard
