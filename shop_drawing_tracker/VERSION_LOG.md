# shop_drawing_tracker — Version Log

Newest entry at the top.

---

## 2026-08-04 — `260804_K5M_Shop Drawing Tracker.xlsx` — V1
First version, built from scratch after discussion (design agreed 2026-08-04, `#execute` given same day). Two sheets:

- **Data** — exact, unmodified copy of the canonical FFE Master SKU List (`260724_WDCOK5M_FFE_Master SKU List.xlsx`, all 26 scope rows, 27 embedded reference images carried over intact). Renamed from "Master SKU List" only — no other changes.
- **Shop Drawing Tracker** — one row per item (26 rows), WDCO Item Code linked live to Data via formula (blank where Data has no code assigned yet — cancelled/moved-to-Fit-Out items). Structure per item:
  - Brief Received from Client (hyperlink)
  - **SHD00** (hyperlink) → collapsible remarks: Client Feedback / Internal Review / Factory-Production Partner Review, each paired with a Value column restricted by dropdown to `TRUE` / `FALSE` / `Not Going Forward` (data validation throws a stop-error on any other entry)
  - **SHD01** (hyperlink) → same collapsible remarks structure as SHD00
  - **SHD02 — Client Sign-Off**: no remarks at all by design — just "SHD01 Feedback Incorporated (Readiness Check)" then the SHD02 hyperlink (client-signed copy). Getting a remark at this stage is meant to be a red flag, not a normal state.

Each item currently has one row. Adding more feedback rows for an item means inserting a row within that item's block and extending the merge on WDCO Item Code / Brief / SHD00 / SHD01 / readiness-check / SHD02 columns to match — these are single-row merges today since no feedback exists yet.

Checkbox mechanism intentionally left as TRUE/FALSE/Not Going Forward text + dropdown, not a native Excel checkbox — user will convert manually if wanted.

Validated before delivery: zip-integrity check passed, all 27 images confirmed present on reload, and the file opens cleanly via Excel COM (no repair prompt) — same corruption check applied after the Internal COC incident (see `internal_COC/VERSION_LOG.md`, 2026-08-03).

Reference checked before building: an older reference file, `Ultimate COC Copy.xlsx` (001_inbox branch, from the "888 Cabana Lobby" project), has its own SHD tab using a rolling dated-status-letter log (A/B/C/S/T/O per date column) instead of remarks tracking — deliberately not adopted; this tracker is a remarks-first design instead, per user's explicit preference.
