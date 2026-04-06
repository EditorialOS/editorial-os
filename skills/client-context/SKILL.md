---
name: client-context
description: Read a client's Google Drive folder and build complete editorial context from real documents — brand guides, audience personas, competitor analyses, content history, performance data. Replaces config files and onboarding interviews. Called silently at the start of every command. Your documents are the config.
---

# Client Context

Read a client's Google Drive folder and extract everything a command needs to work with full personalization. Called silently at the start of every command. Never ask the user to repeat information that lives in their documents.

## Why This Exists

The client already has their brand voice documented somewhere. Their audience personas exist in a deck or brief. Their competitor list is in a strategy doc. Their past newsletters are in a folder. This skill finds all of it and builds structured context from real documents — not from a config interview, not from a settings file, not from a 20-minute onboarding.

This is the core architectural innovation of the plugin: **Google Drive as persistent client context**. Instead of local settings files or conversational customization that resets across sessions, the client's real documents are the source of truth. Update a brand guide in Drive and every command picks it up on the next invocation.

## Reading Sequence

When a command loads, execute this sequence silently — never narrate the loading process to the user.

### Step 1 — Find the Client Folder

Check if a `~~docs` folder has been configured for this client (set during `/setup` or during first command use). Look for:
- A named Google Drive folder
- Image folder reference (Cloudinary or Drive subfolder)
- Active connectors (which `~~email`, `~~crm`, `~~calendar` tools are connected)

If no folder configured → work with whatever the user provides directly. Mention `/setup` at the end of the output as a suggestion, not at the beginning as a gate. First experience is a deliverable, not setup.

### Step 2 — Read the Drive Folder

Use the `~~docs` connector to search the client folder. Read documents in priority order:

#### Priority Documents (Read First)

| Priority | Document Type | Search Terms | What to Extract |
|----------|--------------|-------------|-----------------|
| 1 | Brand guide / style guide | "brand guide", "style guide", "brand voice", "voice and tone" | Voice attributes, vocabulary rules, style rules, headline conventions |
| 2 | Audience personas | "audience", "persona", "segments", "ICP" | Segment names, descriptions, content preferences, funnel stage |
| 3 | Competitor analysis | "competitor", "competitive", "landscape", "battlecard" | Competitor names, URLs, strengths, weaknesses, positioning |
| 4 | Content strategy | "content strategy", "editorial strategy", "pillars", "content plan" | Pillar themes, pillar descriptions, content territories |
| 5 | Editorial calendar | "editorial calendar", "content calendar", "publishing schedule" | Current or recent publishing plans, cadence |
| 6 | Campaign briefs | "brief", "campaign brief", "content brief" | Active campaigns, messaging, target segments |

#### Content History (Read for Patterns)

| Priority | Document Type | What to Extract |
|----------|--------------|-----------------|
| 7 | Past newsletters (most recent 3–5) | Voice patterns, recurring topics, section structure, engagement signals |
| 8 | Recent blog posts (most recent 5) | Topic coverage, depth, angle patterns |
| 9 | Performance reports | Open rates, click rates, top performers, underperformers, audience growth |

#### Image Reference

| Priority | Document Type | What to Extract |
|----------|--------------|-----------------|
| 10 | Asset list / image index | Image categories, naming conventions, usage guidelines |

If no dedicated image document found: note that image queries will use `~~assets` search directly.

### Step 3 — Extract and Structure Context

From the documents found, extract and hold in working context:

#### Brand Identity

| Element | Where to Find It | How to Use It |
|---------|-----------------|---------------|
| Publication name | Brand guide header, newsletter masthead | Use in all output headers |
| Voice attributes | Brand guide "voice" or "personality" section | Apply as baseline tone for all content commands |
| Voice adjectives | Often listed as 3-5 descriptor words | Match these in every /draft and /social-pack output |
| Vocabulary — use list | Style guide terminology section | Hard constraint — always use these terms |
| Vocabulary — avoid list | Style guide terminology section | Hard constraint — never use these terms |
| Headline style | Style guide formatting section | Apply to all headlines (sentence case / title case / AP) |
| Grammar rules | Style guide (Oxford comma, contractions, etc.) | Apply consistently across all content commands |
| Tone adaptation notes | Brand guide tone section | Dial voice attributes up/down by context |

