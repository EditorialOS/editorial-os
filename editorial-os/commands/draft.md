---
description: Draft content in your brand voice — blog posts, newsletter sections, landing page copy, case studies, or any editorial format. Uses your brand guide and audience context from Google Drive when connected.
argument-hint: "Type: <format>, Topic: <topic>"
---

# /draft

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../CONNECTORS.md).

Write content in your brand voice. Works with any editorial format.

## Trigger

User runs `/draft` or asks to write, draft, or create content.

## Inputs

1. **Content to write** — accept in any of these forms:
   - A topic or brief described directly
   - A ~~docs reference (e.g., a brief from the client's Drive folder)
   - Source material to transform (paste an outline, notes, or rough draft)
2. **Format** (optional) — blog post, newsletter section, landing page, case study, etc. If not specified, ask.
3. **Audience** (optional if ~~docs configured) — which segment this is for

## Step 1 — Load Context

Use editorial-config skill. Show one-line status header.

If configured: apply brand voice rules, vocabulary, tone from ~~docs automatically. Don't ask for voice description.
If ⚪ No client: ask for tone, audience, and any voice guidelines. Or accept pasted examples — "content that sounds like you" teaches voice faster than descriptions.

---

## Step 2 — Determine Format

If not specified, ask:

What are we writing?
- Blog post (800-2000 words)
- Newsletter section (300-600 words)
- Newsletter intro / editor's note (150-300 words)
- Landing page copy
- Case study
- Press release
- Campaign brief
- Other — describe it

---

## Step 3 — Write the Draft

**Voice rules (from client context when available):**
- Use documented voice adjectives as the baseline
- Apply vocabulary rules (use/avoid lists) as a hard constraint
- Match headline style from brand guide (sentence case / title case / AP)
- Mirror sentence rhythm from past content examples

**Structure by format:**

**Blog post:**
- Hook that earns the scroll (not a summary — a reason to keep reading)
- Subheads that work as standalone scannable story
- One core argument, not three half-arguments
- CTA that connects to primary business goal
- Word count within specified range

**Newsletter section:**
- Conversational opening — sounds like a person, not a brand
- One idea per section, clearly stated
- Bridge to CTA or next section
- Tone should match what worked in past newsletter issues (from content history)

**Landing page:**
- Headline: benefit-first, specific to audience segment
- Subhead: objection-handling or credibility signal
- Body: problem → solution → proof → action
- CTA: clear, single action, aligned with primary goal

**All formats:**
- First sentence must earn the second sentence
- Remove any sentence that could appear in a competitor's version (substitution test)
- End with a clear next action

---

## Output Format

```
EDITORIAL OS — CONTENT DRAFT
[Config status header]
Generated: [Date]

FORMAT: [{type}] | TOPIC: [{topic}] | AUDIENCE: [{segment name or description}]
VOICE: [{brand personality adjectives, or "as specified"}]
WORD COUNT: [{target range}]

---

[HEADLINE]

[Full draft content — in brand voice, structured for format]

---

DRAFT NOTES

Voice check: [{Which brand voice rules were applied}]
Substitution test: [{Key phrases that are distinctly this brand's, not generic}]
CTA alignment: [{How the CTA connects to primary goal}]
Suggested images: [{If ~~assets connected: specific image recommendations. If not: description of what would work}]

NEXT STEPS
- Edit and refine (paste back for revision)
- Run /subjects to generate subject lines if this is for email
- Run /social-pack to repurpose this into social posts

---

QUALITY GATES
✓ Voice rules applied from brand guide
✓ Vocabulary constraints respected (used: [{terms}] / avoided: [{terms}])
✓ Format structure followed
✓ CTA aligned with primary goal
✓ Substitution test passed — content is differentiated
```
