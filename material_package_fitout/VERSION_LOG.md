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

### V2 revision, same day — user review pass
Based on the client's direct review of this sheet:
- **Removed paint, wallpaper, and carpet entirely** (`A-PT-01`, `A-PT-02`, `A-WP-01`, `A-WP-02`, `A-CA-01`) — confirmed out of Wood Couture's Fit-out scope. Down from 24 to 19 rows; the removed codes are listed in an EXCLUDED footnote at the bottom of the sheet rather than silently dropped.
- **Fixed High-Res Available (Y/N):** several rows incorrectly said "Y" — the only images we have for this sheet are low-resolution crops pulled from a PDF, not true high-resolution photography. All rows now correctly say "N".
- **Localization column fully translated to English** — it previously mixed French location nouns (Entrée, SDB, Chambre, seuil, arche, plinthe, etc., carried over verbatim from the source PDF) with English sentence structure. Now fully English (Entrance/Bathroom/Bedroom/threshold/arch/baseboard/etc.).
- **Localization column header now explicitly cites its source and date:** "Localization per DD-100, dated 21.07.2026" — this sheet's Localization has only ever come from the DD-100-tagged material list (dated 21.07.2026 per that document's own footer), never from the BOQ or from Victoire's separate global soft-materials list. BOQ mentions inside Localization/Remarks text are conflict flags only, never the source of a location.
- **Added a disclaimer note:** FM-001–FM-012 (used throughout Localization/Remarks) are internal cross-references I created myself while reconciling the BOQ/DD-100/material-list versions — confirmed (via a full repo search across every branch, RFI logs, emails, and source PDFs) that they do not correspond to any real RFI numbering system. Not fixed/relabeled per user's choice, but now disclosed directly on the sheet.
- **Samples not needed where scope is unconfirmed:** for `A-ST-03c / A-ST-06c` and `A-WD-03c` (no confirmed Localization or Applicable Task Code yet), Control Sample and High-Res Available changed from "N" to "N/A", with Remarks noting sample sourcing isn't needed until scope is confirmed with Adil.
- **Status column now colored via conditional formatting** (not just plain text) matching the legend — auto-recolors whenever the Status letter is changed. Required a fix mid-implementation: differential/conditional-format fills read `bgColor`, not `fgColor`, unlike normal cell fills — the color didn't render until both were set.
- **Incidental fix:** the "Total" row and both caveat notes previously collided on the same spreadsheet row (the notes were merged directly on top of the Total row, silently hiding its label and COUNTA formula). Each now has its own row.

### V3 — 2026-07-27, styling lock-in + banquette Fabrics tab
This file is being moved to OneDrive after this pass; formatting is now considered locked — future updates should be data-entry only (Status, Remarks, new rows), not structural changes.
- **Anonymized:** removed all design-team/client real names from cell content — replaced with generic references (e.g. "the design team"). Header text, subtitle, and all remark mentions of specific individuals updated.
- **Font locked to Lato, size 11, everywhere** — no more Playfair Display or mixed sizes.
- **Borders switched to solid black** (previously thin tan/rose).
- **Removed the "Description (FR)" column.**
- **Dropped `A-ST-03c / A-ST-06c` and `A-WD-03c`** entirely (19 → 17 rows) — both had no confirmed DD-100 localization or task code, and the user confirmed removing them rather than keeping them flagged.
- **Updated `A-GL-03a`'s Remarks:** "Have made this panel before — a sample should be produced and included in the same box being presented to the client for approval."
- **Added a new Fabrics tab** — the banquette is Fit-out scope, so its 3 fabrics (`FA-04` upholstery, `FA-05` and `FA-08` decorative cushions) are now tracked here too, each with a real photo. None have a WDCO item code assigned yet.

Design decisions behind this layout are recorded in `main/DAILY_LOG.md`, 2026-07-27 entries.