#### Audience

| Element | Where to Find It | How to Use It |
|---------|-----------------|---------------|
| Segment names | Persona docs, strategy docs | Reference by name in all analysis and planning |
| Segment descriptions | Persona docs | Match content angle to segment needs |
| Content preferences by segment | Persona docs, performance reports | Weight format and channel recommendations |
| Geographic context | Persona docs, audience docs | Localize recommendations where relevant |
| Expertise level | Persona docs | Calibrate depth and jargon level |
| Funnel stage | Persona docs, strategy docs | Align content type to buying stage |

#### Competitors

| Element | Where to Find It | How to Use It |
|---------|-----------------|---------------|
| Competitor names and URLs | Competitive analysis docs | Load into /competitor command automatically |
| Documented strengths | Competitive analysis, battlecards | Represent honestly — never soften |
| Documented weaknesses | Competitive analysis, battlecards | Use for white space identification |
| Competitive positioning notes | Strategy docs | Inform differentiation recommendations |
| Competitive staleness | Document modified date | Flag if > 90 days old |

#### Content Pillars and Themes

| Element | Where to Find It | How to Use It |
|---------|-----------------|---------------|
| Core pillar themes | Strategy docs, editorial calendar | Structure all audits and calendars around these |
| Pillar descriptions | Strategy docs | Inform gap analysis scope |
| Content territories | Strategy docs | Define boundaries for recommendations |
| Historical emphasis | Past content, calendar | Identify over/under-indexed pillars |

#### Performance Patterns

| Element | Where to Find It | How to Use It |
|---------|-----------------|---------------|
| Open rates | Performance reports, ~~email data | Set realistic benchmarks for /subjects |
| Click rates | Performance reports | Weight CTA and format recommendations |
| Top-performing content | Performance reports, past newsletters | Identify what works — recommend more of it |
| Underperforming content | Performance reports | Identify what to avoid or rework |
| Audience growth trends | Performance reports | Context for reach and awareness goals |
| Seasonal patterns | Performance reports, calendar | Build into /calendar seasonal planning |

#### Operational Context

| Element | Where to Find It | How to Use It |
|---------|-----------------|---------------|
| Publishing cadence | Briefs, calendar, newsletter frequency | Set capacity ceiling for /calendar |
| Team or solo signal | Brief language ("I" vs "we", byline patterns) | Size all recommendations to team reality |
| Seasonal holds | Calendar, strategy docs | Block these weeks in /calendar |
| Active channels | Past content, strategy docs | Only recommend channels actually in use |
| Active connectors | Setup config | Enable/disable connector-dependent features |

### Step 4 — Flag What's Missing

If a critical document type isn't found, note it briefly — don't block the command:

```
⚠️ No brand guide found in [{folder}] — using voice patterns extracted from past content
⚠️ No competitor list found — /competitor will ask for competitors this session
⚠️ No performance data found — recommendations will use industry benchmarks
⚠️ No audience personas found — using audience signals from newsletter intro copy
```

Missing documents reduce precision but never prevent output. Every command works with partial context.

### Step 5 — Show Status Header

One line at the top of every command output:

```
🟢 [{client name}] | Drive: [{folder}] | [{N} docs read] | ~~email: {✓/–} | ~~crm: {✓/–}
🟡 [{client name}] | Drive: [{folder}] | Partial — [{what's missing}]
⚪ No client folder — working from what you provide directly. Run /setup to connect your docs.
```

## Connector Awareness

After reading Drive context, check which live connectors are active and what they add:

### ~~email Active (Beehiiv, Mailchimp, ConvertKit, Klaviyo)

