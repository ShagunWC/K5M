# K5M — Hard Rules

Every rule below is a standing constraint, not a one-off preference — apply it without being reminded, in every branch, every session. Where a rule has its own detailed doc, this entry is the pointer; don't let the detail file drift from what's stated here.

---

1. **Never name the client or the supplier.** Refer to the project only as **K5M**; refer to the supplier/production company only as **"Production Partner."** No real company name, brand name, or identifying detail in any document, filename, sheet, or communication draft, in any branch.
   → `SECURITY_PROTOCOL.md`, `CONTACT_SHEET.md` (real names + required generic terms — internal only, never copy into a client/supplier-facing document).

2. **Umbrella Task values are always written in full, everywhere. No abbreviations, ever.** The only permitted shorthand is **"UTSK"**, and only as shorthand for the term "Umbrella Task" itself — never for any specific value.
   → `Umbrella_Tasks.md` (`006_task-management-pm`) for the full list of 13.

3. **Never force-kill Excel or PowerPoint** (`Stop-Process -Force` on EXCEL/POWERPNT) to clear a stray COM automation instance. It kills every process of that name indiscriminately, including Shagun's own open, unsaved work. If a COM script hits a conflict, ask her to close it herself — never silently force-kill.

4. **`#totalcheck` only runs when explicitly asked.** Never run it automatically at end of day or on any other trigger.
   → `COMMAND_CENTER.md` for the full checklist.

5. **Don't build ahead on the COC.** Build one tab at a time, only when explicitly directed to build that specific tab. No anticipatory work on tabs not yet requested.

6. **Desktop holds only files actively "in motion,"** not an archive of every tracker ever built. Never proactively delete anything from Desktop — that cleanup is Shagun's call, on her own schedule.

7. **Shagun's stated calendar is authoritative.** If she states a date (e.g. "today is the 29th"), treat it as ground truth for that conversation, even if it appears inconsistent with other tracked dates. Never "correct" her stated dates.

8. **Task Tracker S.No.: Claude assigns the number, Shagun handles the grouping.** Sequential whole numbers (1, 2, 3...) per task, assigned by Claude. Letter-suffix grouping for interdependent tasks (1.a, 1.b...) is Shagun's own call to make later — don't attempt to resolve interdependency sequencing.

9. **No "Owner" column on the Task Tracker.** Shagun is always the default owner; it isn't tracked per row.

10. **Material Package styling is frozen: Lato, size 11, black borders.** No further formatting changes without explicit new direction.

11. **Ambiguous details on `#newtask` / `#projectdevelopment` entries — ask, don't guess.** Category, evidence link, Umbrella Task tagging, or any other unclear specific: ask rather than assume or leave silently blank.

12. **Visually verify every Excel/PowerPoint output before calling it done.** Render to PDF via COM (`excel_to_pdf.py` / `pptx_to_pdf.py`) and read it back — don't rely on code review of the generation script alone.

13. **Never start building a deliverable directly.** First confirm everything is aligned — context, materials, understanding of what's wanted — by asking questions if anything is unclear. Only begin the actual build once **`#execute`** is explicitly given.
   → `COMMAND_CENTER.md` for `#execute`.

14. **FFE project scope: `260724_WDCOK5M_FFE_Master SKU List.xlsx`** (OneDrive, `00_SHARED/Project Scope`) **is the canonical source.** Whenever a tracker needs FFE scope/WDCO item codes, pull from this file — not from the COC, Material Package, or any other copy. WDCO codes use `CHA` (not `CH`) for the Chamber area token; "Temporary WCI Code" is retired, WDCO Code is now the only code that matters.
   **Fitout scope base file is not yet decided** — expected to be confirmed the week of 2026-08-03; add its own entry here once confirmed, don't assume it's the same file or convention as FFE.

15. **Any COM automation script touching Excel/PowerPoint/Word must use `win32com.client.DispatchEx`, never bare `Dispatch`.** `Dispatch` attaches to an already-running instance if one exists (e.g. Shagun's own open window) — the script's own cleanup `Quit()` then closes her whole session, same failure mode as force-killing the process, just via a "graceful" call instead of `-Force`. `DispatchEx` always starts an independent process, so `Quit()` only ever closes what the script itself opened.

16. **The COC is the main/master material tracker.** Shagun works on it directly with Claude. The client-facing and supplier-facing Material Package trackers are downstream copies — updated *from* the COC, not the other way around. What exactly flows into each downstream file is decided case by case, not automatically mirrored.

---

## Amendments

Add new rules below with a date, rather than editing the numbered list above unless a rule is being corrected.

**2026-07-31:** introduced **`#hardrule`** as the trigger phrase for adding a new entry to this file — "#hardrule: <text>" appends it to the numbered list above with today's date noted here. This is the same mechanism as `#newtask` for the Task Tracker, but for this guardrail list. Rule 13 (the `#execute` gate) was added via this mechanism.

**2026-07-31:** added rule 14 (FFE canonical scope file, per Task Tracker row 28) and rule 15 (`DispatchEx` requirement, after `Dispatch` closed Shagun's own open Excel session a second time via a different mechanism than the original force-kill incident).

**2026-08-03:** added rule 16 (COC as main/master tracker, client/supplier-facing files downstream) — this reverses the direction data had been flowing until now (COC was pulling from the supplier-facing Material Package).
