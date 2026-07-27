# material_package_ffe — Version Log

Current file: `260727_K5M_Material Package_FFE.xlsx`

## V1 — 2026-07-27
First version. One row per material-per-item-application (27 rows), status legend/colors per Wood Couture Brand DNA (with two colors — "Approved with comments" and "Submitted" — proposed as an unofficial extension since Brand DNA only defines 5 of Ultimate COC's 6 status categories; confirm or replace). Weekly status log pre-built for 2026-07-27 through 2026-08-24 (5 columns). Materials not used in any K5M FFE product excluded from the working list (see note at the bottom of the sheet) but remain fully documented in `002_knowledge-bank/materials/T1B1_material_cross_reference.md`. Item codes use the corrected `K5M-T1B1-[Area]-[Type]-[##]` WDCO scheme agreed 2026-07-27 (see `DAILY_LOG.md` on `main`). Status column intentionally left blank — current approval state is a judgment call for the project team, not something to assume.

### V1 revision, same day — formatting fix pass
Initial V1 render was unreadable: Playfair Display/Lato aren't installed on the review machine, so Excel silently substituted fonts, and row heights weren't explicitly set, producing broken wrapped-text rows. Fixed by switching to Cambria (headers)/Calibri (body) — both ship with Windows/Office — and computing row height explicitly per row instead of relying on Excel's auto-sizing. Also: embedded actual thumbnail photos (floating images, not the modern "Place in Cell" type — that's Excel-UI-only and can't be scripted) for every material with a sourced image, including several pulled directly out of supplier PDF technical data sheets; Status column defaulted to `T` (To be Submitted) for every row as an explicit starting point rather than left blank; Status and the 5 weekly-log date headers rotated 90° (matching the reference Ultimate COC) so those columns could go much narrower.

**Known gap found during this pass:** `FA-04` (Anubis fabric, for the banquette/`WC-SE-01`) has no row in either the FFE or Fit-out Material Package — the banquette moved to Fit-out scope but its fabric code never got carried over. Not yet fixed.

### V2 — 2026-07-27, real formatting fix
The Cambria/Calibri switch above was a misdiagnosis. The user shared a reference file (`261707_K5M_SHD_Client Remark Tracker.xlsx`) that uses Playfair Display/Lato — the exact fonts already in use here — and is exactly the standard being asked for, proving font substitution was never the actual problem. The real cause was row height: per-row computed heights broke as soon as wrapped text didn't match the estimate. Fixed by reverting to Playfair Display (titles/headers) / Lato (body) and applying one uniform, generously tall row height (88pt) to every row regardless of content, matching the reference file exactly.

Also fixed a separate, more serious bug caught only by visually rendering the sheet (Excel COM automation → PDF export, then reading the PDF): 13 of 15 thumbnail images were silently failing to embed and leaking `[image failed to embed: ...]` text into the Remarks column. Root cause — the image paths pointed into the git repo's `001_inbox`-only working tree, which isn't present on disk once a different branch is checked out. Fixed by copying all source images to a stable, branch-independent location (`material_images/Valentine_Pictures`, `material_images/Fabric_Suppliers`) and removing the try/except so any future embedding failure surfaces loudly at build time instead of corrupting a cell.

This file is now visually verified (rendered to PDF and inspected) as clean: all 15 sourced thumbnails load, uniform readable row heights, rotated Status/date headers, Status defaulted to `T` for every row.

Design decisions behind this layout are recorded in `main/DAILY_LOG.md`, 2026-07-27 entries.
