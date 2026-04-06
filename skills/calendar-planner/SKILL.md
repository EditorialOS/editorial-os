---
name: calendar-planner
description: Build resource-realistic 90-day content calendars grounded in configured pillars, real team constraints, live calendar data, and audience performance patterns. Never plan more than the team can execute. A 90-day calendar that fails at week three is worse than a 60-day calendar that holds. Used by /calendar.
---

# Calendar Planner

Build plans the team can actually execute. A 90-day calendar that fails at week three is worse than a 60-day calendar that holds. Every calendar decision starts with capacity, not ambition.

## The Resource Reality Test

Run this before building any calendar. No exceptions. This is the single most important step — it prevents the #1 failure mode of content calendars: planning more than the team can produce.

### Capacity Calculation

```
Team: {team size or description}
Cadence: {publishing cadence}
90-day total capacity: [{pieces/week} × 12 weeks = {N total pieces}]
Seasonal holds: [{N} weeks blocked]
Available weeks: [12 - holds = {N}]
Effective capacity: [{pieces/week} × {available weeks} = {N}]
```

### Capacity Rules

| Capacity Utilization | Status | Action |
|---------------------|--------|--------|
| < 70% of capacity | Under-planned | Consider adding content types, formats, or channels |
| 70-85% | Healthy | Optimal — leaves room for quality and contingency |
| 85-90% | Tight | Flag to the user — any disruption breaks the plan |
| > 90% | Over-planned | Cut scope before presenting. State what was cut and why. |

State the capacity ceiling explicitly in the output. Clients need to see the math. A calendar that shows "12 pieces planned / 15 capacity = 80%" gives the user confidence. A calendar that just lists dates without capacity context creates silent anxiety about whether they can keep up.

### Team Capacity Benchmarks

Use these only when exact capacity isn't documented. Always verify with the user.

| Team Size | Typical Weekly Capacity | Notes |
|-----------|----------------------|-------|
| Solo creator | 1-2 pieces/week | No parallel production. One sick day = missed week. |
| Creator + part-time editor | 2-3 pieces/week | Can do light parallel production (draft + edit) |
| 2-3 person content team | 3-5 pieces/week | Parallel production possible. Can sustain two channels. |
| 4-6 person team | 5-10 pieces/week | Can sustain 3+ channels with dedicated owners |
| Full content organization | 10+ pieces/week | Multiple channels, specialized roles, production workflows |

### Production Timeline Benchmarks

Factor these into calendar scheduling — content needs lead time.

| Content Type | Production Time | Team Size Adjustment |
|-------------|----------------|---------------------|
| Blog post (800-1500 words) | 3-5 business days | Solo: add 1-2 days |
| Long-form guide (2000+ words) | 5-8 business days | Solo: add 3-5 days |
| Newsletter issue | 2-3 business days | Solo: add 1 day |
| Email sequence (3-5 emails) | 4-6 business days | Solo: add 2-3 days |
| Social media pack (5 posts) | 1-2 business days | Solo: same |
| Case study | 5-10 business days (includes interview) | Solo: add 3-5 days |
| Landing page copy | 3-5 business days | Solo: add 2 days |
| Video script | 2-3 business days (script only) | Production adds 1-3 weeks |
| Infographic | 3-5 business days (includes design) | Solo with no design: add Canva time or cut |

## Seasonal Planning

### Seasonal Lock-In

Check before building any week:

1. **Hard holds** — absolute blackout periods. Nothing goes there. (From ~~docs or user input)
2. **Calendar events** — if ~~calendar is connected, pull upcoming events, launches, campaigns
3. **Industry seasonality** — relevant seasonal moments for this industry
4. **Client seasonality** — the client's own seasonal patterns (busy season, slow season, event season)

### Seasonal Moment Rules

| Rule | Why |
|------|-----|
| Seasonal moments drive editorial angles — they don't invent content | "Valentine's Day" is not a pillar. "Gift guide for [your audience]" is a seasonal angle on an existing pillar. |
| Every seasonal hook must connect to a configured pillar | If a seasonal moment doesn't fit any pillar, skip it |
| Don't plan around seasonal moments irrelevant to the client's industry | A B2B SaaS company doesn't need a "summer reading list" unless it connects to their audience |
| Plan seasonal content 2-4 weeks ahead of the moment | Publishing on Valentine's Day is too late — the gift guide should go live January 25 |
| Mark tentpole moments early in the calendar | These are anchor points — build surrounding content around them |

