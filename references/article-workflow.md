# Article Writing Workflow

This workflow guides users through writing an article from idea to export.

## Triggers

- "I want to write an article about X"
- "help me write an article on X"
- "let's write a blog post about X"
- "start a new article"

## Directory Initialization

On first use, check and create directories as needed:

```
1. Check if cody-projects/ exists → if not, create it
2. Check if cody-projects/article-writer/ exists → if not, create it with:
   ├── styles/
   ├── drafts/
   ├── articles/
   └── archive/
```

Message on creation: "I've created `./cody-projects/article-writer/` to store your styles and drafts."

## Workflow Phases

### Phase 1: Topic Ideation

**Goal:** Refine the raw topic idea into something focused.

1. User provides initial topic idea
2. Iterate with AI:
   - Explore angles
   - Narrow or expand scope
   - Identify unique perspective
3. Check: "Ready to form a thesis?"
   - No → continue refining
   - Yes → proceed to style selection

**Draft state:** Save with `phase: "ideation"`, capture `topic`

### Phase 2: Style Guide Selection

**Goal:** Select or create the style guide for this article.

1. Check if any styles exist in `cody-projects/article-writer/styles/`

2. **If styles exist:**
   ```
   I found these existing styles:
   
   1. **Professional LinkedIn**
      For thought leadership articles targeting enterprise product managers
   
   2. **Casual Newsletter**
      Conversational tone for weekly subscriber updates
   
   Would you like to use one of these, or create a new style?
   ```
   - User selects existing → Load that style
   - User wants new → Offer creation options (see below)

3. **If no styles exist:**
   ```
   You don't have any styles saved yet. Let's create one for this article.
   ```
   - Offer creation options (see below)

4. **Style creation options:**
   ```
   How would you like to create your style?
   
   1. **Guided creation** — I'll walk you through each setting with questions
   2. **Starter style** — I'll suggest a style based on what you've told me, then you can adjust
   ```
   - Option 1 → Trigger full Style Guide Workflow (Phase 1: Configuration)
   - Option 2 → Generate suggested style from topic/context, go directly to Phase 2: Review Settings

5. Load selected/created style
6. Extract **voice** and **context** settings for thesis phase

**Draft state:** Update `style_guide` reference

### Phase 3: Title & Thesis

**Goal:** Craft a compelling title and clear thesis statement.

Apply voice and context from style guide to inform:
- Tone and formality of title
- Strength of thesis claim
- Audience-appropriate framing

1. Generate title and thesis options
2. Iterate until user approves
3. Check: "Ready for outline?"
   - No → continue refining
   - Yes → proceed

**Draft state:** Update `phase: "thesis"`, save `title` and `thesis`

### Phase 4: Outline

**Goal:** Create the article structure.

Extract **structure** settings from style guide:
- Opening type(s) → shapes introduction approach
- Closing type(s) → shapes conclusion approach

1. Generate outline based on thesis and structure settings
2. Iterate until user approves
3. Check: "Start writing?"
   - No → continue refining
   - Yes → proceed to section confirmation

**Draft state:** Update `phase: "outline"`, save `outline` array

### Phase 5: Section Confirmation

**Goal:** Confirm section breakdown before writing.

Present sections derived from outline:

```
I see [N] sections in your outline:
1. Introduction (Opening)
2. [Section heading]
3. [Section heading]
4. [Section heading]
5. Conclusion (Closing)

Want me to write these one at a time, or would you like to split/combine any sections?
```

Update outline based on any changes.

**Draft state:** Update `outline` with confirmed sections

### Phase 6: Write Article

**Goal:** Write each section iteratively.

Extract **formatting** settings from style guide:
- Formatting density
- Emoji usage
- EM dash frequency

For each section:
1. Write section draft (AI)
2. Present to user
3. Iterate until approved
4. Mark section `status: "complete"`
5. Update working draft file: `drafts/[draft-id].md`
6. Move to next section

**Working draft file:** Create `drafts/[draft-id].md` when first section is written. Update it after each section is completed. This gives the user a readable file to review instead of dumping content in chat.

**Draft state:** Update `phase: "writing"`, save completed sections to `sections` object

### Phase 7: Completion Check

After all sections written:

```
All sections are complete! I've assembled the full article here:

📄 cody-projects/article-writer/drafts/[draft-id].md

Please review it and let me know if you'd like to revise any sections, or if you're ready to generate SEO and export.
```

- Revise → return to specific section, update the .md file after changes
- Continue → proceed to SEO

### Phase 8: SEO Generation

**Goal:** Generate metadata for publishing.

Generate:
- **title:** SEO-optimized title (may differ from article title)
- **description:** Meta description (150-160 characters)
- **slug:** URL-friendly version of title
- **keywords:** Array of relevant keywords/tags

Present for approval:

```
SEO Metadata:
- Title: "Your SEO Title Here"
- Description: "A compelling meta description..."
- Slug: your-seo-title-here
- Keywords: [keyword1, keyword2, keyword3]

Approve or adjust?
```

**Draft state:** Update `phase: "seo"`, save `seo` object

### Phase 9: Export

**Goal:** Generate final markdown file.

1. Load template from skill's `assets/templates/article_default.md`
2. Fill placeholders:
   - `{{title}}` → article title
   - `{{date}}` → current date
   - `{{description}}` → SEO description
   - `{{slug}}` → SEO slug
   - `{{keywords}}` → SEO keywords array
   - `{{author}}` → from style guide context
   - `{{content}}` → assembled article sections
3. Save to `cody-projects/article-writer/articles/[slug].md`
4. Move draft JSON to `cody-projects/article-writer/archive/`
5. Delete working draft .md from `cody-projects/article-writer/drafts/`

**Final message:**
```
Article exported successfully!
- Article: cody-projects/article-writer/articles/[slug].md
- Draft archived: cody-projects/article-writer/archive/[draft-id].json
```

## Draft Management Commands

### Show Drafts
Trigger: "show my drafts", "list drafts"

Action: List all JSON files in `cody-projects/article-writer/drafts/` with title, phase, and last updated.

### Continue Draft
Trigger: "continue my article", "continue the X article"

Action:
1. Load draft JSON
2. Resume at saved phase
3. Restore all context (style guide, title, thesis, outline, sections)

### Show Articles
Trigger: "show my articles", "list my articles"

Action: List all markdown files in `cody-projects/article-writer/articles/`

### Show Archive
Trigger: "show my archive"

Action: List all JSON files in `cody-projects/article-writer/archive/`

### Re-export
Trigger: "re-export the X article"

Action:
1. Load from archive
2. Optionally select different template
3. Re-run export phase
