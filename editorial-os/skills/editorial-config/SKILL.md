---
name: editorial-config
description: Load client context at the start of every command by calling client-context skill. Interpret Drive documents into structured editorial intelligence — competitors, pillars, audience segments, constraints, content history, and performance baselines. Run silently. Never narrate the loading process.
---

# Editorial Config — Context Loader

Load all available client context before generating any output. Call the client-context skill, then apply editorial interpretation to what's found. This is the bridge between raw documents and actionable editorial intelligence.

## Loading Sequence

```
1. Call client-context skill
   → Reads ~~docs folder
   → Extracts brand, audience, competitor, pillar, performance, operational context
   → Checks active connectors (~~email, ~~crm, ~~calendar, ~~assets)
   → Returns status: 🟢 Configured / 🟡 Partial / ⚪ No client loaded

2. Apply editorial interpretation layer (this skill)
   → From competitor documents: build competitors[] with genuine strengths and weaknesses
   → From strategy/pillar docs: build pillars[] with current health assessment
   → From audience docs: build segments[] with content preference and funnel stage
   → From past content: extract history.biggest_wins and approaches_tested
   → From briefs/calendar: extract constraints (cadence, team, seasonal holds)
   → From performance reports: extract goals.metrics_that_matter
   → From brand guide: extract voice rules, vocabulary, tone adaptation

3. Show status header (one line — never narrate the loading process)
```

## Status Header

```
🟢 [{client name}] | Drive: [{folder}] | Competitors: {N} | Pillars: {N} | Segments: {N}
🟡 [{client name}] | Drive: [{folder}] | Partial — [{what's missing and effect on output}]
⚪ No client loaded — working from what you provide. Run /setup to connect your docs.
```

## Interpretation Rules by Domain

### Competitors

| Rule | Why |
|------|-----|
| Use competitors found in Drive docs — never invent or generalize | Imagined competitors produce imagined analysis |
| Apply genuine_strengths as documented — don't soften | Honest competitive analysis requires honest competitor assessment |
| Flag if competitive doc is > 90 days old | Competitive intelligence has a short shelf life |
| If no competitor doc found: ask for competitors this session, state they're not in Drive | Don't guess — the user knows their market |
| Distinguish between primary competitors (direct) and secondary (adjacent) | Weight analysis toward primary competitors |
| Note competitor content cadence if observable from docs | Calibrates competitive urgency |

### Brand Voice

| Rule | Why |
|------|-----|
| Extract voice attributes and apply as baseline to all content commands | Voice consistency is the foundation of brand trust |
| Note vocabulary to use (hard constraint) | Brand terms are non-negotiable |
| Note vocabulary to avoid (hard constraint) | Avoided terms exist for reasons — legal, brand, cultural |
| Apply voice rules to /draft, /subjects, /social-pack automatically | The user should never have to re-state their voice |
| If no brand guide: extract patterns from past content, flag as "inferred" | Inferred voice is less reliable than documented voice |
| If brand guide conflicts with past content patterns: prefer the guide | The guide is the intended voice; past content may have drifted |

### Voice Adaptation by Command

Different commands need different emphasis from the same voice:

| Command | Voice Emphasis |
|---------|---------------|
| /draft | Full voice application — vocabulary, tone, style rules, headline conventions |
| /subjects | Subject line voice — conciseness constraints override paragraph-level voice rules |
| /social-pack | Platform-adapted voice — LinkedIn more professional, Twitter/X more punchy, but both recognizably the same brand |
| /audit | Analytical voice — the output is for the strategist, not the audience |
| /competitor | Analytical voice — honest, not promotional |
| /calendar | Planning voice — clear, operational, decision-ready |

### Content Pillars

| Rule | Why |
|------|-----|
| Extract pillar themes from strategy docs and content patterns | Pillars are the structural foundation of editorial planning |
| Assess health from piece count, performance, and competitive position | Health determines where to invest |
| Use four health statuses: Healthy / Developing / Thin / Untested | Anything more granular is false precision |
| If no strategy doc: infer pillars from recurring topics in last 5 newsletters | Better to infer than to ignore |
| Flag inferred pillars clearly — they're hypotheses, not commitments | User should confirm before building a quarter around them |
| Note pillar overlap — some topics span multiple pillars | Prevents double-counting in audits |

### Pillar Health Assessment Criteria

| Status | Signals |
|--------|---------|
| **Healthy** | 10+ pieces covering multiple angles; at least one top performer; competitive position is strong; directly aligned with primary goal |
| **Developing** | 5-10 pieces; some engagement but no standout; building competitive position; clear goal connection |
| **Thin** | < 5 pieces or single angle only; no standout performer; competitors are stronger here; goal connection is clear but underserved |
| **Untested** | 0 pieces; unknown audience response; unknown competitive position; goal connection is hypothetical |

