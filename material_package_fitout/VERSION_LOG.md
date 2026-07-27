# material_package_fitout — Version Log

Current file: `260727_K5M_Material Package_Fitout.xlsx`

## V1 — 2026-07-27
First version. One row per material (24 rows) — all its DD-100-sourced locations listed together in a single cell, with any localization still under scrutiny (matching an open FM-series RFI item) underlined in red rather than force-resolved. Localization is sourced from DD-100 only, per G&B's 23 Jul confirmation that drawings govern over the BOQ where they conflict — the user will re-raise underlined items directly with Adil rather than have this sheet assume an answer. Same status legend/color caveat as the FFE sheet. Compound-finish columns dropped (only one material, `A-ME-02i`, is a genuine base-colour-plus-process case — noted in its Remarks instead of dedicated columns). Supplier column omitted — Fit-out materials are sourced through Wood Couture's own supply chain, not per-material external suppliers like FFE fabrics.

### V1 revision, same day — formatting fix pass
Same font/row-height bug as the FFE sheet, same fix (Cambria/Calibri, explicit computed row heights). Status defaulted to `T` for every row. Status and weekly-log date headers rotated 90°, matching the reference Ultimate COC. Thumbnails **not yet added here** — unlike FFE, Fit-out material photos live embedded inside multi-material table PDFs (the architectural material lists), and matching each embedded image to its correct row programmatically is a more involved extraction pass than the FFE fabric PDFs. Left for a follow-up rather than guessing at image-to-material matches.

Design decisions behind this layout are recorded in `main/DAILY_LOG.md`, 2026-07-27 entries.
