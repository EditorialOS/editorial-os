# Changelog

  All notable changes to Editorial OS are documented here.
  Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/). Versioning follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

  ## [Unreleased]

  ### Planned
  - `/analyze` command — quantified content performance analysis across Drive documents

  ## [1.0.0] — 2026-07-05

  ### Added
  - 7 commands: `/setup`, `/audit`, `/competitor`, `/calendar`, `/draft`, `/subjects`, `/social-pack`
  - 5 specialist skills: `client-context`, `editorial-config`, `content-strategist`, `competitive-intel`, `calendar-planner`
  - Documents-as-configuration: brand guide, audience personas, past content, and competitor research read directly from a connected Google Drive folder
  - Eval scoring on all command outputs: voice consistency, pillar coverage, coherence — failing sections flagged and regenerated before delivery
  - MCP connector support: Google Drive, Beehiiv/Mailchimp, HubSpot/Salesforce, Cloudinary, Google Calendar
  - Graceful degradation documented at each connectivity level (`CONNECTORS.md`)

  [Unreleased]: https://github.com/EditorialOS/editorial-os/compare/v1.0.0...HEAD
  [1.0.0]: https://github.com/EditorialOS/editorial-os/releases/tag/v1.0.0
  