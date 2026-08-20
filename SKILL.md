# Skill: Convert a PDF to Accessible HTML for WordPress and Canvas LMS

## Purpose

Convert an attached PDF into a clean, accessible HTML fragment that can be pasted into a WordPress Custom HTML block, the Gutenberg code editor, or the Canvas LMS HTML editor. Preserve all substantive content while removing page-oriented formatting and other PDF artifacts. Use portable semantic HTML that remains understandable even when either platform removes classes or applies different visual styling.

## Inputs

### Required

- The source PDF.

### Optional

- The existing WordPress post title or Canvas page title, if already set.
- The target platform: WordPress, Canvas LMS, or both.
- The site's preferred heading starting level.
- Instructions about whether figures should be extracted as separate media files.
- Existing HTML to revise instead of starting from the PDF.
- A born-digital source, publisher manuscript, original figure files, or source table data for verification.
- The requested publication scope when the PDF contains front matter, multiple chapters, appendices, or book-wide contents.

## Deliverables

Produce:

1. A downloadable `.html` file containing only the WordPress- and Canvas-ready content fragment.
2. Separate image files for substantive figures and for non-tabular visual frameworks when visual layout carries instructional meaning.
3. An image manifest listing each filename, HTML placeholder, caption, alt text, long-description location, and upload instructions.
4. Suggested alt text of no more than 120 characters, plus captions and visible longer descriptions when needed.
5. A brief validation summary identifying completed checks, unresolved ambiguities, and any accessibility warnings that belong to the WordPress theme, Canvas template, or other platform-level interface rather than the page content.
6. For difficult scans or publisher workflows, a separate conversion report with a candid success assessment, confidence by content type, known limitations, and recommended publisher actions.
7. When Canvas users may not have a source-code editor, an optional plain-text companion containing the identical HTML source for easy copying.

Do not paste a long HTML document into the chat when a downloadable artifact can be provided.

When both platforms are targets, prefer one portable semantic fragment. Create separate WordPress and Canvas variants only when a platform-specific media URL, editor behavior, or optional WordPress layout wrapper makes separate files necessary.

When Canvas LMS is the primary distribution platform, default to Canvas-managed media URLs and portable semantic HTML. Do not depend on WordPress block classes to preserve important visual relationships.

## Output Contract

The HTML must:

- Be a fragment, not a complete webpage.
- Contain no `<!doctype>`, `<html>`, `<head>`, `<title>`, `<body>`, `<main>`, or `<style>` elements.
- Contain no scripts, embedded fonts, layout CSS, page dimensions, or print-specific markup.
- Rely on the WordPress theme or Canvas LMS page styles for visual presentation; do not require custom CSS for meaning or reading order.
- Preserve the complete substantive content within the agreed scope and its logical reading order.
- Exclude page numbers, running headers, running footers, crop marks, scan borders, and repeated page furniture.
- Use semantic HTML rather than visual formatting to communicate structure.
- Use image alt text no longer than 120 characters, including spaces and punctuation.

## Recommended Element Set

Prefer a restrained set of elements:

