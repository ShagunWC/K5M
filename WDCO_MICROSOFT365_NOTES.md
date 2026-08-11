# WDCO Microsoft 365 / Teams Environment — Technical Notes

Wood Couture's entire IT setup runs on Microsoft 365 with Teams as the collaboration backbone. Every project folder lives on SharePoint, synced locally to each person's machine via OneDrive; files are routinely left open, co-edited, or actively synced in the background; and the Microsoft 365 *subscription* channel (not a standalone/perpetual Office license) means newer Excel/PowerPoint features are on by default that a generic "Office automation" mental model won't account for. This file exists because several COM-automation approaches that work fine in a plain Windows+Office setup behave differently — or fail outright — against WDCO's specific environment. Read this before writing any script that touches Excel, PowerPoint, or Outlook here.

This is a technical troubleshooting reference, not a judgment-call document — see `HARD_RULES.md` for the standing constraints (rules 15, 17, 18, 20 in particular are the ones this file expands on).

---

## 1. OneDrive-synced files break COM automation unpredictably

Live files under a synced SharePoint/OneDrive folder (i.e. almost every real project file at WDCO) can fail `Workbooks.Open()` / mid-script COM calls with no useful error (`"You cannot call a method on a null-valued expression"`), non-deterministically — the exact same script works instantly against a local copy every time. Each failure leaves an orphaned, windowless EXCEL.EXE/POWERPNT.EXE process holding the file locked (visible via `Get-Process EXCEL` with `MainWindowTitle` empty) — per Hard Rule 3, never force-kill it; ask Shagun to end the stray task herself.

**Rule (Hard Rule 20): never write directly to a OneDrive-synced file.** Copy it to the Desktop, do all edits there, validate, hand it back — Shagun moves the finalized file to OneDrive herself. This isn't a workaround, it's now the standing workflow.

## 2. Excel's "Place in Cell" images are invisible to legacy image scanning

Modern Excel (Insert > Pictures > Place in Cell, on by default in current-channel Microsoft 365) stores a picture as the cell's actual value — a "rich value" — not as a floating shape anchored to a cell. `openpyxl`'s `worksheet._images` and even COM's `Worksheet.Shapes` collection only see the older floating-anchor type. A sheet can have a mix of both within the same column, and there's no way to tell from a simple image count which rows use which.

**To find genuinely-missing thumbnails, always check both:**
1. Floating images: `ws._images`, anchor `.anchor._from.row/col` (openpyxl).
2. In-cell rich values: does the cell have a `vm="N"` attribute in the raw sheet XML? If so, trace `xl/metadata.xml` (`vm` index → `valueMetadata` `<bk><rc t v></bk>` entry, 1-based) → `xl/richData/rdrichvalue.xml` (`v` → rv index → first `<v>` = rel index) → `xl/richData/richValueRel.xml` (rel index → `rId`) → `xl/richData/_rels/richValueRel.xml.rels` (`rId` → actual `xl/media/imageN.ext` target).

A cell with neither a floating anchor nor a `vm` attribute is genuinely blank. **Critical**: confirm which `sheetN.xml` a given sheet name actually maps to via `xl/workbook.xml` + `xl/_rels/workbook.xml.rels` before checking — sheet order in the workbook is not guaranteed to match `sheet1.xml, sheet2.xml...` sequentially, especially once a workbook has more than a couple of tabs (mis-assuming this cost real rework on the FFE COC — "FFE_Hard Material" was `sheet2.xml`, not `sheet1.xml`, because "FFE_Main Data Sheet" came first).

## 3. Clipboard-based `Copy()` / `PasteSpecial()` is fragile here

Using `Range.Copy()` + `Range.PasteSpecial(xlPasteFormats)` to replicate cell formatting across many cells in a loop has caused `RPC_E_CALL_REJECTED` and `CutCopyMode` type-binding errors specifically when run against WDCO's environment (Teams/OneDrive background sync activity plausibly contending for the same clipboard/COM message pump). **Prefer direct property assignment** — copy `.Font.Name/.Size/.Bold/.Color`, `.Interior.Color`, `.Borders.Item(edge).LineStyle/.Weight/.Color` one property at a time from a reference cell — no clipboard involved, and it's been reliable every time it's been used as the fix.

## 4. `GetActiveObject()` read-only attach is unreliable

Attaching to an already-running Excel/PowerPoint instance via `[Runtime.InteropServices.Marshal]::GetActiveObject("Excel.Application")` to read a file the user has open (without disturbing her session) works sometimes and throws `MK_E_UNAVAILABLE` (`Operation unavailable`) other times, for no visible reason tied to what's actually open. Don't rely on it as a guaranteed read path — if it fails, just ask Shagun to close the file so a fresh `DispatchEx` open can read it instead. When it *does* work, remember `Workbook.Name` may not match what you expect if the file was opened via a SharePoint URL rather than a local path — match on `.Name -like "*partial*"` or enumerate all open workbooks first.

## 5. PowerPoint COM specifics

- `Application.Visible = $true` fails in PowerShell (`Cannot convert value "True" to type "Microsoft.Office.Core.MsoTriState"`) — bare booleans don't coerce to the enum. Avoid setting `Visible` at all when possible.
- `Presentation.ExportAsFixedFormat(path, 2)` has thrown type-binding errors via PowerShell late-bound COM (`Cannot convert the "2" value of type "int" to type "Object"`) inconsistently. **`Presentation.SaveCopyAs(path, 32)` (32 = `ppSaveAsPDF`) has been the reliable PDF-export path** throughout this project — use it instead, including for attach-to-open-instance read-only exports.
- Setting `Range.Resize(1, 2)` on a full-column `Range` object (e.g. `Columns.Item(11)`) does *not* give you "2 full columns" — it collapses to row 1 of those columns, since `Resize` keeps the original range's top-left cell. To insert full columns, build the range from `Cells(1, col)` to `Cells(1, col+1)` and call `.EntireColumn.Insert()` on that.

## 6. Microsoft 365 MCP connector (mail) specifics

- **Read-only in practice, always** — never call `send_mail` / `create_draft` / `reply` / `forward_mail` / `delete` / `trash` / `modify_labels` / any `outlook_batch_*` tool without Shagun's explicit go-ahead for that specific message, regardless of what read access has been granted.
- `outlook_email_search`: `order` is incompatible with a free-text `query` (validation error) — drop `order` and use `sender`/`afterDateTime` filters instead when you need newest-first sorting alongside a keyword search.
- `recipient` is incompatible with `folderName`, `mailboxOwnerEmail`, and `order` — pick one axis (recipient-based across all folders, or folder-scoped) per search.
- Full-mailbox free-text search is relevance-ranked, not date-ranked — a real, recent email can rank below older ones and simply not appear in the first page. If a specific email isn't turning up, pin down its subject/thread and search on that directly (or `folderName="Sent Items"` if it's likely her own outgoing mail) before concluding it doesn't exist.

---

## Amendments

**2026-08-11:** initial version, written after four consecutive failed COM automation attempts against a live OneDrive-synced Fitout Material Package file (each leaving an orphaned Excel process) and the FFE COC sheet-mapping/in-cell-image mistakes made while building the Material Package Photo Presentation.
