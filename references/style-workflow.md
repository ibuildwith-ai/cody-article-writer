# Style Guide Workflow

This workflow guides users through creating or editing a style guide.

## Triggers

- "create a new writing style"
- "create a new article style called X"
- "edit my X style"
- "update the X writing style"

## Workflow Phases

### Phase 1: Configuration

Guide the user through each category. These can be set in any order, but present them sequentially for clarity.

**Voice Settings:**
```
Let's configure the voice for your style.

1. Tone (0-10): How formal should the writing be?
   0 = Casual, conversational | 10 = Professional, formal

2. Humor (0-10): How much levity?
   0 = Playful, witty | 10 = Serious, straightforward

3. Opinion (0-10): How strong is your viewpoint?
   0 = Balanced, presenting multiple sides | 10 = Opinionated, clear stance

4. Technical (0-10): How deep into technical details?
   0 = Accessible to all | 10 = Technical depth assumed
```

**Formatting Settings:**
```
Now let's set formatting preferences.

1. Density (0-10): How much visual structure?
   0 = Minimal (prose-focused) | 10 = Heavy (headers, lists, bold)

2. Emojis (0-10): Emoji usage?
   0 = None | 10 = Frequent

3. EM Dashes (0-10): Em dash frequency?
   0 = Avoid entirely | 10 = Use freely
   (Note: Overuse is a common AI tell)
```

**Structure Settings:**
```
Let's define article structure.

Opening style (select one or more):
- Direct: State the main point immediately
- Contextual: Set the scene first
- Narrative: Open with a story
- Tension: Create stakes, pose a problem

Closing style (select one or more):
- Summary: Recap key points
- Call to Action: Tell reader what to do
- Open Question: Leave them thinking
- Callback: Reference the opening
- Provocation: Challenge assumptions
```

**Context Settings:**
```
Finally, let's set the context.

1. Author Role: How do you want to be positioned?
   (e.g., "AI Educator", "Startup Founder", "Product Manager")

2. Author Topic Knowledge (0-10):
   0 = Learning alongside reader | 10 = Established expert

3. Audience Role: Who are you writing for?
   (e.g., "Enterprise PMs", "Indie Hackers", "Technical Leaders")

4. Audience Topic Knowledge (0-10):
   0 = New to the topic | 10 = Deep expertise

5. Author-Audience Relationship (0-10):
   0 = Peer, equal footing | 10 = Expert teaching
```

### Phase 2: Review & Finalize

Present the complete style guide configuration:

```
Here's your style guide configuration:

**Name:** [Style Name]
**Description:** [Brief description]

**Voice:**
- Tone: 7/10 (leaning professional)
- Humor: 3/10 (mostly serious)
- Opinion: 8/10 (opinionated)
- Technical: 5/10 (balanced)

**Formatting:**
- Density: 4/10 (moderate structure)
- Emojis: 0/10 (none)
- EM Dashes: 2/10 (minimal)

**Structure:**
- Opening: Narrative + Tension
- Closing: Callback + Call to Action

**Context:**
- Author Role: AI Educator and Startup Founder
- Author Knowledge: 8/10
- Audience Role: Enterprise Product Managers
- Audience Knowledge: 4/10
- Relationship: 7/10 (expert positioning)

Does this look correct? Say "save" to save it, or tell me what to adjust.
```

### Phase 3: Save

On confirmation:
1. Generate filename from style name (kebab-case)
2. Validate all required fields
3. Save to `cody-projects/article-writer/styles/[name].json`
4. Confirm: "Saved style guide as `professional-linkedin.json`"

## Style Management Commands

### List Styles
Trigger: "list my writing styles", "show my styles"

Action: List all JSON files in `cody-projects/article-writer/styles/`

### Edit Style
Trigger: "edit my X style"

Action:
1. Load the style JSON
2. Show current configuration
3. Ask what to change
4. Update and save

### Delete Style
Trigger: "delete the X style"

Action:
1. Confirm deletion: "Are you sure you want to delete 'X'? This cannot be undone."
2. On confirmation, remove the JSON file
