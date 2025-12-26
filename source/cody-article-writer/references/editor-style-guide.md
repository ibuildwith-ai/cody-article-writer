# Editor Style Guide

This guide defines the editorial pass workflow. The editor reviews the article after writing is complete and applies formatting, tightening, and style guide adherence.

## Files

| File | Purpose |
|------|---------|
| `[id].md` | Original writer output (preserved as backup) |
| `[id]-editorpass.md` | Editor's revised version |

Always create `-editorpass.md` as a new file. Never overwrite the original.

## Editorial Checks

### 1. Formatting (calibrated by `formatting.density`)

| Density | Formatting Level |
|---------|------------------|
| 0-2 | Minimal — avoid lists, minimal bold, no pull quotes |
| 3-5 | Moderate — occasional lists, bold key terms, 1 pull quote |
| 6-8 | Substantial — use lists where helpful, bold important points, 1-2 pull quotes |
| 9-10 | Heavy — liberal use of lists, headers, bold, italics, 2+ pull quotes |

**Actions:**
- Add bulleted/numbered lists where items are enumerated
- Add subheadings (H3) to break up long sections
- Bold key terms and important phrases
- Italicize for emphasis (sparingly)
- Remove excessive formatting if density is low

### 2. Pull Quotes

If `formatting.density` > 3, identify 1-2 standout sentences to highlight:

```markdown
> "This is a compelling quote that captures a key insight."
```

Good pull quotes:
- Capture a key insight succinctly
- Are provocative or memorable
- Work out of context

### 3. Em Dashes (calibrated by `formatting.em_dashes`)

| Setting | Action |
|---------|--------|
| 0-2 | Replace em dashes with commas, parentheses, or periods |
| 3-5 | Use sparingly (max 1-2 per article) |
| 6-10 | Acceptable to use where appropriate |

### 4. Emoji Usage (calibrated by `formatting.emojis`)

| Setting | Action |
|---------|--------|
| 0 | Remove all emojis |
| 1-3 | Max 1-2 emojis in entire article |
| 4-6 | Occasional use in headers or key points |
| 7-10 | Liberal use throughout |

### 5. AI Tell Removal (always applied)

Remove or rephrase these common AI patterns:

**Filler phrases to remove:**
- "It's important to note that..."
- "It's worth mentioning that..."
- "Interestingly enough..."
- "In today's world..."
- "In this article, we will..."

**Transition words to reduce:**
- "Additionally" → vary with "Also," "Beyond this," or restructure
- "Furthermore" → often unnecessary, delete or restructure
- "Moreover" → same as above
- "However" → fine occasionally, but vary with "But," "Yet," "Still"
- "Therefore" → vary with "So," "This means," or restructure

**Overused structures:**
- Starting multiple paragraphs with "This..."
- "When it comes to [X]..."
- "[X] is a [Y] that [Z]" (weak opener pattern)

### 6. Tone Consistency (calibrated by `voice.tone`)

Review entire article for tone drift:
- Casual (0-3): Conversational, contractions okay, "you" and "I"
- Balanced (4-6): Professional but approachable
- Professional (7-10): Formal, minimal contractions, third person acceptable

Flag sections where tone shifts unexpectedly.

### 7. Prose Tightening (always applied)

**Remove:**
- Redundant words ("very unique" → "unique")
- Weasel words ("somewhat," "quite," "rather")
- Unnecessary qualifiers ("I think," "I believe" — unless voice calls for it)
- Repeated words in close proximity

**Improve:**
- Passive voice → active voice (where appropriate)
- Long sentences → break into shorter ones
- Weak verbs → stronger alternatives

### 8. Spelling & Grammar (always applied)

- Fix typos
- Correct grammar errors
- Ensure consistent punctuation style

### 9. Flow & Transitions

- Ensure smooth transitions between sections
- Check that each section connects logically to the next
- Break up walls of text (no paragraphs > 5-6 sentences)

## Output Summary

After completing the editor pass, provide a summary of changes:

```
Editorial pass complete! Here's what I updated:

**Formatting:**
- Added 2 bulleted lists
- Bolded 5 key terms
- Added 1 pull quote

**Tightening:**
- Removed 3 instances of "Additionally"
- Replaced 2 em dashes with commas
- Shortened 4 long sentences

**Fixes:**
- Corrected 2 typos
- Fixed 1 grammar issue

📄 Review the edited version: cody-projects/article-writer/drafts/[id]-editorpass.md
📄 Original preserved at: cody-projects/article-writer/drafts/[id].md

Approve the changes, or let me know what to adjust.
```

## Iteration

If user requests changes:
1. Update `[id]-editorpass.md` directly
2. Keep original `[id].md` untouched
3. Show updated summary of what changed