- `<h2>` through `<h6>` for verified section headings
- `<p>` for body paragraphs, author information, dates, and other prose
- `<strong>` and `<em>` for meaningful emphasis
- `<ul>`, `<ol>`, and `<li>` for lists
- `<a>` for descriptive links
- `<figure>`, `<img>`, and `<figcaption>` for figures
- `<blockquote>` for genuine quotations
- `<aside>` for supplementary callouts when the content is truly complementary
- `<table>`, `<caption>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, and `<td>` for genuine tabular data
- `<dl>`, `<dt>`, and `<dd>` for repeated named attributes or scenario records
- `<sup>` for footnote markers when appropriate
- `<section>` only when it adds meaningful document structure

Avoid generic wrappers such as `<div>` and `<span>` unless no semantic element is suitable. WordPress core Columns classes may be used as an optional WordPress-only presentation enhancement around semantic groups, but the same content must remain complete and understandable when pasted into Canvas LMS, where those classes may have no visual effect or may be removed. Such wrappers must not carry false table or grid semantics.

## Workflow

### 1. Inspect the source before converting

Review the entire PDF before transcribing it. Identify both its content structure and its scan geometry:

- Document title, authors, subtitle, date, edition, publisher, and introductory metadata
- Requested publication scope, including whether front matter, overview material, references, or appendices belong in the output
- Major sections and subsections
- Paragraph boundaries
- Ordered and unordered lists
- Emphasis that carries meaning
- Figures, diagrams, tables, text boxes, quadrant models, and matrix-like frameworks
- Footnotes, endnotes, references, and URLs
- Repeated headers, footers, and page numbers
- Text continued across page breaks
- OCR errors, ligatures, hyphenation, and broken lines
- Page rotation, upside-down pages, two-up book spreads, mixed orientations, skew, edge noise, and missing or unreliable text layers
- Whether the PDF contains cover art, copyright boilerplate, book-wide tables of contents, or other material that may be outside the requested web excerpt

For a rotated, two-up, or image-only scan, normalize the source before relying on OCR: rotate pages, split each spread into individual logical pages, preserve a page map, and then establish reading order. OCR output is evidence, not authority; compare it with the page image whenever wording, punctuation, names, numbers, or hierarchy is uncertain.

Do not infer document structure from font size alone. Use wording, numbering, placement, repetition, and the surrounding content together. Record any intentional exclusions in the conversion report rather than silently dropping them.

### 2. Define and document the publication scope

When the source is a book scan or a larger document, distinguish substantive excerpt content from print-only or book-wide material.

Usually retain when relevant to the requested excerpt:

- Title and author information
- Dedication, preface, overview, or introduction
- The complete requested chapter or article
- Sidebars, tables, figures, notes, references, and suggested readings belonging to that excerpt

Usually omit unless explicitly requested:

- Cover artwork and decorative logos
- Copyright, manufacturing, and production boilerplate
- Blank pages
- Running heads and printed page numbers
- Book-wide brief or detailed tables of contents that mainly point to chapters outside the excerpt
- Printer marks, scan borders, and binding artifacts

Do not treat these as universal deletion rules. Make a content decision based on the requested scope, document context, and publisher needs, then disclose the decision in the report.

### 3. Establish the heading hierarchy

Determine the hierarchy before writing HTML.

When the WordPress post title or Canvas page title serves as the page-level `<h1>`, begin the article fragment at `<h2>`. Do not duplicate the page title as another `<h1>` inside the HTML fragment unless the user explicitly requests it or the target template does not expose the page title as a heading.

Apply these rules:

- Use `<h2>` for top-level sections within the article.
- Use `<h3>` for subsections of an `<h2>`.
- Use `<h4>` only for material nested within an `<h3>`.
- Do not choose a heading level because of appearance.
- Do not tag an entire paragraph as a heading.
- Do not convert bold introductory sentences into headings unless they function as section labels.
- Avoid skipped heading levels.
- Keep section numbers in the heading text when they are part of the source.

Before delivery, generate a heading outline and read it independently. It should accurately summarize the document's organization.

### 4. Reconstruct paragraphs and reading order

Join lines that were broken only because of the PDF's column or page width. Preserve paragraph breaks that represent actual conceptual divisions.

- Rejoin sentences and paragraphs split across pages.
- Remove discretionary hyphens introduced at line endings.
- Preserve real hyphens in compound words.
- Follow the intended reading order in multi-column layouts, sidebars, and two-up scans.
- Do not interleave running headers, captions, or marginal text with body paragraphs.
- Retain meaningful transitions between prose and figures, boxes, or tables.

For image-only scans, manually verify names, dates, percentages, citations, punctuation, and the beginning and end of every page. These are common OCR failure points.

### 5. Remove PDF-only artifacts

Remove:

- Printed page numbers
- Running headers and footers
- Repeated chapter labels
- Crop marks and scan borders
- Page-break whitespace
- Decorative rules that carry no meaning
- Empty OCR fragments
- Duplicate text caused by overlapping OCR regions

Do not reproduce page dimensions, fixed positioning, line-by-line layout, or page images as the primary content.

### 6. Preserve meaningful inline formatting

Use:

- `<em>` for book titles, journal titles, terms intentionally emphasized, and other meaningful italics
- `<strong>` for genuine strong emphasis or short labels
- `<blockquote>` for substantial quotations
- Quotation marks for short inline quotations

Do not reproduce decorative typography, drop caps, letter spacing, all-caps styling, or visual indentation unless it communicates meaning. Do not wrap an entire paragraph in `<strong>` or `<em>` merely because the source used a display style.

### 7. Convert lists semantically

Use `<ol>` when sequence, rank, priority, or numbering matters. Use `<ul>` when order does not matter.

- Each item must be a real `<li>`.
- Preserve nested list relationships.
- Do not simulate lists with bullets, hyphens, manual numbers, or `<br>` elements.
- Use definition lists for repeated term-and-description pairs or scenario attributes.

### 8. Handle figures and diagrams

Extract substantive figures as separate image files when that improves clarity, fidelity, editor compatibility, or preservation of an important visual layout. For Canvas LMS, separate media is the default: upload the files through Canvas Files or the Rich Content Editor and replace the supplied placeholders with Canvas-managed URLs. Do not embed images as Base64 data URIs; Canvas may sanitize them, they enlarge the HTML, and they are difficult to edit or reuse.

For each figure:

- Preserve the figure number and title in a visible `<figcaption>`.
- Include the source or attribution when present.
- Write concise alt text no longer than 120 characters, including punctuation and spaces.
- Count alt-text characters before delivery.
- Do not begin alt text with “Image of” or “Graphic of.”
- Do not repeat the caption verbatim in alt text.
- Use `alt=""` only for genuinely decorative images.
- Provide a visible long description when the figure contains relationships, data, sequence, direction, or other meaning that cannot fit in 120 characters.
- Put the long description immediately after the figure or clearly associate it through nearby headings and prose.
- Keep the visual and its semantic equivalent together so that neither is mistaken for unrelated content.

Example:

```html
<figure>
  <img src="REPLACE-WITH-CANVAS-IMAGE-URL/figure-1.png" alt="Planning inputs converge into issues, goals, strategies, objectives, and operational plans.">
  <figcaption>Figure 1. Basic strategic planning model.</figcaption>
