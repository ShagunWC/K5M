# 006_task-management-pm

Read `SECURITY_PROTOCOL.md` on the `main` branch before adding or naming anything here.

## Purpose

Open task tracking and meeting records for project management.

## Contents

- `open_tasks.md` — running list of open tasks (not project scope lines — those live in `003_trackers` — but PM-level to-dos: follow-ups, pending decisions, things owed to someone).
- `meetings/` — one dated folder per meeting.
- **`260807_K5M_Project Management_Tasks and Calendar.xlsx`** — the current, live tracker: Task Tracker + Project Calendar merged into one workbook (`Data`, month tabs, `Hard Milestones`, `Project Development Log`, `Task Tracker`, `Change Log`). Built 2026-08-07. Connecting key between the Task sheet and the calendar is each task's **Task Number**: calendar entries get tagged `(#N)` and hyperlinked to the matching Task sheet row; the Task sheet's `Logged on Calendar?` column checks the relevant month tab for that tag and reports Yes/Missing/N/A. Tagging is applied going forward on new entries, not backfilled onto old ones.
  - `260729_K5M_Project Calendar.xlsx` and `260730_K5M_Task Tracker.xlsx` are now **superseded** by the merged file — kept in place for history, not deleted, but no longer the current file to edit.

## Meeting folders

Naming: `YYMMDD_K5M_Meeting_<topic or attendee>` (same date-first convention as the rest of the repo).

Each meeting folder contains:
- `pre-meeting/` — agenda, prep notes, questions to raise
- `minutes/` — what was discussed and decided
- `post-meeting/` — action items and follow-ups sent

Content can duplicate across meeting folders (e.g. the same action item reappearing in the next meeting's pre-meeting notes) — the goal is a complete before/during/after record per meeting, not a single deduplicated task list.

See `meetings/260724_K5M_Meeting_EXAMPLE/` for the folder shape.
