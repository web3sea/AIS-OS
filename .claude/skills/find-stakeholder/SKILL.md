---
bike-method-phase: 1  # Phase 1 — Training wheels. Run manually first.
three-ms-attribution: |
  Adapted from The Three Ms of AI™ © 2026 Nate Herk.
name: find-stakeholder
description: Find every known email address for a named person by searching all connected meeting-intelligence tools at once (Granola, Fireflies, Wispr Flow, Read.ai), instead of querying each one by hand. Use when adding a new stakeholder to a client registry, verifying an existing stakeholder's address, or when someone says "find X's email" or "who is X and what's their email". Drafts a candidate entry with evidence; never writes to a registry itself.
---

# Find Stakeholder

Collapse a multi-tool manual search (Granola, then Fireflies, then Wispr Flow, then Read.ai, then cross-referencing dates by hand) into one pass. This came out of a real `/level-up` session on 2026-09-22: two separate stakeholder lookups that day each took 4-5 tool calls and several minutes.

## Core rule: record every address, never pick one

A person can legitimately hold multiple addresses (a work email and a personal one, for example). **Surface every distinct email found — do not collapse to a single "best" answer and discard the rest.** The 2026-09-22 session added a stakeholder with both a work and a personal address on the same entry; this skill exists to make that the default outcome, not a manual afterthought.

## Protocol

1. **Get the name and any known context** (which client/organization they're associated with, if any) from the user.
2. **Search every connected meeting-intelligence tool for that name**, in parallel where the tool calls allow it:
   - Granola: `query_granola_meetings` with a natural-language query naming the person (and any co-attendees mentioned), or `list_meetings` over a relevant date range if a targeted query comes back empty.
   - Fireflies: `fireflies_search` with `keyword:"<name>"`.
   - Wispr Flow: `search_meetings` with the name in `query`, `field: "both"`.
   - Read.ai: `list_meetings`, filtered by date range if the person's timeframe is known; Read.ai has no name-search, so this one is coarser.
   - If any of these tools are deferred, load them first via `ToolSearch` with a single `select:` call listing everything needed — don't load one at a time.
3. **Extract every email address associated with that name** from each source's participant/attendee metadata. Prefer calendar-derived attendee emails (exact addresses) over free-text mentions in a transcript body.
4. **Filter obvious noise:**
   - Drop addresses that match the project's internal-people list (e.g. the `internal:` block in a client registry like `clients.yaml`), if the project has one — those are colleagues, not the stakeholder being looked up, unless the name search was specifically for an internal person.
   - Do not drop a personal-provider address (gmail, etc.) just because it looks informal — personal addresses are common and legitimate for external stakeholders.
5. **Reconcile across sources.** Group by distinct address. For each address, note which source(s) it came from, how many meetings, and the date range. If two different addresses both look plausible for the same person (e.g. a work address and a `smallwinston@gmail.com`-style personal address), keep both — do not force a single pick.
6. **Report a draft, not a write.** Present:
   - The name searched
   - Every distinct email found, each with its evidence (source, meeting title(s), date(s))
   - A confidence note per address (e.g. "seen in 4 calendar invites across 2 tools" vs. "mentioned once in a transcript body, unconfirmed as calendar metadata")
   - Explicit **"nothing found"** if a source and the name search turned up nothing — never guess or fabricate an address
7. **Stop there.** Adding the confirmed entry to a client registry or other source-of-truth file is a separate, explicit step the user takes (or asks for) after reviewing the draft. This skill never writes to a registry on its own.

## What this skill is not

- Not a registry-write tool. It only searches and drafts.
- Not a dedupe-to-one-address tool. Multiple real addresses for one person is the expected, correct outcome in many cases.
- Not a guarantee of completeness — meeting-tool participant metadata can be incomplete (see each tool's own caveats, e.g. Wispr Flow's "participant metadata can be incomplete and does not prove attendance"). State what was searched and what that does and doesn't cover, per this kit's evidence-before-confidence standard.