</figure>
<p><strong>Figure description:</strong> The process begins with preparation. Situation assessment and mission, values, and vision feed into strategic issues, followed by goals, strategies, objectives, and operational plans.</p>
```

For charts, retain or recreate the visual when useful, but also provide the data or findings in accessible text or a genuine data table. Prefer original source data or vector artwork over a scan extraction when available.

Do not rasterize text-heavy callout boxes merely to preserve their appearance. Recreate their text as semantic HTML unless spatial design itself is essential. Conversely, when a matrix, quadrant, flowchart, or other instructional framework depends on spatial arrangement, preserve or recreate that visual as an image and provide a complete semantic equivalent.

Optimize extracted images for legibility and reasonable file size. Crop page borders, neighboring text, page numbers, shadows, and scanner artifacts without removing substantive labels. Do not upscale a poor scan and imply that it is publication quality.

### 9. Handle matrix-like, quadrant, and scenario content

Do not use a `<table>` merely because content is drawn inside a grid.

Apply this decision test before using table markup:

1. Every data cell has a meaningful relationship to both a row header and a column header.
2. Users would reasonably navigate and compare the content by row and column.
3. Accurate `<th>` elements and `scope` attributes can describe every relationship.
4. The grid itself is data, rather than a visual device for showing categories, intersections, scenarios, sequence, or spatial relationships.

If any condition is false, use a semantic non-table representation.

#### Semantic patterns

- **Quadrants or named categories:** use a parent `<section>` and one child `<section>` per quadrant. Give every child a complete heading that includes the relevant axis context, such as “Internal strengths” or “Organizational strength and environmental threat.”
- **Scenario matrices:** use a heading for each scenario and a `<dl>` for repeated attributes such as competitive position, attractiveness, alternative coverage, strategy, and explanation.
- **Choices, criteria, or outcomes:** use ordered or unordered lists.
- **Spatial diagrams with arrows or convergence:** retain or extract the figure and provide concise alt text plus a visible equivalent description.
- **Important instructional frameworks:** use a hybrid representation containing both the visual and an equivalent semantic text version.

Do not add `role="table"`, `role="grid"`, `role="row"`, or related ARIA roles to non-tabular content. Do not use headings that depend on visual position alone, such as “Top left.” Each group must remain understandable when read independently and in a single linear column.

#### Canvas-first matrix pattern

When Canvas LMS is the primary distribution platform and the matrix layout matters, use this default pattern:

1. Extract or recreate the matrix as a separate image.
2. Upload it to Canvas and insert its Canvas-managed URL.
3. Give it alt text of 120 characters or fewer that identifies the framework without trying to transcribe it.
4. Preserve the figure or table number and source in a visible caption.
5. Follow the image immediately with a complete semantic equivalent using headings, lists, paragraphs, or definition lists.
6. Keep the semantic equivalent in a logical reading order, normally left to right and then top to bottom.
7. Do not hide the semantic equivalent visually; it benefits all learners and remains available if the image fails to load.

Example:

```html
<figure>
  <img src="REPLACE-WITH-CANVAS-IMAGE-URL/swot-matrix.png" alt="SWOT matrix of internal and external factors for a performing arts organization.">
  <figcaption>Table 7.1. SWOT analysis of a performing arts organization.</figcaption>
