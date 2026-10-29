---
name: build-website
description: Build a website with Pugi from a plain-language brief. Use when the user asks to build, make, create or generate a website, landing page, portfolio, shop or site for a business, person or project, or asks what Pugi can build.
---

Pugi builds a website from a brief and returns a preview link. Use the `build_site` tool from the connected Pugi server. Web apps are not built here; for an app, tell the user to use the Pugi console at https://app.pugi.io.

1. Collect the brief: what the site is for, who it is for, the pages and sections it needs, any texts, colours, style or language. Keep it to 10–8000 characters. If the user chose a catalogue card (see the start-from-template skill), name it and what they liked. If the user kept a logo from `make_logo`, pass its `logo_id`. Set `site_language` when the site's language differs from the conversation.
2. Call `build_site` with `brief` and a fresh `idempotency_key` (8–128 characters: letters, digits, dots, underscores, colons or hyphens). On a retry or timeout reuse the same key; the same key returns the same job and is never charged twice. Do not start a second job because the first one seems slow.
3. Billing: on a Pugi plan builds are included; on a prepaid-credit account a build is billed by its actual cost and never above `max_usd` (the tool's default applies when you leave it out). Do not ask the user to negotiate a budget; set `max_usd` only when the user names a limit. If the call answers that credit is missing, show the `buy_credits_link` result and stop; never pay on the user's behalf.
4. A build takes several minutes; the call answers with state "running" and a `job_id`, and the account runs one build at a time. Call `job_status` with the `job_id` about once a minute until the state is final; tell the user you are waiting rather than calling it in a tight loop.
5. When the job is done, show the `preview_url`. If it stopped or failed, say so plainly with the message the tool returned; do not invent a result.

Changing the site and putting it live are covered by the change-and-publish skill. A request to build a site is not a request to publish it; the user reviews the preview first.
