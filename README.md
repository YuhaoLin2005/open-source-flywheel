# Open Source Flywheel

A methodology for turning personal tools into battle-tested open source contributions.

**Core insight:** The best open source contribution isn't "build something cool and release it." It's "find a high-star community with a gap, submit a PR, let their review process harden your code, then extract it as a standalone project."

## The Four Steps

```
1. EXTRACT → Personal tool/config → general-purpose module (no personal data)
2. FIND    → High-star repo with a complementary gap (fills, not replaces)
3. HARDEN  → Submit PR → community bots + human review → fix real bugs
4. LAUNCH  → Extract as standalone repo with proper README → share
```

## Why This Works

- **Community review is free quality assurance.** CodeRabbit, Greptile, and human maintainers find bugs you never would have caught alone
- **Generality is forced by others.** Python 3.8 compat, cross-platform paths, configurable defaults — these emerge from review, not foresight
- **The gap must be real.** If your tool doesn't fill a missing piece in the target repo, the PR won't merge. This filters out vanity contributions

## How to Find the Right Community

Not any high-star repo. The one where your tool is **complementary**, not redundant:

| Your tool | Good community | Why |
|-----------|---------------|-----|
| Quality gate for AI sessions | ECC (100K★) | Has code quality checks, missing thinking quality |
| Session quality checklist | agent-skills (66K★) | Has REVIEW/SHIP phases, missing learning capture |
| Output self-audit | anthropics/skills (154K★) | Has document skills, missing quality gate for AI output |

Bad fits: repos where your tool overlaps with existing features, repos that aren't actively maintained, repos without review infrastructure.

## Validated Cases

### delivery-gate (2026-06-27)

```
CLAUDE.md five-library rules → ECC PR #2365 → 4 rounds of bot review → 9 bugs fixed → independent repo
```

- **Extracted:** Stop hook from personal CLAUDE.md config
- **Found:** ECC (affaan-m/ECC, 100K★) — had verification-loop for code, nothing for thinking quality
- **Hardened:** CodeRabbit + Greptile found stdin pass-through bug, Python 3.8 crash, non-recursive directory scan, exception handling gaps
- **Launched:** [delivery-gate](https://github.com/YuhaoLin2005/delivery-gate) — 200 lines, stdlib, cross-platform

### self-audit framework (2026-06-27)

```
Four-dimension self-check → agent-skills PR #331 → anthropics/skills PR #1360
```

- **Extracted:** Consistency/Completeness/Groundedness/Honesty framework from self-audit practice
- **Found:** anthropics/skills has document tools, no output quality gate
- **Hardened:** Verified originality through web search — no existing four-dimension framework for AI agents
- **Launched:** Standalone skill at anthropics/skills

### RapidOCR wrapper (2026-06-27)

- **Extracted:** OCR wrapper from PaddleOCR replacement need
- **Found:** Not submitted — RapidOCR is RapidAI's work, properly attributed
- **Lesson:** Not everything should be submitted. Credit where it's due

## What Makes a Good Contribution

1. **Original**, not a wrapper around someone else's work
2. **General**, not tied to your personal setup
3. **Complementary**, fills a real gap in the target community
4. **Minimal**, the smallest thing that solves the problem
5. **Attributed**, credit all dependencies and inspirations

## What NOT to Submit

- Thin wrappers around other open source projects (credit, don't repackage)
- Personal configurations that can't be generalized
- Tools with no clear gap in any community
- Anything you wouldn't want someone else to review line-by-line

## See Also

- [delivery-gate](https://github.com/YuhaoLin2005/delivery-gate) — The first validated case
- [open-source-sync-strategy](memory) — Internal memory document with decision record