</figure>

<section aria-labelledby="swot-equivalent">
  <h3 id="swot-equivalent">SWOT analysis in text</h3>
  <section aria-labelledby="internal-strengths">
    <h4 id="internal-strengths">Internal strengths</h4>
    <ul>
      <li>...</li>
    </ul>
  </section>
  <section aria-labelledby="internal-weaknesses">
    <h4 id="internal-weaknesses">Internal weaknesses</h4>
    <ul>
      <li>...</li>
    </ul>
  </section>
  <section aria-labelledby="external-opportunities">
    <h4 id="external-opportunities">External opportunities</h4>
    <ul>
      <li>...</li>
    </ul>
  </section>
  <section aria-labelledby="external-threats">
    <h4 id="external-threats">External threats</h4>
    <ul>
      <li>...</li>
    </ul>
  </section>
</section>
```

For multi-variable scenario matrices, preserve the visual as an image when useful, then represent each scenario as a self-contained record. A definition list is usually clearer than attempting to reproduce a three-dimensional model:

```html
<section aria-labelledby="scenario-1">
  <h4 id="scenario-1">Scenario 1: Aggressive competition</h4>
  <dl>
    <dt>Competitive position</dt>
    <dd>Strong</dd>
    <dt>Program attractiveness</dt>
    <dd>High</dd>
    <dt>Alternative coverage</dt>
    <dd>High</dd>
    <dt>Suggested strategy</dt>
    <dd>Aggressive competition</dd>
  </dl>
  <p>...</p>
</section>
```

#### Optional WordPress matrix presentation

When the output is intended specifically for WordPress/Gutenberg and the site loads WordPress core block styles, semantic sections may be placed inside `wp-block-columns` and `wp-block-column` wrappers to create an optional visual grid without custom CSS.

This enhancement is not portable to Canvas and must never carry the meaning. The child sections, complete headings, lists, and logical source order remain authoritative. Do not add inline styles, a `<style>` element, custom stylesheets, CSS ordering, or false table semantics.

If one fragment must serve both platforms, prefer the Canvas-first hybrid pattern whenever the two-dimensional layout is important. WordPress can also display the same image-plus-text representation reliably.

For three-dimensional or unusually complex matrices, do not force every dimension into a visual grid. Use repeated self-contained scenario records as the accessible equivalent.

### 10. Handle tables

Use `<table>` only for genuine data tables whose information depends on stable row and column relationships.

Every data table must include:

- A concise `<caption>` identifying the table
- `<thead>` and `<tbody>` where appropriate
- `<th scope="col">` for column headers
- `<th scope="row">` for row headers
- Grouped headers only when needed and accurately associated
- No merged cells used merely for visual layout
- No empty header cells unless the structure genuinely requires them and remains understandable

For complex tables, simplify the structure when possible without changing the data. If the table cannot be made understandable with native HTML associations, provide an accessible alternative or recommend editorial redesign.

Verify all values against the source. Dense tables, negative numbers, percentages, footnote markers, and grouped headings are high-risk OCR content.

Do not use tables for:

- Page layout
- Side-by-side prose
- Callout boxes
- Quadrants or SWOT frameworks
- Flowcharts
- Conceptual intersections
- Collections of scenario records

### 11. Handle links, citations, references, and notes

Use descriptive link text.

- Link the title of a report, article, book, organization, or resource.
- Do not use a raw URL as linked text when a meaningful title is available.
- If preserving a printed URL is necessary, leave the raw URL as unlinked text and apply the hyperlink to the associated title.
- Verify that links resolve when internet access and scope permit.
- Retain complete citation information even if a link is removed or cannot be verified.
- Do not silently replace the cited edition with a newer source.

For footnotes or endnotes:

- Use linked superscript markers when notes are retained inline.
- Give each note a stable `id`.
- Provide a return link with descriptive accessible text, such as “Return to note 1 reference.”
- Do not expose a long raw URL as the only link text.

Example:

```html
<p>Research use may take several forms.<sup><a href="#note-1" id="note-ref-1">1</a></sup></p>
<ol>
  <li id="note-1"><a href="https://example.org/report">Use of Research Evidence Methods Repository</a>. https://example.org/report <a href="#note-ref-1" aria-label="Return to note 1 reference">↩</a></li>
