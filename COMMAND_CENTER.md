# K5M — Command Center

Trigger phrases Shagun uses in conversation to fire a standing action. Read this before treating any of these as a one-off — they're standing behavior, not something to re-confirm each time.

---

## `#newtask`

**Says:** "#newtask: <description>"

**Does:** Adds a new row to the K5M Task Tracker (`006_task-management-pm/260730_K5M_Task Tracker.xlsx`, or its OneDrive location once handed off) — Date Raised, the task description in full, and best-guess Umbrella Task (written in full — no abbreviations; "UTSK" is only ever shorthand for the term "Umbrella Task" itself, not for any value)/Priority/Type of Task/Dependent On 1/Dependent On 2/Status, flagged for Shagun to correct. There is no "Owner" column — Shagun is always the default owner, so it isn't tracked per row. Commit and push immediately.

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
4. **This is where Woody does the actual tracker upkeep** (see "Woody" below): review every open row, mark anything no longer relevant/actionable as **Stale** in the Status column, and hide that row (never delete it). The Task Tracker must be clean and current by the end of this step — that's what makes tomorrow's `#GoodMorning` view trustworthy.
5. Confirms the Task Tracker (wherever it currently lives — OneDrive once Shagun hands it off) reflects every task raised today, with Status/Dependent On/Priority updated for anything that changed during the day.
6. Confirms all of today's file changes are actually pushed to the correct branch in git — nothing sitting locally only.
7. Confirms `DAILY_LOG.md` has today's entry.
8. Updates `PROJECT_BRIEFING.md`'s "Where we left off" section (main branch) so it reflects today's actual state — not just `DAILY_LOG.md`. This is what a brand-new session (or `SESSION_START.md`) reads to get caught up; it must never be allowed to go stale again the way it did before 2026-08-04.
9. Reports back: what's clean, what's still open/pending, anything inconsistent found.

---

## `#GoodMorning`

**Says:** "#GoodMorning"

**Does:** opens the actual K5M Task Tracker file directly (from its OneDrive location once handed off) so Shagun can view the full, current tracker herself. She builds her own day's schedule from it — this does **not** generate a filtered "my day" list or a summary; it just opens the live file. It should already be clean and up to date, because the previous evening's `#totalcheck` did that work.

---

## `#ShowMeMyKanban`

**Says:** "#ShowMeMyKanban" — a separate, on-demand command, not part of the morning routine.

**Does:** reads the Task Tracker and generates a Kanban view grouped by Status, shown directly in the conversation. Only given when specifically asked for — not automatically every morning.

---

## Woody

**Woody** is the name for Claude's maintenance role on the Task Tracker — whenever "Woody" is used (by Shagun, or in any note/log), it means Claude acting in this capacity: reviewing tasks, marking things Stale, keeping the tracker clean. It is not a separate tool or system, just a name for this specific job so it's easy to refer to in conversation (e.g. "let Woody handle that" = Claude will mark/clean it during `#totalcheck`, not something Shagun needs to do herself).

---

## `#hardrule`

**Says:** "#hardrule: <text>"

**Does:** Appends a new numbered entry to `HARD_RULES.md` (main branch) with the given rule, and logs the date under that file's Amendments section. Same mechanism as `#newtask`, but for the standing guardrail list instead of the Task Tracker.

---

## `#execute`

**Says:** "#execute"

**Does:** Gives the explicit go-ahead to start building a deliverable. Per Hard Rule 13: never start building directly — gather full context, confirm understanding, and ask any clarifying questions first; only begin the actual build once `#execute` is given. If Shagun hasn't said it yet, keep clarifying/aligning rather than building.

---

## `#refreshmenow`

**Says:** "#refreshmenow: <umbrella task or topic>"

**Does:** Gives Shagun a full briefing of everything currently known/built on that umbrella topic — pulled from across the repo, memory, and any live files, not just one tracker. Covers: what exists, what's been built, current status, open items, and anything unresolved. This is a knowledge-recall/briefing command, not a build or edit — it never modifies anything, just reports.

---

## `#STOP`

**Says:** "#STOP"

**Does:** Stops whatever Claude is doing or about to do, immediately — no further tool calls, no continuing the current plan — and gives full attention to whatever Shagun says next. Nothing resumes from before the `#STOP` until she explicitly says to continue it.

---

## Amendments

Add new commands below with a date, rather than editing the list above, unless a command's behavior is being corrected.

**2026-07-29:** `#totalcheck` extended to include asking for unlogged project developments and end-of-day Umbrella Task tagging, once the Umbrella Tasks concept was introduced (see `Umbrella_Tasks.md`).

**2026-07-29:** standardized the task-log trigger as `#newtask` (previously used inconsistently as "new task" / "#newtask" / "#new task" — this is now the one form).

**2026-07-30:** added `#GoodMorning` / `#ShowMeMyKanban` once the task-management Excel sheet and Kanban-by-Status concept were agreed.

**2026-07-30:** corrected — `#GoodMorning` and `#ShowMeMyKanban` are separate commands, not interchangeable. `#GoodMorning` just opens the live tracker file; `#ShowMeMyKanban` is the on-demand Kanban view. Also removed the "Owner" column (Shagun is always the default owner), added "Woody" as the name for Claude's tracker-maintenance role, and gave `#totalcheck` an explicit Stale-marking/row-hiding step so the tracker is clean by the next morning.

**2026-07-31:** added `#hardrule` (adds an entry to `HARD_RULES.md`) and `#execute` (the explicit go-ahead to start building — nothing gets built directly before it, per Hard Rule 13).

**2026-08-04:** added `#refreshmenow` — an on-demand full briefing on any umbrella topic, read-only, no edits.

**2026-08-04:** added a `#totalcheck` step to update `PROJECT_BRIEFING.md`'s "Where we left off" section daily — it had gone stale (still describing 2026-07-24's initial onboarding) because it was only ever updated on an ad-hoc basis. `#totalcheck` is the natural daily checkpoint to keep it current.

**2026-08-06:** added `#STOP` — an immediate hard interrupt, distinct from a plain "wait." Stops all in-progress action and gives full attention to what Shagun says next.
