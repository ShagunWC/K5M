# 005_project-discovery

Read `SECURITY_PROTOCOL.md` on the `main` branch before adding or naming anything here.

## Purpose

This branch is deliberately kept generic — it is not K5M-specific. It holds reusable templates, trackers, and frameworks (e.g. a blank COC workbook template, a blank fit-out scope audit template, a blank tracker naming/version-log pattern) that can be copied as the starting point for a future project, not just K5M.

## Rules

- Nothing in this branch should reference K5M, the client, or the supplier by name or code — it should be reusable as-is for any project.
- When a pattern proves itself useful on K5M (e.g. the tracker naming convention, the VERSION_LOG.md format, the SHD version workflow), bring a genericized copy of it here.

## Current contents

- `Making_and_Maintaining_a_COC.md` — lessons from building/maintaining a Control Centre workbook.
- `OneDrive_Project_Folder_Structure.md` — starting folder structure and naming conventions for a new project's live OneDrive workspace, generalized from K5M's own structure and the issues found auditing it (2026-08-07).
- `AI_Tool_Roadmap.md`, `brand/`, `material_package_ffe/`, `material_package_fitout/` — other reusable material.
