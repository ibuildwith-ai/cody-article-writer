# Cody Article Writer

© Copyright 2025 – Red Pill Blue Pill Studios, LLC – All Rights Reserved.

![Cody Article Writer Logo](images/cody-article-writer-logo.png)

![Version](https://img.shields.io/badge/version-1.5.2-blue)
[![License](https://img.shields.io/badge/license-Custom-orange)](LICENSE.md)
[![iBuildWith.ai](https://img.shields.io/badge/by-iBuildWith.ai-20c05b)](https://www.ibuildwith.ai)

**Cody Article Writer** is an AI Agent Skill (following the [agentskills.io](https://agentskills.io/specification) specification) that transforms how you write articles. Instead of staring at a blank page, you collaborate with AI through a structured, iterative workflow with customizable style guides. Each phase includes iteration loops where nothing moves forward until you're satisfied - from topic ideation all the way to markdown export.

## The Workflow

1. **Topic Ideation** — Refine rough concepts with AI brainstorming until focused
2. **Style Selection** — Choose or create reusable style guides that capture your voice
3. **Title & Thesis** — Craft compelling titles and clear thesis statements
4. **Outline** — Structure your article with opening/closing strategies
5. **Write Article** — Review sections, then iterate on each until complete
6. **Editor Pass** (optional) — AI-powered editing for formatting and polish
7. **Add Metadata** — Generate title, description, and keywords for frontmatter
8. **Export Article** — Choose your filename and generate clean markdown with frontmatter

## Installation

**Download:** [cody-article-writer.skill](cody-article-writer.skill)

### Claude AI Desktop App

1. Double-click the downloaded `.skill` file or "Open with Claude AI"
2. Start writing: "I want to write an article about..."

### Claude Code (VS Code)

Extract to your project or global skills directory:

```bash
# Project-level
unzip cody-article-writer.skill -d .claude/skills/

# Or global
unzip cody-article-writer.skill -d ~/.claude/skills/
```

## Features

### Customizable Style Guides

Create and save style guides that capture your unique voice:

- **Voice** — Tone (casual to professional), humor level, opinion strength, technical depth
- **Formatting** — Structure density, emoji usage, em dash frequency
- **Structure** — Opening styles (narrative, direct, tension, contextual) and closing styles (CTA, summary, callback, provocation, key takeaways)
- **Context** — Author role, audience role, expertise levels, relationship dynamics

Style guides are applied progressively throughout the workflow:
- **Voice + Context** during thesis development
- **Structure** during outline creation
- **Formatting** during section writing

### Iterative Workflow

Every phase includes iteration loops. AI acts as a firm sounding board, providing honest feedback and challenging weak ideas. Nothing moves forward until you're satisfied:

- Topic ideation with AI brainstorming
- Title and thesis refinement
- Outline structuring
- Section-by-section writing
- Optional editorial polish

### Editor Pass

An optional AI editing phase calibrated to your style guide that:

- Adds formatting (lists, bold, pull quotes) based on density settings
- Removes AI tells ("Additionally", "It's important to note...", excessive em dashes)
- Tightens prose and fixes grammar
- Ensures tone consistency
- Preserves your original as backup

### State Persistence

Your work is automatically saved throughout the entire process. Stop anytime and pick up exactly where you left off:

- **Resume at any phase** - Your current phase, topic, thesis, outline, and completed sections are preserved
- **Preview as you write** - See a readable markdown file of your work-in-progress without scrolling through chat
- **Complete article history** - Every finished article is archived with its original idea, thesis, sections, and metadata for potential re-export
- **No lost work** - All style guides are saved and reusable across articles

### Centralized Project Storage

All Cody Skills store their outputs in a single `cody-projects/` directory in your working folder. This keeps all your AI-assisted work organized in one place:

- `cody-projects/article-writer/` - Articles, styles, drafts, and archives from Cody Article Writer
- `cody-projects/product-builder/` - Product projects from Cody Product Builder
- Additional Cody Skills will add their own subdirectories

This centralized approach makes it easy to find all your Cody-generated work, back up your projects, and manage outputs across different skills.

## Example Commands

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

## Skill Structure

```
cody-article-writer/
├── SKILL.md                           # Main skill instructions
├── references/
│   ├── style-schema.md                # Style guide field definitions
│   ├── style-workflow.md              # Style creation workflow
│   ├── article-workflow.md            # Article writing phases
│   └── editor-style-guide.md          # Editorial pass guidelines
└── assets/
    └── templates/
        └── article_default.md         # Export template
```

## Requirements

- Claude AI Desktop App or Claude Code
- File system access for saving styles and drafts

## Collaboration Philosophy

Cody Article Writer acts as a **firm sounding board**, not a sycophant:

- Provides honest feedback on weak ideas
- Challenges assumptions and points out gaps
- Offers constructive critique instead of empty praise
- Maintains objective assessment even when you disagree
- Helps you produce your best work, not just feel good

## Author

**iBuildWith.ai**

Part of the Cody family of AI Agent Skills:
- Cody Product Builder — Build products with AI
- Cody Article Writer — Write articles with AI

## License

Cody Article Writer is licensed under a custom license that permits free use for article writing and content creation (including commercial use), but prohibits redistribution, modification, and sale of the software itself.

See [LICENSE.md](LICENSE.md) for complete terms.

## Release Notes

See [Release Notes.md](Release%20Notes.md) for version history and updates.

## Links

- [iBuildWith.ai](https://www.ibuildwith.ai)
- [Agent Skills Specification](https://agentskills.io/specification)
