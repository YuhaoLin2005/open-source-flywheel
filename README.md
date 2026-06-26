# Open Source Flywheel

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Validated](https://img.shields.io/badge/validated-6%20cases-brightgreen.svg)](#validated-cases)
[![Reviewed](https://img.shields.io/badge/reviewed-24%20personas-orange.svg)](#)

> **The problem:** You've built something useful. Self-publishing rarely works. Community review is free QA — if you know where to submit.
>
> **The solution:** Extract → Find gap → PR hardening → Launch. 4 rounds of bot review found 9 bugs in a 200-line script.

---

## Pre-Flight

**Any "no" → stop.** Ask someone else — self-assessment of originality is biased.

- [ ] **Original?** Not a wrapper. Credit ≠ originality. If you wouldn't present it as your own in an interview, don't submit.
- [ ] **General?** No personal paths, secrets, or machine-specific config.
- [ ] **<500 lines?** Smaller = faster review. If larger, extract the core.

**⚠️ No review bots in target repo?** Warn user. Use [Named-Persona Adversarial Review](https://github.com/YuhaoLin2005/claude-config) — 3+ rounds, 3 personas each (2 engineers + 1 product). Minimum 9 independent perspectives before submitting.

---

## Steps (~hours → days → weeks → hours → ongoing)

### 1. EXTRACT — Make it standalone
Strip personal data. Stdlib preferred. 3-line usage at top.
**Gate:** Stranger runs it cold. No secrets. Clear enough for 6 months from now.

### 2. FIND — Locate the right community
Complementary gap, not redundant. Search:
```
github.com/search: "claude code" stars:>1000 path:skills
```
**Evaluate:** Stars >1K, commits <30d, **has review bots**, gap confirmed, external PRs accepted.
**⚠️ Bot check:** Verify `/.github/workflows/` and closed PRs for bot activity.
**Skip if:** >90 days stale, 50+ open PRs, 3+ feature overlaps.

### 3. HARDEN — Let review find your bugs
Match their format exactly. Single commit. **Respect maintainer time — small PRs, prompt responses to feedback.**
| Review source | Catch | Response |
|---------------|-------|----------|
| Bots | Structural bugs, edge cases, compat | Minutes |
| Human | Architecture, naming, scope | Days-weeks |
| Community | Real-world patterns | Ongoing |

**No bots?** Named-persona review (see Pre-Flight). **Stuck 2+ weeks?** Comment. 4 weeks? Launch with review alone. **Rejected?** Fix, resubmit — feedback is valuable.

### 4. LAUNCH — Standalone repo
Push hardened code. README: what/why/install/examples. License compatible. Link PR. Attribute borrowed patterns.

### 5. LEARN — Close the loop
After launching: What worked? What broke? Update validated cases. The flywheel improves with every cycle.

---

## Attribution

- **Code deps:** Link upstream, state what it provides
- **Format patterns:** "Inspired by [repo]'s [pattern]" in README
- **Reviewers:** Thank by name in commit messages
- **This method borrows:** agent-skills invented Rationalizations + Red Flags format — credited

---

## Validated Cases

**✅ delivery-gate:** ECC (100K★, ✅bots) → 4 rounds, 9 bugs → [repo](https://github.com/YuhaoLin2005/delivery-gate)
**✅ self-audit:** anthropics/skills (154K★, ⚠️no bots, 17-reviewer hardened) → PR #1360
**✅ flywheel:** → 8 rounds, 24 persona views → this repo
**❌ RapidOCR:** Pre-Flight filtered — thin wrapper. **❌ session-quality-gate:** no bots, no response. **❌ compact-counter:** channel blocked by karma requirements.

## FAQ

**Q: PR rejected?** Read reason. Fix. Resubmit. **Q: No community fits?** Too niche, or search broader — try adjacent ecosystems. **Q: Why not self-publish directly?** Bots catch bugs you'll never find alone. Our 200-line script had 9 bugs — 8 found by bots.

## See Also

[delivery-gate](https://github.com/YuhaoLin2005/delivery-gate) · [opensource.guide](https://opensource.guide) · [agent-skills](https://github.com/addyosmani/agent-skills) · [Named-Persona Review](https://github.com/YuhaoLin2005/claude-config)
