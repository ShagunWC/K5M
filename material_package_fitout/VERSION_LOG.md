# material_package_fitout — Version Log

Current file: `260727_K5M_Material Package_Fitout.xlsx`

## V1 — 2026-07-27
First version. One row per material (24 rows) — all its DD-100-sourced locations listed together in a single cell, with any localization still under scrutiny (matching an open FM-series RFI item) underlined in red rather than force-resolved. Localization is sourced from DD-100 only, per G&B's 23 Jul confirmation that drawings govern over the BOQ where they conflict — the user will re-raise underlined items directly with Adil rather than have this sheet assume an answer. Same status legend/color caveat as the FFE sheet. Compound-finish columns dropped (only one material, `A-ME-02i`, is a genuine base-colour-plus-process case — noted in its Remarks instead of dedicated columns). Supplier column omitted — Fit-out materials are sourced through Wood Couture's own supply chain, not per-material external suppliers like FFE fabrics.

### V1 revision, same day — formatting fix pass
Same font/row-height bug as the FFE sheet, same fix (Cambria/Calibri, explicit computed row heights). Status defaulted to `T` for every row. Status and weekly-log date headers rotated 90°, matching the reference Ultimate COC. Thumbnails **not yet added here** — unlike FFE, Fit-out material photos live embedded inside multi-material table PDFs (the architectural material lists), and matching each embedded image to its correct row programmatically is a more involved extraction pass than the FFE fabric PDFs. Left for a follow-up rather than guessing at image-to-material matches.

### V2 — 2026-07-27, real formatting fix + rich-text bug + thumbnails
Font/row-height fix corrected the same way as FFE (Playfair Display/Lato restored, uniform 150pt row height — taller than FFE's 88pt since Localization/Remarks content runs longer here).

**Severe bug found and fixed:** the Localization column (this sheet's core feature — showing every DD-100 location per material with unresolved items underlined in red) was rendering as only a single stray character per row when opened in Excel. Root cause: the rich-text `InlineFont` was built with `sz=1000`, which Excel reads as a literal 1000-point font size (not "10.00pt" as assumed) — every character rendered as a full-page-sized glyph, of which only a sliver was visible in the cell. Fixed by changing `sz=1000` to `sz=11` for both the normal and underlined-red inline fonts. Confirmed via Excel COM → PDF export: all 24 rows now show full, correctly-underlined Localization text.

Thumbnails added: extracted directly from the source `Fitout - 20260721_GB_PHC_CHAMBRES-ETAGE01-T1B1-MUR-LISTE DES MATERIAUX (Victoire update).pdf` (the architectural "LISTE DES MATERIAUX" table), matching each material CODE to its PHOTO-column cell by position and rendering that cell region to a cropped PNG (bypasses ambiguity from stacked/duplicate image layers in the PDF). Where a code appeared twice — an original material plus its "Remplacé par" substitution — the later (replacement) occurrence's photo was used, matching what this sheet's Description/Remarks already say. 21 of 24 rows now have a thumbnail; the remaining 3 (`A-WD-01d`, `A-GL-04a`, `A-CA-01`) have no source photo available in any document reviewed, consistent with their existing Remarks.

This file is now visually verified (rendered to PDF and inspected) as clean.

Design decisions behind this layout are recorded in `main/DAILY_LOG.md`, 2026-07-27 entries.
