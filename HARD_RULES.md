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

---

## Amendments

Add new rules below with a date, rather than editing the numbered list above unless a rule is being corrected.

*No amendments yet.*
