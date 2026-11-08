---
name: image-to-editable-ppt
description: 图片转可编辑PPT。Rebuild slide images, screenshots, AI-generated slides, or flattened PPTX into editable PowerPoint while preserving approved wording and composition and checking the final rendered result. Use for image-to-editable-PPT requests.
---

# Image to Editable PPT Skill

## Local and cloud execution

This package is a portable instruction workflow; it does not install PowerPoint, rendering engines, OCR, or authoring libraries. Use the current environment's available presentation tools and authoring guidance. Never assume Windows paths, local files, local skills, desktop access, or bundled dependencies exist in cloud sessions. Prefer installed PowerPoint for target-application rendering when accessible. If it is inaccessible, use available rendering tools, report their exact scope, and leave Microsoft PowerPoint verification not checked. Do not claim cloud output has passed local PowerPoint testing. Installation and @/$ selection are managed by each host/account; saving this folder locally does not install it into a cloud account.

## Mandatory acceptance workflow

Apply this section over conflicting legacy recommendations below. Follow the user's latest approved design and wording. Rebuilding means preserving the composition, not redesigning it. Standard or complex icons and complex infographics should use independent PNG/SVG assets rather than PowerPoint line drawings. Do not infer underlying chart data from bar heights or invent unreadable text.

Before rebuilding, read [references/acceptance.md](references/acceptance.md). Create a per-slide source inventory of visible text, key numbers, modules, assets, and required editable objects. OCR is a draft, not ground truth. Visually verify it against the source. Mark unresolved readings explicitly; never silently correct or guess source wording, especially distorted AI-generated Chinese.

After rebuilding, reconcile the inventory against actual PPTX text and objects, render the final PPTX with installed Microsoft PowerPoint when available, and visually inspect every slide and dense region against the source. Run a separate acceptance pass against the inventory rather than relying on recollection of the build. Repair defects, regenerate, and repeat affected checks. A changed final file invalidates its prior acceptance evidence.

Deliver only when all applicable gates in the reference have evidence. Object counts, image-area thresholds, OCR agreement, or low pixel difference alone cannot establish editability or fidelity. A legitimate large photograph is not an automatic failure. Treat a large source-slide screenshot with duplicate or hidden text overlays as a failure of editable reconstruction. Do not claim independent human review or another reviewer unless it actually happened.

This skill specifies a workflow; it does not itself provide automated audit scripts. Use available tools and retain their actual outputs. If a required check cannot run, report it as not checked and do not claim full acceptance. A separate fidelity deck is optional for image reconstruction unless requested; the user's mandatory two-deck rule applies to HTML-to-PPT conversion.

## When to use this skill

Use this skill when the user provides:

- A slide image
- A screenshot of a slide
- An AI-generated slide visual
- A PPTX where each slide is a flattened image
- A non-editable PowerPoint that needs to become editable
- A request such as “turn this image into editable PPT” or “make this PPT editable”

The goal is not to convert the image directly. The goal is to rebuild the slide from scratch using native PowerPoint objects, while using the image only as visual reference.

---

## Core rule

Do not paste the original image as the final slide.

The final PPT must be editable.

Use the source image only as a reference layer. Recreate the slide with:

- Editable text boxes
- Editable shapes
- Editable rounded rectangles
- Editable lines and dividers
- Editable data numbers
- Editable tables or shape-based tables
- Editable chart labels
- Independent icons
- Independent logo/image objects

Complex photos, mascots, realistic illustrations, product images, and official brand logos may remain as separate image objects, but they must not be merged with text or layout elements.

---

## Required output files

Always create:

```text
editable_rebuild.pptx
preview.png or preview.pdf
audit_report.md
```

`editable_rebuild.pptx` is the final editable PowerPoint.

`preview.png` or `preview.pdf` is the visual preview for comparison.

`audit_report.md` proves that the slide is not just a screenshot and confirms object editability.

---

## Recommended approach

Prefer `pptxgenjs` when precise visual reconstruction is needed.

Use `python-pptx` only for simpler slides.

If the input is a PPTX with flattened image slides, first export each slide as a reference image, then rebuild each page.

Use a 16:9 slide size by default unless the source clearly uses another ratio.

Recommended canvas:

```text
Width: 13.333 in
Height: 7.5 in
```

---

## Reconstruction workflow

For each slide:

1. Inspect the reference image.
2. Identify the layout zones: header, title, subtitle, left panel, center content, right panel, data cards, footer, logo area, page number.
3. Identify all visible text.
4. Identify all cards, lines, dividers, borders, shapes, icons, tables, charts, and data modules.
5. Estimate x / y / w / h for each object.
6. Rebuild all text as PowerPoint text boxes.
7. Rebuild all cards and containers as native shapes.
8. Rebuild all lines and dividers as native line objects.
9. Rebuild all simple icons as SVG or editable shapes when possible.
10. Insert complex photos, mascots, illustrations, and logos as independent image objects only when necessary.
11. Export a preview.
12. Compare the preview against the source image.
13. Fix obvious differences in position, size, font, color, spacing, alignment, and layering.
14. Run the editability audit.
15. If the result is still mostly a screenshot, rebuild again.

