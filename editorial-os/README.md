
# Editorial OS

Editorial OS is a **modular editorial operations system for Claude and Cowork**.

It helps teams plan strategy, analyze competitors, build editorial calendars, draft content, generate email subject lines, and repurpose content for social — all grounded in your **real documents**.

Point it at a Google Drive folder containing your brand guide, competitor research, audience personas, and past content.

Your documents become the system's configuration.

---

## Install

```
github.com/EditorialOS/editorial-os
```

Once installed, commands become available directly inside Claude.

---

## Quick Demo

Try this sequence to see Editorial OS in action:

```
/audit Website: example.com Goals: grow organic traffic
/calendar Start: next month
/draft Type: newsletter intro, Topic: summer travel planning
/social-pack Source: [paste draft]
```

---

## What Editorial OS Does

Editorial OS turns Claude into an **editorial strategy engine**.

Instead of prompting from scratch every time, the system loads structured editorial context from your documents and uses it to guide every command.

It helps you:

• identify content gaps  
• analyze competitor strategy  
• plan realistic editorial calendars  
• draft content in your voice  
• optimize email subject lines  
• repurpose content for social channels  

The result is **a full editorial workflow inside Claude**.

---

## What Editorial OS Replaces

Editorial OS compresses several traditional marketing roles into a single workflow.

Typical teams divide this work across:

• Content Strategist — identifying topic gaps  
• Competitive Analyst — monitoring market positioning  
• Editorial Planner — building publishing calendars  
• Writer — drafting content  
• Email Marketer — writing subject lines  
• Social Media Manager — repurposing content  

Editorial OS unifies these functions into a single system powered by your documents.

---

## Commands

### /setup

Connect your Google Drive folder.

```
/setup
```

---

### /audit

Content gap analysis against your pillars and competitive landscape.

```
/audit
/audit Focus: pillar gaps only
/audit Website: example.com Goals: grow organic traffic
```

---

### /competitor

Battlefield-style competitor analysis.

```
/competitor
/competitor Add: competitor-site.com
```

---

### /calendar

Creates a **90‑day editorial calendar** grounded in real constraints.

```
/calendar Start: March 1
/calendar Start: April 1, Focus: email + LinkedIn
```

---

### /draft

Writes content using your voice and editorial context.

Supported formats:

• blog posts  
• newsletters  
• landing pages  
• case studies  
• editorial features  

```
/draft Type: blog post, Topic: why shoulder season travel is underrated
```

---

### /subjects

Generates email subject lines with preview text and optimization ideas.

```
/subjects Topic: spring travel guide newsletter
```

---

### /social-pack

Turns one piece of content into a multi-platform social package.

```
/social-pack Source: [paste blog post]
```

Outputs include:

• LinkedIn posts  
• Twitter/X threads  
• hooks for short-form content  
• distribution ideas  

---

## Typical Workflow

Editorial OS is designed to run as a **complete editorial pipeline**.

```
/setup
→ connect documents

/audit
→ identify content gaps

/competitor
→ analyze market positioning

/calendar
→ generate a 90‑day publishing plan

/draft
→ create articles or newsletters

/social-pack
→ repurpose content for distribution
```

Each step feeds the next.

---

## Skills

Editorial OS uses modular skills that load automatically during commands.

client-context  
Reads Google Drive documents and builds editorial context.

editorial-config  
Transforms documents into structured intelligence.

content-strategist  
Analyzes pillar health, opportunity scoring, and sequencing.

competitive-intel  
Battlefield competitor analysis and white space validation.

calendar-planner  
Capacity-aware editorial planning.

---

## How It Works

The core idea is **documents as configuration**.

Instead of filling out long setup forms, Editorial OS reads documents you already maintain:

• brand guides  
• audience personas  
• competitor analyses  
• past content  
• editorial calendars  

This creates persistent editorial context that loads automatically whenever a command runs.

Your documents become the **source of truth**.

---

## Connectors

The plugin works standalone but becomes more powerful with MCP connectors configured in `.mcp.json`.

Examples:

• Google Drive — editorial context  
• Cloudinary — image assets  
• Beehiiv / Mailchimp — email campaigns  
• HubSpot / Salesforce — CRM data  
• Google Calendar — planning and seasonality  

Connector configuration details are available in `CONNECTORS.md`.

---

## Support

Questions, feedback, or collaboration:

editorial.operating.system@gmail.com
