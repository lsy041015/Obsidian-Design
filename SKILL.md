---
name: obsidian-design
description: >-
  Create or improve polished, portable Obsidian and Markdown documents: project notes, guides, reports, design proposals, meeting records, and technical documentation. Use for document structure, clear prose, source-backed content, links, tables, and publication-ready Markdown; not application UI design or incidental code comments.
---

# Obsidian Design

Produce a finished document that helps its intended reader understand, decide, or act. Prefer clear structure and accurate content over decoration. Write in the user's language and preserve their terminology. Scale the work to the document; a short note does not need a report template.

## Establish the document contract

Infer purpose, audience, destination, and document type from the request and supplied material. If a target note exists, read it and only the relevant local conventions or neighboring notes. Preserve established frontmatter, links, block IDs, and user-authored content when editing. Ask only for information that blocks correct work; do not repeatedly request an already specified destination.

Choose the target format: standard Markdown for portability; Obsidian features when requested or established by the vault. Follow the user's template first. Never hard-code a project, vault path, date, status, or coordinate system from an example.

## Compose for the reader

1. Open with a descriptive title and the purpose, outcome, or decision the reader needs. Put essential context before detail.
2. Use a coherent heading hierarchy and descriptive headings. Organize by reader questions or workflow, not the order in which research happened. Add a table of contents only when length and navigation justify it.
3. Explain important claims with relevant evidence, examples, or reasoning. Define unfamiliar terms once; use consistent names, units, dates, and status labels. Separate observed facts, interpretation, assumptions, and unresolved questions. Never invent citations, measurements, owners, deadlines, or test results.
4. Use paragraphs for explanation, lists for steps or parallel items, and tables for genuine comparisons. Keep tables narrow; move long explanations into prose. Use callouts sparingly for decisions, cautions, or exceptions, not as decoration.
5. Add images, diagrams, or code only when they clarify the subject. Use meaningful alt text and captions for informative images, label code fences with the actual language, and preserve copyable commands. A screenshot is not proof of a successful test.
6. End with the outcome, next actions, or open questions when useful. Do not force a checklist, empty sections, `N/A` rows, repeated conclusion, or release gates into every note.

For structures and syntax details, read only the relevant section of [document patterns](references/document-patterns.md). For CAD/STL/URDF measurements or other project-specific evidence, additionally use [CAD rules](references/manual-rules.md); its project-specific conventions are not defaults for general writing.

## Markdown and Obsidian quality

- Prefer portable Markdown links and image embeds; use vault-relative paths for saved notes. Preserve established wikilinks and embeds when editing an Obsidian vault. Verify local targets and heading/block references; do not invent notes to make links look complete.
- Add YAML properties only when useful or required by the vault. Put frontmatter at the start and quote values containing YAML-sensitive syntax, including wikilinks. Preserve existing property types. Do not add arbitrary graph metadata to a generic Markdown file.
- Keep blank lines around headings, lists, tables, and fenced blocks. Escape literal pipes inside tables. Close fences and callouts correctly. Avoid raw HTML, CSS, plugin-dependent features, and ornamental badges unless the target renderer or user requires them.
- Use a descriptive filename consistent with the destination. Do not rename existing notes or move assets without handling inbound links within the authorized scope. Keep original evidence intact and write derived artifacts separately.

## Keep the skill portable

- Never copy user names, absolute host paths, vault-specific IDs, credentials, or private project details into this skill or its examples.
- Resolve local manuals and assets from the active vault or project root. Use placeholders in reusable examples, and disclose when a local reference is unavailable.
- Treat project-specific references as optional routing aids; do not apply their conventions to unrelated notes.

## Finish and verify

Read the saved document as its intended audience. Check factual consistency, unsupported claims, omissions, repeated content, heading flow, unfinished placeholders, links/assets, frontmatter, and Markdown syntax. Run an existing Markdown checker when available and relevant; do not install a toolchain for a single note. Preview in the target renderer if available and visual layout matters; otherwise state that rendering was not checked rather than claiming visual verification.

Review the diff for updates: preserve unrelated edits, historical corrections, IDs, and references. Documentation authorization does not authorize source-code edits, Git cleanup, publishing, or changes to source CAD/URDF. Respect host filesystem permissions without inventing additional approval gates. Deliver the file link and any material unresolved limitation; do not paste the whole document unless requested.