---

## Text reconstruction rules

Every visible text block must become editable text.

Do not leave business text embedded inside an image.

Preserve original wording, line breaks, font size hierarchy, font weight, text color, alignment, position, and spacing.

Split text into separate text boxes when different parts have different visual styles.

For example, this should not be one image:

```text
45%
EC Incremental
```

It should be editable text boxes, usually with `45%` as a separate large bold text box and `EC Incremental` as a separate label.

Recommended fonts:

- Chinese: Microsoft YaHei, DengXian, SimHei, Noto Sans CJK SC
- English: Arial, Aptos, Helvetica, Calibri

For business slides, default to Arial + Microsoft YaHei.

---

## Shape reconstruction rules

The following must be editable PowerPoint objects, not images:

- Title boxes
- Rounded cards
- Data cards
- Footer bars
- Header bars
- Background color blocks
- Borders
- Dividers
- Lines
- Circles
- Pills / labels
- Callout boxes
- Tables
- Simple charts

Use native PowerPoint shapes whenever possible.

Match fill color, border color, border width, rounded corners, shadow, transparency, size, alignment, and spacing.

---

## Icon and image rules

Simple icons should be rebuilt as SVG or editable shapes when possible.

Examples: arrow, star, crown, medal, clock, warehouse, shopping basket, user icon, bar chart icon, checkmark.

Allowed as image objects:

- Complex people photos
- Complex AI illustrations
- Mascots
- Product photos
- Official brand logos
- Complex background textures

Not allowed as image objects:

- Text
- Data numbers
- Cards
- Lines
- Tables
- Simple charts
- Footer summaries
- Header titles

If an image contains important text, cover or crop the embedded text when possible, then recreate the text as editable text on top.

---

## Visual fidelity rules

The rebuilt slide should look as close as possible to the reference image in normal presentation view.

Match slide ratio, margins, module positions, card sizes, column widths, font sizes, font weights, text colors, shape colors, border colors, icon sizes, logo positions, footer position, page number position, and overall visual hierarchy.

Minor differences are acceptable only for complex photos, mascots, illustrations, or unavailable fonts.

Major layout differences are not acceptable.

---

## Strict quality gates

Before delivery, run these checks.

### Gate 1: No full-slide screenshot

Fail the slide if:

- It contains one image covering more than 80% of the slide area.
- It has no editable text boxes while the reference contains text.
- It has fewer than 5 editable objects on a content-heavy slide.
- The main content is still a flattened screenshot.

If failed, rebuild again.

### Gate 2: Text editability

Check that main title, subtitle, body text, labels, data numbers, footnotes, footer summary, and page number are editable.

Fail if important text is still embedded in an image.

### Gate 3: Shape editability

Check that cards, containers, lines, dividers, borders, data blocks, tables, and simple charts are editable.

Fail if major layout objects are still part of a screenshot.

### Gate 4: Visual fidelity

Export a preview and compare against the source. Fix obvious issues: wrong position, size, font size, color, spacing, alignment, layering, missing text, or missing module.

### Gate 5: Layering

Use this order:

1. Background
2. Large image assets
3. Cards / containers
4. Icons
5. Text
6. Logos
7. Page number

No text should be hidden behind an image or shape.

---

## Audit report requirements

Create `audit_report.md` with this structure:

```markdown
# Editable PPT Rebuild Audit Report

## Source

- Input file:
- Number of slides:
- Slide size:
- Tool used:

---

## Slide 1

### Object Counts

- Text boxes:
- Shapes:
- Lines:
- Images:
- SVG icons:
- Tables:
- Charts:

### Editability Check

- Title editable: Yes/No
- Subtitle editable: Yes/No
- Body text editable: Yes/No
- Data numbers editable: Yes/No
- Cards editable: Yes/No
- Lines editable: Yes/No
- Icons editable: Yes/No
- Footer editable: Yes/No
- Page number editable: Yes/No

### Full-Slide Image Check

- Full-slide screenshot retained: Yes/No
- Largest image coverage:
- Pass/Fail:

### Raster Assets Kept

| Asset | Reason | Can be replaced independently |
|---|---|---|
|  |  |  |

### Visual Fidelity Notes

- Matched well:
- Known differences:
- Needs manual review:

### Final Status

- No full-slide screenshot: Pass/Fail
- Text editability: Pass/Fail
- Shape editability: Pass/Fail
- Visual fidelity: Pass/Fail
- Overall: Pass/Fail
```

---

## Final acceptance criteria

The task is complete only when:

- The PPT opens normally.
- The slide visually matches the source image closely.
- All important text is editable.
- All important data numbers are editable.
- All cards can be moved or edited.
- All lines and dividers can be edited.
- Logos and complex images are independent objects.
- No full-slide screenshot remains as the main content.
- A preview has been exported.
- An audit report has been generated.

If these conditions are not met, continue revising.
