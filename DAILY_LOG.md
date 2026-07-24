# Daily Log

Newest entry at the top. One entry per day, added by whoever (or whichever LLM session) did the work.

---

## 2026-07-24
Repo structure designed and agreed: 7 branches (`main`, `001_inbox`, `002_knowledge-bank`, `003_trackers`, `004_communication`, `005_project-discovery`, `006_task-management-pm`). Folder numbering, tracker file-naming convention (`YYMMDD_ProjectCode_Category_SpecificName`), and the security protocol (project code only, "Production Partner" only, brand guidelines) were defined. Decided against migrating the old `building-COC-Version-00` branch content — clean start on this new repo. Scaffolding files (README, SECURITY_PROTOCOL, this log) created for the `main` branch.

Git installed and authenticated (via `gh`) so Claude manages the repo directly going forward — no manual uploads needed. All 7 branches created and pushed live to `github.com/ShagunWC/K5M`. Added `PROJECT_BRIEFING.md` to `main` as a standing catch-up document, since Claude Code's session resume is local to one machine and this project needs to survive a system change. Session ended with the BOQ about to be shared; goal is full project onboarding before any building resumes.

Reviewed, in full: the T1B1 BOQ (FF&E sheet $24,724.89 / 24 lines; Fit-out sheet $122,069.58), all architectural/FF&E/fabric/equipment/hardware material lists, the drawing index, the kick-off-meeting email thread (revealed real stakeholder map: client Park Hyatt Casablanca, designer Gilles & Boissier, owner's rep Interedec Maroc, architect Adil Mokaddem, Production Partner Wood Couture; mock-up deadline 30 Nov 2026), all 14 individual FF&E item drawings, the 57-page Schematic Design set, and the 69-page DD100 detailed drawing set (both via background research agents).

Key findings to act on:
- Bedroom furniture Options A/B (Schematic Design) share identical FF&E codes despite being physically different pieces (headboard, nightstand, console, bedside light). User confirmed **Option A matches the confirmed/priced FF&E** (table lamp, not pendant) — needs a real code fix before these can drive procurement.
- DD100 set has several drafting/QA issues worth raising with G&B: missing GEN-120/GEN-130 sheets, 7 CHAMBRE sheets with a placeholder project name never filled in, 7 CHAMBRE detail sheets mis-stamped with the SDB drawing-number prefix (2 also keep a stale "BANQUETTE" label instead of "TV surround"), an undocumented extra SDB-201 sheet, an unresolved bedroom-cornice "OPTION B" callout, and a bathroom pendant-light quantity still TBC by the lighting designer.
- Discovered a **live SharePoint COC system for K5M**, independent of this repo (`sharepoint_coc_server` connector): `261507_K5M_COC_Fitout.xlsx` and `261307_K5M_COC_FFE.xlsx`, both modified 2026-07-17. The Fitout file's `RFI_Fitout Data` sheet (dated 15.07.2026) appears to match a OneDrive-linked RFI the user shared separately — cross-check still pending, blocked on Microsoft 365 MCP authentication (user needs to run `/mcp`).
- User instructed: stop treating the old `building-COC-Version-00` repo as a reference source at all — it's being deleted. `PROJECT_BRIEFING.md` updated accordingly.
- Open correction pending from user: something in the README's project description ("K5M is a hotel project for Wood Couture... a parallel Fit-out COC is being built") is "not fully correct" — exact fix not yet clarified.
