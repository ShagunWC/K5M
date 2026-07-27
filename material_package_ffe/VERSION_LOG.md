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

### V3 — 2026-07-27, restructure per user review
Based on the client's direct review:
- **Split into two tabs in one workbook: "Hard Materials" (12 rows) and "Fabrics" (9 rows).** Same workbook, not separate files, per user preference.
- **Consolidated to one row per material** (was one row per material-per-item-application, 27 rows total). The former "Item Code (WDCO)" column is now **"Applicable Item Code(s) (WDCO)"** — a comma-separated list of every product code that material applies to. Sourcing confirmed directly in the subtitle of each tab: this mapping comes from the FF&E material list PDF (`LISTE DES MATÉRIAUX MOBILIER`) + individual FF&E item shop drawings, cross-referenced in `002_knowledge-bank/materials/T1B1_material_cross_reference.md` — never from DD-100, which is Fit-out only.
- **Removed Finish Type / Base Colour / Applied Process columns** (only `FFE-ME-02` was a genuine compound case) — that detail now lives in `FFE-ME-02`'s Remarks instead of three mostly-empty dedicated columns.
- **Finish/Varnish translated:** a new visible "Finish/Varnish (EN)" column is now the primary one; the original French ("Finish/Vernis (FR)") is kept but hidden — unhide if needed for client-facing French communication.
- **Status column now colored via conditional formatting** matching the legend (same fix as Fitout: differential-format fills need `bgColor` set, not just `fgColor`, or the color silently doesn't render).
- **Remarks cleaned** — dropped restatements of which furniture piece each row was for (e.g. "Bedside table legs", "Headboard frame"); that's now covered by the Item Code(s) column, so Remarks only carries genuinely new information (sourcing status, substitutions, open decisions).
- **Category column made sortable** — AutoFilter added to both tabs' header row.
- **Fabric thumbnails extracted** from Victoire's 21 Jul 2026 global soft-materials list PDF (`LISTING GLOBAL MATERIAUX SOUPLES`) and supplier technical data sheets, matched by fabric code.
- **`FA-04` gap fixed:** added as a new row in Fabrics (Anubis, col. 203, Les Créations de la Maison) with its real supplier TDS photo. No WDCO item code is assigned yet since its banquette moved to Fit-out scope (tracked under Fitout's `A-WD-02c`) — flagged in Remarks for the team to resolve.
- **Fixed a High-Res Available inconsistency found during this pass:** `PP-01` (Samuel & Sons trim) was marked "Y" despite never having had an actual image — corrected to "N", since a listing-table PDF crop (now added as its thumbnail) isn't true high-resolution supplier photography, matching the standard applied on the Fitout sheet.
- Two newly-discovered soft-material codes from the Victoire PDF (`FA-05`, `FA-08` — banquette decorative cushions, and `RU-01` — bedside rug) were **not** added; they weren't previously tracked in either Material Package and adding them wasn't part of this review pass. Flagged here for a future pass.

This file is now visually verified (rendered to PDF and inspected) as clean.

### V4 — 2026-07-27, styling lock-in + content review
This file is being moved to OneDrive after this pass; formatting is now considered locked — future updates should be data-entry only (Status, Remarks, new rows), not structural changes.
- **Anonymized:** removed all design-team/client real names from cell content — replaced with generic references (e.g. "the design team"). Supplier/brand names (Elitis, Naturtex, Dedar, etc.) are kept, since those are sourcing information, not client/design-team identity.
- **Font locked to Lato, size 11, everywhere** — titles, headers, body, and notes. No more Playfair Display or mixed sizes.
- **Borders switched to solid black** (previously thin tan/rose).
- **Removed the "Description (FR)" column** from both tabs.
- **Fabrics tab:** removed the Finish/Varnish columns entirely (only `FA-02` ever had finish info — folded into its Remarks instead). Hard Materials tab keeps "Finish/Vernis (FR)" as a hidden column.
- **Added `PP-03`** to the Fabrics tab — a fabric swatch noted in the design team's shop drawings for `K5M-T1B1-CHA-TL-01`, with no material-list code assigned yet.
- **`FA-04`** now also has its own row on the Fitout Fabrics tab (new this pass), since its banquette is Fit-out scope — kept here too rather than removed, per direct user confirmation.

Design decisions behind this layout are recorded in `main/DAILY_LOG.md`, 2026-07-27 entries.
