# K5M — Command Center

Trigger phrases Shagun uses in conversation to fire a standing action. Read this before treating any of these as a one-off — they're standing behavior, not something to re-confirm each time.

---

## `#newtask`

**Says:** "#newtask: <description>"

**Does:** Adds a new row to the Task Tracker sheet in `006_task-management-pm/260807_K5M_Project Management_Tasks and Calendar.xlsx` (or its OneDrive location once handed off) — Date Raised, the task description in full, and best-guess Umbrella Task (written in full — no abbreviations; "UTSK" is only ever shorthand for the term "Umbrella Task" itself, not for any value)/Priority/Type of Task/Dependent On 1/Dependent On 2/Status, flagged for Shagun to correct. Task Number is assigned by Claude (Hard Rule 8) — it also doubles as the connecting key to the Calendar (see `#projectdevelopment`). There is no "Owner" column — Shagun is always the default owner, so it isn't tracked per row. Commit and push immediately.

Superseded the one-file-per-day `YYMMDD_Task_List.md` markdown convention on 2026-07-30 — the Task Tracker is now the single running record.

---

## `#projectdevelopment`

**Says:** "#projectdevelopment — <date> — <category> — <update> — <evidence link>" (category and evidence link are optional per entry)

**Does:**
1. Appends the entry to the "Project Development Log" tab in `260807_K5M_Project Management_Tasks and Calendar.xlsx` (`006_task-management-pm`).
2. If the update implies an actual schedule change (a date moving, a new milestone, a decision affecting an existing activity), reflects that into the Data tab and the relevant month tab too — not just logged passively.
3. If the update ties to a specific Task Tracker row, tag the calendar entry `(#TaskNumber)` and hyperlink it back to that row — this is what the Task sheet's `Logged on Calendar?` column checks against. Applies going forward on new entries; old entries weren't backfilled when the merge was built (2026-08-07).
4. If category or evidence link is left blank, ask rather than guess or leave silently blank.

---

## `#totalcheck`

**Says:** "#totalcheck" (or "do a total check") — only ever run when Shagun explicitly asks, never automatically at end of day without being asked.

**Does, in order:**
1. Confirms every tracker (COC files, Material Packages, the merged Tasks and Calendar workbook) reflects the latest agreed state — nothing discussed but not yet applied.
2. Asks Shagun for any `#projectdevelopment` updates from today that haven't been logged yet — don't assume everything worth logging was already flagged live during the day.
3. Tags every one of today's `#newtask` entries and Development Log entries with its Umbrella Task, written in full (see `Umbrella_Tasks.md`, same branch — no abbreviations for the values themselves; "UTSK" is only ever shorthand for the term "Umbrella Task") — tagging happens in this end-of-day batch, not live at the moment each entry is created.
4. **This is where Woody does the actual tracker upkeep** (see "Woody" below): review every open row, mark anything no longer relevant/actionable as **Stale** in the Status column, and hide that row (never delete it). The Task Tracker must be clean and current by the end of this step — that's what makes tomorrow's `#GoodMorning` view trustworthy.
5. Confirms the Task Tracker sheet (wherever the merged workbook currently lives — OneDrive once Shagun hands it off) reflects every task raised today, with Status/Dependent On/Priority updated for anything that changed during the day.
6. Confirms all of today's file changes are actually pushed to the correct branch in git — nothing sitting locally only.
7. Confirms `DAILY_LOG.md` has today's entry.
8. Updates `PROJECT_BRIEFING.md`'s "Where we left off" section (main branch) so it reflects today's actual state — not just `DAILY_LOG.md`. This is what a brand-new session (or `SESSION_START.md`) reads to get caught up; it must never be allowed to go stale again the way it did before 2026-08-04.
9. Reports back: what's clean, what's still open/pending, anything inconsistent found.

---

## `#GoodMorning`

**Says:** "#GoodMorning"

