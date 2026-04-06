---
description: Connect your Google Drive folder so every command reads your real documents — brand guide, competitor analysis, audience personas, past content. Three questions, 60 seconds. Optional — every command also works without setup.
---

# /setup

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../CONNECTORS.md).

Connect your documents. Three questions. Every command gets smarter after this.

## Trigger

User runs `/setup` or asks to connect their documents, configure the plugin, or set up client context.

## Inputs

No inputs required — the command asks three questions interactively.

---

**1. What's your Google Drive folder for this client?**

The folder where your brand guide, audience personas, past content, and strategy documents live. Exact folder name or path.

*Example: "See Monterey" or "Clients/See Monterey/Content"*

---

**2. Where are your images?**

A Cloudinary folder, a Drive subfolder, or both?

*Example: "see-monterey" in Cloudinary, or "See Monterey/Assets/Images" in Drive*

---

**3. Which connectors are active?**

a. ~~email (Beehiiv, Mailchimp, etc.)
b. ~~crm (HubSpot, Salesforce, etc.)
c. Both
d. Neither — working from Drive documents only

---

After you answer, I'll connect to your folder, read what's there, and show you a one-line summary of what I found. Then every command loads your client's context automatically.

If something important is missing from your folder, I'll tell you what it is and how it affects output — but I won't block you from running commands.

---

*This is optional. Every command works without setup — you can paste content, provide URLs, or describe your situation directly. Setup just means you don't have to repeat yourself.*
