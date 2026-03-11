---
description: 90-day content calendar built from real pillars, real constraints, and live seasonal data. Never plans more than the team can execute. Includes repurposing chains and contingency planning.
argument-hint: "Start: <date>, Focus: <channels>"
---

# /calendar

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../CONNECTORS.md).

90-day content calendar grounded in your real context. Not a template — a plan sized to your actual capacity.

## Trigger

User runs `/calendar` or asks to build a content calendar, plan a content schedule, or create an editorial calendar.

## Inputs

1. **Start date** — when the 90-day calendar begins (default: next Monday)
2. **Focus channels** (optional) — limit to specific platforms (e.g., "email + LinkedIn")
3. **Seasonal moments** (optional) — events not already in ~~calendar data

If ~~docs is connected, pillars, constraints, team size, cadence, and history load automatically. If not, ask for business goals, 3 content pillars, channels, team size, and publishing cadence.

## Step 1 — Load Context

Use editorial-config skill. Show one-line status header.

If configured: only ask for START DATE and any seasonal moments not already in ~~calendar data.
If ⚪ No client: ask for business goals, 3 content pillars, channels, team size, publishing cadence. State calendar will be illustrative.

---

## Step 2 — Resource Reality Test

Use calendar-planner skill. Run this before building a single week.

```
CAPACITY CHECK

Team: [{team description}]
Cadence: [{publishing cadence}]
90-day capacity: [{pieces/week} × 12 weeks = {N total pieces}]
Seasonal holds: [{blackout weeks}]
Available weeks: [12 minus holds = {N}]
Effective capacity: [{pieces/week} × {available weeks} = {N}]

This calendar plans to [{N} pieces] = [{X}% of capacity].
```

If planning would exceed 90% of capacity: reduce scope, state what was cut and why.

---

## Step 3 — Build the Calendar

Use calendar-planner skill throughout.

Assign monthly themes (specific and evocative). Rotate pillars by health status. Cover all segments at least once per month. Build repurposing chains with time savings. Mark one week per month as flex/buffer. Identify 2 evergreen standbys from content history.

If ~~calendar connected: read upcoming events and build into weekly angles.
If performance data exists: weight format recommendations toward high performers.

---

## Output Format

```
EDITORIAL OS — 90-DAY CONTENT CALENDAR
[Config status header]
Generated: [Date] | Start: [{start date}]

---

FOUNDATION

Channels: [{active content platforms only}]
Velocity: {cadence} = {N} pieces over 90 days
Pillars: [{pillar names with health status icons}]
  🟢 Healthy · 🟡 Developing · 🔴 Thin · ⚪ Untested
Team: {team description}
Primary goal: {goal}

Capacity: [{N} pieces planned / {N} capacity] = [{X}%]

---

QUARTERLY THEME MAP

MONTH 1 ({dates}): "{Theme — specific, evocative}"
Lead pillar: [{pillar}] [{status}]
Segments served: [{names}]
Seasonal hook: [{from ~~calendar, or "Evergreen month"}]
Goal tie: [How this advances the primary goal]

MONTH 2 ({dates}): "{Theme}"
[Same structure — different pillar]

MONTH 3 ({dates}): "{Theme}"
[Same structure — closes the loop]

---

WEEK-BY-WEEK PLAN

WEEK 1 ({dates}) | Pillar: [{pillar}] | Segment: [{segment}]
→ [{Platform}]: "{Angle}" — Hook: [{why now}] — CTA: [{action}]
→ [{Platform}]: "{Angle}" — Hook: [{why now}] — CTA: [{action}]
Repurposing: [{Main piece}] → [{excerpt}] → [{social hook}] — saves ~{N} hours

[Weeks 2-3 same structure]

WEEK 4 — FLEX BUFFER
[One piece planned not committed — overflow or evergreen standby]

[Weeks 5–12 same structure with flex weeks at 8 and 12]

---

CALENDAR ANALYTICS

Pillar balance: [{distribution across pillars}]
Segment coverage: [{distribution across segments}]
Repurposing efficiency: {N} chains built, ~{N} hours saved

---

EVERGREEN STANDBYS
1. "{[From content history]}" — refresh angle: [{update hook}]
2. "{[From content history]}" — refresh angle: [{update hook}]

---

QUALITY GATES
✓ Resource reality test: {X}% of capacity
✓ Seasonal holds respected
✓ All pillars rotated
✓ All segments served monthly
✓ Repurposing chains built
✓ Flex weeks marked
✓ Evergreen standbys identified
✓ All content tied to primary goal
```
