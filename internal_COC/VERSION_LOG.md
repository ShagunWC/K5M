# internal_COC — Version Log

Newest entry at the top.

---

## 2026-07-28 — `260728_K5M_Internal COC_FFE.xlsx` — V1
First version of the FFE COC, built from scratch (not carried over from the old SharePoint COC files, which were confirmed to be an empty shell). Five sheets: **Data** (Master Scope, from the FFE Master SKU List v2 — all 26 BOQ rows kept including Fit-out-moved and cancelled items, flagged via Status/Remark, CH corrected to CHA), **Hard Material** and **Fabrics** (unchanged from the 27 July Material Package build), **Shop Drawings** (17 FFE-scope items with an assigned code; WDCO Code + Item Description pre-filled, rest left blank for manual fill; tap-through hyperlink to the Data sheet), **Change Log** (empty, ready for use).

A large feedback round was received the same day on Data/Hard Material/Fabrics/SHD — not yet incorporated, several open questions pending. See `006_task-management-pm/260728_Task_List.md` for the open items.

Note: this file is ~36MB, almost entirely from full-resolution images embedded as thumbnails (display size is scaled down but the underlying embedded file isn't compressed/resized first) — worth revisiting before this grows much further, especially once a dedicated image folder is added.

*Prior history (V01–V04) existed in the old `ShagunWC/K5M_FFE-_COC-_Management` repo, branch `building-COC-Version-00`; this repo is a clean start and does not carry that file history forward. See `main/DAILY_LOG.md` entry for 2026-07-24.*
