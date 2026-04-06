---
description: Generate 10 email subject line variants with preview text, strategic analysis, A/B test plan, and mobile preview. Uses real brand voice and benchmark data when connected.
argument-hint: "<topic or paste newsletter draft>"
---

# /subjects

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../CONNECTORS.md).

10 subject line variants with matching preview text, strategic rationale, and A/B test recommendations.

## Trigger

User runs `/subjects` or asks for email subject lines, newsletter subject lines, or A/B test subject line variants.

## Inputs

1. **Topic or draft** — accept in any of these forms:
   - A topic described briefly ("spring travel guide newsletter")
   - Full newsletter content pasted directly
   - A ~~docs reference to a draft in the client's Drive folder
2. **Goal** — Open / Click / Reply / Share / Purchase (ask if not specified)

## Step 1 — Load Context

Use editorial-config skill. Show one-line status header.

If configured: apply brand voice, vocabulary rules, segment context, and real email benchmarks from ~~docs and ~~email automatically. Don't ask for voice or audience info.
If ⚪ No client: ask for topic/draft, audience, tone, goal, and any constraints.

**Always ask for:**
- TOPIC or DRAFT (paste the newsletter content or describe)
- GOAL: Open / Click / Reply / Share / Purchase

---

## Step 2 — Generate Subject Lines

Generate exactly 10 subject lines — each a different approach:

1. Curiosity — information gap that demands opening
2. Benefit — clear value promise
3. Urgency — time-sensitive without being manipulative
4. Social proof — evidence others care about this
5. News — positions content as timely or breaking
6. Question — engages by prompting internal answer
7. How-to — practical promise
8. Contrarian — challenges expected thinking
9. Personal — feels like it's from a person, not a brand
10. Exclusivity — insider access or limited framing

For each: write preview text that complements (never repeats) the subject line.

Apply subject line rules from brand context: character limits, style notes, words to avoid.

---

## Output Format

```
EDITORIAL OS — SUBJECT LINE ANALYSIS
[Config status header]
Generated: [Date]

TOPIC: [{topic}] | GOAL: [{selected}]
VOICE: [{brand personality, or "as specified"}]
BENCHMARKS: [{real open rate from ~~email, or "industry average"}]

---

| # | Subject Line | Chars | Preview Text | Chars | Approach | Best For |
|---|-------------|-------|--------------|-------|----------|----------|
| 1 | [Subject] | XX | [Preview] | XX | Curiosity | [{segment name}] |
| 2 | [Subject] | XX | [Preview] | XX | Benefit | [{segment}] |
| 3-10 | [...] | | [...] | | [...] | [...] |

---

STRATEGIC ANALYSIS

TOP PICK: #[X] — [{Why — reference performance data if available}]
DARK HORSE: #[X] — [{Unexpected angle that might outperform}]
AVOID: #[X] — [{Flags against brand rules or audience mismatch}]

---

MOBILE PREVIEW

iPhone (45 char subject / 90 char preview):
[#1 truncated to actual visible text]

Android (60 char subject / 100 char preview):
[#1 as it would appear]

---

A/B TEST PLAN

Test: #[X] vs #[Y]
Split: 20% A / 20% B / 60% winner
Winner metric: [{based on goal}]
Test window: [{based on send cadence if known}]

---

QUALITY GATES
✓ Mobile-optimized (max {char limit} chars)
✓ Preview text complements subject (no repeats)
✓ No spam trigger words
✓ Brand vocabulary rules applied
✓ Goal-aligned
✓ 10 distinct approaches
```
