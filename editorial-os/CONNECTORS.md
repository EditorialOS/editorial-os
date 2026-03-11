# Connectors

## How tool references work

Plugin files use `~~category` as a placeholder for whatever tool the user connects in that category. For example, `~~email` might mean Beehiiv, Mailchimp, or any other newsletter platform with an MCP server.

Plugins are **tool-agnostic** — they describe workflows in terms of categories (documents, email, assets, etc.) rather than specific products. The `.mcp.json` pre-configures specific MCP servers, but any MCP server in that category works.

## Connectors for this plugin

| Category | Placeholder | Included servers | Other options |
|----------|-------------|-----------------|---------------|
| Documents | `~~docs` | Google Drive | Notion, Dropbox |
| Assets | `~~assets` | Cloudinary | — |
| Email marketing | `~~email` | Beehiiv | Mailchimp, ConvertKit, Klaviyo |
| CRM | `~~crm` | HubSpot | Salesforce, Close |
| Calendar | `~~calendar` | Google Calendar | — |
| Mail | `~~mail` | Gmail | — |

## How Connectors Enhance Commands

| Command | Works standalone? | Enhanced by |
|---------|:-:|---|
| `/audit` | ✅ paste content or describe | `~~docs` (reads existing content library), `~~email` (real open/click rates) |
| `/competitor` | ✅ provide competitor URLs | `~~docs` (pre-loaded competitor analysis from Drive) |
| `/calendar` | ✅ describe goals and pillars | `~~docs` (real pillars and constraints), `~~calendar` (seasonal events) |
| `/draft` | ✅ describe what to write | `~~docs` (brand voice from style guide), `~~assets` (image selection) |
| `/subjects` | ✅ paste newsletter draft | `~~docs` (brand voice rules), `~~email` (real benchmark data) |
| `/social-pack` | ✅ paste source content | `~~docs` (brand voice), `~~assets` (image assets for posts) |
| `/setup` | — | `~~docs` (required — this is how client context loads) |

## Configuring Connectors

Edit `.mcp.json` to point at your specific tools. The plugin gracefully degrades when tools are unavailable — it will note what's missing and work with what you provide directly.

The core connector is `~~docs` (Google Drive). This is what makes the plugin client-aware across sessions. All other connectors add capability but aren't required.
