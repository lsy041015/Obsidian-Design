# Document patterns

Select a structure that fits the reader's task; omit sections that add no value. These are starting points, not mandatory templates.

| Type | Useful progression |
| --- | --- |
| Project overview | Purpose → current state → scope → key decisions → resources → next steps |
| How-to | Expected result → prerequisites → numbered steps → verification → troubleshooting |
| Design proposal | Problem → constraints → alternatives and tradeoffs → chosen design → validation → open decisions |
| Research/report | Question → evidence and method → findings → limitations → implications |
| Meeting record | Context/date → decisions → essential discussion → actions and unresolved questions |
| Technical reference | Purpose → inputs/outputs → contracts and examples → edge cases → sources |

Keep a how-to executable: identify where a command runs, required inputs, the expected result, and recovery for likely failures. Do not execute a documented command just to format it. In meeting notes, omit or mark unknown owners and dates instead of guessing them.

## Properties and links

Respect the vault's existing schema. A generic report may need no YAML. A project note might use `type`, `status`, `tags`, and `project`, but only add values supported by the task. Frontmatter must be first, with matching `---` delimiters. Quote an Obsidian link used as a YAML value, such as `project: "[[Project index]]"`.

Use `[descriptive label](relative-note.md)` for portable links. In an established vault, preserve `[[Note]]`, `[[Note#Heading|label]]`, and `[[Note#^block-id]]`. Check targets using the vault's path conventions; Obsidian and GitHub may resolve headings differently. Do not apply one renderer's anchor rules blindly to the other.

For asset paths containing spaces, a portable image embed can use `![Description](<assets/example image.png>)`. Keep the asset accessible from the destination, not from a temporary working directory. Place a short italic caption below an informative image. Do not rename an asset solely for style if that would break other notes.

## Visual hierarchy

- Start with one document title unless the vault deliberately uses the filename as its displayed title. Do not duplicate a title already supplied by the user's template.
- Use sequential heading levels without arbitrary jumps. Prefer descriptive labels over a fixed numbered outline.
- Use numbered lists when order matters and checkboxes only for actionable work. Keep nesting shallow.
- In tables, put units in column labels and use consistent precision. Distinguish missing data from zero. Long commands and multiline explanations belong outside tables.
- For Obsidian, use a callout only for content that deserves distinct emphasis:

```markdown
> [!note] Scope
> This conclusion covers the tested configuration only.
```

For a standard Markdown target, use ordinary prose or a blockquote instead. Do not use callout colors as the only indication of severity.

Use Mermaid only for relationships or sequences that prose cannot explain as clearly and when the renderer supports it. Give diagrams readable labels and explain their implication in text. Do not add dependencies or generate decorative graphics just to make a note look polished.

## Editorial pass

Check that the opening answers why this document exists; each section adds new information; evidence supports the strength of each claim; instructions have enough context to follow; conclusions acknowledge relevant uncertainty; and action items are distinguishable from discussion. Remove repeated summaries, decorative separators, empty template fields, and speculative scope.

For an update, retain existing citations and record material corrections instead of silently erasing the prior result. Link directly to the source supporting a claim. A source list alone does not explain which claim a source supports.
