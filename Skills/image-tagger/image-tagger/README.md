# Construction Image Tagger

A simple Copilot-in-SharePoint Skill that analyzes a selected images, extracts primary and background objects, and writes those values back into a SharePoint document library's metadata columns.

## What this repo contains
- **Skill definition:** [Skill.md](Skill.md) — the skill manifest and instructions used by Copilot in SharePoint.
- **Demo script:** [DemoScript.md](DemoScript.md) — step-by-step demo prompts and the SharePoint demo link.
- **Article / background:** [construction-image-tagger-substack.md](construction-image-tagger-substack.md) — long-form writeup and rationale.
- **Sample images:** [Sample Images/](Sample%20Images/)

## Purpose
Make images in a SharePoint library searchable by content rather than filename by automatically populating the `Primary Objects` and `Background Objects` columns with comma-delimited object lists produced by image analysis.

## Usage
1. Open the target SharePoint document library and select one or more image files.
2. Invoke the skill by using natural-language trigger phrases described in [Skill.md](Skill.md) (for example: "Tag this construction image").
3. The skill will:
   - Extract a single-line, comma-delimited list of primary objects.
   - Extract a single-line, comma-delimited list of background objects.
   - Update the file's `Primary Objects` and `Background Objects` columns.

## Output format
- Primary: a single line like `workbench, circular saw, tape measure`
- Background: a single line like `wall, drywall patches, floor`

## Demo
Follow the steps in [DemoScript.md](DemoScript.md) to try the skill in the SharePoint demo site referenced there.

## Publishing to GitHub
1. Add this folder to a Git repository and commit the files:

```bash
git init
git add .
git commit -m "Add Construction Image Tagger skill and docs"
git remote add origin <your-repo-url>
git push -u origin main
```

2. Optionally add a license and CI as desired.

## Notes
- The skill is designed to fail loudly: if image analysis returns empty or an update fails, the skill will report the failure rather than invent tags.
- For context and narrative on why this helps, see [construction-image-tagger-substack.md](construction-image-tagger-substack.md).

---
If you want, I can commit these changes to a branch and open a PR for you. Would you like that?