**Does:** opens `260807_K5M_Project Management_Tasks and Calendar.xlsx` directly (from its OneDrive location once handed off) so Shagun can view the full, current tracker herself. She builds her own day's schedule from it — this does **not** generate a filtered "my day" list or a summary; it just opens the live file. It should already be clean and up to date, because the previous evening's `#totalcheck` did that work. Also checks Outlook (via the Microsoft 365 connector — working since 11 Aug, no longer blocked) for anything tagged/subject-prefixed "K5M" since the last check and reports what's new, across all folders (inbox and sent both).

Also flags, separately: any email Shagun **sent** (K5M-tagged) more than 24 hours ago that has **no reply yet** — detected by matching subject lines across folders for anything arriving after the sent timestamp from someone other than Shagun. Report these distinctly from "what's new," since a stalled thread is a different kind of signal than new mail. **Known limitation**: this matches on subject line, not a true conversation-thread ID (the connector doesn't expose one) — reliable for subjects that stay consistent, but could miss a reply under a changed subject, or misjudge a very generic subject. Flag anything borderline as uncertain rather than stating it as settled.

Also gives a standing reminder: **check Sreejith's onboarding checklist** (`260813_WC_PC_Onboarding_Checklist.md`, `007_wdco-internal-team-management`) — just the reminder itself, not a status readout of which boxes are checked.

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

## `#checkonedriveproject`

**Says:** "#checkonedriveproject" — on-demand only. Never automatic, never folded into `#totalcheck` or any daily routine. Shagun's own habit is roughly weekly, not daily — Claude doesn't need to track or remind her of that cadence.

**Does:**
1. Compares the current OneDrive K5M folder (`Wood Couture - Live Projects_SL\K5M`) against `_K5M_File_Index.xlsx` (same folder) to find what's new or changed since the last check.
2. Actually reads/audits the new or changed material (not just notes that it exists) for the same issue patterns found in the 2026-08-07 baseline study: naming inconsistencies, broken formulas/data quality, duplicated files, stale trackers, tracker-vs-reality mismatches.
3. Regenerates `_K5M_File_Index.xlsx` and refreshes `_K5M_Folder_Guide.md` (both live at the OneDrive root, not in git — they carry real names/numbers the git repo's redaction rule doesn't allow) so they reflect current state, tagged by Umbrella Task at the folder level where determinable.
4. Hands Shagun a fresh findings list. Claude does not decide what to do about any finding — she triages each one herself.

The reusable, redacted version of the folder structure this is built around lives in `005_project-discovery/OneDrive_Project_Folder_Structure.md` — the starting template for any *future* project's OneDrive workspace.

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

**2026-08-07:** Task Tracker and Project Calendar merged into one workbook, `260807_K5M_Project Management_Tasks and Calendar.xlsx` — updated every reference above accordingly. New connecting mechanism: each task's Task Number (renamed from "S.No.," see Hard Rule 8) tags the matching calendar entry as `(#N)` with a hyperlink back to its row; the Task sheet's `Logged on Calendar?` column checks for that tag and reports Yes/Missing/N/A. Tagging applies going forward, not backfilled onto existing entries. The two old separate files are superseded, not deleted.

**2026-08-07:** added `#checkonedriveproject` — on-demand (weekly-ish, Shagun's own cadence, never automatic) audit of the OneDrive K5M folder against a saved file index, following a full baseline study of all ~700 files that day. Also added Umbrella Task 15, "Contractual - Client Facing" (BOQs/pricing/proposals didn't fit any existing category).

**2026-08-13:** `#GoodMorning` extended with a standing reminder to check Sreejith's (new Project Coordinator) onboarding checklist — added while setting up `007_wdco-internal-team-management`. Just the reminder, not a checklist-completion status check.

**2026-08-18:** `#GoodMorning` extended to also flag sent K5M-tagged emails older than 24 hours with no reply yet, reported separately from "what's new" — Shagun asked for this directly after noticing the mail check hadn't distinguished stalled outbound threads from new inbound mail. Same amendment corrected a stale note claiming Outlook access was still tenant-blocked — it's been working via the Microsoft 365 connector since 11 Aug.
