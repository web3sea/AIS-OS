# AIS-OS Intake

This is the source-of-truth file for your AIOS. Fill it in by typing, voice-pasting (Wispr Flow / OS dictation), or running `/onboard` for a guided conversation. Whichever mode, this file is what `/onboard` reads to scaffold your Day-1 setup.

**Hard cap: 7 questions.** Each answerable in under 60 seconds. Don't overthink — you can edit and re-run `/onboard` any time.

---

## Q1 — Who are you, what do you sell, who do you sell it to?

Identity, offer, ICP. One paragraph each is fine.

```
I am Brad Wilcox. I sell 3 products for solo founders, plus custom automation
solutions.

ICP: solo founders.

Products: AIOS Coffee, AIOS Signals, AIOS IQ.

- Signals - self-serve relationship intelligence: import your contacts, see your
  relationship map, and get three ranked next actions. Positioning line: "Know
  which relationships need you today."
- Coffee - your daily briefing and meeting prep: what is on today, what you need
  to know before each meeting, and a draft reply ready to send. Positioning
  line: "Walk into every meeting prepared."
- IQ - the knowledge base behind every client and lead: confirm what is true
  once, and Coffee, Signals and your agents all work from it. Drafted by the AI
  from your emails, documents and meetings; confirmed or corrected by you as it
  grows. Positioning line: "Confirm it once, everywhere gets it right."

AIOS CDP - shared infrastructure, not sold separately. The single connection
layer the three products run on. Positioning line: "One connection, every
product."

Custom automation engagements run in two shapes, both active at once:

- Retainers, monthly, ongoing.
- Projects, fixed scope and fixed fee.

As of Sep 2026: 2 retainers and 5 active projects running concurrently.
Retainer band roughly $2k to $5.6k per month. Project band roughly $1.6k to
$8k. Entry point is $1,500 for a basic automation.

Duration depends on scope: minimum 2 weeks, average 8 weeks.

Exact per-engagement figures are deliberately not recorded here: this repo is
public. Detail belongs in Dropbox under Products/AIOS.
```

---

## Q2 — Paste 1-2 things you've written recently. Don't edit them.

An email, a LinkedIn post, a DM, a doc — anything that sounds like you when you're not trying. **Paste verbatim.** Do not type these mid-conversation with Claude — chat-shaped samples are worse than no samples (voice contamination).

```
I spent 15 years as a product in tech startups and enterprise. That experience is exactly why I started Automation Architecture AI, and am able to build software and automations that users want, and that drive success for my clients.



I built an agency to be the strategic partner that helps ambitious companies implement AI, from fully automated lead generation pipelines to content automation, CRM integration, and operational AI that reduces the cost of running a growing business.



What I bring that most agencies don't: I've sat in the operator's seat. I understand product, growth, and what it takes to get a team to actually use something. 



If you're trying to figure out where AI fits in your business, and how to move from "we should do something" to a system that runs, let's talk.
```

```
Dear Hiring Team,
I have been consulting for Preferred Travel Group since October 2025. The first two products I built for you
were the Content Generation Admin tool and the Client Portal. I am applying for this role because the
problems in the job description are ones I have already been working on from the outside, and I would
rather solve them from the inside with a real mandate.
I have come to think of AI as a great solution for leaks and clogs! Please allow me to explain:
Leaks are where value escapes. A guest who cannot get an answer at 11pm and books elsewhere. A
property whose descriptions, amenities, or offers have drifted out of date and quietly stops being surfaced
or cited. A member whose profile is fragmented across booking, loyalty, and clickstream systems, so
personalization never fires. Leaks rarely show up in a P&L, because nobody invoices for revenue that never
arrived.
Clogs are where throughput is constrained. Hotel onboarding that takes weeks of manual content collection.
Content refresh queues that depend on a person moving data between systems. Member inquiries stacked
behind human capacity.
Leaks cost revenue. Clogs cost time, margin, and morale. AI is unusually good at both, but only after
someone has done the unglamorous work of finding them and putting numbers on them. That is the work I
want to do here.
Three priorities I would bring to the role:
Break down the internal data silos to drive user personalization. Booking, loyalty, clickstream, and
marketing data have to resolve into one member profile before AI grounding can mean anything. I have
done this before: at Campus Labs, the core value proposition was connecting disconnected campus systems
into a unified view of the student, across thousands of institutions.
Personalize the guest experience. Once that profile layer exists, guest-facing surfaces can respond to intent
and history instead of treating every visitor as a stranger. I have built and shipped the conversational half of
this already, including AI agents handling email and webchat that passed graded output testing and were
approved by clients to respond autonomously.
Smooth hotel onboarding to keep content current. The Content Generation Admin tool was a first step.
Automated content ingestion that keeps property data accurate across owned channels fixes a clog for
internal teams and a leak for AI discoverability at the same time, because LLMs cite what is structured,
current, and unambiguous. AI is great at solving leaks and clogs.
I already know the systems, the constraints, and several of the people. I would like to keep going, with more
scope.
Thank you for your consideration.
Brad Wilcox
```

