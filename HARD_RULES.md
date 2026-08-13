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

8. **Task Tracker Task Number (renamed from "S.No." on 2026-08-07): Claude assigns the number, Shagun handles the grouping.** Sequential whole numbers (1, 2, 3...) per task, assigned by Claude. Letter-suffix grouping for interdependent tasks (1.a, 1.b...) is Shagun's own call to make later — don't attempt to resolve interdependency sequencing. Task Number also doubles as the connecting key for the planned Task Tracker/Calendar merge (see `COMMAND_CENTER.md` context / Task Tracker row on that merge).

9. **No "Owner" column on the Task Tracker.** Shagun is always the default owner; it isn't tracked per row.

10. **Material Package styling is frozen: Lato, size 11, black borders.** No further formatting changes without explicit new direction.

11. **Ambiguous details on `#newtask` / `#projectdevelopment` entries — ask, don't guess.** Category, evidence link, Umbrella Task tagging, or any other unclear specific: ask rather than assume or leave silently blank.

12. **Visually verify every Excel/PowerPoint output before calling it done.** Render to PDF via COM (`excel_to_pdf.py` / `pptx_to_pdf.py`) and read it back — don't rely on code review of the generation script alone.

13. **Never start building a deliverable directly.** First confirm everything is aligned — context, materials, understanding of what's wanted — by asking questions if anything is unclear. Only begin the actual build once **`#execute`** is explicitly given.
   → `COMMAND_CENTER.md` for `#execute`.

14. **FFE project scope: `260724_WDCOK5M_FFE_Master SKU List.xlsx`** (OneDrive, `00_SHARED/Project Scope`) **is the canonical source.** Whenever a tracker needs FFE scope/WDCO item codes, pull from this file — not from the COC, Material Package, or any other copy. WDCO codes use `CHA` (not `CH`) for the Chamber area token; "Temporary WCI Code" is retired, WDCO Code is now the only code that matters.
   **Fitout scope base file is not yet decided** — expected to be confirmed the week of 2026-08-03; add its own entry here once confirmed, don't assume it's the same file or convention as FFE.

15. **Any COM automation script touching Excel/PowerPoint/Word must use `win32com.client.DispatchEx`, never bare `Dispatch`.** `Dispatch` attaches to an already-running instance if one exists (e.g. Shagun's own open window) — the script's own cleanup `Quit()` then closes her whole session, same failure mode as force-killing the process, just via a "graceful" call instead of `-Force`. `DispatchEx` always starts an independent process, so `Quit()` only ever closes what the script itself opened.
   → `WDCO_MICROSOFT365_NOTES.md` for the fuller set of COM/Microsoft 365-specific gotchas learned since (OneDrive file locks, in-cell images, clipboard fragility, PowerPoint export quirks).

16. **The COC is the main/master material tracker.** Shagun works on it directly with Claude. The client-facing and supplier-facing Material Package trackers are downstream copies — updated *from* the COC, not the other way around. What exactly flows into each downstream file is decided case by case, not automatically mirrored.

17. **Any Excel file that gets a structural edit (column/row insert or delete, image added, outline/grouping applied) must be validated before it's delivered — on a scratch copy first, never on the live Desktop/git file directly.** Validation = a zip-integrity check (`zipfile.testzip()`), an image/anchor-count check if images are involved, and a clean Excel COM open (no repair prompt) — not just a visual PDF render. Only copy over the live file once the scratch copy passes all of these.

18. **Excel COM's `Columns.Insert()` / `Rows.Insert()` auto-expands adjacent data validation ranges into the newly inserted column, and can corrupt a merged range if the insertion point falls inside it.** Always: (a) re-check and re-scope data validation ranges after any column/row insert near one, and (b) unmerge any merged range the insertion point falls inside *before* inserting, then re-merge over the correct new span afterward — never insert into a live merge and hope it shifts correctly.

19. **When copying an image into a new location in a workbook (not just preserving an existing one), compress/resize it — don't reuse the full-resolution original.** Duplicating full-resolution images doubles a file's embedded-image weight for no display benefit; this is the same root cause already flagged as a risk on the 36MB COC.

20. **Never write directly to a OneDrive-synced file.** When a task requires editing a file that lives on OneDrive, copy it to the Desktop first and do all work there. Once Shagun confirms the Desktop version is final, she moves it to OneDrive herself — that move is not Claude's job. This is a hard requirement now, not just a preference: live COM automation against a OneDrive-synced file has repeatedly failed unpredictably (leaving orphaned Excel processes), while the identical script worked instantly against a local Desktop copy every time.
   → `WDCO_MICROSOFT365_NOTES.md` §1 for why this happens.

21. **When Shagun says "give me a PDF," always ask first which kind she means: a straight export of what's on screen, or a printable version (fixed paper size, single page, print-optimized layout)?** These are genuinely different jobs, not two flavors of the same export. A screen export is fast — render what exists as-is. A printable version means fitting an on-screen (usually responsive) layout into a hard page-size constraint it wasn't designed against, which is closer to a print-layout redesign: it takes real iteration (shrink → regenerate → measure the exact overflow → repeat), because there's no "shrink to fit one page" feature in headless PDF export. Don't guess which one is wanted and don't default to either — the two have very different time costs, and guessing wrong means redoing the work.

---

## Amendments

Add new rules below with a date, rather than editing the numbered list above unless a rule is being corrected.

**2026-07-31:** introduced **`#hardrule`** as the trigger phrase for adding a new entry to this file — "#hardrule: <text>" appends it to the numbered list above with today's date noted here. This is the same mechanism as `#newtask` for the Task Tracker, but for this guardrail list. Rule 13 (the `#execute` gate) was added via this mechanism.

**2026-07-31:** added rule 14 (FFE canonical scope file, per Task Tracker row 28) and rule 15 (`DispatchEx` requirement, after `Dispatch` closed Shagun's own open Excel session a second time via a different mechanism than the original force-kill incident).

**2026-08-03:** added rule 16 (COC as main/master tracker, client/supplier-facing files downstream) — this reverses the direction data had been flowing until now (COC was pulling from the supplier-facing Material Package).

**2026-08-04:** added rules 17-19 while building the Shop Drawing Tracker: scratch-copy-first validation for any structurally-edited Excel file (zip test + image check + clean COM open, not just a PDF render), the Excel COM column-insert gotcha (validation ranges auto-expand into new adjacent columns, merges can be corrupted if the insert point falls inside them), and compressing images before duplicating them into a new location rather than reusing full-resolution originals.

**2026-08-07:** rule 8 updated — Task Tracker's "S.No." column renamed to "Task Number," since it's about to double as the connecting key for the planned Task Tracker/Calendar merge (hyperlinks one way, a "Logged on Calendar?" cross-check the other).

**2026-08-11:** added rule 20 (never write directly to OneDrive files) — prompted by four consecutive failed COM automation attempts against the live `260727_K5M_Material Package_Fitout.xlsx` (each leaving an orphaned Excel process), resolved only once Shagun provided a Desktop copy to work from instead.

**2026-08-13:** added rule 21 (always ask "screen export or printable?" for a PDF request) — prompted by a Project Coordinator onboarding mind map that took much longer than expected to turn into a PDF: the first ask was assumed to be a simple screen export, but what was actually wanted was a single-page, print-ready A3 landscape layout, which needed real iterative redesign (shrinking content, hunting down a print-pagination gotcha where flex/grid blocks jump to the next page whole rather than partially overflowing) rather than a straight render.
