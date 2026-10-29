---
name: start-from-template
description: Find a site or app in the public Pugi catalogue to start a new website from. Use when the user wants examples, ideas, templates or a starting point for a site ("show me restaurant websites", "a template for a dental clinic") before or instead of writing a brief.
---

Use `catalog_search` from the connected Pugi server. It is free and read-only and returns published sites and apps people built with Pugi.

1. Search with the user's words in `query` (up to 80 characters), or with one `category` from the tool's list (for example `food`, `services`, `portfolio`, `landing_page`, `ecommerce`, `real_estate`) and optional `tags`. The catalogue is curated and small: when a query returns nothing, try the category alone or no filter, and say how many cards exist.
2. Show the best few matches: title, one-line description, preview image and page URL. Let the user pick.
3. When they pick one, carry its title and what they liked into the brief for `build_site` (see the build-website skill). A card is inspiration for a new site, not a copy of that site's code, and it is not the user's own site. Each card also has a `start_from_this_url` that opens the same brief in the Pugi console; offer it when the user prefers to continue there.
