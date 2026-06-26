# Open Source Flywheel

A rigorous method for turning personal tools into battle-tested open source contributions — validated across three cases in June 2026.

**Core insight:** The strongest open source contributions don't start with "I built something cool." They start with "I use this daily, and a high-star community has a gap it fits."

---

## Pre-Flight Checklist

Before step 1, answer three questions:

- [ ] Is the tool **original**? (Not a thin wrapper around someone else's work. Attribution ≠ originality.)
- [ ] Can it be **generalized**? (No hardcoded personal paths, secrets, or assumptions about your setup.)
- [ ] Is the code **under 500 lines**? (If larger, extract the core. Small tools review faster and merge more often.)

If any answer is "no" → this method isn't the right fit. Write a blog post instead.

---

## Step 1: EXTRACT

**Goal:** Turn a personal module into a self-contained, dependency-minimal artifact.

**Process:**
- Strip all personal paths, secrets, user-specific configuration
- Reduce dependencies to minimum (stdlib preferred)
- Write 3-line usage in a comment at the top of the file
- Keep it under 500 lines. If larger, extract the core piece first

**Gate — verify before proceeding:**
- [ ] Can a stranger run this with zero knowledge of your setup?
- [ ] Does `grep -i "C:/Users"` or equivalent return nothing?
- [ ] Is the README or docstring clear enough that you'd understand it in 6 months?

---

## Step 2: FIND

**Goal:** Locate a high-star, active community where your tool fills a specific gap.

**Search methodology (concrete):**

```
# GitHub code search for active repos with hooks/plugins/skills directories
github.com/search: "claude code" hooks path:skills stars:>1000

# Find repos that mention your tool's domain but lack your specific feature
github.com/search: "quality gate" OR "stop hook" repo:owner/name

# Check recent commit activity (last 30 days = active)
github.com/owner/repo/commits/main
```

**Evaluation rubric:**

| Criterion | Threshold | Why |
|-----------|-----------|-----|
| Stars | >1,000 | Enough users for meaningful review |
| Last commit | <30 days | Maintainer is active |
| Has review bots | CodeRabbit/Greptile configured | Automated hardening |
| Gap exists | Your tool's function NOT in their existing features | Avoids redundancy |
| Accepts PRs | Recent merged PRs from external contributors | Actually open to contributions |

**Gate — verify before proceeding:**
- [ ] Searched at least 3 different communities
- [ ] Confirmed the gap is real (searched existing issues/PRs for similar proposals)
- [ ] No open PR already covering the same gap
- [ ] Maintainer has merged external PRs in the last 60 days

**Red flags — skip this community if:**
- Repo is a personal collection with no review process
- Last commit >90 days ago
- PR queue has 50+ open with no recent merges
- Your tool would overlap with 3+ existing features

---

## Step 3: HARDEN

**Goal:** Use community review to find and fix real bugs before standalone release.

**Before submitting:**
- [ ] Read CONTRIBUTING.md (format, conventions, test requirements)
- [ ] Match their file naming, directory structure, and frontmatter format exactly
- [ ] Include a PR description with: what it does, why it's complementary, what gap it fills
- [ ] Single commit preferred (squash before submitting)

**During review — expect multiple rounds:**

| Review source | What they catch | Response time |
|---------------|----------------|---------------|
| Automated bots | Structural bugs, compatibility, edge cases | Minutes |
| Human maintainer | Architectural fit, naming, scope | Days to weeks |
| Community | Real-world usage patterns | Over time |

Do NOT argue with bot findings. They are usually right. Fix, thank, move on.

**Gate — verify before proceeding:**
- [ ] All bot reviews resolved (PASS/APPROVED)
- [ ] At least one round of human review (if maintainer is active)
- [ ] All review-discovered bugs applied BACK to your local copy
- [ ] PR is mergeable (no conflicts with base branch)

**Failure modes — what to do if:**
- **PR ignored for 2+ weeks:** Comment politely asking for review. If no response after 4 weeks, proceed to LAUNCH anyway — the bot review alone has value
- **PR rejected with reason:** Fix the issue and re-submit. A rejection with feedback is better than no review
- **Community is inactive:** Extract what you learned from bot review (even unmerged) and launch standalone
- **PR merged but maintainer asks for changes post-merge:** Happy path. This is continued hardening

---

## Step 4: LAUNCH

**Goal:** Extract the hardened code as a standalone repository with proper documentation.

**Launch checklist:**
- [ ] Code is the reviewed version (not the original pre-PR version)
- [ ] README answers: what, why, how to install, how to configure, examples
- [ ] License matches or is compatible with the community repo's license
- [ ] Topics set (5-8 relevant keywords)
- [ ] Link back to the original PR in README ("Originally submitted as...")
- [ ] Attribution section if you adapted patterns from other projects
- [ ] No personal data, secrets, or local paths

**After launch:**
- [ ] If PR was merged, add "Now part of [community repo]" badge
- [ ] Cross-link from the community PR to your standalone repo
- [ ] Write a short share (dev.to, Reddit, Discord) explaining the problem it solves

---

## When NOT to Use This Method

| Situation | Alternative |
|-----------|-------------|
| Tool is a wrapper around others' work | Credit the original, don't repackage |
| Too personal to generalize | Keep it in your dotfiles, write a blog post |
| >500 lines, tightly coupled | Extract the core 200 lines, submit that |
| No active community fits | Self-publish with extra documentation |
| Contains proprietary logic | Don't open source it |

---

## Attribution Standards

This method depends on learning from others. Attribute properly:

- **Code dependencies:** Link to upstream repo, state what it provides
- **Format/convention inspiration:** "Inspired by [repo]'s [specific pattern]" in README
- **Review feedback:** Thank reviewers by name in commit messages or PR comments
- **Methodology patterns:** `agent-skills` invented the Rationalizations + Red Flags format — we adopted it and credited them

Attribution is not weakness. It's how open source works.

---

## Validated Cases

### Case 1: delivery-gate
```
EXTRACT: CLAUDE.md five-library rules
FIND:    ECC (100K★) — code quality checks exist, thinking quality missing
HARDEN:  PR #2365 → 4 rounds → 9 bugs fixed (stdin contract, Python 3.8 crash, os.walk, ...)
LAUNCH:  github.com/YuhaoLin2005/delivery-gate
```

### Case 2: self-audit framework
```
EXTRACT: Four-dimension self-check (Consistency/Completeness/Groundedness/Honesty)
FIND:    anthropics/skills (154K★) — document skills exist, output quality gate missing
HARDEN:  Originality verified via web search → PR #1360
LAUNCH:  Standalone skill + cross-linked to agent-skills session-quality-gate
```

### Case 3: RapidOCR wrapper (counter-example)
```
EXTRACT: PaddleOCR replacement → RapidOCR wrapper
FIND:    No suitable community — RapidOCR is RapidAI's work
DECISION: NOT submitted. Attribution: "Powered by RapidAI/RapidOCR"
LESSON:  Thin wrappers fail the originality check. Credit, don't repackage.
```

---

## See Also

- [delivery-gate](https://github.com/YuhaoLin2005/delivery-gate) — Case 1 standalone repo
- [open-source-sync-strategy](https://github.com/YuhaoLin2005/claude-config) — Internal decision record
- [agent-skills CONTRIBUTING.md](https://github.com/addyosmani/agent-skills) — The gold standard for skill contribution guidelines
