# 002_knowledge-bank

Read `SECURITY_PROTOCOL.md` on the `main` branch before adding or naming anything here.

## Purpose

This branch holds the common threads shared by every downstream tracker and audience-facing output — the working, processed content that `003_trackers`, `004_communication`, and eventually a client tracker all draw from. Content is segregated by subject, not by audience.

## Subfolders

- `materials/` — material codes, specifications, finishes, supplier reference sheets, control-sample status
- `shop_drawings/` — shop drawing files and revision history by product/scope line
- `inspection_reports/` — QC/inspection records
- `logistics/` — shipping, customs, delivery schedule data
- `commercial/` — cost, contract, and commercial reference data (subject to `SECURITY_PROTOCOL.md` — no client or supplier names)

## Relationship to `001_inbox`

Content here is the processed/translated version of raw files in `001_inbox`. When adding something here, it's fine (and encouraged) to note which inbox file it was derived from, so the evidence trail is traceable in both directions.