---

## Q3 — What are your 2-3 biggest priorities for the next 90 days?

Quarterly priorities. Not yearly aspirations. Things that, if not done by July, would make you say "I wasted Q2."

```
1. Launch all 3 products and reach 30 paying AIOS Coffee users by Dec 20, 2026.
   Coffee is the wedge; adoption is expected to spill over into IQ and Signals.
2. Stand up an agent team that reliably delivers the end-to-end product
   lifecycle workflow.
   Definition of done: agents clear all nine stages without intervention -
   intake, discovery, intent, plan, build, qa, uat, feedback, prod - while
   documenting every task, updating the client in the client dashboard, and
   with the "Rabbit" agent conversing with the client, returning feedback, and
   fixing and deploying against it on demand.
```

---

## Q4 — Where does revenue actually land, and where is it tracked?

Multiple answers OK. Stripe? Skool? GoHighLevel? QuickBooks? A spreadsheet?

```
Today:
- Product revenue: Stripe (rail decided; products not yet launched).
- Consulting / custom automation revenue: invoices land in Wise bank.
- Tracking: nothing consolidated yet.

Planned:
- Xero for accounting (needs to be set up).
- A custom app to track product growth against monthly goals and KPIs.
```

---

## Q5 — Where do you talk to customers, your team, and the outside world day-to-day?

Email (which one — Gmail / Outlook)? Slack? Teams? DMs (Skool / Discord / iMessage)? Phone?

```
- Customers: Microsoft Teams, Slack, email, WhatsApp.
- Team: Slack.
- Outside world: LinkedIn, cold email, X, my podcast.

Email providers: Gmail (Google Workspace) is the primary, day-to-day account.
Microsoft 365 Outlook is secondary - a single client added me to their tenant,
so that mailbox is client-specific.

Calendar (Domain 3, inferred): Google Calendar primary, with the client's
Microsoft 365 / Outlook calendar secondary.
```

---

## Q6 — Where do meeting recordings, notes, and important docs live?

Granola? Otter? Fireflies? Google Drive? Notion? Dropbox? A folder on your desktop you keep meaning to organize?

```
Meeting intelligence (recordings and notes): Granola, Fireflies, Wispr Flow,
Read.ai, Microsoft Teams recordings.

Documents and knowledge:
- Dropbox - source of truth.
- Google Drive - client and team collaboration.
- Notion - team wiki.
- GitHub - spec and plan working docs.
```

---

## Q7 — What's the one task that eats your week, and where do you currently track work?

The single biggest time-suck or recurring drudgery. Plus where tasks/projects live (ClickUp / Asana / Linear / Notion / a notebook).

```
Top pain: automating the agent merge workflow while still keeping code release
quality high. Review and merge of agent-produced work is the recurring
time-suck.

Work tracking: transitioning from Jira to Linear. Linear is the destination;
Jira is the legacy system still in play during the move.
```

---

When this file is filled, run `/onboard` (or re-run it) and the wizard will scaffold your Day-1 file set: `context/`, `references/voice.md`, populated `connections.md`, and a filled `CLAUDE.md`.