### Common Seasonal Patterns by Industry

Use these as starting points only — verify against the client's actual industry:

| Industry | Seasonal Peaks | Content Implications |
|----------|---------------|---------------------|
| Travel/Hospitality | Spring (planning), Summer (travel), Holiday (gifting) | Lead content by 4-6 weeks; shoulder season is underserved |
| B2B SaaS | Q1 (budget season), Q4 (renewal/planning) | Budget justification content in Q4; new year goal content in Q1 |
| E-commerce | Black Friday/Holiday, Back to School, Valentine's | Gift guides, deals content, seasonal buying guides |
| Education | Back to school, enrollment periods, academic year | Align to academic calendar; summer is quiet |
| Finance | Tax season, year-end, quarterly reporting | Timely regulatory and planning content |
| Health/Wellness | New Year, Spring, Back to School | Resolution content, seasonal wellness, routine shifts |

## Pillar Rotation Logic

A healthy 90-day calendar rotates across all pillars — no pillar dominates every week, no pillar disappears for a month.

### Default Rotation

| Number of Pillars | Distribution | Notes |
|-------------------|-------------|-------|
| 2 pillars | 50% / 50% | Alternate weeks |
| 3 pillars | 33% / 33% / 34% | Rotate across weeks |
| 4 pillars | 25% each | Each pillar appears at least once per month |
| 5+ pillars | Equal distribution, grouped | Consider combining thin pillars |

### Rotation Adjustments

| Pillar Status | Weight Adjustment | Rationale |
|---------------|------------------|-----------|
| **Thin** | Increase to max 40% for 30-60 days | Build the pillar with concentrated investment |
| **Healthy** | Maintain at default weight | Sustain the position without over-investing |
| **Over-saturated** | Reduce to min 15% | Prevent content fatigue; audience needs variety |
| **Untested** | Test at 20-25% for 30 days, then reassess | Gather data before committing |

### Pillar Balance Visualization

Show this in every calendar output:

```
PILLAR BALANCE (90 days)
[Pillar A]: ████████████ 35% (target: 33%) — Building (Thin pillar)
[Pillar B]: ██████████ 30% (target: 33%) — On track
[Pillar C]: ██████████ 30% (target: 34%) — On track
[Pillar D]: █████ 5% — Seasonal only
```

If the balance is off from default, explain why in one line.

## Segment Coverage

### Monthly Coverage Requirements

Every configured audience segment must be served at least once per month. Not every piece — but every segment gets at least one primary piece per month.

| Segment Priority | Monthly Minimum | Rationale |
|-----------------|----------------|-----------|
| Primary segment | 2-3 pieces directly addressing their needs | This is your core audience |
| Secondary segment | 1-2 pieces | Growing audience or strategic audience |
| Emerging segment | 1 piece | Testing whether this audience responds |

### Segment Coverage Check

After building the calendar, verify:
- [ ] Every segment is served at least once per month
- [ ] Underserved segments (from /audit) are prioritized in Month 1
- [ ] No segment goes more than 2 weeks without primary content
- [ ] High-value segments get the highest-quality content formats

## Repurposing Chains

A well-built repurposing chain doubles effective output without doubling effort. Build chains into the plan explicitly — don't leave repurposing as an afterthought.

### Standard Repurposing Chains

| Chain | Source → Derivative | Time Savings vs. Creating Separately |
|-------|-------------------|--------------------------------------|
| **Basic** | Blog post → Newsletter excerpt → Social post | ~3-4 hours |
| **Extended** | Blog post → Newsletter excerpt → Social post → Email teaser → Pull quote graphic | ~6-8 hours |
| **Video** | Webinar/Video → Blog recap → Social clips → Email highlights | ~8-12 hours |
| **Research** | Survey/Report → Blog series (3-5 posts) → Infographic → Social series → Email nurture | ~15-20 hours |
| **Event** | Conference talk → Blog post → LinkedIn article → Twitter thread → Newsletter feature | ~8-10 hours |

### Repurposing Rules

| Rule | Why |
|------|-----|
| Every long-form piece gets at least a Basic chain | Minimum viable repurposing — no content should exist in only one format |
| Repurposed content must be platform-native | A blog post excerpt ≠ a LinkedIn post. Rewrite for the platform. |
| Schedule derivatives within 3-7 days of the source | Freshness matters — don't repurpose a January blog in March |
| Show time savings in the calendar output | The user needs to see the efficiency argument, not just the volume |
| Don't count repurposed content toward capacity | It's derived, not original — capacity counts original pieces only |