### Audience Segments

| Rule | Why |
|------|-----|
| Use segment names from persona docs — don't rename them | Consistency with the client's internal language |
| Map each segment to content preferences if documented | Enables segment-specific recommendations |
| Note funnel stage for each segment | Aligns content type to buying stage |
| If segments are documented differently across docs: use the most recent | Segment definitions evolve |
| If no segments documented: note "general audience" and flag | Segment-specific recommendations require segment data |

### Email Context

| Rule | Why |
|------|-----|
| If ~~email connected: pull real open rates, click rates, list size | Real data beats industry benchmarks |
| Use real benchmarks, not industry averages, when real data exists | "Your 22% open rate" is more useful than "industry average 18-22%" |
| Apply subject line rules from brand guide if documented | Subject lines are brand expression |
| If no email data: label all performance predictions as "estimated" | Never present guesses as data |
| Note list size for audience context | A 500-person list has different dynamics than a 50,000-person list |

### Email Benchmarks (Use Only When No Real Data Available)

| Metric | General Benchmark | B2B Benchmark | B2C Benchmark |
|--------|-----------------|---------------|---------------|
| Open rate | 18-25% | 20-28% | 15-22% |
| Click-through rate | 2-5% | 2-4% | 3-5% |
| Click-to-open rate | 10-17% | 10-15% | 12-18% |
| Unsubscribe rate | < 0.5% | < 0.3% | < 0.5% |
| List growth rate (monthly) | 2-5% | 2-4% | 3-6% |

Always label these as "industry benchmarks" when used. Never present them as if they're the client's data.

### Content History

| Rule | Why |
|------|-----|
| Extract "what worked" from past newsletters and performance reports | Repeat and amplify proven approaches |
| Extract "what failed" from retrospective docs or performance drops | Don't recommend what's already been tried and abandoned |
| Note content formats that have been used vs. not used | Format gaps are opportunities or deliberate choices |
| Identify recurring topics vs. one-off experiments | Recurring topics signal pillar commitment |
| Note seasonal patterns in past publishing | Build into /calendar planning |

### Operational Constraints

| Rule | Why |
|------|-----|
| Extract cadence from briefs and calendar documents | Capacity ceiling — never plan beyond what the team can execute |
| Extract team signals from brief language | "I write everything" = solo operation. "The team" = at least 2-3 people. |
| Respect blackout periods in calendar or strategy docs | These are hard constraints, not suggestions |
| Only reference channels that appear in client's documents | Don't recommend TikTok to a B2B newsletter operation |
| Note publishing tools in use (Beehiiv, WordPress, etc.) | Practical context for execution recommendations |

### Team Size Heuristics

When team size isn't explicitly stated, use these signals:

| Signal | Likely Team Size | Capacity Implication |
|--------|-----------------|---------------------|
| "I" throughout briefs, single byline | Solo creator | 1-2 pieces/week max, no parallel production |
| "We" with 1-2 bylines | 2-3 person team | 2-4 pieces/week, some parallel production |
| Multiple bylines, departments mentioned | Full content team | 5+ pieces/week, parallel production possible |
| Agency/consultant language | External team | Variable — ask about hours allocated |

## When Documents Are Ambiguous

| Situation | Action |
|-----------|--------|
| Multiple strategy docs | Synthesize, prefer most recent by modified date |
| Competitors mentioned in passing (not in dedicated doc) | Include with lower confidence, flag |
| No clear cadence signal | Ask once in the command output, don't block |
| Conflicting audience descriptions | Note the conflict, use most recent document |
| Brand guide says one thing, past content shows another | Prefer the guide (intended voice); note the drift |
| Performance data exists but is > 90 days old | Use for patterns, flag as potentially stale |
| Documents are in another language | Extract what you can, note language barrier |

## Never Do

- Never ask the user to re-enter information that's in their Drive documents
- Never use generic "your competitors probably..." when Drive docs have real competitors
- Never recommend approaches that past content shows were tried and dropped
- Never narrate the loading process — show the status header only
- Never block on missing context — flag what's missing and continue
- Never present industry benchmarks as if they're the client's real data
- Never make up competitors, segments, or pillars that aren't in the documents
- Never apply voice rules from one client to another client's context

## Cross-Skill Dependencies

- **Calls:** client-context (reads Drive, extracts raw context)
- **Called by:** All commands as the first step
- **Feeds into:** content-strategist (pillar health, gaps, history)
- **Feeds into:** competitive-intel (competitor list, strengths, weaknesses)
- **Feeds into:** calendar-planner (constraints, cadence, seasonal data)
