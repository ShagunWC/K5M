# 003_trackers

Read `SECURITY_PROTOCOL.md` on the `main` branch before adding or naming anything here.

## Purpose

Every Excel workbook we build lives here — one subfolder per tracker.

## File naming convention

`YYMMDD_ProjectCode_Category_SpecificName`

- `SpecificName` is only included when there's more than one variant of the same category in the same folder.
- Examples: `260724_K5M_Internal COC.xlsx`, `260724_K5M_Material Package_Supplier facing.xlsx`

## Versioning

Each tracker keeps:
- A single current file, always the latest date for that category.
- A `versions/` subfolder holding prior dated snapshots — do not overwrite/delete a prior version, add a new dated file instead.
- A `VERSION_LOG.md` describing what changed at each version and why.

## Current subfolders

- `internal_COC/` — the FF&E + Fit-out Control Centre workbook(s), Wood Couture's internal operational view.
- `production_tracker/` — the supplier/production-facing tracker.
- `shop_drawing_tracker/` — the FFE Shop Drawing Tracker (SHD00/SHD01/SHD02 progress, per item).

Add a new subfolder here whenever a new tracker is built (e.g. a future client-facing tracker).
