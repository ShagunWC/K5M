# K5M — Project Briefing (read this first, every session)

This document exists so that any person, or any LLM session with zero prior memory, can read it once and be caught up — no need to reconstruct context from old conversations. Update it at the end of any session where something material changed. Keep `DAILY_LOG.md` (also in this branch) as the terse day-by-day companion to this file's narrative summary.

Read `SECURITY_PROTOCOL.md` in this branch too, before touching anything else.

## What K5M is

**Flagged 2026-07-24: the user said this description is "not fully correct" — exact correction not yet given. Do not treat the wording below as settled; update once clarified.**

A hotel project (Park Hyatt Casablanca) that Wood Couture is executing as Production Partner, covering two related but distinct scopes:
- **FF&E** (Furniture, Fixtures & Equipment) — the more mature workstream, tracked via the COC (Control Centre) workbook.
- **Fit-out** — stone/timber/metal/glass work across corridors, T1B1 entrance/bathroom/bedroom, etc. A Fit-out COC already exists live on SharePoint (`261507_K5M_COC_Fitout.xlsx`, modified 2026-07-17) — it is not merely "being planned."

## Where this repo came from

An older repo (`ShagunWC/K5M_FFE-_COC-_Management`, branch `building-COC-Version-00`) existed prior to this one. It is **not a reference source** — the user found it explained nothing meaningfully and is deleting that branch. Do not cite it, its version history (V01–V04), or its Fit-out scope audit draft as fact. Anything from it that turned out to still be true was independently re-confirmed from live sources below; anything not re-confirmed should be treated as unknown, not assumed.

## Authoritative sources going forward

- **A live SharePoint COC system already exists for K5M**, independent of this git repo, accessed here via a `sharepoint_coc_server` MCP connector: project folder `K5M`, containing `261507_K5M_COC_Fitout.xlsx` and `261307_K5M_COC_FFE.xlsx` (both last modified 2026-07-17). The Fitout workbook has a `RFI_Fitout Data` sheet (dated 15.07.2026) with detailed line-by-line scope understanding and open questions to G&B — this appears to be the same document the user separately shared via a OneDrive link, pending cross-check.
- **Source documents shared directly by the user from 2026-07-24 onward** (BOQ, drawings, kickoff-meeting email, etc.) — see `DAILY_LOG.md` for what's been reviewed.
- Whether the SharePoint COC system should be treated as *the* live source of truth (vs. this git repo, or alongside it) is an open question — see below.

## What we've actually confirmed so far

- **Project:** K5M = internal code for a Park Hyatt Casablanca renovation. Designer: Gilles & Boissier (G&B). Owner's rep: Interedec Maroc. Executive Architect: Adil Mokaddem. Production Partner: Wood Couture.
- **Commercial status:** Wood Couture's revised proposal (29 Jun 2026) selected as the working basis for FF&E/Fit-Out guestrooms. A full T1B1 mock-up room must be completed and ready for review by **30 November 2026** (critical contractual milestone per the kickoff email thread — reconcile against any other date found elsewhere before relying on either).
- **BOQ (T1B1, current):** FF&E sheet totals $24,724.89 across 24 line items; Fit-out sheet totals $122,069.58 across Hall/Corridor, Entrance, Bathroom, and Bedroom scope groups.
- **RFI:** ~26 open line items with the team's understanding and questions back to G&B, covering the same Hall/Entrance/Bathroom/Bedroom scope groups as the BOQ.
- **Known open issue:** the Schematic Design set shows two bedroom furniture options (A/B) sharing identical FF&E codes despite being physically different pieces; Option A (table lamp, not pendant) matches what's actually priced in the confirmed FF&E BOQ.
- **DD100 (69-page detailed drawing set) drafting/QA issues worth raising with G&B:** missing GEN-120/GEN-130 general sheets; 7 CHAMBRE sheets carry a placeholder "PROJET/VILLE" project name never filled in; 7 CHAMBRE detail sheets (303–309) mis-stamped with the SDB drawing-number prefix instead of CHA, 2 of which also keep a stale "BANQUETTE" label instead of "TV surround"; an extra SDB-201 elevation sheet not in the official drawing index; bedroom ceiling cornice explicitly marked "OPTION B" (unresolved); bathroom vanity pendant-light quantity marked TBC by the lighting designer; recurring "provide electrical supply" callouts across all areas (electrical coordination not finalized); all revision logs are still dummy placeholders.

