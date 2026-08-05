# Starting a new session on this project

Paste this at the start of any new Claude Code session (this machine, or any other) to get it fully caught up before it does anything:

---

This is a continuation of the K5M project (Wood Couture — Park Hyatt Casablanca FF&E + Fit-out). Before doing anything else:

1. If `git` and `gh` aren't installed and authenticated on this machine yet, set that up first: `winget install --id Git.Git -e --source winget --accept-package-agreements --accept-source-agreements`, then `winget install --id GitHub.cli -e --source winget --accept-package-agreements --accept-source-agreements`, then `gh auth login --hostname github.com --git-protocol https --web` (one-time browser approval).
2. Clone or pull `github.com/ShagunWC/K5M`.
3. Read, in this order: `main/README.md`, `main/SECURITY_PROTOCOL.md`, `main/COMMAND_CENTER.md`, `main/HARD_RULES.md`, `main/PROJECT_BRIEFING.md`, `main/DAILY_LOG.md` (newest entry first — this is the most current record, more so than `PROJECT_BRIEFING.md`'s narrative summary).
4. Check the `sharepoint_coc_server` MCP connector (`list_coc_files` / `get_sheet_content` for project `K5M`) for anything on the live SharePoint COC that's changed since the last `DAILY_LOG.md` entry.
5. Give a short summary of where things stand and what's open — do not start building, editing, or committing anything until the next steps are confirmed.

---
