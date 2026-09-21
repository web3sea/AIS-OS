# Connections

Registry of every system your AIOS can reach. Seeded by `/onboard` from Q4-Q7 answers; hand-edited from then on as tools get wired (`/onboard` only scaffolds this file, it does not own it). `/audit` checks this file for domain coverage and freshness.

Seeded Sep 21, 2026. **Verified by live read-only calls Sep 21, 2026.** Twelve tools across all 7 domains answered; the rest are named but unwired. Per-tool detail and access routes are below the table.

> **Scope caveat, read this before trusting a row.** Every verified connection below is an **MCP server configured in Brad's Claude Code environment at user level**, not in this repository. A fresh clone of this repo on another machine, or a runtime without those servers, has none of them. "Connected" here means *this operator's session can reach it*, not *the repo carries the connection*. Codex sessions have not been checked at all.

| # | Domain | Tool | Mechanism | Auth | Last checked |
|---|---|---|---|---|---|
| 1 | Revenue / Financials | **Stripe** (products) | `mcp` | verified | 2026-09-21 |
| | | Wise (project milestones), Upwork (some retainers) | not yet connected | — | — |
| | | Xero (planned) | server available, auth in progress 2026-09-21 | — | — |
| 2 | Customer interactions | **Gmail**, **Slack** | `mcp` | verified | 2026-09-21 |
| | | Microsoft Teams (one client tenant) | **declined on purpose** (see Permissions) | — | — |
| | | WhatsApp | not yet connected | — | — |
| 3 | Calendar | **Google Calendar** (primary, 6 calendars) | `mcp` | verified | 2026-09-21 |
| | | Microsoft 365 / Outlook calendar (client tenant) | **declined on purpose** (see Permissions) | — | — |
| 4 | Communication | **Slack** (team) | `mcp` | verified | 2026-09-21 |
| | | Apollo (cold email / sequences) | `mcp`, configured, not verified | unverified | — |
| | | LinkedIn, X, podcast | not yet connected | — | — |
| 5 | Project / task tracking | **Linear** (destination), **Jira / Atlassian** (legacy) | `mcp` | verified | 2026-09-21 |
| 6 | Meeting intelligence | **Granola**, **Fireflies**, **Wispr Flow**, **Read.ai** | `mcp` | verified | 2026-09-21 |
| | | Zoom (a router source; API docs captured, client not built) | specified, not yet implemented | — | — |
| | | Microsoft Teams recordings | not yet connected | — | — |
| 7 | Knowledge / files | **Dropbox** (source of truth), **Google Drive**, **Notion** (team wiki) | `mcp` | verified | 2026-09-21 |
| | | **GitHub** (spec + plan docs) | `script` (`gh` CLI, account `web3sea`) | verified | 2026-09-21 |

**Mechanism options:** `mcp` (MCP server), `script` (Python/Bash hitting an API, in `scripts/`), `export` (CSV/JSON dump pipeline), `key+ref` (`.env` key + `references/{tool}-api.md` guide), `server available, not authenticated` (the connector exists in this runtime but the account is not linked), `not yet connected`.

When you wire a new tool, also save `references/{tool}-api.md` capturing endpoints, auth flow, and common queries — researched-once-saved-forever.

## Access routes and what each check proved

One safe read-only call per tool. Reuse these as the verification probe; none of them writes, posts, or spends.

| Tool | Probe | What it returned on 2026-09-21 |
|---|---|---|
| Stripe | list available accounts | Both live and test contexts for the company account |
| Gmail | list labels | 30 labels, including the client and finance taxonomy |
| Google Calendar | list calendars | 6 calendars across the company and personal accounts |
| Slack | list my channels | 20+ channels; result was paginated and not followed to the end |
| Linear | list teams | One team, "Automation Architecture AI", updated 2026-09-20 |
| Jira / Atlassian | current user info | Active account, org "Automation Architecture AI" |
| Granola | account info | Workspace "Automation Architecture", personal + public note scopes |
| Fireflies | current user | Admin account; Slack and Zoom integrations active |
| Wispr Flow | account info | Identity and calendar aliases resolved |
| Read.ai | list folders | Auto-folder set; most recent item activity 2026-09-20 |
| Dropbox | list `/Products/AIOS` | 5 expected folders, newest modified 2026-09-21 |
| Google Drive | list recent files | Recent documents across owned and shared files |
| Notion | list recent pages | Wiki content reachable: product pages, the PR review playbook, the executive priorities database. **Do not probe with "list teamspaces"** — this workspace has none, so that call returns empty and looks like a dead connection |
| GitHub | `gh api user` | Account `web3sea`; token scopes `repo`, `workflow`, `admin:org`, `gist` |

## Freshness and failure handling

