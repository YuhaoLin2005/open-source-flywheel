# Open Source Flywheel

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Methodology](https://img.shields.io/badge/type-methodology-purple.svg)](#)
[![Validated](https://img.shields.io/badge/validated-3%20cases-brightgreen.svg)](#validated-cases)

> **The problem:** You've built something useful. You want others to use it. But self-publishing rarely works — most standalone repos get zero traction. Community review is free QA, if you know where to submit.
>
> **The solution:** Personal tool → find gap → PR review hardening → standalone launch. 4 rounds of bot review found 9 real bugs in a 200-line script. The same process turns your personal config into a battle-tested contribution.

---

## Pre-Flight

Answer three questions. **Any "no" → don't use this method.**

- [ ] **Original?** Not a thin wrapper. (Credit, don't repackage.)
- [ ] **General?** No personal paths, secrets, or machine-specific config.
- [ ] **<500 lines?** Smaller = faster review. If larger, extract the core.

**If the target repo has no automated review bots → warn user, let them decide.**

---

## The Four Steps

### 1. EXTRACT — Make it standalone

Strip everything personal. Stdlib preferred. 3-line usage at top.

**Gate:** stranger runs it cold. No personal data. Clear enough for 6 months from now.

### 2. FIND — Locate the right community

Not any repo. The one where your tool is **complementary**, not redundant.

**Evaluate:**

| Criterion | Threshold |
|-----------|-----------|
| Stars | >1,000 |
| Last commit | <30 days |
| **Has review bots** | **CodeRabbit/Greptile/CI** |
| Gap exists | Your function NOT in their features |
| Accepts PRs | Recent external PRs merged |

**⚠️ Bot Check:** Verify `/.github/workflows/` and closed PRs for bot comments. If none → warn user.

**Gate:** searched ≥3 communities. Gap confirmed. No duplicates. **Bot presence verified or warned.**

**Skip if:** >90 days stale, 50+ open PRs, 3+ feature overlaps, or no automated review.

### 3. HARDEN — Let review find your bugs

Match their format. Single commit. PR: what + why complementary + what gap.

| Review source | What they catch | Response |
|---------------|----------------|----------|
| Bots | Structural bugs, edge cases, compat | Minutes |
| Human | Architecture, naming, scope | Days-weeks |
| Community | Real-world patterns | Ongoing |

**No bots?** Use [Named-Persona Adversarial Review](https://github.com/YuhaoLin2005/claude-config) — web-search real engineers' philosophies, 3+ rounds × 3 personas (2 eng + 1 product). Simulates what bots catch.

**Gate:** All bots/personas resolved. Bugs applied locally. PR mergeable.

**Stuck 2+ weeks?** Comment. 4 weeks? Launch with review alone.
**Rejected?** Fix, resubmit. Feedback is valuable.
**Community inactive?** Extract bot value, launch standalone.

### 4. LAUNCH — Standalone repo

Push hardened code. README: what/why/install/examples. License compatible. Link PR. Attribution included.

---

## Attribution Standards

- **Code deps:** Link upstream, state what it provides
- **Format inspiration:** "Inspired by [repo]'s [pattern]"
- **Review feedback:** Thank reviewers by name
- **Borrowed methodology:** agent-skills invented Rationalizations + Red Flags — credited

---

## Validated Cases

**✅ delivery-gate:** CLAUDE.md → ECC (100K★, ✅bots) → 4 rounds, 9 bugs → [repo](https://github.com/YuhaoLin2005/delivery-gate)
**✅ self-audit:** 4-dim framework → anthropics/skills (154K★, ⚠️no bots, 17-reviewer hardened) → PR #1360
**⚠️ session-quality-gate:** → agent-skills (66K★, ⚠️no bots, 17-reviewer hardened) → PR #331 pending
**❌ RapidOCR:** Failed originality. Credited RapidAI.

---

## FAQ

**Q: PR rejected?** Fix, resubmit.
**Q: No community?** Too niche or search broader.
**Q: Original enough?** Would you present it as your own in an interview?
**Q: Why not self-publish?** Community review catches bugs you'll never find alone.

---

## See Also

- [delivery-gate](https://github.com/YuhaoLin2005/delivery-gate)
- [opensource.guide](https://opensource.guide)
- [agent-skills CONTRIBUTING.md](https://github.com/addyosmani/agent-skills)
- [Named-Persona Adversarial Review](https://github.com/YuhaoLin2005/claude-config) — Pre-submit hardening for no-bot repos
