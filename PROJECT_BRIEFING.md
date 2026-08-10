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

**As of 2026-08-07 (end of day):** read `DAILY_LOG.md` (newest entry first) for the actual day-by-day record — it is far more current and detailed than this section. In brief, the project now runs on:
- `COMMAND_CENTER.md` (this branch) — standing trigger phrases (`#newtask`, `#projectdevelopment`, `#totalcheck`, `#GoodMorning`, `#ShowMeMyKanban`, `#hardrule`, `#execute`, `#refreshmenow`, `#STOP`, `#checkonedriveproject`). **Read this before doing anything** — it governs how work actually gets done here.
- `HARD_RULES.md` (this branch) — 19 standing constraints, several from real incidents (Excel COM force-closing Shagun's own window, a COC corruption incident, recurring Excel column-insert gotchas). **Read this too, before touching any file.**
- `SECURITY_PROTOCOL.md` (this branch) — one explicit, named, codeword-gated exception now exists: `_K5M_Folder_Guide.md` (real names, git-only). Don't open/quote it without the codeword documented there.
- `Umbrella_Tasks.md` (`006_task-management-pm`) — 15 categories now ("Contractual - Client Facing" added 7 Aug), the shared vocabulary tagging every task/log entry.
- **The merged workbook is built and live**: `260807_K5M_Project Management_Tasks and Calendar.xlsx` (`006_task-management-pm`) replaces the old separate Task Tracker and Calendar files (kept, superseded, not deleted). Connecting key is each task's **Task Number** (renamed from "S.No.," Hard Rule 8): calendar entries tag `(#N)` + hyperlink back to the row; the Task sheet's `Logged on Calendar?` column cross-checks. Tagging applies going forward, not backfilled.
- **The canonical FFE COC now has a settled home**: `03_TECHNICAL/001_COC/260804_K5M_FFE_COC.xlsx` (OneDrive) — Shagun's direct build, studied read-only 7 Aug (healthy, 5 sheets, SHD tracker at 68 remarks with real internal-review actions attached, still all-SHD00-stage). Materials/SHD get updated there; client-facing files flow *from* it, not the reverse. Don't rebuild a competing COC anywhere else.
- **The OneDrive project folder now has standing documentation**: a real, codeword-gated `_K5M_Folder_Guide.md` (git, main) and a real `_K5M_File_Index.xlsx` (OneDrive root, 707 files tagged by Umbrella Task), refreshed via the new on-demand `#checkonedriveproject` command — never automatic, roughly weekly at Shagun's discretion. A generic, redacted version of the folder structure lives at `005_project-discovery/OneDrive_Project_Folder_Structure.md` for future projects.
- **Material Package restructure, still mid-discussion, not resolved:** three trackers — Main Central (= the COC), Client-facing, Supplier-facing — same column format across all three, diverging only past a sensitivity threshold. Where exactly that divergence point is still hasn't been pinned down.
- **Outlook/mail access — working now.** The `outlook-email-drafter` connector stayed blocked even after IT's fix; the claude.ai **Microsoft 365** connector (authorized via `/mcp`) has full read access, no tenant block. Strictly read-only in practice so far — never use send/draft/reply/forward/delete tools without Shagun's explicit go-ahead. The `#GoodMorning`/`#checkmail` mail-monitoring design (checking "K5M"-tagged mail, cross-checking against the Task Tracker) is still just designed, not yet formally wired up to this connector.
- **A real schedule discrepancy is now flagged, not yet resolved with Shagun's leadership**: the actual contractual mock-up deadline is **30 Nov 2026** (per the original award letter); the Hard Milestones list's prior "20 Dec" figure was a later internal revision that had quietly drifted past it. Logged as Task Number 49 and in Hard Milestones — needs a real conversation with Filippo/Claire, not just a tracker note.
- **A live H&T capacity/responsiveness risk is being tracked** (Task Number 56): K5M factory materials now flagged for 16 Aug completion (was believed already in preparation), compounded by H&T splitting capacity with another WDCO project ("2576-F"). Layered under Shagun's own 8 Aug Plan-B escalation threat over the sample box (Task Number 50) — same underlying issue, two symptoms.
- The Fitout scope base file is still undecided; `#projectdevelopment` logging gaps should be checked with Shagun directly each `#totalcheck` rather than assumed closed.
- The Task Tracker's dropdown validation (Umbrella Task/Priority/Type/Status) only covers rows 11-33 — every row added since has none. Logged as its own task, not yet fixed.

The paragraph and open items below reflect where things stood on 2026-07-24, at the very start of this repo — kept for historical continuity, not current status:

User is about to share the BOQ (Bill of Quantities), then walk through the rest of the project narratively. Stated goal: full onboarding first — no building — Claude asks clarifying questions only after everything has been shared.

## Open items / not yet decided

- Whether the SharePoint COC system is the live source of truth going forward, and how it relates to this git repo.
- Cross-check pending: does the OneDrive-linked RFI match the SharePoint `RFI_Fitout Data` sheet exactly? (Blocked on Microsoft 365 MCP authentication — user needs to run `/mcp` and authorize it.)
- Resolving the bedroom Option A/B FF&E code collision (see above) so codes map to one physical product each.
- Whether/how the FF&E COC and Fit-out COC ultimately relate (kept fully separate trackers under `003_trackers`, most likely, but not explicitly re-confirmed since rebuild).
