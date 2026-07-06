# Architecture — Editorial OS

  **Status:** Shipped · v1.0.0 · [PRD](PRD.md) · [Changelog](CHANGELOG.md)

  ---

  ## System Pattern

  ```
  Documents (Google Drive)
      ↓
  client-context skill          ← reads, structures, and caches brand context
      ↓
  Specialist skill routing      ← loads the right domain skill per command
      ↓
  Output + eval layer           ← scores output against a rubric before delivery
      ↓
  Learning loop                 ← results logged back to Drive; each run reads prior learnings
  ```

  Document grounding → specialist routing → eval layer → compounding learning loops.

  ---

  ## Layers

  ### Document grounding

  The system reads a connected Google Drive folder on every command. No setup forms. The documents you already maintain — brand guide, audience personas, past content, competitor research — become the system's configuration. If a document is missing, the system says so rather than inventing context.

  Handled by: `client-context` skill

  ### Skill routing

  Each command loads only the specialist skill it needs. No command loads all five skills at once. This keeps context focused and degradation clean — a missing connector or thin document affects only the skill that depends on it.

  | Command | Skill loaded |
  |---|---|
  | `/setup` | `client-context` + `editorial-config` |
  | `/audit` | `content-strategist` |
  | `/competitor` | `competitive-intel` |
  | `/calendar` | `calendar-planner` |
  | `/draft` | `content-strategist` |
  | `/subjects` | `content-strategist` |
  | `/social-pack` | `content-strategist` |

  ### Eval layer

  Every command output is scored against three criteria before delivery:

  | Criterion | What it checks |
  |---|---|
  | **Voice consistency** | Output matches the tone, vocabulary, and register of the brand guide |
  | **Pillar coverage** | Content maps to defined editorial pillars — gaps are flagged |
  | **Coherence** | Structure, argument, and flow hold together as a complete piece |

  Sections that fail the threshold are flagged and regenerated. Output is only delivered when it passes — or when the system reports specifically what it couldn't satisfy.

  The Gate implements this eval pattern as a standalone REST API callable by any pipeline: [github.com/EditorialOS/The-Gate](https://github.com/EditorialOS/The-Gate)

  ### Learning loop

  Editorial OS does not fine-tune. Learnings are stored as plain markdown in the connected Drive folder, readable and correctable by any team member. Each run reads prior learnings before executing — the system improves through accumulated context, not weight updates.

  ---

  ## Connector model

  The plugin works standalone but expands with MCP connectors in `.mcp.json`. Degradation at each connectivity level is documented in `CONNECTORS.md`.

  | Connector | What it enables |
  |---|---|
  | Google Drive | Brand context, past content, performance data |
  | Beehiiv / Mailchimp | Email campaign integration |
  | HubSpot / Salesforce | CRM and audience data |
  | Cloudinary | Image asset library |
  | Google Calendar | Planning context and seasonality |

  ---

  ## Design decisions

  **Documents as configuration** — a brand guide written for real use carries more signal than a form filled out for an AI tool. This is the constraint the whole architecture is built around.

  **Per-command skill loading** — v0 loaded everything in one pass and degraded badly on incomplete inputs. Scoping each command to one well-defined task with documented degradation produced the shipped architecture.

  **Markdown skills over a prompt database** — skills are plain markdown, readable, versionable, and auditable by non-developers.

  **Learning files over fine-tuning** — wrong patterns are a text edit, not a retraining run. The learning loop is transparent and correctable by design.
  