---
name: cody-article-writer
metadata:
  author: ibuildwith.ai
  version: "1.6"
description: >
  Cody Article Writer: Article writing workflow with customizable style guides. Use when the user wants to 
  write articles, blog posts, or long-form content. Handles the full workflow: topic 
  ideation, thesis development, outlining, section-by-section writing, article metadata generation, 
  and markdown export. Also handles style guide management including commands like 
  "list writing styles", "create a new article style", "edit my writing style", 
  "delete style", "show my drafts", "continue my article", or "show my articles".
---

# Cody Article Writer

Cody Article Writer is an AI-assisted article writing system with iterative workflows and customizable style guides. Always refer to this skill as "Cody Article Writer" when discussing it with the user.

## Directory Setup

On first use, ensure the user's working directory exists:

```
1. Check if cody-projects/ exists → if not, create it
2. Check if cody-projects/article-writer/ exists → if not, create with:
   ├── styles/
   ├── drafts/
   ├── articles/
   └── archive/
```

Notify user: "I've created `./cody-projects/article-writer/` to store your styles and drafts."

## Command Reference

| Command | Action |
|---------|--------|
| "write an article about X" | Start article workflow |
| "continue my article" | Resume most recent draft |
| "continue the X article" | Resume specific draft |
| "show my drafts" | List in-progress articles |
| "show my articles" | List exported articles |
| "list my writing styles" | List available style guides |
| "create a new article style" | Start style guide workflow |
| "edit my X style" | Modify existing style |
| "delete the X style" | Remove style guide |
| "show my archive" | List completed draft states |
| "re-export the X article" | Re-export from archive |

## Article Workflow Overview

```
Start → Topic Ideation → Style Selection → Title/Thesis → Outline → 
Section Confirmation → Write Article → Article Approval → [Editor Pass] → Article Metadata → Export Article → Finished
```

Each phase has an iteration loop (user + AI collaborate until satisfied).

### Phase Flow

1. **Topic Ideation** — Refine raw idea with AI. Save draft with `phase: "ideation"`.
2. **Style Selection** — Choose existing style or create new one. Load voice + context.
3. **Title & Thesis** — Craft title and thesis using voice/context. Iterate until approved.
4. **Outline** — Generate structure using style's opening/closing types. Iterate until approved.
5. **Section Confirmation** — Present sections from outline, allow user to split/combine.
6. **Write Article** — Choose writing mode (section-by-section or full draft), then write and iterate.
7. **Article Approval** — User reviews completed article and approves or requests changes.
8. **Editorial Decision** — Offer optional editor pass or skip to Article Metadata.
9. **Editor Pass** (optional) — Polish formatting, tighten prose, apply style guide. Creates `-editorpass.md`.
10. **Article Metadata Generation** — Generate title, description, keywords. Get approval.
11. **Export Article** — Fill template, save to `articles/`, clean up drafts, archive JSON.

For detailed phase instructions, see `references/article-workflow.md`.

## Style Guide System

Style guides control how articles are written across four categories:

**Voice** (0-10 sliders): tone, humor, opinion, technical

**Formatting** (0-10 sliders): density, emojis, em_dashes

**Structure** (multi-select): opening types, closing types

**Context** (mixed): author_role, author_topic_knowledge, audience_role, audience_topic_knowledge, author_relationship_to_audience

Style guides are applied progressively:
- Voice + Context → during thesis development
- Structure → during outline creation
- Formatting → during section writing

For schema details, see `references/style-schema.md`.
For style creation workflow, see `references/style-workflow.md`.

## Draft State

Drafts are JSON files tracking article progress:

```json
{
  "id": "unique-identifier-date",
  "created_at": "ISO timestamp",
  "updated_at": "ISO timestamp",
  "phase": "ideation|thesis|outline|writing|approval|editor|metadata|export",
  "style_guide": "style-filename",
  "initial_idea": "raw user input before refinement",
  "topic": "refined topic",
  "title": "approved title",
  "thesis": "thesis statement",
  "outline": [
    { "heading": "Section Name", "type": "opening|closing|null", "status": "pending|in_progress|complete" }
  ],
  "writing_mode": "section|full",
  "sections": {
    "section-slug": "written content"
  },
  "metadata": {
    "title": "article title",
    "description": "meta description",
    "keywords": ["keyword1", "keyword2"]
  },
  "filename": "user-approved-filename"
}
```

## Export

Use template from `assets/templates/article_default.md`.

Fill placeholders:
- `{{title}}` → article title
- `{{date}}` → current date (YYYY-MM-DD)
- `{{description}}` → meta description
- `{{keywords}}` → comma-separated keywords
- `{{author}}` → from style guide's author_role
- `{{content}}` → assembled sections

Filename: Suggest kebab-case from title (e.g., "When Context Becomes Content" → `when-context-becomes-content.md`). User can override. Extension always `.md`.

Save to: `cody-projects/article-writer/articles/[filename].md`
Archive draft to: `cody-projects/article-writer/archive/[draft-id].json`

## Resources

- `references/style-schema.md` — Complete style guide field definitions
- `references/style-workflow.md` — Style creation/editing workflow
- `references/article-workflow.md` — Detailed article writing phases
- `references/editor-style-guide.md` — Editorial pass guidelines and checks
- `assets/templates/article_default.md` — Default export template
