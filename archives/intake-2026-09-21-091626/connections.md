# Connections

Registry of every system your AIOS can reach. Filled by `/onboard` from Q4-Q7 answers; expanded over time as you wire new tools. `/audit` checks this file for domain coverage and freshness.

Populated Sep 21, 2026. Every row is "not yet connected" by design: Day 1 records what exists, Day 2 wires it.

| # | Domain | Tool | Mechanism | Auth | Last checked |
|---|---|---|---|---|---|
| 1 | Revenue / Financials | Stripe (products), Wise (consulting invoices); Xero planned | not yet connected | — | — |
| 2 | Customer interactions | Microsoft Teams, Slack, Gmail, WhatsApp | not yet connected | — | — |
| 3 | Calendar | Google Calendar (primary); Microsoft 365 / Outlook calendar (one client tenant) | not yet connected | — | — |
| 4 | Communication | Slack (team); LinkedIn, cold email, X, podcast (outside world) | not yet connected | — | — |
| 5 | Project / task tracking | Linear (migrating to); Jira (legacy, still in play) | not yet connected | — | — |
| 6 | Meeting intelligence | Granola, Fireflies, Wispr Flow, Read.ai, Teams recordings | not yet connected | — | — |
| 7 | Knowledge / files | Dropbox (source of truth), Google Drive (client + team collab), Notion (team wiki), GitHub (spec + plan docs) | not yet connected | — | — |

**Mechanism options:** `mcp` (MCP server), `script` (Python/Bash hitting an API, in `scripts/`), `export` (CSV/JSON dump pipeline), `key+ref` (`.env` key + `references/{tool}-api.md` guide), `not yet connected`.

When you wire a new tool, also save `references/{tool}-api.md` capturing endpoints, auth flow, and common queries — researched-once-saved-forever.

## Notes for Day 2

- Domain 6 runs five tools on purpose (Granola, Fireflies, Wispr Flow, Read.ai, Teams recordings). This is not sprawl: users arrive on whichever meeting tool they already use, so AIOS CDP has to connect to all of them. Brad runs all five in his own meetings as the test harness for the connector matrix. Do not consolidate.
- Domain 5 is mid-migration. Wire Linear, not Jira, unless the Jira board is still where the work actually is.
- Domain 1 has no tracking layer yet. Xero and the custom KPI app are planned, not live.