### Repurposing Efficiency Summary

Show this in every calendar output:

```
REPURPOSING EFFICIENCY
Original pieces: {N}
Derived pieces: {N} (from {N} repurposing chains)
Time saved: ~{N} hours vs. creating each piece separately
Effective output: {N} total pieces from {N} originals
```

## Monthly Theme Logic

Each month needs a theme — specific, evocative, grounded in the client's voice. Not generic editorial labels.

### Theme Quality Criteria

| Good Theme | Bad Theme | Why |
|-----------|-----------|-----|
| "The Operator's Advantage" | "Building Awareness" | Good: specific, evocative, could be a section title. Bad: generic marketing label. |
| "Why {Destination} in Shoulder Season" | "Spring Content" | Good: audience-relevant, specific. Bad: internal planning term. |
| "The Stack Nobody Talks About" | "Technology Month" | Good: curiosity-driven, positions a pillar. Bad: category label. |

### Theme Selection Process

1. Which pillar is the primary focus for this month? (From rotation logic)
2. Is there a seasonal moment that creates a natural hook?
3. What's the strongest angle within this pillar that serves the primary segment?
4. Can the theme be expressed in language the audience would recognize and find interesting?

## Contingency Planning

Every calendar needs a buffer. Things fall through — interviews cancel, drafts miss deadlines, breaking news changes priorities. Plan for it.

### Buffer Week

Mark one week per month as flex — content is planned but not committed. This is your pressure relief valve.

| Month | Flex Week | Planned Content | Fallback |
|-------|-----------|-----------------|----------|
| Month 1 | Week 4 | [{Planned piece}] | Evergreen standby #1 |
| Month 2 | Week 8 | [{Planned piece}] | Evergreen standby #2 |
| Month 3 | Week 12 | [{Planned piece}] | Refresh of a top performer |

### Evergreen Standbys

Identify 2-3 evergreen pieces from content history that can republish or refresh if a planned piece falls through.

**Good evergreen standbys:**
- Top-performing pieces that are 3+ months old (refresh with current data)
- Foundational explainers that don't go stale
- Best-of compilations or round-ups that can be quickly updated
- FAQ or how-to content with perennial relevance

**Selection criteria:**
- Previously performed well (top quartile by engagement)
- Not heavily time-stamped (no "in 2024" in the headline)
- Can be refreshed in < 2 hours
- Serves a high-priority segment

## Performance Weighting

If performance data exists and is recent (< 30 days from ~~email or ~~docs), use it to weight format and topic decisions.

### Weighting Rules

| Signal | Calendar Action |
|--------|----------------|
| Format consistently outperforms others | Weight recommendations toward that format |
| A specific pillar consistently underperforms | Investigate — angle problem? format problem? audience mismatch? |
| A topic drove unusual engagement | Plan a follow-up or series |
| A content type consistently underperforms | Flag it — recommend testing alternatives or cutting |
| Open rates are declining over time | Recommend subject line testing and list hygiene |

### When No Performance Data Exists

- Weight toward the client's most-used content format (from content history)
- Note that recommendations are based on content patterns, not engagement data
- Recommend establishing baseline tracking as a 30-day action

## Always Do

- Run the resource reality test before building — show the math
- Check seasonal holds before placing any content
- Show pillar balance percentages across the full 90 days
- Build repurposing chains with explicit time savings
- Mark one week per month as flex/buffer
- Identify evergreen standbys from content history
- Serve every configured segment at least once per month
- Include production lead time in scheduling
- Show capacity utilization as a percentage

## Never Do

- Plan content into blackout periods
- Build a calendar that exceeds 90% of publishing capacity without flagging it
- Recommend channels the client doesn't use
- Use generic seasonal moments that don't apply to the client's industry
- Let one pillar dominate the full 90 days without acknowledging the imbalance
- Plan without a contingency — something always falls through
- Present a calendar without the capacity math
- Assume repurposing takes zero time — it takes less time, not no time
- Schedule derived content more than 7 days after the source piece

## Cross-Skill Dependencies

- **Receives from:** editorial-config (all constraints, pillar statuses, history, calendar data, performance)
- **Receives from:** content-strategist (priority recommendations — P1s drive Month 1 planning)
- **Used by:** /calendar command
- **Informs:** /draft (calendar-planned pieces feed into content drafting)
