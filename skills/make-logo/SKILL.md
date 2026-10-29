---
name: make-logo
description: Make logo concepts for a business or project name with Pugi. Use when the user asks for a logo, a logo idea, a brand mark or several logo options for a name, including a logo for a site they are building.
---

Use the `make_logo` tool from the connected Pugi server. One call returns four whole logos (the name with a drawn mark) as images.

1. Ask for the business name if it is missing (1–60 characters). Pass what the user said as given: `industry`, `description`, `styles` or `style`, `tagline`, and `colours` as hex values when they named colours. Do not ask for an imitation of an existing brand's logo.
2. Call `make_logo` with `business_name` and a fresh `idempotency_key` (8–128 characters: letters, digits, dots, underscores, colons or hyphens). Reuse the key on a retry; the same key with the same arguments is never charged twice.
3. Allowance: every account has a few free calls a day, and paid plans include more; beyond that a call is paid from prepaid credit at the listed price. The tool's response shows what was charged. When the user has already used the free calls today, say that the next call is paid and let them decide before you call.
4. Show the returned images as they are, with the `logo_id` of each. If the user wants variations, call again with their feedback in `refines` or `refine_notes`. If the response has a brand kit link, give it to the user; what that page offers depends on their Pugi plan. If no image comes back, report the failure as returned; do not describe logos that do not exist.
5. A kept `logo_id` can be passed to `build_site` or `edit` so the site uses that logo.

These are design concepts, not a trademark search or a trademark clearance.
