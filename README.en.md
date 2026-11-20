<p align="center">
  <img src="assets/obsidian-design-banner.png" alt="Obsidian Design — a Codex skill for polished, portable Markdown documents" width="100%">
</p>

<p align="center"><a href="README.md">한국어</a> · <b>English</b></p>

# Obsidian Design

A Codex skill that makes the agent write or edit Obsidian and Markdown documents a reader can actually understand and act on.

Documents written by an agent tend to get the shape right before the content. So there were three things I wanted this skill to stop.

- **Decoration first** — badges, empty sections, `N/A` rows, forced checklists. A short note doesn't get a report template.
- **Notes broken by an edit** — existing frontmatter, wikilinks, block IDs, attachments and user content stay put, and the diff gets reviewed.
- **Plausible filler** — no invented citations, measurements, owners, deadlines or test results. Unknowns are left out or marked.

The skill is one [`SKILL.md`](SKILL.md) plus two reference files. Before writing, the agent settles purpose, audience,
destination and document type; then it orders sections by the reader's questions, tidies links and frontmatter, and rereads
the result as the reader. If it couldn't check the rendering, it says so. A screenshot isn't proof that a test passed.

It also minds the small stuff. Portable Markdown links come first, but wikilinks already in the vault are left alone; wikilinks
inside YAML get quoted, like `project: "[[Project index]]"`; and pipes inside tables are escaped. Tables are for real comparisons
only, callouts for decisions, warnings and exceptions. And a request to edit docs doesn't count as permission to change source
code, clean up Git or publish anything.

[`document-patterns.md`](references/document-patterns.md) has section flows per document type. They're starting points, not
required templates, and unused sections get dropped.

| Type | Section flow |
|---|---|
| Project overview | Purpose → current state → scope → key decisions → resources → next steps |
| How-to | Expected result → prerequisites → numbered steps → verification → troubleshooting |
| Design proposal | Problem → constraints → alternatives and tradeoffs → chosen design → validation → open decisions |
| Research/report | Question → evidence and method → findings → limitations → implications |
| Meeting record | Context/date → decisions → essential discussion → actions and unresolved questions |
| Technical reference | Purpose → inputs/outputs → contracts and examples → edge cases → sources |

[`manual-rules.md`](references/manual-rules.md) is only read for CAD/STL/URDF docs. Things like `1 µm` URDF checks and a `16 MB`
HTML budget are project conventions, so they live in their own file and never become defaults for normal writing. A wrong
measurement is never silently deleted; the doc records what was wrong. The manual those rules point to isn't in this repo, so
when it's missing the agent says so instead of claiming it checked.

## Install

This is set up for Codex. Clone it into a folder named `obsidian-design`, same as the skill.

```bash
git clone https://github.com/lsy041015/Obsidian-Design.git obsidian-design
cp -R obsidian-design "${CODEX_HOME:-$HOME/.codex}/skills/"
```

Add `$obsidian-design` to your request to call it. Implicit invocation is on, so Codex may also pick it by itself.
Telling it the audience, destination or the note to edit means less guessing.

Validate with the checker from Codex's `skill-creator` (not included here, so adjust the path).

```bash
python /path/to/skill-creator/scripts/quick_validate.py obsidian-design
```

Claude Code uses the same frontmatter format, so it should load as `/obsidian-design` from the path below, but I haven't tried it there yet.

```bash
git clone https://github.com/lsy041015/Obsidian-Design.git ~/.claude/skills/obsidian-design
```

## Not there yet

No version number, tests or example outputs. The behavior is described only by the rules in `SKILL.md`.
MIT license ([LICENSE](LICENSE)).

<sub>[More projects](https://github.com/lsy041015)</sub>
