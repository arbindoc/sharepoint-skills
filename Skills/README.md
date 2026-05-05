# Skills

AI skills are instruction files that give a Copilot agent a focused capability. Each skill lives in its own folder and is installed by uploading that folder to the **Skills** library in SharePoint.

---

## SharePoint Skills

| Folder | Skill | Description |
|---|---|---|
| [file-classifier/](./file-classifier/) | File Classifier | Classifies files in a SharePoint document library by reading their content and matching them to known content types (Contracts, Invoices, Purchase Orders). Creates the appropriate metadata columns, extracts values from each file, and saves them automatically. Use when asked to classify, tag, or extract metadata from documents in a library. |
| [library-cleanup/](./library-cleanup/) | Library Cleanup | Organizes a document library by scanning for duplicates, bad file names, empty folders, and excessive nesting. Reads file content to generate meaningful rename suggestions, presents a visual before/after comparison with an Organization Score, then executes the full cleanup with a live TODO checklist the user can follow along with. Triggered when someone says "clean up file demo". |
| [organize-library/](./organize-library/) | Organize Library | Fully organizes a SharePoint document library end-to-end: classifies files by content type, applies brand-consistent column formatting (pills, data bars, overdue highlights), creates filtered views per content type, colors folders, and sets up notification rules for overdue items. Orchestrates the file-classifier skill and reads SHAREPOINT.md for brand colors. |
| [site-storage-heatmap/](./site-storage-heatmap/) | Site Storage Heatmap | Generates an interactive HTML site map showing storage breakdown and hot/cold activity heatmap across all document libraries, lists, and site pages. Includes site-wide summary stacked bars and per-library click-through drill-downs. Saves the file to the site's document library and navigates the user directly to it. |

---

## Installing a Skill

Skills follow the [agentskills.io specification](https://agentskills.io/specification). The `Skills/` library in SharePoint is created automatically — install by uploading the skill folder into it.

1. Download the skill folder (e.g., `file-classifier/`)
2. In your SharePoint site, open the **Agent Assets** library
3. Navigate into the **Skills** folder (auto-created)
4. Upload the skill folder — the agent discovers it by the `name` field in `SKILL.md`

## Creating a Skill

A skill is a folder containing a single `SKILL.md` file. The folder name must match the `name` field in the frontmatter exactly.

**Where it goes in this repo:** `Skills/<skill-name>/SKILL.md`

**Where it goes in SharePoint:** `Skills/<skill-name>/SKILL.md` (upload the skill folder directly)

**Minimal example — `Skills/summarize-page/SKILL.md`:**

```markdown
---
name: summarize-page
description: Summarizes a SharePoint page in 3 bullet points.
  Use when the user asks for a quick summary of a page.
---

# Summarize Page

## Instructions

1. Read the full content of the specified page.
2. Identify the 3 most important points.
3. Return a bulleted summary, each bullet no longer than one sentence.
```

That's a complete, valid skill. The frontmatter tells the agent when to activate it; the body tells it what to do.

## Contributing a Skill

Skills work best when they are:
- **Focused** — one capability per file
- **Self-contained** — no external dependencies required to use it
- **Documented** — frontmatter with `name` and `description` so agents can self-select the skill

To contribute, create a feature branch, add your skill folder to the `Skills/` directory following the naming conventions above, and submit a pull request with a description of what the skill does.
