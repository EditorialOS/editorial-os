---
description: Competitive content analysis. Maps battlefields against your competitors, finds real white space, and identifies defensible positions — sized to your team's ability to win and hold ground.
argument-hint: "<competitor URLs or names>"
---

# /competitor

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../CONNECTORS.md).

Battlefield-level competitive analysis. Uses your configured competitor list, pillars, and constraints.

## Trigger

User runs `/competitor` or asks to analyze competitors, find competitive gaps, map the competitive landscape, or identify white space.

## Inputs

1. **Competitor names or URLs** (optional if ~~docs has competitor analysis) — who to analyze
2. **Additional competitors** — add to the configured list with "Add: competitor.com"

If ~~docs is connected, competitor list loads from your competitive analysis documents. If not, provide competitor URLs or names directly.

## Step 1 — Load Context

Use editorial-config skill. Show one-line status header.

If configured and competitors found in ~~docs: confirm the list before running:

```
Analyzing competitors from your documents:
- [{name}] ({url}) — {content approach}
[...]
Add a competitor or proceed?
```

Flag any competitive data > 90 days old: ⚠️ Data may be outdated.

If ⚪ No client: ask for competitor URLs + one-line descriptions. Analysis without pre-loaded context is directional only.

---

## Step 2 — Run Competitive Analysis

Use competitive-intel skill throughout.

For each competitor: map their position across all configured pillars. Apply the four-position framework (Dominating / Competing / Thin / Absent).

Identify additional battlefields competitors have opened that aren't in the pillar list.

Apply the substitution test to every recommended angle: "Could [{competitor}] publish this verbatim?" If yes — find a more differentiated angle.

---

## Step 3 — White Space Test

For each white space candidate: run the three-test check.
1. Audience actually wants it (check segment content preferences)
2. No competitor dominates it
3. Client can execute on it (check team constraints)

Discard any candidate that fails any single test. Label remaining: True white space / Contested gap / Temporary gap.

---

## Output Format

```
EDITORIAL OS — COMPETITIVE ANALYSIS
[Config status header]
Generated: [Date]

YOUR POSITIONING: [{primary goal} expressed through {pillars}]
AUDIENCE LENS: Competing for [{segment names}]

---

COMPETITIVE LANDSCAPE

COMPETITOR: [{name}] — {url}
Content approach: [{approach}]
Genuine strengths: [{as documented — not softened}]
Real weaknesses for your audience: [{weaknesses + assessment}]
Content gaps: [What they're missing that your segments want]
Your opportunity: [How you differentiate — specific]

[Repeat for each competitor]

---

BATTLEFIELD ANALYSIS

BATTLEFIELD: [{pillar name}]
Current leader: [{name} — why they lead]
How they win: [Specific tactics]
What's underserved for [{segment}]: [Specific gap]
Your angle: [Differentiated approach — passes substitution test]
Executable for your team? [Yes / Tight / No]
Winning move: [One specific initiative]

[Repeat for each pillar + additional battlefields]

---

DIFFERENTIATION MATRIX

| Content Approach | You | {competitor 1} | {competitor 2} |
|-----------------|:---:|:---:|:---:|
| [{pillar 1}] | [Position] | [Position] | [Position] |
| [{pillar 2}] | [Position] | [Position] | [Position] |

Position key: 🟢 Dominating / 🟡 Competing / 🟠 Thin / ⚪ Absent

---

WHITE SPACE MAP

TRUE WHITE SPACE (uncontested + audience-relevant + executable):
- [{White space}]: [{Why real, who it serves, why you can own it}]

CONTESTED GAPS (winnable with sustained effort):
- [{Gap}]: [{Who's competing, what winning requires}]

TEMPORARY GAPS (don't build strategy on these):
- [{Gap}]: [{Why temporary}]

---

STRATEGIC RECOMMENDATIONS

Immediate (30 days): [2-3 moves to exploit clear gaps]
Short-term (90 days): [Build differentiated position]
Long-term (6 months): [What owning a battlefield looks like]

---

RISK ASSESSMENT

Their likely counter-move: [How competitors respond]
Your sustainable moat: [What's hard to copy — specific]
Vulnerability: [Where you're exposed — honest]

---

QUALITY GATES
✓ Competitor strengths represented honestly
✓ Stale data flagged
✓ White space candidates passed three-test check
✓ Angles passed substitution test
✓ Recommendations sized to team capacity
✓ Risks acknowledged
```
