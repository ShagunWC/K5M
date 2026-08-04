# K5M — Fit-out BOQ Scope Gap: Stone Arch Study

**Date:** 2026-08-04
**Scope:** Comparing every stone arch physically drawn in the T1B1 DD-100 set (`20260601_DD100_T1B1.pdf`) against what's priced in the Sales Order (K5M-101) and the detailed Fit-out Excel — arch by arch, with single-instance quantities measured directly off the drawings.

## Method

- Every one of the 69 DD-100 pages was rendered and read visually (not text-extracted — these are CAD-exported drawings).
- Each arch's linear-meter (ML) quantity = 2 × (opening height) + 1 × (opening width), using the overall/outer dimension chain printed on the drawing (jamb + jamb + head, no floor threshold — thresholds are priced separately in the BOQ).
- "Qty per Task" = the single physical instance measured from the drawing. "Total Qty" = per-task × confirmed/assumed instance count.

## Final table

| # | Location | Material | Pages | BOQ Row No. / Sales Order Item No. | Drawing No. (per BOQ/Sales Order) | Qty per Proposal (BOQ) | Qty per Task (Woody) | Total Qty (Woody) | Notes / Reconciliation |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Arch to Salle de Bains (Entrée) | A-ST-07a | 2, 8, 20-23 | Not found in BOQ | — | — | 5.31 ML | 5.31 ML (×1) | No traceable BOQ line at all. |
| 2 | Arch to Chambre (Entrée) | A-ST-07a | 2, 8, 20-23 | Not found in BOQ | — | — | 5.31 ML | 5.31 ML (×1) | No traceable BOQ line at all. |
| 3 | Arch over Mini-bar niche | A-ST-07a | 2, 18-19 | Not found in BOQ | — | — | 5.55 ML | 5.55 ML (×1) | No traceable BOQ line at all. |
| 4 | Arch over Dressing/Wardrobe | A-ST-07a | 2, 8, 13-17 | Same as Row 3 | Same as Row 3 | — | Same as Row 3 | Same as Row 3 | Not a separate arch — confirmed the same physical element as Row 3 (the "wardrobe arch" callout is the mini-bar arch's jamb bleeding into the adjacent detail sheet). |
| 5 | Arch over Vasque/Vanity (basin) | A-ST-07a | 24, 30, 36-37 | S.No. 60 / ITEM3350 | `ET01-T1B1-SDB-100` | 9 ML | 5.60 ML | **5.60 × 2 = 11.20 ML** | 2 basins confirmed (S.No. 59, qty 2 in Sales Order). Total (11.20) close to BOQ (9) but not exact. |
| 6 | Arch at Toilet door | A-ST-01c | 24, 30-31, 41-42 | S.No. 55 / ITEM3345 | `ET01-T1B1-SDB-309` | 11 ML | 4.88 ML | **4.88 × 2 = 9.76 ML** *(if 2 toilets — unconfirmed)* | Close to BOQ's 11 ML if a 2-toilet assumption holds, but no confirmed "qty 2" BOQ line backs this the way the basin has. |
| 7 | Arch at Shower door | A-ST-01c (drawn) vs A-ST-07a (priced) | 24, 30-31, 43-44 | S.No. 45 / ITEM3335 | `ET01-T1B1-SDB-312` | 21 ML | 4.88 ML | **4.88 × 1 = 4.88 ML** | Only one shower per room — no multiplier applies. BOQ's 21 ML remains ~4.3× unexplained — genuine flagged discrepancy. Also: drawing shows this arch's material as A-ST-01c, but the BOQ prices it as A-ST-07a — a separate, real material mismatch. |
| 8 | Arch over Banquette (fitted sofa) | A-ST-07a | 53, 58-59, 63-67 | S.No. 67 / ITEM3357 *(tentative match)* | `ET01-T1B1-CHA-120` | 18.6 ML | 5.36 ML | **5.36 × 2 = 10.72 ML** | 2 confirmed physical arches (both ends of the banquette). Match to this specific BOQ line is tentative — the ref code doesn't align with the banquette's own page range in the drawing set. |

## Open items for follow-up

- Rows 1-3: no BOQ line found at all for these three arches (entry-to-bathroom door, entry-to-bedroom door, mini-bar niche) — confirm whether they're priced elsewhere or genuinely missing from scope.
- Row 6: confirm whether there are actually 2 toilets in this room type (would explain the BOQ quantity via the same logic as the basins).
- Row 7: the shower arch discrepancy (21 ML BOQ vs. 4.88 ML single-instance, and a material mismatch) is the most significant unresolved item — worth raising directly with the supplier/design team.
- Row 8: confirm the BOQ line (S.No. 67, `CHA-120`) is actually the right match for the banquette arches, given the page-reference mismatch.

## Supporting materials

Relevant DD-100 page renders and dimension-verification crops are saved alongside this file, in `dd100_pages/` and `verification_crops/`.
