---
name: construction-image-tagger
description: |-
  Analyze a selected construction image, identify primary and background objects, format each result as a single comma-delimited line, and write the results back to the corresponding SharePoint library columns.

  Use when the user says:
    - "Tag this construction image"
    - "Identify primary and background objects from the selected image"
    - "Analyze this image and update the object columns"
    - "Populate Primary Objects and Background Objects for this photo"
---
# Construction Image Tagger

## When to use
Use this skill when the user wants to analyze a selected construction image, extract visible objects, and update the image library metadata automatically. Use it when the selected file is an image in a SharePoint document library and the target columns are `Primary Objects` and `Background Objects`.

## Inputs
- A selected image file in SharePoint
- The current document library context
- The target columns:
  - `Primary Objects`
  - `Background Objects`
- The expected format for each value: a single line of comma-delimited object names

## Steps
1. Confirm there is a selected image file in the current SharePoint context.
2. Use image analysis on the selected file to identify the main foreground or primary objects. Ask for the output as a single line of comma-delimited objects.
3. Use image analysis on the same selected file to identify background or secondary objects. Ask for the output as a single line of comma-delimited objects.
4. Read the current library schema only as needed to resolve the exact internal names for the target columns.
5. Find the selected file's list item ID in the current library.
6. Update the corresponding item with:
   - `Primary Objects` column = primary object output
   - `Background Objects` column = background object output
7. Return the extracted primary and background object lines in the response.
8. If image analysis or the update fails or returns empty, say so plainly and do not invent objects.

## Output format
Return a concise result containing:
- The primary objects line
- The background objects line
- A brief confirmation that both SharePoint columns were updated

Example:
Primary: workbench, circular saw, tape measure
Background: wall, drywall patches, floor
Updated both columns.
