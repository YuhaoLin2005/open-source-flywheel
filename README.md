# Open Source Flywheel

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Validated](https://img.shields.io/badge/validated-3%20cases-brightgreen.svg)](#cases)

> Personal tool → find gap → PR review hardening → standalone launch. Community review is free QA — 4 rounds of bot review found 9 bugs in 200 lines.

## Pre-Flight

- [ ] **Original?** Not a wrapper. Attribution ≠ originality.
- [ ] **General?** No personal paths, secrets, machine-specific config.
- [ ] **<500 lines?** Smaller = faster review. If larger, extract the core.

## Steps

### 1. EXTRACT
Strip personal data. Stdlib preferred. 3-line usage at top. **Gate:** stranger runs it cold.

### 2. FIND
Search: `github.com/search: "claude code" stars:>1000 path:skills`

| Criterion | Threshold |
|-----------|-----------|
| Stars | >1,000 |
| Last commit | <30 days |
| **Has review bots** | **CodeRabbit/Greptile/CI** |
| Gap exists | Your function NOT in their features |
| Accepts PRs | Recent external PRs merged |

**⚠️ No bots? Warn user clearly before proceeding.** Verify: check `/.github/workflows/` and closed PRs for bot comments.

### 3. HARDEN
Match their format. Single commit. PR: what + why complementary + what gap. Bots catch structural bugs in minutes; humans take days.

**Gate:** all bots resolved → apply fixes to local copy → mergeable.
**Stuck 2+ weeks?** Comment. 4 weeks? Launch with bot review alone.
**Rejected?** Fix, resubmit. Feedback is valuable.

### 4. LAUNCH
Push HARDENED code (not original). README: what/why/install/examples. Link back to PR. Topics set. Attribution for borrowed patterns.

## When NOT to Use

| Situation | Alternative |
|-----------|-------------|
| Wrapper around others' work | Credit, don't repackage |
| Personal config, can't generalize | Dotfiles + blog post |
| >500 lines | Extract 200-line core |
| No active community | Self-publish + extra docs |
| **No review bots** | **Warn user, let them decide** |

## Cases

**✅ delivery-gate:** CLAUDE.md → ECC (100K★, ✅bots) → 4 rounds, 9 bugs → [repo](https://github.com/YuhaoLin2005/delivery-gate)
**✅ self-audit:** 4-dim framework → anthropics/skills (154K★, ⚠️no bots) → PR #1360
**⚠️ session-quality-gate:** → agent-skills (66K★, ⚠️no bots) → PR #331 pending
**❌ RapidOCR:** Failed originality check. Credited RapidAI.

## See Also

- [delivery-gate](https://github.com/YuhaoLin2005/delivery-gate)
- [opensource.guide](https://opensource.guide)
- [agent-skills CONTRIBUTING.md](https://github.com/addyosmani/agent-skills)
