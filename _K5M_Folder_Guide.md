> ⚠ **CODEWORD-GATED FILE.** Do not open, quote, or summarize any content below unless the current request explicitly includes the codeword "Mad Max Fury Road." See `SECURITY_PROTOCOL.md` (this branch), Amendments, 2026-08-07. This is a deliberate, explicit exception to Rules 1-2 of that protocol — it contains real names.

---

# K5M Project Folder — Orientation Guide

**Start here if you're new to this project.** This file explains what K5M is and where everything in the OneDrive folder lives. Maintained via `#checkonedriveproject` (see `COMMAND_CENTER.md`, main branch) — re-run periodically, roughly weekly, to keep this current. Last generated/reviewed: **2026-08-07**.

A companion, project-agnostic version of this structure (without the real names/numbers below) lives at `005_project-discovery/OneDrive_Project_Folder_Structure.md` — use that as the starting template for a *new* project's OneDrive folder.

---

## What K5M is

**K5M** is Wood Couture's internal project code for the **Park Hyatt Casablanca** renovation — a 165-key, 11-floor, 7-room-typology hotel guestroom + public-area renovation, interior design by **Gilles & Boissier** (Paris), owner's rep **Interdec Maroc SA**. Wood Couture is contracted as FF&E (Furniture, Fixtures & Equipment) and Fit-out (joinery/stone/millwork) contractor.

What's live right now is a single **T1B1 mock-up room** — a proof-of-concept phase before a much larger multi-year phased rollout across the whole hotel. A T2B2 pricing template already exists for the next room type, unpriced, awaiting the mock-up outcome.

**Commercial basis** (as of the 6 Jul 2026 provisional confirmation — not yet final, pending mock-up evaluation): awarded T1B1+T2B2 package ~$261,550 including shipping. Payment terms 50/20/20/10 (deposit / pre-shipping / on-site arrival / installation).

**Key dates:** mock-up room must be complete and ready for client approval — currently targeting **20 December 2026** (slipped once from an original 30 November target, driven by the design team's August unavailability).

## People

| Name | Organization | Role |
|---|---|---|
| Paolo Della Casa | Wood Couture | CEO |
| Filippo Sona | Wood Couture | Co-Chairman / CCO |
| Shagun Gupta | Wood Couture | Project Manager, K5M |
| Claire Padilla | Wood Couture | Director of China Operations |
| Restituto "Rusti" Pammit Jr | Wood Couture | Technical Head |
| Rahul Venugopal, Fabrizio Pensalfini, Khamille De Leon | Wood Couture | Project team |
| Cathy Yang | Wood Couture | China-side production liaison |
| "Arlene" | Wood Couture (China office, presumed) | Recurring material/swatch feedback contributor — role/email not yet documented anywhere; worth confirming and adding to `CONTACT_SHEET.md` |
| Ahamad Musharraff | Wood Couture | Project Coordinator (Colombo) |
| Victoire Gonnord, Valentine Jenn, Marie-Alix Perles | Gilles & Boissier | Design team |
| Adil Mokaddem | Independent | Executive Architect |
| Abdellatif Menbar | Interdec Maroc SA | Director of Engineering (client-side) |
| Wadiaa Benazzouz, Nasser Kabbaj, Omar Kabbaj, Mounir Mouhib | Interdec Maroc SA | Owner's PM/engineering team |
| Gisela Steiger | Autentico | Lighting design consultant |
| Sophia Wu, Alfred (alfredli0817@163.com) | H&T Furnishings | Production partner — Alfred is primary POC |
| Ariel Comoylao | External | Shop-drawing drafting vendor |
| Justin Meath Baker | Hyatt | Director Interior Design EMEA — referral source for this project |

## Folder structure — what's where (OneDrive: `Wood Couture - Live Projects_SL\K5M`)

```
K5M/
├── 00_SHARED/ — cross-functional working trackers (client + internal use)
│   ├── General/ — kickoff MOM, RFI/spec duplicates
│   ├── Project Scope/ — Fitout BOQ, FFE Master SKU List
│   ├── Project Schedule/ — schedule revisions
│   ├── RFI/ — Client Facing RFI Tracker (FFE/Fitout/Lighting tabs)
│   ├── Hard Materials and Fabric/ — client-facing Material Package trackers + Fit-Out Material Compare
│   └── Shop Drawings/ — Client Remark Tracker + REV00 markups
│
├── 01_INTERNAL/ — organized by person (Claire / Musharraf / Shagun), not function
│   ├── Claire/ — kickoff meeting record
│   ├── Musharraf/ — RFI drafting, mockup schedule, Morocco fit-out subcontractor sourcing
│   └── Shagun/ — prep materials, AI-assistant chat log exports, stone reference images, a working COC copy
│
├── 02_COMMERCIAL/ — pricing, proposals, RFQs, BOQs
│   ├── BOQ/, Pricing Comparison_Mockup/, Project Awarded/, Proposals/(From_Supplier + To_Supplier)/
│
├── 03_TECHNICAL/ — the technical backbone
│   ├── 001_COC/ — the Internal Central COC (current) + Archive
│   ├── 002_Specifications/ — G&B DD-100 packages, per-item FFE spec sheets
│   ├── 003_Materials/ — material lists, fabric tracker, client-facing material package
│   ├── 004_Internal WC_RFI Clarifications/ — RFI-against-BOQ log
│   ├── 005_Shop Drawings/ — SHD lifecycle + raw AutoCAD working files
│   └── 007_Project Scope/ — stone-arch BOQ reconciliation work
│
├── 04_SHIPPING/ — currently empty
├── 05_REPORTS/ — currently empty
├── 06_SUPPLIERS/ — H&T Furnishings collaboration hub (process docs, material packages, communications)
└── 07_ACTONA/ — a single alternate-vendor proposal, currently orphaned/no follow-up logged
```

See `_K5M_File_Index.xlsx` (OneDrive root — not codeword-gated, no real names beyond file paths) for the actual current file-by-file listing, tagged by Umbrella Task where determinable.

## Known open items (as of 2026-08-07)

- Three parallel item-coding schemes in live use for the same products (client code / WDCO code / bare T1B1 code).
- Project code has ≥4 variants in circulation (K5M-101, KM05-101, K53-101, PHC-101).
- Every material/fabric/SHD status field is stuck at "To Be Submitted" despite real progress in remarks columns.
- 12 Fit-Out Material RFIs open 2+ weeks with no logged response.
- Multiple COC-named files exist in parallel (`03_TECHNICAL/001_COC/`, `01_INTERNAL/Shagun/20260807_Prep/KM05101-COC.xlsx`, and the git repo's own COC) — worth confirming which is canonical.
- `07_ACTONA` — unclear if this vendor thread is closed or just unlogged.

Full detail on these and further findings: ask Claude for the 2026-08-07 OneDrive study, or run `#checkonedriveproject` for a fresh pass. Both require the codeword to surface anything from this specific file, per the gate above — the underlying research (agent reports) is not itself gated, only this document is.
