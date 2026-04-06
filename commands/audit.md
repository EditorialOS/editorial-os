---
description: Content gap analysis against your pillars and competitive landscape. Identifies what's missing, what's underperforming, and what to build next — sized to your actual team capacity.
argument-hint: "<website or focus area>"
---

# /audit

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../CONNECTORS.md).

Full content gap analysis. Uses your configured pillars, competitive intel, audience segments, and constraints.

## Trigger

User runs `/audit` or asks to audit content, find content gaps, assess pillar health, or identify what's missing from their content strategy.

## Inputs

1. **Focus area** (optional) — a specific pillar, format, or audience segment to focus on
2. **Website URL** (optional, if no ~~docs configured) — to assess current published content
3. **Goals** (optional, if not in ~~docs) — what the content strategy should achieve

If ~~docs is connected, all context loads automatically. If not, accept any combination of pasted content, URLs, or descriptions.

## Step 1 — Load Context

Use editorial-config skill. Show one-line status header.

If 🟢 Configured: only ask for any specific focus area. All context loads from ~~docs.
If ⚪ No client: ask for website URL, industry, 3 content pillars, primary goal, team size. Run the audit with what's provided — state output is directional without full context.

---

## Step 2 — Pillar Assessment

For each configured pillar:

Use content-strategist skill to assess:
- Coverage depth (piece count + top performer quality)
- Competitive position (who owns this pillar? do any competitors dominate it?)
- Audience fit (which segments does this serve? are underserved segments getting anything here?)
- Goal alignment (does it advance the primary goal?)
- History filter (does content history flag anything to avoid in this pillar?)

Rate each pillar on four dimensions (Strong / Developing / Thin / Missing).

---

## Step 3 — Gap Identification

For each pillar, identify gaps using content-strategist skill gap types:
- Format gap, Depth gap, Recency gap, Angle gap, Segment gap, Pillar gap

For each gap:
- Name the gap type
- Identify which segment is underserved by it
- Score it (goal alignment + effort + differentiation + audience fit, max 12)
- Check against content history — if it's been tried and failed, skip it

Discard any gap with score < 6.

---

## Step 4 — Opportunity Prioritization

Rank all gaps with score ≥ 6. Group into P1 (score ≥ 9), P2 (6–8).

Apply the resource reality test from calendar-planner skill:
- P1 recommendations must be executable at current team capacity
- If a P1 gap requires more than 90% of capacity — flag it honestly

---

## Output Format

```
EDITORIAL OS — CONTENT AUDIT
[Config status header]
Generated: [Date]

---

PILLAR HEALTH SNAPSHOT

[pillar name]
Coverage:     [rating] — [specifics]
Competitive:  [rating] — [who leads, who challenges]
Audience fit: [rating] — [segments served, segments missing]
Goal tie:     [rating] — [connection to primary goal]

[Repeat for each pillar]

OVERALL HEALTH: [{N} pillars strong / {N} developing / {N} thin / {N} missing]

---

GAPS IDENTIFIED: [{N} total | {N} P1 | {N} P2]

P1 GAPS (Score 9–12)

GAP 1: [{Gap name — specific}]
Type: [Format / Depth / Recency / Angle / Segment / Pillar]
Pillar: [{pillar name}]
Segment underserved: [{segment name}]
Competitive position: [{who fills this now, or "uncontested"}]
Score: [{N}/12] — Goal: {N}/3 | Effort: {N}/3 | Differentiation: {N}/3 | Audience: {N}/3
Winning move: [{Specific, executable recommendation — calibrated to team capacity}]
Estimated effort: [{hours/pieces}] — executable at current cadence? [Yes/Tight/No]

[Repeat for all P1 gaps]

P2 GAPS (Score 6–8)
[Abbreviated — name + type + winning move]

SKIPPED (Tried and failed):
[Gaps blocked by content history — name what was tried and why it's blocked]

---

IMMEDIATE ACTIONS (30 days)
[Top 2-3 P1 recommendations sized to team capacity]

STRATEGIC BUILD (90 days)
[2-3 pillar development initiatives]

POSITION TO OWN (6 months)
[What winning looks like — specific, defensible]

---

QUALITY GATES
✓ All gaps tied to configured pillars
✓ All recommendations sized to team capacity
✓ Previously failed approaches excluded
✓ All P1 gaps connected to primary goal
✓ Underserved segments prioritized
✓ Competitive position honest for all pillars
```
