# Decisions Log

Append-only record of meaningful decisions and why they were made. `/level-up` Phase 2 (Method interview) writes scoped automation specs here. You can also append manually whenever you decide something worth remembering.

**Format per entry:**

```
## YYYY-MM-DD — Short title

**Decision:** what was decided.

**Why:** the reasoning, constraints, and what would change your mind.

**Alternatives considered:** what else was on the table.

**Owner:** who's accountable.
```

Keep it terse. Future-you will thank present-you for capturing the *why*, not just the *what*.

---

## 2026-09-06 - Audit evidence and routing maintenance

**Decision:** Ship audit rubric v2 and a small /link skill. Audit scores working evidence across the Four Cs, checks operating-manual routing and freshness, and passes one concrete gap into /level-up. A selected repair can improve an existing workflow instead of creating another skill.

**Why:** File counts, configured keys, named rituals, and recent edits do not prove an operational AIOS. Source findability and freshness need explicit checks.

**Alternatives considered:** Keeping presence-based scoring or requiring a hot cache. Neither reliably establishes retrieval quality or successful execution.

## 2026-09-06 - Portable skills and automatic audit history

**Decision:** Ship all four skills for Claude Code and Codex, with bundled resources, matching operating manuals, and a script for regenerating Codex copies. Audit reports are saved automatically, preserve previous runs, and track findings across comparable inspections.

**Why:** Students need the same shared guidance when switching assistants and evidence of actual improvements over time. Intentional runtime adaptations, unknown verification, and confirmed defects are reported separately.

## 2026-09-06 - Portable 3D Brain skill

**Decision:** Add `/3d-brain` for Claude Code and Codex. Ask for a name and categories, map selected local folders, and scaffold a bundled, configurable application with spherical placement, Cinema, and interactive growth replay.

**Why:** Shipping the working renderer preserves the intended appearance and interactions across AIOS installations. A prose-only prompt would produce inconsistent recreations. User config and graph data remain local; the public package includes only code, documentation, dependency notices, and fictional test inputs.

## 2026-09-06 - Add ongoing context interviews

**Decision:** Adapt Herk-2's grill-me skill for the student kit and ship matching Claude/Codex packages. Save every answer to brainstorms/, preserve resumable Q&A history, and update canonical context only with confirmed facts during requested context-building sessions.

**Why:** Onboarding is an initial snapshot. Ongoing interviews capture changing priorities, decisions, and preferences while keeping tentative ideas distinct from current business facts.

## 2026-09-21 - AIOS IQ is the knowledge layer, not a retrieval tool

**Decision:** IQ is the knowledge base behind every client and lead, where you confirm what is true once and Coffee, Signals and the agents all stop getting it wrong. AI drafts each record from email, documents and meetings; the user confirms or corrects it as it grows. Positioning line unchanged: "The memory your AI actually trusts."

**Why:** The first framing was stateless retrieval (ask a question, get a cited answer). That made IQ a fourth thing to buy and left the product line unexplained. The leverage framing makes IQ the foundation the other two products read from, which is also what justifies Coffee as the wedge: daily Coffee use produces the confirmed record that IQ sells. Build-order consequence: Coffee and Signals must read from IQ rather than re-deriving from raw email, otherwise "confirm once" is false.

**Alternatives considered:** Three variants were on the table. The working-file angle (one document per client that never goes stale) was most concrete about the artifact but weakest on why you would want it, and "never goes stale" is a claim every CRM makes. The dependency angle (every client and lead your business depends on gets a working file) was the tightest sentence but described IQ alone, leaving the family unexplained. The original retrieval framing was dropped for the reasons above.

## 2026-09-21 - AIOS CDP is infrastructure, not a fourth product

**Decision:** AIOS CDP is the shared connection layer all three products run on. It is not sold separately and does not appear as a fourth product. Line: "One connection, every product." The product line stays at three: Coffee, Signals, IQ.

**Why:** CDP surfaced in a nav-bar and pricing-table list alongside the three products, which implied it was sold. Naming it as infrastructure keeps the pricing story simple and the Dec 20 target unchanged. It also makes the stack legible: CDP connects once, IQ turns what flows in into confirmed records, Coffee and Signals are the surfaces. Each layer's promise depends on the one below it, "one connection" is what makes "confirm it once" possible.

**Consequence:** CDP is now a hard dependency of all three launches, not a parallel workstream. If it slips, all three slip together. The riskiest part is normalizing five overlapping meeting sources (Granola, Fireflies, Wispr Flow, Read.ai, Teams recordings) into one, which is a reason to consolidate that domain before building against it.

**Alternatives considered:** Selling CDP as a fourth product, which would have changed the shape of the quarter's launch target. Leaving it undecided, which would have left the three-product framing quietly contradicted by the pricing table.

## 2026-09-21 - CDP scope narrowed to data connectors; Priority 2 gets a bar

**Decision (CDP):** CDP is the data connector layer only. It is not a product and is not sold separately. The stack is CDP (connectors) -> IQ (confirmed knowledge) -> Coffee and Signals (surfaces). IQ sits directly on CDP; the other two products read from IQ rather than from connectors.

