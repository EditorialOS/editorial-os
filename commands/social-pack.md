---
description: Turn one piece of content into a full social media package — LinkedIn posts, Twitter/X threads, and short-form hooks. Written in your brand voice with real posting schedule when configured.
argument-hint: "<paste content or describe topic>"
---

# /social-pack

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../CONNECTORS.md).

Turn one piece of content into a multi-platform social package. Different formats, different hooks, same voice.

## Trigger

User runs `/social-pack` or asks to repurpose content for social media, create LinkedIn posts, write a Twitter/X thread, or turn a blog post into social content.

## Inputs

1. **Source content** — accept in any of these forms:
   - Content pasted directly (blog post, newsletter, article)
   - A ~~docs reference to content in the client's Drive folder
   - A URL to published content
   - A topic described briefly (less effective than source content)
2. **Platforms** (optional) — LinkedIn / Twitter-X / Both (default: Both)

## Step 1 — Load Context

Use editorial-config skill. Show one-line status header.

If configured: apply brand voice, vocabulary rules, segment data, and posting schedule from ~~docs automatically.
If ⚪ No client: ask for source content, author persona, audience, and platforms.

**Always ask for:**
- SOURCE CONTENT (paste the content or describe the topic)
- PLATFORMS (LinkedIn / Twitter-X / Both — default: Both)

---

## Step 2 — Extract Angles

From the source content, identify 8-10 genuinely distinct angles — not 10 rewordings of the same point. Each angle should be a different:
- Insight or claim
- Story or example
- Framework or principle
- Data point or proof
- Contrarian take or hot take

---

## Step 3 — Generate Platform Content

### LinkedIn Posts (5 posts)

Write 5 LinkedIn posts, each a different format:
1. **Hook/Contrarian** — Opens with a bold or unexpected claim
2. **Story** — Personal narrative that illustrates the insight
3. **Framework** — Structured breakdown (steps, pillars, principles)
4. **Proof/Results** — Data, outcomes, case study
5. **Direct CTA** — Clear ask aligned with primary goal

Each post: written in the author's real voice (from brand context), appropriate LinkedIn length (150-300 words), ends with engagement prompt or CTA.

### Twitter/X Thread (1 thread, 5-8 tweets)

Build one thread with:
- Hook tweet that earns the scroll (disproportionate effort here)
- Each tweet stands alone AND flows to the next
- Vary sentence length — short punchy mixed with longer
- Final tweet: clear CTA aligned with primary goal
- All tweets strictly under 280 characters

### Short-Form Hooks (3 hooks)

For Instagram stories, newsletter teasers, or Slack shares:
- One-liner that makes someone click through
- Under 100 characters each
- Three different angles from the source

---

## Output Format

```
EDITORIAL OS — SOCIAL PACK
[Config status header]
Generated: [Date]

SOURCE: [{content type}] | CORE INSIGHT: [{one sentence}]
VOICE: [{brand personality}]
PLATFORMS: [{selected}]

---

LINKEDIN POSTS

POST 1 — HOOK/CONTRARIAN
[Full post text in brand voice]
---
Best time: [{from client context, or "Estimated"}]
Best for: [{segment name}]

POST 2 — STORY
[Full post text]
---
Best time: [{time}] | Best for: [{segment}]

[Posts 3-5 same structure]

---

TWITTER/X THREAD

1/{N} — HOOK
[Tweet text]
(Chars: XX/280)

2/{N}
[Tweet text]
(Chars: XX/280)

[Continue for thread length]

{N}/{N} — CTA
[Tweet text]
(Chars: XX/280)

---

SHORT-FORM HOOKS

1. [{Hook — under 100 chars}]
2. [{Hook — under 100 chars}]
3. [{Hook — under 100 chars}]

---

POSTING SCHEDULE

[If client context has posting data:]
Week 1:
- [{Day/time from context}]: LinkedIn Post #[X]
- [{Day/time}]: Thread
- [{Day/time}]: LinkedIn Post #[Y]

Week 2:
- [{Day/time}]: LinkedIn Post #[Z]
- [{Day/time}]: LinkedIn Post #[A]

[If no posting data:]
Recommended 2-week schedule (estimated — run /setup to use your real posting times):
[Generic schedule]

---

QUALITY GATES
✓ 5 LinkedIn posts with distinct formats and hooks
✓ Thread tweets all under 280 chars
✓ Each tweet stands alone and flows
✓ Voice consistent with brand personality
✓ Vocabulary rules applied
✓ Short-form hooks under 100 chars
✓ All CTAs aligned with primary goal
[✓ Schedule from real data / ⚠ Schedule estimated]
```
