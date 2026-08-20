# PDF to HTML Conversion Skill

A prompt-based skill that instructs an AI agent to convert a PDF document into a clean,
accessible HTML fragment — plus extracted images and an image manifest — ready to paste into
a **WordPress** Custom HTML block or a **Canvas LMS** page.

## What problem it solves

Remediating a PDF is a poor use of everyone's time. Tagging structure, fixing reading order,
adding alt text, and re-checking the whole thing is slow, hard to verify, easily broken by the
next revision — and at the end of it you still have a PDF: a fixed-page format that reflows
badly on a phone and reads worse than a web page ever would.

Converting to HTML is the more manageable path. The web platform handles the hard parts for
free — headings are real headings, text reflows, zoom works, screen readers get semantics
rather than a tag tree someone assembled by hand. The obstacle has always been conversion
cost. Doing it well manually takes hours per document, and asking an AI to "convert this PDF
to HTML" without guidance produces either a visual copy of the PDF (fixed dimensions, bold
text standing in for headings, running footers left in place) or quietly lost content (text
broken at page boundaries, two-up scans read out of order, conceptual diagrams flattened into
data tables).

This skill makes the path practical. It gives the agent an explicit workflow, an output
contract, and a QA checklist, so conversion becomes cheap enough to be the default choice
instead of the ambitious one.

## What you get back

| Deliverable | Notes |
| --- | --- |
| `.html` fragment | Content only — no `<html>`, `<head>`, `<body>`, CSS, or scripts |
| `.txt` companion | Identical HTML source, for Canvas users without a code editor |
| Image files | Substantive figures and spatial frameworks, cropped and named |
| Image manifest | Filename, placeholder string, caption, alt text, upload steps |
| Validation summary | Checks performed, open questions, platform-level warnings |
| Conversion report | For difficult scans: candid success assessment and publisher actions |

## How to use it

The skill is a single instruction file, [SKILL.md](SKILL.md). There is no code to install.

**Option 1 — paste it into a chat.** Start a new conversation with an AI assistant that can
read PDFs and produce file downloads (Claude, ChatGPT, or similar). Paste the contents of
`SKILL.md`, attach your PDF, and state your target platform. Then say what you want:

> Convert the attached PDF following the skill above. Target platform: Canvas LMS.
> Scope: Chapter 7 only, plus its references. The Canvas page title is already set.

**Option 2 — use the short version.** The final section of `SKILL.md`
("Reusable Execution Prompt") condenses the whole thing into two paragraphs. Use that when
you want a faster, lower-token run and you trust the model to fill in the details.

**Option 3 — install it as an agent skill.** Drop `SKILL.md` into your agent's skills
directory so it loads automatically when a PDF conversion comes up. For Claude Code that is
`.claude/skills/pdf-to-html/SKILL.md`; note that the Agent Skills format expects YAML
frontmatter (`name` and `description`) at the top of the file, which this version does not
yet have.

### What to tell the agent

The conversion goes better when you supply these up front:

- **Target platform** — WordPress, Canvas LMS, or both.
- **Publication scope** — which chapter or section, and whether front matter, references,
  and appendices are in or out.
- **Page title** — if the WordPress post or Canvas page title is already set, the fragment
  starts at `<h2>` instead of duplicating an `<h1>`.
- **Figure handling** — whether you want figures extracted as separate image files.
- **Better sources** — a born-digital PDF, the publisher manuscript, or original figure
  files will beat anything OCR can recover from a scan.

### Publishing the result

Text first, images second:

1. Paste the HTML into the **Canvas HTML Editor** (not the Rich Content Editor), or into a
   WordPress **Custom HTML block**, and save.
2. Switch to the Rich Content Editor and insert each image at its placeholder, using the
   manifest to match figure to filename. Letting the editor upload and link the file is
   easier than hunting down media URLs to paste in by hand.
3. Confirm the alt text and caption survived for each figure — inserting through the editor
   may not carry them over from the placeholder.
4. Reopen the HTML Editor and check that headings, lists, figures, and IDs survived the
   platform's sanitizer. If Canvas reports that the page has no headings, verify real `<h2>`
   tags are present; bold paragraphs are not headings.

## Design decisions worth knowing

These are the opinionated parts of the skill — the places where it will push back on a
naive conversion:

- **A visual grid is not a table.** SWOT matrices, quadrants, flowcharts, and scenario
  models get a figure plus a semantic text equivalent, not `<table>` markup. The skill
  includes a four-part decision test.
- **Alt text is capped at 120 characters.** Complex figures get a *visible* long
  description underneath instead of an overloaded `alt` attribute.
- **References link the title, not the URL.** A printed URL stays as plain text. This is
  handled entry by entry, because the failure mode is degrading halfway through a long list.
- **Platform problems stay platform problems.** A missing document `<title>` or page-level
  `<h1>` is a theme or template issue and gets reported, not patched with document-level
  tags smuggled into the fragment.
- **No CSS carries meaning.** WordPress column classes are allowed as optional visual
  polish only; the content must read correctly in a single linear column.

## Limitations

- Output quality is bounded by scan quality. Image-only PDFs need human proofreading against
  the source — names, dates, numbers, and citations especially.
- The skill does not verify facts, update citations, or modernize source language, and it
  will not silently correct the original.
- Rights and permissions for excerpted text, figures, and tables are the publisher's
  responsibility, not the agent's.
- Automated accessibility checks are recommended but are not proof of accessibility; test
  the published page with a keyboard and a screen reader.

## Repository contents

- [SKILL.md](SKILL.md) — the full skill: workflow, output contract, semantic patterns,
  QA checklist, common failure modes, and the condensed execution prompt.