</ol>
```

#### Reference list formatting

References are the highest concentration of link decisions in an academic document. Process each entry with the same three steps, in this order:

1. Identify the title of the work being cited — the article, chapter, report, book, or resource.
2. Apply the hyperlink to that title.
3. Render any printed URL that follows as unlinked plain text.

Apply these steps to every entry individually. A references list is not a batch operation; a decision made correctly for the first entry does not carry itself forward to the twentieth.

Incorrect — the URL carries the link and the title is inert:

```html
<li>Weiss, C. H. (1979). The many meanings of research utilization. <em>Public Administration Review</em>, 39(5), 426–431. <a href="https://example.org/many-meanings">https://example.org/many-meanings</a></li>
```

Correct — the title carries the link and the printed URL remains visible as plain text:

```html
<li>Weiss, C. H. (1979). <a href="https://example.org/many-meanings">The many meanings of research utilization</a>. <em>Public Administration Review</em>, 39(5), 426–431. https://example.org/many-meanings</li>
```

When an entry has no linkable title — a personal communication, an unpublished document, or a bare database record — leave the entry unlinked rather than promoting its URL to link text.

### 12. Distinguish content issues from platform-level issues

Do not attempt to solve document-level or template-level accessibility problems inside the content fragment.

Examples:

- A missing browser `<title>` belongs to the WordPress theme, SEO configuration, or Canvas template, not the Custom HTML block.
- A missing page-level `<h1>` may be a theme or template issue if the post or page title is not rendered semantically.
- Landmark structure, skip links, global navigation, focus styling, and site color contrast belong to the platform or theme.

Document these issues in the validation summary and tell the publisher or site administrator where they must be fixed. Do not insert `<html>`, `<head>`, `<title>`, `<body>`, or `<main>` into the page fragment as a workaround.

### 13. Prepare files for Canvas insertion

Canvas users often open `.html` files in a browser and see rendered text rather than source code. Make the delivery usable without assuming a code editor.

- Provide the HTML fragment as `.html`.
- When appropriate, provide an identical `.txt` source companion.
- Provide an image manifest with exact placeholder strings and Canvas upload instructions.
- Tell users to paste the source into Canvas's HTML Editor, not the visual Rich Content Editor.
- After saving, reopen the HTML Editor and confirm that `<h2>`, `<h3>`, lists, figures, and image URLs remain.
- If Canvas reports that the page has no headings, verify that actual heading tags survived; bold paragraphs are not headings.
- The Canvas page title normally supplies the page-level `<h1>`, so the fragment should usually begin with `<h2>`.
- A missing document `<title>` warning is a site or template issue and cannot be repaired inside a page-content fragment.
- Keep ordinary `<img src="...">` references. Do not use Base64 image data, scripts, `<style>`, document-level tags, or unsupported embedded objects.

On macOS, users can reveal source with a code editor such as Visual Studio Code, BBEdit, or CotEditor. TextEdit can also display source when “Display HTML files as HTML code instead of formatted text” is enabled. The plain-text companion is the most reliable no-configuration option.

### 14. Validate the HTML

Validate both the source fragment and the published result when platform access is available.

#### Content fidelity

- Compare the first and last sentence of every source page with the reconstructed text.
- Confirm that no paragraph, list item, box, figure, table, note, or reference was omitted.
- Verify names, dates, quotations, statistics, and citations.
- Confirm that exclusions match the documented publication scope.

#### Semantic structure

- Review the heading outline independently.
- Confirm no skipped heading levels.
- Confirm no paragraph-length headings.
- Confirm all lists use list markup.
- Confirm quotations, callouts, figures, and tables use appropriate elements.
- Confirm matrix-like content was not automatically treated as a table.

#### Accessibility

- Confirm every informative image has useful alt text of 120 characters or fewer.
- Confirm decorative images use empty alt text.
- Confirm complex images have visible long descriptions or equivalent data.
- Confirm every genuine table has a caption and accurate header associations.
- Confirm linked text is descriptive and raw URLs are not used as the only link text.
- Walk the references list entry by entry and confirm each one links its title rather than its URL.
- Confirm reading order remains logical without CSS.
- Confirm no meaning depends only on color, position, font size, or visual grouping.

#### WordPress and Canvas LMS compatibility

- Confirm the fragment contains no document-level elements.
- Confirm it does not depend on scripts, custom CSS, embedded fonts, or fixed page dimensions.
- Paste into the target editor and save.
- Reopen the HTML editor and confirm headings, figures, links, lists, and IDs remain intact.
- Test the published page at narrow widths and high zoom.
- Test keyboard navigation and at least one screen reader when possible.
- Run available automated accessibility checks, but do not treat a passing automated score as proof of accessibility.

## Conversion Assessment and Publisher Report

For difficult scans, image-only documents, publisher workflows, or large excerpts, provide a separate report.

### Success assessment

State the result candidly, for example:

- Successful and publication-ready after routine editorial review
- Successful but not publication-final without source verification
- Partially successful; substantial manual reconstruction remains
- Unsuccessful because the source quality does not support reliable transcription

Provide confidence by content type, such as:

- Prose and headings
- Tables
- Figures and charts
- References and links
- Exact typography and emphasis
- Character-perfect transcription

Do not assign false precision. Explain the principal risks behind the assessment.

### Recommended publisher actions

Address, as applicable:

1. Rights and permissions for the excerpt, figures, tables, and third-party content
2. Replacement of image placeholders with WordPress or Canvas-managed media URLs
3. Use of original source data, vector files, manuscripts, or production assets
4. Cell-by-cell verification of reconstructed tables
5. Editorial proofreading against a publisher-controlled source
6. Verification of reference links and cited editions
7. Correct WordPress post-title or Canvas page-title configuration
8. Published-page accessibility testing
9. Creation of an accessible source of record, such as tagged PDF or EPUB
10. Documentation of any intentional corrections or deviations from the source

## Quality-Assurance Checklist

- [ ] Publication scope was defined and documented.
- [ ] Scan rotation, spread geometry, and reading order were checked.
- [ ] Running headers, footers, page numbers, and scan artifacts were removed.
- [ ] Paragraphs split across pages were rejoined.
- [ ] Heading hierarchy was manually reviewed.
- [ ] No complete prose paragraph was marked as a heading.
- [ ] Lists use `<ul>` or `<ol>` and real `<li>` elements.
- [ ] Meaningful emphasis was preserved without copying decorative typography.
- [ ] All substantive figures, boxes, genuine tables, and matrices were represented.
- [ ] Every non-empty alt attribute is 120 characters or fewer.
- [ ] Complex figures have visible descriptions.
- [ ] Every genuine table has a caption and accurate header relationships.
- [ ] Every grid-like visual passed the table decision test.
- [ ] Non-tabular matrices use complete cell headings and logical source order.
- [ ] Canvas-first matrices that depend on spatial layout include a separate image and a complete visible semantic equivalent.
- [ ] Every image placeholder appears in the image manifest with alt text, caption, and upload instructions.
- [ ] WordPress Columns wrappers, if used, contain semantic groups, have no false ARIA table or grid roles, and are nonessential in Canvas LMS.
- [ ] Matrix content remains understandable if it falls back to one column.
- [ ] No custom or inline CSS was added solely to reproduce a matrix layout.
- [ ] Every reference entry was checked individually—no raw URL serves as the sole or primary linked text when a title is available.
- [ ] Footnote and endnote navigation is accessible.
- [ ] Site-level warnings are separated from content-level findings.
- [ ] HTML contains no document-level tags, scripts, embedded styling, Base64 images, local paths, or temporary session URLs.
- [ ] Canvas source instructions or a plain-text HTML companion were supplied when needed.
- [ ] Saved Canvas HTML was checked to confirm that heading tags and image URLs survived sanitization.
- [ ] The final output was tested in every target platform—WordPress, Canvas LMS, or both—or identified as requiring publisher-side testing.

## Common Failure Modes

### Trusting OCR before correcting scan geometry

A rotated or two-up scan can produce plausible but badly ordered text. Normalize orientation, split spreads, establish a page map, and then OCR.

### Treating front matter and book-wide contents as one undifferentiated body

Not every printed page belongs in a web excerpt. Define scope deliberately and disclose exclusions.

### Treating every bold line as a heading

Bold text may be a label, lead-in, quotation, or visual emphasis. Determine function from context.

### Converting a whole paragraph into a heading

A heading should name the section that follows. Prose belongs in `<p>` even if the source uses large or bold type.

### Reproducing the PDF's appearance instead of its meaning

Fixed coordinates, line-by-line spans, page images, manual spacing, and embedded fonts make poor web content. Reconstruct semantic structure instead.

### Losing text at page boundaries

Always compare the end of one page with the beginning of the next and rejoin split sentences and paragraphs.

### Converting conceptual matrices into data tables

A visual grid is not automatically tabular data. If accurate row and column headers cannot be assigned, use semantic groups, scenario records, or a figure plus text equivalent.

### Publishing figures as inaccessible screenshots

An image alone is insufficient when it contains data, relationships, or text. Add concise alt text and a visible equivalent description.

### Depending on platform-specific layout classes

WordPress Columns may improve presentation in WordPress but are not dependable in Canvas. Meaning and reading order must survive without them.

### Overloading alt text

Do not put a complete chart or matrix transcription into the alt attribute. Keep alt text within 120 characters and provide the details nearby.

### Linking raw URLs, especially in bulk reference processing

Link the relevant title. If the printed URL must remain visible, leave it as plain text.

This error appears most often partway through a long references list: the first several entries are formatted correctly, then the pattern degrades into URL-as-link for the remainder. Re-check the middle and end of the list, not only the beginning, and treat each entry as its own decision.

### Attempting to fix a missing document title inside the post

A browser `<title>` belongs in the document `<head>`. Report the problem to the site or template administrator.

### Silently changing source content

Do not modernize, fact-check, repair historical claims, or update citations without disclosure. Preserve the source and document editorial corrections separately.

## Delivery Format

Deliver a repository-ready package containing, as applicable:

1. The WordPress- and Canvas-ready `.html` fragment.
2. A plain-text copy of the identical HTML source for Canvas users who lack a code editor.
3. Separate media assets with stable, descriptive filenames.
4. An image manifest containing filenames, placeholders, alt text, captions, long-description notes, and upload steps.
5. A short validation summary.
6. For difficult or publisher-facing projects, a conversion report with success assessment, limitations, and action items.
7. A brief `README.md` when the files will be distributed through GitHub or another repository.

Use relative filenames and clear placeholders rather than temporary chat URLs inside deliverable HTML. Do not include credentials, local filesystem paths, generated-session IDs, or inaccessible private links.

In the chat response, provide only a brief explanation and links to the artifacts. Do not repeat the full HTML or report.

## Reusable Execution Prompt

Convert the attached PDF into an accessible HTML fragment suitable for WordPress/Gutenberg and Canvas LMS pages. Preserve all substantive content and logical reading order while removing page numbers, running headers and footers, scan artifacts, page dimensions, embedded styling, and document-level tags. Use the WordPress post title or Canvas page title as the page-level H1 and begin the fragment at H2 unless instructed otherwise. Manually verify heading hierarchy and never mark full prose paragraphs as headings.

Use portable semantic lists, quotations, callouts, figures, and genuine data tables. Apply the table decision test to every grid-like visual. Do not convert conceptual matrices, quadrants, decision frameworks, or multi-variable scenarios into tables when accurate row and column headers cannot be assigned. When Canvas is primary and spatial layout matters, extract or recreate the visual as a separate image and follow it immediately with a complete semantic equivalent using sections, headings, lists, paragraphs, or definition lists. Use Canvas-managed image URL placeholders and create an image manifest. Keep every non-empty alt attribute to 120 characters or fewer and provide visible long descriptions for complex visuals.

WordPress core column classes may be used only as optional WordPress presentation enhancements; never depend on them in Canvas. Do not require custom CSS, scripts, Base64 images, or platform-specific classes for meaning. Link resource titles instead of raw URLs. In references, footnotes, and endnotes, handle every entry individually: link the title of the cited work and leave any printed URL as unlinked plain text, checking the end of a long list as carefully as the beginning. Provide an optional plain-text copy of the HTML source for Canvas users, and instruct users to paste it into Canvas's HTML Editor and verify that heading tags survive after saving. Separate page-content accessibility issues from platform-level warnings such as a missing document title. For difficult scans, provide a candid success assessment and a publisher action report covering rights, proofreading, source assets, table and matrix verification, link validation, platform configuration, and final accessibility testing. Package outputs with stable filenames and repository-ready documentation when requested.