**Why:** The earlier entry established CDP was not a fourth product but left its job vague, describing it as the layer "all three products run on". It is narrower than that: connecting sources, nothing else. Knowledge lives in IQ. Keeping that boundary sharp stops connector work and knowledge work from blurring into one component.

**Decision (Priority 2):** "Reliably delivers the end-to-end product lifecycle workflow" now means: agents autonomously clear all nine stages, intake -> discovery -> intent -> plan -> build -> qa -> uat -> feedback -> prod, without intervention, while documenting every task and updating the client in the client dashboard, with the "Rabbit" agent conversing with the client, returning feedback, and fixing and deploying against it on demand.

**Why:** The priority previously had a deliverable and no bar, so December could not judge it. Stages cleared without intervention, out of nine, is countable. The three conditions (documentation, client visibility, Rabbit's feedback loop) prevent a hollow pass where stages complete but nobody outside the system can see or steer it.

## 2026-09-21 - The client Microsoft 365 tenant stays disconnected

**Decision:** Do not authenticate the client's Microsoft 365 tenant. Teams, the Outlook calendar and that mailbox are out of reach for this AIOS by choice. This is a standing position, not a backlog item, and future sessions should not offer to wire it. Xero is being connected; M365 is not.

**Why:** Privacy and security. A single client added Brad to their tenant, so that mailbox and calendar hold their data, not his. Authenticating it would put a client's correspondence within reach of every session running in this runtime, for the sake of convenience on one account. The exposure is continuous while the benefit is occasional. What would change this: the client asking for it, a genuine delivery need that cannot be met another way, or a scoped credential limited to specific shared calendars rather than tenant-wide access.

**Alternatives considered:** Connecting it and relying on care at the point of use, which makes every future session a place where that judgment has to hold. Connecting it temporarily for a specific task, which is defensible but needs a revocation step nobody currently owns.

## 2026-09-21 - Stripe durability belongs to the products, not to this AIOS

**Decision:** This AIOS does not build its own Stripe plumbing. Product revenue is already connected on the product side, and the Priority 1 count of paying AIOS Coffee users comes from there. The Stripe MCP row in `connections.md` is for ad-hoc reads from a session and nothing more.

**Why:** The first audit flagged Stripe as the only path to measuring Priority 1 and recorded having no committed script for it as a gap. That was the wrong frame. Product revenue plumbing is product work with its own paying users and its own connections; duplicating a read path here would be a second source of truth for a number the products already own. Recording it as "not a gap" rather than deleting the row means a later audit will not rediscover it and file the same finding again. What would change this: the agency needing a revenue view that spans Stripe, Wise and Upwork, which is a different problem from counting product users and is still unsolved.

**Alternatives considered:** Building a committed Stripe read in the internal CLI pattern, which solves a problem nobody has until products launch. Leaving the gap on the books, which would have kept generating the same audit finding every run.

## 2026-09-22 — Weekly scheduled `/audit` run as a cloud routine

**Decision:** Created a cloud routine (`AIS-OS Weekly Audit`, id `trig_013izD2c4YPcYacrAwt5mCeN`) that runs Fridays 5pm Asia/Makassar against `web3sea/AIS-OS`. It reads and follows `.claude/skills/audit/SKILL.md` directly, saves a dated report under `audits/`, and always opens a PR against `main` with the report as the durable run record — even when nothing changed that week. It never merges its own PR.

**Why:** Run 2 of the 2026-09-21 audit found the score exactly capped at 49/100 by Cadence (2/25): "any C below 10 caps the total at 49... every further point of documentation work is now worth nothing." Run 3 (2026-09-22) confirmed this held even after two real repairs — raw rose to 55, final stayed 49. Cadence was the only lever left, and it required an actual unattended trigger, not more documentation. A PR-per-run (rather than a silent commit to main) keeps a human checkpoint on an automated repo write while still producing durable, inspectable run evidence for D1/D2.

**Alternatives considered:** Committing straight to `main` with no review step — faster, but removes the one human checkpoint on writes an automated routine makes to the repo. A local cron job instead of a cloud routine — rejected because it depends on a laptop being on, which the audit rubric explicitly does not count as reliable unattended execution.

## 2026-09-22 — Microsoft Teams meeting recordings, confirmed out of scope

**Decision:** Teams meeting-recording connectivity is confirmed out of scope for this release, not merely an unaddressed row. `connections.md` and `context/priorities.md` now agree explicitly, and the Teams recordings row in `connections.md` reads "out of scope for this release" instead of "not yet connected."

**Why:** The 2026-09-22 audit (run 3) flagged this as the one remaining unresolved conflict between the two files, since `priorities.md` had always said Teams was out of scope but `connections.md` still framed it as an open question "worth settling." It's the same shape of decision already made about the client M365 tenant: don't offer to wire it, don't treat it as a pending task.

**Alternatives considered:** Leaving it open pending a future release-scoping conversation — rejected because "worth settling" had already sat unresolved across two prior audits with no new information arriving in between; there was nothing left to wait for.
