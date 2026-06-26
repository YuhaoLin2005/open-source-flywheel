# Open Source Flywheel

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Methodology](https://img.shields.io/badge/type-methodology-purple.svg)](#)
[![Validated](https://img.shields.io/badge/validated-6%20cases-brightgreen.svg)](#validated-cases)
[![Reviewed](https://img.shields.io/badge/reviewed-24%20personas-orange.svg)](#)

> **The problem:** You've built something useful. Self-publishing rarely works — most standalone repos get zero traction. Community review is free QA, if you know where to submit.
>
> **The solution:** Extract → Find gap → PR hardening → Launch. 4 rounds of bot review found 9 bugs in 200 lines.

---

## Pre-Flight

**Any "no" → stop.** Ask someone else — self-assessment of originality is biased.

- [ ] **Original?** Not a wrapper. (Credit ≠ originality.)
- [ ] **General?** No personal paths, secrets, machine config.
- [ ] **<500 lines?** Smaller = faster review.

**No review bots?** Warn user. Use [Named-Persona Adversarial Review](https://github.com/YuhaoLin2005/claude-config) as fallback.

---

## Steps (~hours → days → hours)

### 1. EXTRACT
Strip personal. Stdlib preferred. **Gate:** stranger runs it cold.

### 2. FIND
Complementary gap, not redundant. Stars >1K, commits <30d, has bots, gap confirmed, PRs accepted. **⚠️ Verify bots in `/.github/workflows/`**

### 3. HARDEN
Match their format. Single commit. **Respect maintainer time.** No bots? Named-persona: 3+ rounds × 3 personas.

**Stuck?** 4 weeks → launch. **Rejected?** Fix, resubmit.

### 4. LAUNCH
Hardened code. README: what/why/install/examples. Link PR. Attribute.

### 5. LEARN
After launching, feed back into the method: What worked? What broke? Update validated cases. The flywheel gets better every cycle.

---

## Validated Cases

**✅ delivery-gate:** ECC (100K★, ✅bots) → 4 rounds, 9 bugs → [repo](https://github.com/YuhaoLin2005/delivery-gate)
**✅ self-audit:** anthropics/skills (154K★, ⚠️no bots, 17-reviewer hardened) → PR #1360
**✅ flywheel:** → 8 rounds, 24 persona views → this repo
**❌ RapidOCR:** Pre-Flight filtered. ❌ session-quality-gate: no bots, no response. ❌ compact-counter: channel blocked.

---

## FAQ

**Rejected?** Fix. **No community?** Search broader. **Original?** Would you present it in an interview? **Why not self-publish?** Bots catch bugs you won't.

## See Also

[delivery-gate](https://github.com/YuhaoLin2005/delivery-gate) · [opensource.guide](https://opensource.guide) · [agent-skills](https://github.com/addyosmani/agent-skills) · [Named-Persona Review](https://github.com/YuhaoLin2005/claude-config)
