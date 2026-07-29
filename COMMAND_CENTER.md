# K5M — Command Center

Trigger phrases Shagun uses in conversation to fire a standing action. Read this before treating any of these as a one-off — they're standing behavior, not something to re-confirm each time.

---

## `#newtask`

**Says:** "#newtask: <description>"

**Does:** Appends a new numbered entry to today's dated task list on `006_task-management-pm` (`YYMMDD_Task_List.md` — created fresh if today doesn't have one yet). One line per task, no elaboration into prose. Commit and push immediately.

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
1. Confirms every tracker (COC files, Material Packages, Project Calendar) reflects the latest agreed state — nothing discussed but not yet applied.
2. Asks Shagun for any `#projectdevelopment` updates from today that haven't been logged yet — don't assume everything worth logging was already flagged live during the day.
3. Tags every one of today's `#newtask` and Development Log entries with its Umbrella Task code (see `Umbrella_Tasks.md`, same branch) — tagging happens in this end-of-day batch, not live at the moment each entry is created.
4. Confirms all of today's file changes are actually pushed to the correct branch in git — nothing sitting locally only.
5. Confirms today's task list (`006_task-management-pm`) is up to date with everything raised today.
6. Confirms `DAILY_LOG.md` has today's entry.
7. Reports back: what's clean, what's still open/pending, anything inconsistent found.

---

## Amendments

Add new commands below with a date, rather than editing the list above, unless a command's behavior is being corrected.

**2026-07-29:** `#totalcheck` extended to include asking for unlogged project developments and end-of-day Umbrella Task tagging, once the Umbrella Tasks concept was introduced (see `Umbrella_Tasks.md`).

**2026-07-29:** standardized the task-log trigger as `#newtask` (previously used inconsistently as "new task" / "#newtask" / "#new task" — this is now the one form).
