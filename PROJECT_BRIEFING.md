# K5M — Project Briefing (read this first, every session)

This document exists so that any person, or any LLM session with zero prior memory, can read it once and be caught up — no need to reconstruct context from old conversations. Update it at the end of any session where something material changed. Keep `DAILY_LOG.md` (also in this branch) as the terse day-by-day companion to this file's narrative summary.

Read `SECURITY_PROTOCOL.md` in this branch too, before touching anything else.

## What K5M is

A hotel project for Wood Couture, covering two related but distinct scopes:
- **FF&E** (Furniture, Fixtures & Equipment) — the more mature workstream, tracked via the COC (Control Centre) workbook.
- **Fit-out** — a newer, still-being-scoped workstream (stone/timber/metal/glass work across corridors, T1B1 entrance/bathroom/bedroom, etc.), with its own COC being planned.

## Where this repo came from

An older repo (`ShagunWC/K5M_FFE-_COC-_Management`, branch `building-COC-Version-00`) held prior FF&E COC work (versions V01–V04) and a Fit-out scope audit draft. It was reviewed for context but **not migrated** — this repo (`ShagunWC/K5M`) is a deliberate clean start, decided 2026-07-24 since the prior work was only ~3 weeks old.

## What we know about the project so far (from the old repo's content)

**FF&E COC:** Master SKU List + Material List (French/English) + Data Sheet + SHD Sheet. As of the old repo: 26 Master SKU products, 13 with V00 drawings, all pending technical/client review, zero cleared for production. Version history V01 (base) → V02 (shop drawing linkage) → V03 (SHD tracker) → V04 (formal SHD version workflow V00→V01→V02 + final verification checkpoints).

**Fit-out COC (still a scoping draft, not yet built):** Current priority is the **T1B1 mock-up room**. Key facts from the scope audit:
- Source precedence: awarded BOQ → latest architectural drawings → approved RFI → approved material package → site survey/V01 drawings → FF&E-transferred items as separate lines.
- Scope groups: (A) Hall/Elevator Lobby/Corridors, (B) T1B1 Entrance, (C) T1B1 Bathroom/WC/Shower, (D) T1B1 Bedroom.
- Six FF&E products flagged as possibly transferred into fit-out scope, pending commercial reconciliation.
- Schedule: Fit-out V00 + prelim material package due 24 Aug 2026; site survey 31 Aug 2026; **overall room-complete target of 15 Nov 2026 flagged as at risk**.
- Six open decisions listed in the audit (full scope vs. T1B1-only first, corridor DD-package gap, carpet scope confirmation, etc.) — not yet resolved as of this writing.

**This repo does not yet contain the actual BOQ, RFI, or COC workbook files** — those are about to be shared and walked through.

## Repo structure (full detail in `README.md`, this branch)

7 branches: `main` (this one — orientation only), `001_inbox` (raw uploads, kept permanently), `002_knowledge-bank` (materials/shop_drawings/inspection_reports/logistics/commercial), `003_trackers` (internal_COC, production_tracker, future trackers), `004_communication` (internal/client/supplier), `005_project-discovery` (reusable templates for future projects, kept generic), `006_task-management-pm` (open tasks + per-meeting folders).

Tracker file naming: `YYMMDD_ProjectCode_Category_SpecificName`. Folder naming: numbered prefixes fix reading order.

Git is managed directly by Claude (cloned, authenticated via `gh`) — no manual upload needed going forward.

## Where we left off

User is about to share the BOQ (Bill of Quantities), then walk through the rest of the project narratively. Stated goal: full onboarding first — no building — Claude asks clarifying questions only after everything has been shared.

## Open items / not yet decided

- The six open decisions listed in the Fit-out scope audit (above) — status unconfirmed in this repo.
- Whether/how the FF&E COC and Fit-out COC ultimately relate (kept fully separate trackers under `003_trackers`, most likely, but not explicitly re-confirmed since rebuild).
