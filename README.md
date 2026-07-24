# 001_inbox

Read `SECURITY_PROTOCOL.md` on the `main` branch before adding or naming anything here.

## Purpose

This branch holds every raw document as received — client uploads, RFIs, BOQs, drawings, supplier submissions — before any processing or translation into a knowledge bank sheet or tracker.

## Rules

- **Files stay here permanently.** Once a document has been read and its content translated into `002_knowledge-bank` or a tracker in `003_trackers`, the original is not deleted or moved. It remains as the evidentiary record — if a tracker value is ever questioned, the source document that justified it should still be findable here.
- Preserve original filenames as received where possible. If a file must be renamed for clarity, keep the original name in parentheses or in a short note alongside it.
- This branch is not organized by the `YYMMDD_ProjectCode_Category_SpecificName` convention used in `003_trackers` — file naming here should stay as close to "as received" as practical. Subfolder by rough source/date if the volume of files makes that useful.

## What does not belong here

- Anything already translated into a sheet — that's a duplicate; the sheet belongs in `002_knowledge-bank` or `003_trackers`, referencing this branch as its source if needed.
- Emails — those belong in `004_communication`.