| Data Available | How Commands Use It |
|---------------|-------------------|
| Subscriber count and segments | Size audience references in /audit and /calendar |
| Recent send metrics (open rate, CTR) | Set real benchmarks in /subjects instead of industry averages |
| Top-performing sends | Inform content-strategist skill recommendations |
| List growth trend | Context for awareness and growth goals |
| Scheduled sends | Avoid conflicts in /calendar |

### ~~crm Active (HubSpot, Salesforce, Close)

| Data Available | How Commands Use It |
|---------------|-------------------|
| Contact lists and segments | Map content to real audience segments |
| Pipeline data | Context for B2B content priorities |
| Lifecycle stage data | Align content to funnel stage |
| Company/contact properties | Personalization signals for /draft |

### ~~calendar Active (Google Calendar)

| Data Available | How Commands Use It |
|---------------|-------------------|
| Upcoming events | Build into /calendar seasonal planning |
| Deadlines and milestones | Anchor calendar themes |
| Recurring meetings | Understand team time constraints |

### ~~assets Active (Cloudinary)

| Data Available | How Commands Use It |
|---------------|-------------------|
| Image library | Suggest specific images in /draft and /social-pack |
| Asset tags and categories | Match images to content themes |
| Recent uploads | Surface new assets for timely content |

### No Connectors Active

Work from Drive documents and direct user input only. Note at the end of output which connectors would enhance results:

```
💡 Connect ~~email to use your real open rates instead of industry benchmarks.
💡 Connect ~~calendar to build seasonal events into your editorial calendar.
```

## Working With Ambiguous Documents

Drive folders are not always tidy. Real client folders have outdated docs, conflicting information, and missing pieces. Apply judgment:

### Multiple Documents of the Same Type
- Read all versions
- Prefer the most recently modified
- If they conflict, use the most recent document's position and flag the conflict briefly

### Outdated Documents
- Use for structural context (pillars, competitors, audience segments)
- Flag recency concern if document is > 90 days old
- Don't use outdated performance data as current benchmarks

### No Dedicated Document
- **No brand guide** → extract voice patterns from the last 3-5 newsletters. Look for recurring phrases, sentence structure, formality level, and vocabulary patterns. Flag as "inferred voice" — less reliable than documented voice.
- **No audience doc** → extract audience signals from newsletter intro copy, brief descriptions, and CTA targeting. Flag as "inferred audience."
- **No competitor doc** → leave competitor fields empty. /competitor will ask for competitors in the session.
- **No strategy doc** → infer pillars from recurring topics in the last 5 newsletters. Flag as "inferred pillars."

### Conflicting Information
- Note the conflict in the status header
- Use the most recent document's position
- Ask the user to resolve only if the conflict materially affects the output

## Document Type Recognition

Not every client labels their documents neatly. Use content signals to identify document types:

| If the document contains... | Treat it as... |
|----------------------------|----------------|
| Voice adjectives, tone descriptions, "we are / we are not" language | Brand guide |
| Demographic or psychographic descriptions, segment names, "ICP" | Audience personas |
| Competitor names with analysis, strengths/weaknesses, positioning | Competitive analysis |
| Theme names with descriptions, "pillar", "content territory" | Content strategy |
| Dates with content assignments, publishing schedule | Editorial calendar |
| Open rates, click rates, subscriber counts, engagement data | Performance report |
| "Brief:", objective, target audience, key message, deliverables | Campaign brief |

## What This Skill Does NOT Do

- Does not ask the user to re-enter information that's in their documents
- Does not require a specific folder structure — works with whatever documents exist
- Does not block on missing documents — flags gaps and continues
- Does not write or modify Drive documents — read-only
- Does not cache context across sessions — reads fresh each invocation
- Does not narrate the loading process — shows status header only
- Does not require /setup before working — any command works cold

## Cross-Skill Dependencies

- **Used by:** editorial-config (interprets raw context into structured intelligence)
- **Used by:** All commands (via editorial-config)
- **Designed for reuse:** Copy this skill into any plugin that needs client context from Google Drive
