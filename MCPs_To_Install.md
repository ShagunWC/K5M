# MCPs / Connectors — Installed & In Use

A running record of every connector actually authorized/installed for this work — not the full marketplace list of what's *available*, only what's actually been turned on and why. Update this whenever a new one gets installed or an existing one changes status.

## Status legend

- **Active** — authorized and in real use.
- **Blocked** — attempted, not working (reason noted).
- **Requested** — a need has been identified, not yet installed (usually tracked as its own Task Tracker row too).

## Current list

| Connector | Status | Purpose | Notes |
|---|---|---|---|
| **Microsoft 365** | Active | Outlook mail search (`#GoodMorning` mail check), calendar, SharePoint, Teams | Authorized via `/mcp`. Full read access, no tenant block. Write actions (send/draft/reply/delete) are available but never used without Shagun's explicit go-ahead each time. |
| **sharepoint_coc_server** | Active | Reads the live SharePoint-hosted COC directly (`list_projects`, `get_coc`, `get_coc_dashboard`, `get_sheet_content`, etc.) | Project-specific COC connector — check this for anything changed on the live SharePoint COC since the last `DAILY_LOG.md` entry, per `SESSION_START.md`. |
| **outlook-email-drafter** | Blocked | Would have handled mail drafting/sending directly | Stayed blocked even after IT's tenant-level fix. Superseded in practice by the Microsoft 365 connector above for read access; drafting/sending still has no working connector. |
| **Document generation** (Word/PowerPoint/PDF) | Requested | Reduce reliance on COM automation + headless-Chrome-print workarounds for trackers, decks, and print-ready exports | Not yet installed — see Task Tracker Task Number 58 (raised 2026-08-14). |

## Amendments

Add new connectors below with a date, rather than editing the table above unless a status is being corrected.

**2026-08-14:** File created. Captured the two connectors already in active use (Microsoft 365, sharepoint_coc_server), the one attempted-but-blocked (outlook-email-drafter), and the one currently requested (document generation, Task 58).
