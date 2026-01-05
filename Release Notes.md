# Release Notes

> ### Version 1.7
>> Enhanced style guide system with improved structure settings and editorial content enhancement pass.
>>> January 5, 2026

---

### Added
- **Structure settings expanded:**
  - `visual_breaks` (minimal/moderate/generous) — Controls white space and paragraph spacing (replaces confusing "density" field)
  - `examples` (none/some/many) — Default preference for including examples
  - `example_types` (lists, tables, diagrams, code_snippets, quotes, case_studies) — Preferred example types with implementation details (Mermaid diagrams, 2-4 paragraph case studies)
- **Formatting setting:**
  - `blockquotes` (never/rare/occasional/frequent) — Preference for using blockquotes/pull quotes
- **Editorial content enhancement pass** — AI now suggests contextual examples (lists, tables, code snippets, diagrams, quotes, case studies) and blockquotes during editorial review based on style guide preferences
- **Bold/italic guidelines** — Clear instructions for when and how to use text emphasis
- **Collaboration Principles** — Explicit anti-sycophancy guidelines now loaded immediately when skill triggers, ensuring AI challenges weak ideas and provides honest feedback from the start
- **AI-recommended style guide settings** — Option to get AI-suggested style configurations based on writing purpose and audience before manual configuration
- **Recommended editor pass** — Editorial decision phase now emphasizes benefits and recommends running the editor pass with clear explanation of improvements

### Changed
- **Removed** `formatting.density` — Replaced with `structure.visual_breaks` for clearer intent (white space vs. formatting richness)
- **Editorial workflow enhanced** — Editor pass now includes content enhancement suggestions (examples, blockquotes) tailored to each article
- **Style guide structure** — Moved visual/structural decisions to Structure category where they belong

### Fixed
- Eliminated confusion around "density" property which users interpreted as article density rather than formatting richness

---

> ### Version 1.6
>> Choose your writing style: collaborate section-by-section or let AI draft the full article first, then iterate until you're satisfied.
>>> December 27, 2025

---

### Added
- Writing mode choice to decide whether to write section-by-section or have AI write the full draft first
- Article Approval phase — explicit checkpoint where you approve the completed article before moving to editor review

### Changed
- Workflow expanded to accommodate the new approval step

### Fixed
- No fixes in this release.

---

> ### Version 1.5.2
>> Refocused the final steps on article metadata, leaving SEO optimization for a dedicated skill in the future.
>>> December 26, 2025

---

### Added
- Filename selection step — you can now choose your exported article's filename (a kebab-case suggestion is provided based on your title, but you can override it)

### Changed
- "SEO Generation" phase renamed to "Article Metadata Generation" — focuses on title, description, and keywords for your article frontmatter
- "Export" phase renamed to "Export Article" for clarity
- Removed slug generation — SEO-specific features will be handled by a dedicated SEO skill in the future

### Fixed
- No fixes in this release.

---

> ### Version 1.5.1
>> Improved collaboration quality through constructive AI feedback.
>>> December 25, 2025

---

### Added
- AI now acts as a firm sounding board during all workflow phases, providing honest feedback and challenging weak ideas instead of simply agreeing with everything you propose.

### Changed
- No changes in this release.

### Fixed
- No fixes in this release.

---

> ### Version 1.5
>> Enhanced editing workflow with optional AI-powered editorial pass and improved draft preview experience.
>>> December 25, 2025

---

### Added
- **Optional Editor Pass** - New phase after writing where AI polishes your article based on your style guide settings. Removes common AI writing tells, tightens prose, adds formatting (lists, bold, pull quotes), and fixes grammar. Your original is preserved as backup.
- **Working Draft Files** - As you write each section, see a clean markdown preview file instead of scrolling through chat history to review your work.
- **Editorial Decision Point** - After completing all sections, choose whether to run the editor pass for polish or skip directly to SEO and export.

### Changed
- Workflow expanded from 9 to 10 phases to accommodate the optional editor pass.
- Export now uses either your original draft or the editor-polished version, depending on your choice.
- Draft JSON now captures your initial raw idea separately from the refined topic, preserving your complete thought process.

### Fixed
- No fixes in this release.

---

> ### Version 1.0.1
>> Metadata and versioning improvements.
>>> December 25, 2025

---

### Added
- Version tracking in skill metadata for better release management.

### Changed
- No changes in this release.

### Fixed
- No fixes in this release.

---

> ### Version 1.0
>> Initial release of Cody Article Writer with complete workflow and style guide system.
>>> December 23, 2025

---

### Added
- **Complete Article Workflow** - 9-phase guided process from topic ideation through SEO-optimized export.
- **Customizable Style Guides** - Save reusable writing styles with 14 configurable settings across voice, formatting, structure, and context.
- **State Persistence** - Automatically save your progress at every phase and resume exactly where you left off.
- **Style Management** - Create new styles through guided workflow or starter templates. Edit and delete existing styles.
- **Draft Management** - Continue working on any in-progress article, view all drafts, and access exported articles.
- **Archive System** - Every completed article is archived with full context (original idea, thesis, sections, SEO) for potential re-export.
- **SEO Generation** - AI-generated metadata including title, description, slug, and keywords.
- **Markdown Export** - Clean export with frontmatter for publishing platforms.

### Changed
- Not applicable for initial release.

### Fixed
- Not applicable for initial release.
