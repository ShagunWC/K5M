# K5M — Command Center

Trigger phrases Shagun uses in conversation to fire a standing action. Read this before treating any of these as a one-off — they're standing behavior, not something to re-confirm each time.

---

## `#newtask`

**Says:** "#newtask: <description>"

**Does:** Adds a new row to the K5M Task Tracker (`006_task-management-pm/260730_K5M_Task Tracker.xlsx`, or its OneDrive location once handed off) — Date Raised, the task description in full, and best-guess Umbrella Task (written in full — no abbreviations; "UTSK" is only ever shorthand for the term "Umbrella Task" itself, not for any value)/Priority/Type of Task/Owner/Status, flagged for Shagun to correct. Commit and push immediately.

Superseded the one-file-per-day `YYMMDD_Task_List.md` markdown convention on 2026-07-30 — the Task Tracker is now the single running record.

---

## `#projectdevelopment`

**Says:** "#projectdevelopment — <date> — <category> — <update> — <evidence link>" (category and evidence link are optional per entry)

**Does:**
1. Appends the entry to the "Project Development Log" tab in `260729_K5M_Project Calendar.xlsx` (`006_task-management-pm`).
2. If the update implies an actual schedule change (a date moving, a new milestone, a decision affecting an existing activity), reflects that into the Data tab and the relevant month tab too — not just logged passively.
3. If category or evidence link is left blank, ask rather than guess or leave silently blank.

---

## `#totalcheck`

**Says:** "#totalcheck" (or "do a total check") — only ever run when Shagun explicitly asks, never automatically at end of day without being asked.

**Does, in order:**
1. Confirms every tracker (COC files, Material Packages, Project Calendar, Task Tracker) reflects the latest agreed state — nothing discussed but not yet applied.
2. Asks Shagun for any `#projectdevelopment` updates from today that haven't been logged yet — don't assume everything worth logging was already flagged live during the day.
3. Tags every one of today's `#newtask` entries and Development Log entries with its Umbrella Task, written in full (see `Umbrella_Tasks.md`, same branch — no abbreviations for the values themselves; "UTSK" is only ever shorthand for the term "Umbrella Task") — tagging happens in this end-of-day batch, not live at the moment each entry is created.
4. Confirms the Task Tracker (`260730_K5M_Task Tracker.xlsx` or wherever it currently lives — OneDrive once Shagun hands it off) reflects every task raised today, with Status/Owner/Priority updated for anything that changed during the day.
5. Confirms all of today's file changes are actually pushed to the correct branch in git — nothing sitting locally only.
6. Confirms `DAILY_LOG.md` has today's entry.
7. Reports back: what's clean, what's still open/pending, anything inconsistent found.

---

## `#GoodMorning` / `#ShowMeMyKanban`

**Says:** either phrase — they're interchangeable, same trigger.

**Does:** reads the task-management Excel sheet (`006_task-management-pm`) and generates an up-to-date Kanban view grouped by Status, shown directly in the conversation. This is generated fresh on request, not a live-updating board — ask again any time for a current view.

**Note on automation:** there is no reliable way to have this fire automatically every morning without Shagun asking — the available scheduling tool is session-only (nothing persists to disk, gone when the session ends, capped at 7 days even if kept open) and she starts a fresh session each day. So this trigger firing the moment she opens a session and says "Good morning" *is* the practical version of "automatic."

---

## Amendments

Add new commands below with a date, rather than editing the list above, unless a command's behavior is being corrected.

**2026-07-29:** `#totalcheck` extended to include asking for unlogged project developments and end-of-day Umbrella Task tagging, once the Umbrella Tasks concept was introduced (see `Umbrella_Tasks.md`).

**2026-07-29:** standardized the task-log trigger as `#newtask` (previously used inconsistently as "new task" / "#newtask" / "#new task" — this is now the one form).

**2026-07-30:** added `#GoodMorning` / `#ShowMeMyKanban` once the task-management Excel sheet and Kanban-by-Status concept were agreed.