- **Expected interval: 30 days** for a connection to count as verified, except where the data itself is volatile. Calendar, tasks and meeting sources are worth a fresh read at point of use rather than trusting a date in this table.
- **A row past its interval is stale, not broken.** Re-run that tool's probe from the table above and update Last checked. Do not silently serve an older answer as current.
- **On an auth failure, say so.** If a probe fails, report the failure and which domain went dark. Never substitute cached or remembered data for a source that did not answer, and never mark a row verified on the strength of a configured server alone.
- **A probe can fail for reasons that have nothing to do with the connection.** Notion was the live example: "list teamspaces" returned empty and looked dead, but the workspace simply has no teamspaces and every page was reachable all along. Before recording a domain as unreachable, check that the probe suits how that account is actually shaped.

## Permissions and boundaries

- **Default posture is read-only.** Reads need no approval. Anything that writes, sends, posts, schedules, spends or deletes needs Brad's say-so first, per interaction.
- **Outbound content always shows a draft first** (`CLAUDE.md` § Voice): LinkedIn, client email, anything external, no exceptions.
- **Credit-consuming calls** (Apollo enrichment in particular) get flagged with the estimated cost before running, never fired speculatively.
- **The client Microsoft 365 tenant stays disconnected, deliberately.** Decided 2026-09-21 on privacy and security grounds: authenticating it would put a client's mail and calendar within reach of every session in this runtime. This is a standing choice, not a pending task. Do not offer to wire it, and do not treat Teams, the Outlook calendar or that mailbox as connectable. Xero is being connected; Teams and M365 are not.
- **This repo is public.** Account identifiers, client names, meeting IDs, tokens and per-engagement amounts stay out of it, including out of this file. The probes above are named by what they read, never by what they returned.

## Notes for Day 2

- Domain 6 runs four verified tools on purpose (Granola, Fireflies, Wispr Flow, Read.ai). This is not sprawl: users arrive on whichever meeting tool they already use, so AIOS CDP has to connect to all of them. Brad runs them in his own meetings as the test harness for the connector matrix. Do not consolidate. **Teams recordings remain unwired, and `context/priorities.md` puts Teams out of scope for this release** — worth settling in one place, since the manuals still list it.
- Domain 5 is mid-migration and **both ends are now reachable**, so the AIOS can compare them. Wire work *into* Linear; read Jira only to see what has not moved yet.
- Domain 1 still has no tracking layer and three billing rails (Stripe, Wise, Upwork) with no single view. Only Stripe is reachable. Xero and the custom KPI app are planned, not live. The Priority 1 user count comes from the product side's Stripe connection, not from anything this AIOS needs to build.
- The gap that remains is not access, it is durability: the `mcp` rows above live in one operator's runtime config and exist only while a session is open. See **Durable paths** below for what already survives without one.

## Durable paths

An `mcp` row means *a live session can reach it*. It says nothing about whether a script, a scheduled job or a second machine can. That is a separate axis, and for several domains the agency already solved it — the work below is mostly connecting this registry to plumbing that exists, not building plumbing.

| Domain | Committed path today | Still session-only |
|---|---|---|
| 1 Revenue | n/a for this AIOS — product revenue plumbing lives on the product side | Stripe, for ad-hoc reads from a session |
| 2 Customers | Slack outbound webhook (alerts only) | **Gmail**, Slack reads |
| 3 Calendar | Google service account with delegated subject (the router service) | Google Calendar via MCP |
| 4 Communication | Slack outbound webhook | Apollo |
| 5 Tasks | **Jira** (the internal CLI repo ships a Jira client) | **Linear** |
| 6 Meetings | **Fireflies** only (GraphQL + HMAC webhooks) in the meeting-transcript router service. Granola and Zoom are specified and their API docs captured, but no client or job handler is built | Granola, Zoom, Wispr Flow, Read.ai |
| 7 Files | **Google Drive** (service account), **GitHub** (`gh`, plus app/token auth in the router) | **Dropbox**, Notion |

**Use the conventions that exist. Do not invent new ones.**

- **Secrets live in 1Password**, referenced as `op://<vault>/<item>/<field>`. the internal CLI repo's env-setter pushes them into Vercel and GitHub secrets; the credential-sync skill reconciles `.env` against 1Password and Railway by fingerprint without printing values. Headless access uses the `op` service account, not a human login.
- **Committed CLIs follow the internal CLI repo's pattern**: a script in `bin/`, symlinked by `install.sh`, prerequisite CLIs checked with a friendly exit 2, per-machine settings in a config file that is never committed.
- **Unattended work runs on Railway**, the way the router service does: Dockerfile build, health check, pre-deploy migrations, restart policy, retry limits and Slack alerting on failure.
- **API research is already captured.** The router service's repo holds source-linked developer docs for the meeting sources under `resources/`. Check there before writing a `references/{tool}-api.md` page here, and link rather than duplicate.

**One observation worth acting on.** Jira has committed tooling and Linear does not, which is backwards for a migration whose destination is Linear.

**Not a gap:** Stripe. Product revenue is connected on the product side, which is where the Priority 1 user count will come from. This AIOS does not need its own Stripe plumbing, and the MCP row above is for ad-hoc reads, nothing more.
