# Style Guide Schema

Style guides are saved as JSON files in `cody-projects/article-writer/styles/`.

## File Naming

- Filename: kebab-case version of the style name
- Example: "Professional LinkedIn" → `professional-linkedin.json`
- No special characters, lowercase only

## JSON Structure

```json
{
  "name": "Style Name",
  "description": "Brief description of when to use this style",
  "voice": {
    "tone": 5,
    "humor": 5,
    "opinion": 5,
    "technical": 5
  },
  "formatting": {
    "density": 5,
    "emojis": 0,
    "em_dashes": 2
  },
  "structure": {
    "opening": ["narrative"],
    "closing": ["call_to_action"]
  },
  "context": {
    "author_role": "Role description",
    "author_topic_knowledge": 5,
    "audience_role": "Audience description",
    "audience_topic_knowledge": 5,
    "author_relationship_to_audience": 5
  }
}
```

## Field Definitions

### Voice (0-10 sliders)

| Field | 0 | 10 | Description |
|-------|---|-----|-------------|
| tone | Casual | Professional | Formality level |
| humor | Playful | Serious | Use of wit and levity |
| opinion | Balanced | Opinionated | Strength of viewpoint |
| technical | Less | More | Depth of technical detail |

### Formatting (0-10 sliders)

| Field | 0 | 10 | Description |
|-------|---|-----|-------------|
| density | Minimal | Heavy | Use of headers, lists, bold |
| emojis | None | Heavy | Emoji frequency |
| em_dashes | None | Frequent | Em dash usage (AI tell when overused) |

### Structure (categorical, multi-select)

| Field | Valid Values | Description |
|-------|--------------|-------------|
| opening | `direct`, `contextual`, `narrative`, `tension` | How to begin the article |
| closing | `summary`, `call_to_action`, `open_question`, `callback`, `provocation`, `key_takeaways` | How to end the article |

**Opening types:**
- `direct` — State the main point immediately
- `contextual` — Set the scene, provide background first
- `narrative` — Open with a story or anecdote
- `tension` — Create stakes, pose a problem

**Closing types:**
- `summary` — Recap key points
- `call_to_action` — Tell reader what to do next
- `open_question` — Leave them thinking
- `callback` — Reference the opening
- `provocation` — Challenge assumptions
- `key_takeaways` — Bullet list of main insights

### Context

| Field | Type | Range/Format | Description |
|-------|------|--------------|-------------|
| author_role | string | Free text | e.g., "AI Educator", "Product Manager" |
| author_topic_knowledge | integer | 0 (Learning) to 10 (Expert) | Author's expertise level |
| audience_role | string | Free text | e.g., "Enterprise PMs", "Indie Hackers" |
| audience_topic_knowledge | integer | 0 (Learning) to 10 (Expert) | Audience's expertise level |
| author_relationship_to_audience | integer | 0 (Peer) to 10 (Expert) | Authority dynamic |

## Validation Rules

- All slider values must be integers 0-10
- `name` is required and must be non-empty
- `opening` and `closing` must contain at least one valid value
- `author_role` and `audience_role` should be non-empty strings
