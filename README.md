# K5M — FF&E and Interior Fit-out Project

This repository is the single source of truth for the K5M project. It is structured so that any person — or any LLM session with no prior memory of this project — can open it cold and understand what exists, where it lives, and how to work with it.

**Read `SECURITY_PROTOCOL.md` in this branch before creating or editing any document in any branch.**

## How this repo is organized

This repo uses branches, not folders, as the top-level division of content. Each branch is a self-contained area for one category of work. This `main` branch holds no project content itself — it is the front door: orientation, rules, and the daily log.

| Branch | Contents |
|---|---|
| `main` | This README, `SECURITY_PROTOCOL.md`, `DAILY_LOG.md` — orientation only, no project content |
| `001_inbox` | Raw uploads: everything received from the client or elsewhere, unprocessed. Files stay here permanently as the evidentiary record, even after being translated into knowledge bank sheets |
| `002_knowledge-bank` | The common threads shared by every downstream tracker, segregated by subject: materials, shop drawings, inspection reports, logistics, commercial data |
| `003_trackers` | Every Excel workbook we build: `internal_COC`, `production_tracker`, and any future trackers |
| `004_communication` | Saved emails and LLM-drafted correspondence, split into `internal/`, `client/`, `supplier/` |
| `005_project-discovery` | Reusable templates and frameworks, kept generic enough to reuse as a starting point for a future project beyond K5M |
| `006_task-management-pm` | Open task log, meeting minutes — one dated folder per meeting, covering pre-meeting, minutes, and post-meeting follow-up |

## Naming conventions

**Folders:** numbered by branch/section, e.g. `001_inbox`, `002_knowledge-bank`. The number fixes reading order; the name states the purpose.

**Files (mainly inside `003_trackers`):**
`YYMMDD_ProjectCode_Category_SpecificName`
- `SpecificName` is only included when there's more than one variant of that category (e.g. supplier-facing vs. client-facing material package).
- Example: `260724_K5M_Internal COC.xlsx`
- Example: `260724_K5M_Material Package_Supplier facing.xlsx`

## Project in one paragraph

K5M is a hotel project for Wood Couture, covering FF&E (Furniture, Fixtures & Equipment) and a separate but related Fit-out scope. The COC (Control Centre) workbook is the operational source of truth connecting products to materials, shop drawings, and production readiness. A parallel Fit-out COC is being built to track awarded fit-out scope, mock-up priority items, and products transferred from FF&E.

## Daily Log

See `DAILY_LOG.md` in this branch — updated once per day, newest entry on top.
