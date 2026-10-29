---
name: change-and-publish
description: Change a website Pugi built, or put it live on its public address. Use when the user asks to edit, update, fix, redesign or add something to a site Pugi built, asks to publish, go live, deploy or launch it, or asks which Pugi sites are published and where.
---

Use the `edit`, `publish`, `publish_status` and `job_status` tools from the connected Pugi server. They work on sites this account built with Pugi; a site built elsewhere cannot be edited or published here.

To change a site:

1. Identify the site by the `job_id` of its build or latest edit, or its `project_id`. If the user does not know it, `publish_status` lists the account's published projects.
2. Call `edit` with `instruction` (the change in plain words, 10–8000 characters) and a fresh `idempotency_key`; reuse the key on a retry. On a plan edits are included; on prepaid credit an edit is billed by actual cost and never above `max_usd`. Set `max_usd` only when the user names a limit.
3. An edit takes a few minutes and answers with a `job_id`. Call `job_status` about once a minute until the state is final. Show the new `preview_url` when it is ready.

To put a site live:

1. Publish only after the user has looked at the preview and asks to go live. A build or edit request alone is not that request.
2. Call `publish` with the `job_id` of the build or latest edit (or the `project_id`). Pugi runs its security check on the exact code before it goes live, and the account's hosting limit on live sites applies. Show the live address the tool returns; if it answers status "building", use `publish_status` to get the address once it is up. Do not say a site is live until the address is returned.
3. `publish_status` returns the published projects of the account and their addresses. A custom domain is set up in the Pugi console, not through these tools.
