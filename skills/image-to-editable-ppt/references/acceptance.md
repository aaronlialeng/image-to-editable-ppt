# Image-to-PPT acceptance

## Preflight learned from a real reconstruction

Before building an entire deck, export a small representative image/text sample and open/render it in the target application. When using Artifact Tool, prefer explicit embedded image bytes with contentType and verify the exported images display in PowerPoint; a successful export or valid package alone does not prove image compatibility. Check actual glyph widths and paragraph spacing, not only text equality. Separate lines only when necessary for source fidelity and disclose that large paragraph rewrites will require reflow. Search for original photographic assets before using generated background repairs; disclose any reconstructed-photo differences. Report file integrity, transcription, editability, visual fidelity and source-fact verification as separate conclusions.

## 1. Source inventory

For every slide record source image, dimensions/aspect ratio, approved change scope, exact visible text blocks, key numbers with units/signs/decimal places, module order, table cells, chart labels, logos, photos, icons, arrows and their relationships. Give each item an ID and expected reconstruction type: native text, native table/chart/shape, or independent image.

Source legibility is a prerequisite: magnify/crop for reading where needed. Distinguish source defects from conversion defects. Flag ambiguous words/numbers for confirmation only when they cannot be resolved from supplied materials. Never reconstruct a data series from visual proportions and present it as known. Without underlying data, preserve complex charts as images and disclose the limitation; required fully editable data charts remain pending until reliable data is available.

## 2. Content reconciliation

Compare extracted PPTX text to the verified inventory by slide and item. Check omissions, duplicate text, Chinese characters, English spelling, punctuation that changes meaning, minus signs, percent versus percentage points, currency, UC/RE/MM, dates, rankings and total rows. Whitespace/line wrapping normalization must not hide altered words or numbers. Visible artwork lettering such as official logos may remain in the artwork; required business text must remain editable.

Pass: every required item is matched or an authorized change is recorded. Unresolved meaningful text/data differences block full acceptance. This verifies transcription and preservation, not the truth of source business data unless that was separately checked.

## 3. Structure and editability

Inspect actual PPTX objects, not only the preview. Confirm headings, body text, required metrics and table cells are genuinely editable and visible. Audit picture regions and disclose their role. Check slide bounds, hidden/duplicate source images, unintended off-canvas objects, leftover template content, full-slide screenshot concealment, and layering.

On a copy, edit representative heading, metric and table/chart content where present; save and reopen. Confirm edits remain usable. A native text box does not prove visible text is editable if an opaque image covers it. Native shape-based tables must be described accurately, not called native PowerPoint tables. A picture of a chart is not a data-editable chart.

## 4. Final rendering and visual review

Render every final PPTX page, preferably in the installed PowerPoint engine when that is the target application. Record renderer and exact final file hash. Keep source and rendered images at matching aspect ratios; reject dimension/page-count mismatches before pixel comparison. Do not stretch one image to hide geometry differences.

Inspect source/render side by side and, when helpful, overlay/difference images. Review every page at full view and dense areas enlarged: composition, text hierarchy and line breaks, alignment and spacing, cropping, font fallback/missing glyphs, label-number pairing, table rows/columns, arrow direction, z-order, logos, image proportions, seams/halos/residual old lettering after text removal. No universal pixel-difference percentage proves acceptance. Available-font detection alone cannot prove actual glyph rendering.

Pass: no missing content, illegible text, unintended occlusion, clipping, distortion, major layout drift or wrong relationships. Small rendering differences may be accepted with disclosure if they do not alter readability or the approved design. Preserve source typography where possible; disclose unavailable-font substitution. If only another renderer was available, state the limit and leave target-PowerPoint display unverified.

## 5. Repair, evidence and delivery

Log defects by slide/item with severity, repair and recheck evidence. Regenerate after repairs; rescan the whole deck for structural/content checks and review changed/affected pages. Global font/master/export changes require reviewing all pages again. Do not invent repairs when none were needed.

Bind report and preview to the final PPTX hash; do not use screenshots from an older revision. Record source files, page count, renderer, font substitutions, content reconciliation, actual editable/raster regions, edit/save/reopen results, reviewed pages, remaining exceptions and overall status. Allowed statuses: passed, pending confirmation, failed, not checked. Any required unperformed check prevents an overall passed status.

Return a short acceptance card with content, version, fonts, layout, final display and editability statuses, actual repairs and material limitations. Keep detailed build evidence available without overwhelming the user. User review should focus on business decisions and design preferences, not routine defect detection. Do not promise zero errors or claim checks that were not executed.
