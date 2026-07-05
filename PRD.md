# PRD — Editorial OS v1.0

  **Status:** Shipped · v1.0.0 · [Changelog](CHANGELOG.md) · [Architecture](ARCHITECTURE.md)
  **Owner:** Roger Gurbani

  ---

  ## Problem

  Editorial strategy work — audits, competitive analysis, calendars, drafting — is done from scratch every cycle because the context that should inform it lives in scattered documents nobody re-reads. AI tools make this worse when they're configured through setup forms: forms capture what a team *thinks* it should say, while the brand guide, personas, and past content capture what the team actually does. Generic context in, generic strategy out.

  ## Users

  - **Solo content leads and small editorial teams** who own strategy and production with no analyst support
  - **Agencies** running editorial operations for multiple clients, each with its own document set
  - **Marketing teams** who maintain brand documentation but have no system that operationalizes it

  ## What v1 does

  - Connects to a Google Drive folder and treats its documents as the configuration — brand guide, audience personas, competitor research, past content, performance data
  - Runs a seven-command pipeline: `/setup`, `/audit`, `/competitor`, `/calendar`, `/draft`, `/subjects`, `/social-pack` — each step's output feeds the next
  - Routes each command to only the specialist skills it needs (five skills; no command loads all of them)
  - Scores every output before delivery on voice consistency, pillar coverage, and coherence; flags and regenerates failing sections
  - States what it found and what's missing — degrades gracefully and visibly instead of hallucinating context
  - Extends via MCP connectors (Drive, email platforms, CRM, Cloudinary, Calendar), with degradation behavior documented per level in `CONNECTORS.md`

  ## What v1 explicitly does NOT do

  - **Does not work from descriptions.** No setup questionnaire that substitutes for documents. If the Drive folder is thin, the system says so rather than inventing a brand.
  - **Does not publish.** Output is delivered for human review; no auto-posting to a CMS or social platform.
  - **Does not measure live performance.** `/audit` analyzes content and pillars; quantified performance analytics is the `/analyze` command scoped for v1.1.
  - **Does not fine-tune.** Voice comes from document grounding at runtime, not from model training. Learnings live in readable markdown, not weights.
  - **One brand context per Drive folder.** Multi-client work means one folder per client, by design.

  ## Success criteria

  - `/setup` correctly inventories a real client folder: reports what it found and what's missing with zero false positives <!-- ⚠️ RAJ: run this against your best-documented test folder and your thinnest one; note both results here. -->
  - Every command output passes the three-criterion eval or visibly flags what failed
  - `/draft` output passes the substitution test — a reader familiar with the brand can't swap in a competitor's name without it reading wrong <!-- ⚠️ RAJ: if you've had anyone blind-test a draft against the brand guide, cite it. -->
  - Full pipeline (audit → calendar → draft → social-pack) runs on one context load without re-configuration

  ## v1.1 roadmap

  - `/analyze` — quantified content performance analysis across Drive documents

  ## Decision log

  - **Documents as configuration** — a brand guide written for a real purpose carries more signal than a form filled out for an AI tool
  - **Per-command skill loading** — v0 loaded everything in one pass and degraded badly under incomplete inputs; scoping each command to one well-defined task with documented degradation produced the shipped architecture
  - **Markdown skills over a prompt database** — readable, versionable, auditable by non-developers
  