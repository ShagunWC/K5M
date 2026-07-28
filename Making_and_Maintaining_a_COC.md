# Making and Maintaining a COC

A COC ("Center of Control") is a project's master tracking workbook — the single place that ties every product/scope item to its materials, shop drawings, and approval status. This doc captures what we've learned building one, so the next project doesn't start from zero.

## Core sheet shape

- **Data (Master Scope)** — one row per scope item (product or task), with its own code, description, area/category, and quantity/size fields. This is the spine every other sheet cross-references.
- **Material sheets (Hard / Soft, or however the project's materials split)** — one row per material code, not per item, since one material is usually used by several items. Needs a status legend (e.g. Approved / Approved with comments / Rejected / Submitted / To be Submitted / Omitted), a weekly status-snapshot section, and a thumbnail.
- **Shop Drawings** — tracks the drawing/approval lifecycle per item: draft → review round(s) → compliance check → client signature.
- **Change Log** — a single running record of actual content changes (new rows added, codes corrected, items reassigned) across every sheet.

## Lessons learned

1. **Don't force one project's shape onto another.** A template built for item-based scope (discrete products) doesn't fit task-based scope (e.g. construction tasks tied to drawings) cleanly. Adapt the Data sheet's shape to what the project actually tracks — item or task — rather than copying a prior project's structure wholesale.
2. **Check for embedded images properly.** Reading a workbook's cell text values will miss images embedded in cells — they're a separate object layer, not a cell value. Always check the workbook's image/drawing objects directly (or just ask whoever built the source file whether images exist) before concluding a sheet "has no images."
3. **Separate the routine status snapshot from the change log.** A weekly "what's the status now" check-in and a log of actual structural edits (new material added, a code corrected) are two different things and shouldn't be conflated into the same mechanism — one is expected/periodic, the other is ad hoc.
4. **Use a generic cross-reference column name from the start.** Calling it "Reference Code" rather than "Item Code" (or similar) means it still makes sense once more sheets are added later (shop drawings, and whatever comes after) that all need to point back to the same Data-sheet row.
5. **Tap-through hyperlinks only work cleanly for one-to-one relationships.** A cell can only hyperlink to one place — great for "one shop drawing → one item," useless for "one material → many items" (a list in one cell). Don't force a hyperlink where the data shape is many-to-one; skip it there rather than picking an arbitrary "first match."
6. **Sequence structural dependencies before functional ones.** A tap-through hyperlink needs its target sheet's row layout finalized first — build the Data sheet's structure before wiring links into other sheets that reference it.
7. **Build tab by tab, only on explicit direction.** Resist building the whole workbook at once even when the shape seems obvious — a half-aligned assumption compounds across five sheets instead of one. Confirm each tab's structure before moving to the next.
8. **Once a live file gets manually re-styled, stop regenerating it from a script.** A build script re-run will stamp its own formatting back over any manual styling. Switch to targeted live edits (open the file, touch only the specific cells/rows that need to change) once the file has been handed off and personalized — full rebuilds only when explicitly asked for again.