## Repo structure (full detail in `README.md`, this branch)

7 branches: `main` (this one — orientation only), `001_inbox` (raw uploads, kept permanently), `002_knowledge-bank` (materials/shop_drawings/inspection_reports/logistics/commercial), `003_trackers` (internal_COC, production_tracker, future trackers), `004_communication` (internal/client/supplier), `005_project-discovery` (reusable templates for future projects, kept generic), `006_task-management-pm` (open tasks + per-meeting folders).

Tracker file naming: `YYMMDD_ProjectCode_Category_SpecificName`. Folder naming: numbered prefixes fix reading order.

Git is managed directly by Claude (cloned, authenticated via `gh`) — no manual upload needed going forward.

## Where we left off

**This section is stale below the "as of 2026-08-04" line — kept for history, but read the top first.**

**As of 2026-08-04 (end of day):** the initial-onboarding phase (BOQ walkthrough, narrative briefing) described in the paragraph below this is long done. Read `DAILY_LOG.md` (newest entry first) for the actual day-by-day record — it is far more current and detailed than this section. In brief, the project now runs on:
- `COMMAND_CENTER.md` (this branch) — standing trigger phrases (`#newtask`, `#projectdevelopment`, `#totalcheck`, `#GoodMorning`, `#ShowMeMyKanban`, `#hardrule`, `#execute`, `#refreshmenow`). **Read this before doing anything** — it governs how work actually gets done here.
- `HARD_RULES.md` (this branch) — 19 standing constraints, several from real incidents (Excel COM force-closing Shagun's own window, a COC corruption incident, recurring Excel column-insert gotchas). **Read this too, before touching any file.**
- `Umbrella_Tasks.md` (`006_task-management-pm`) — the 13-category shared vocabulary tagging every task/log entry.
- Live trackers: `260730_K5M_Task Tracker.xlsx` and `260729_K5M_Project Calendar.xlsx` (`006_task-management-pm`), `internal_COC/260728_K5M_Internal COC_FFE.xlsx` and `shop_drawing_tracker/260804_K5M_Shop Drawing Tracker.xlsx` (`003_trackers`).
- **Currently open, carried into the next session:** a full COC rebuild-from-scratch is agreed in principle (data was fine, but the file itself is suspected of being too fragile/bloated — see Hard Rule 17-19) but deliberately deferred until the Calendar/Task Tracker work is finished; a merged `Project Management_Tasks and Calendar.xlsx` workbook is scoped and agreed but not yet built; `#projectdevelopment` logging has a 2-day gap (3-4 Aug) that Shagun explicitly wants to close out together next session, not rushed; the Fitout scope base file is still undecided.

The paragraph and open items below reflect where things stood on 2026-07-24, at the very start of this repo — kept for historical continuity, not current status:

User is about to share the BOQ (Bill of Quantities), then walk through the rest of the project narratively. Stated goal: full onboarding first — no building — Claude asks clarifying questions only after everything has been shared.

## Open items / not yet decided

- Whether the SharePoint COC system is the live source of truth going forward, and how it relates to this git repo.
- Cross-check pending: does the OneDrive-linked RFI match the SharePoint `RFI_Fitout Data` sheet exactly? (Blocked on Microsoft 365 MCP authentication — user needs to run `/mcp` and authorize it.)
- Resolving the bedroom Option A/B FF&E code collision (see above) so codes map to one physical product each.
- Whether/how the FF&E COC and Fit-out COC ultimately relate (kept fully separate trackers under `003_trackers`, most likely, but not explicitly re-confirmed since rebuild).
