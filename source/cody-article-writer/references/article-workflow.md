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

## Collaboration Principles

During all iteration phases, act as a firm sounding board, not a sycophant.

- **Be honest:** If an idea is weak, say so constructively. Don't just agree.
- **Push back:** Challenge assumptions, point out gaps, suggest alternatives.
- **Critique constructively:** When reviewing user's work, provide real feedback—not empty praise.
- **Stay objective:** Don't change your assessment just because the user disagrees.
- **Explain your reasoning:** When you disagree, articulate why with specifics.

The goal is to help the user produce their best work, not to make them feel good in the moment.

## Workflow Phases

### Phase 1: Topic Ideation

**Goal:** Refine the raw topic idea into something focused.

1. User provides initial topic idea
2. Capture raw input as `initial_idea` (preserve exactly as user typed it)
3. Iterate with AI:
   - Explore angles
   - Narrow or expand scope
   - Identify unique perspective
4. Check: "Ready to form a thesis?"
   - No → continue refining
   - Yes → proceed to style selection

**Draft state:** Save with `phase: "ideation"`, capture `initial_idea` (raw input) and `topic` (refined version)

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

Would you like to split or combine any sections before we start writing?
```

Update outline based on any changes.

**Draft state:** Update `outline` with confirmed sections

### Phase 6: Write Article

**Goal:** Write the article content.

Extract **formatting** settings from style guide:
- Formatting density
- Emoji usage
- EM dash frequency

#### Writing Mode Decision

Ask user how they want to write:

```
How would you like to write this article?

1. **Section by section** — We'll write and refine each section together before moving to the next
2. **Full draft first** — I'll write the entire article, then you can review and we'll iterate on the whole thing
```

#### Mode A: Section by Section

For each section:
1. Write section draft (AI)
2. Present to user
3. Iterate until approved
4. Mark section `status: "complete"`
5. Update working draft file: `drafts/[draft-id].md`
6. Move to next section

When all sections complete → AI declares "Article Completed" → proceed to Article Approval

#### Mode B: Full Draft First

1. Write entire article at once (AI)
2. Populate all `sections` in the JSON (same structure as Mode A, just all at once)
3. Save to `drafts/[draft-id].md`
4. AI declares "Article Completed" → proceed to Article Approval

**Working draft file:** Create `drafts/[draft-id].md` during writing. This gives the user a readable file to review instead of dumping content in chat.

**Draft state:** Update `phase: "writing"`, save `writing_mode` ("section" or "full"), save completed sections to `sections` object

### Phase 7: Article Approval

**Goal:** Get user approval on the completed article.

```
The article is complete! I've saved it here:

📄 cody-projects/article-writer/drafts/[draft-id].md

Please review it. Are you satisfied with the article, or would you like to make changes?
```

- **Approved** → proceed to Editorial Decision (Phase 8)
- **Needs changes** → user specifies what to change (e.g., "In section 2, make X more concise"), AI updates the specific section in `sections` object, regenerates `[id].md`, loop until approved

**Draft state:** Update `phase: "approval"`

### Phase 8: Editorial Decision

After article is approved:

```
Would you like me to run an editorial pass? I'll review formatting, tighten the prose, and ensure it follows your style guide.

Or we can skip ahead to article metadata and export.
```

- Editorial pass → proceed to Phase 9
- Skip to Article Metadata → proceed to Phase 10 (uses `[id].md` as source)

### Phase 9: Editor Pass (Optional)

**Goal:** Polish the article with formatting, tightening, and style guide adherence.

See `references/editor-style-guide.md` for complete editorial guidelines.

1. Read the original `drafts/[draft-id].md`
2. Apply editorial checks (formatting, pull quotes, AI tell removal, tightening, etc.)
3. Calibrate changes based on style guide settings (density, em_dashes, emojis)
4. Create new file: `drafts/[draft-id]-editorpass.md`
5. Preserve original `[draft-id].md` as backup
6. Output summary of changes to chat

```
Editorial pass complete! Here's what I updated:

**Formatting:**
- Added 2 bulleted lists
- Bolded 5 key terms
- Added 1 pull quote

**Tightening:**
- Removed 3 instances of "Additionally"
- Replaced 2 em dashes with commas

📄 Review the edited version: cody-projects/article-writer/drafts/[draft-id]-editorpass.md
📄 Original preserved at: cody-projects/article-writer/drafts/[draft-id].md

Approve the changes, or let me know what to adjust.
```

- Approve → proceed to Phase 10 (uses `[id]-editorpass.md` as source)
- Iterate → make requested changes to `-editorpass.md`, show updated summary

**Draft state:** Update `phase: "editor"`

### Phase 10: Article Metadata Generation

**Goal:** Generate metadata for the article frontmatter.

Generate:
- **title:** Article title (confirm or refine the working title)
- **description:** Meta description (150-160 characters)
- **keywords:** Array of relevant keywords/tags

Present for approval:

```
Article Metadata:
- Title: "Your Article Title Here"
- Description: "A compelling meta description..."
- Keywords: [keyword1, keyword2, keyword3]

Approve or adjust?
```

After metadata is approved, suggest a filename:

```
Suggested filename: your-article-title-here.md

Use this, or provide your own filename (extension will always be .md):
```

**Draft state:** Update `phase: "metadata"`, save `metadata` object and `filename`

### Phase 11: Export Article

**Goal:** Generate final markdown file.

1. Determine source file:
   - If editor pass was done → use `drafts/[draft-id]-editorpass.md`
   - If editor pass was skipped → use `drafts/[draft-id].md`
2. Load template from skill's `assets/templates/article_default.md`
3. Fill placeholders:
   - `{{title}}` → article title
   - `{{date}}` → current date
   - `{{description}}` → meta description
   - `{{keywords}}` → keywords array
   - `{{author}}` → from style guide context
   - `{{content}}` → content from source file
4. Save to `cody-projects/article-writer/articles/[filename].md`
5. Move `drafts/[draft-id].json` to `cody-projects/article-writer/archive/`
6. Delete `drafts/[draft-id].md`
7. Delete `drafts/[draft-id]-editorpass.md` (if exists)

**Final message:**
```
Article exported successfully!
- Article: cody-projects/article-writer/articles/[filename].md
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
