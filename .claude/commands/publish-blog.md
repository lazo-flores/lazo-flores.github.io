# Publish a Blog Post

Render a finalized markdown draft into a live post at `/blog/<slug>/index.html`, following the established post template, and activate its Insights card. Content only; do not invent layout.

## Source

Finalized drafts live in:
`/Users/joselazoflores/Work/Udemy/Agents_Projects/proposals/business-dev/Website/blog_drafts/*.md`

Frontmatter fields: `title, slug, url, seo_title, meta_description, publication_date, estimated_read_time, post_number`.

## Hard rules

- **No em-dashes** anywhere in rendered output (body, title, seo_title, meta_description, card text). Render the source faithfully; if a sentence would want an em-dash, rewrite it so it does not need one. Never just swap a dash for a colon, comma, or parenthesis. (See the `feedback_no_em_dashes` memory.) A PostToolUse hook also warns if an em-dash lands in an edited `.html`.
- After rendering, verify zero: `perl -ne 'print "$.: $_" if /\x{2014}/ or /&mdash;/' blog/<slug>/index.html` must print nothing.
- Do not invent or change facts. If the source reads as an overclaim, ask Jose rather than rewriting.
- Match the existing posts' typography: smart quotes (`&rsquo; &ldquo; &rdquo;`), `&middot;` separators, `&times;` multiplication sign, `&rarr; &larr;` arrows.

## Instructions

1. Read the source draft. Confirm `slug` matches the convention of the live posts (`/blog/<slug>/`).
2. Create a feature branch: `feature/publish-<slug>`.
3. **Clone an existing post as the template** so the wrapper is guaranteed correct: copy `blog/the-ai-sweet-spot/index.html` to `blog/<slug>/index.html`, then replace its content. Do NOT hand-build the nav, hero, CTAs, footer, scripts, discovery widget, or sticky button.
4. Replace, in the clone:
   - `<title>` = `<seo_title> | Jose Lazo-Flores` (colon or paren form, no em-dash).
   - `<meta name="description">` = the draft `meta_description`.
   - Hero `<h1>` = the draft H1.
   - `.post-meta` = `Published <Month D, YYYY> <span class="sep">&middot;</span> <N> minute read` (convert the ISO `publication_date`).
   - Keep the `.post-byline-cta` line (light top-of-post CTA) as-is.
   - `#post-body` inner HTML = the draft body rendered to HTML (`##` to `<h2>`, `###` to `<h3>`, paragraphs to `<p>`, lists to `<ul>/<li>`, `**x**` to `<strong>`, `[t](u)` to `<a>`). Rewrite cross-post `/blog/...` links to relative `../<other-slug>/`. Smart-quote apostrophes and quotes. Do NOT enable any smartypants/typographic transform that could insert em-dashes.
   - Keep the closing `.post-cta` block (two CTAs to `../../consulting.html` and `../../consulting.html#consulting-cta`).
   - Keep the `.sticky-cta` button and the back-link (`../../consulting.html#consulting-insights`).
5. **Activate the Insights card** in `consulting.html` under `#consulting-insights`: add an `<a class="platform-card" href="blog/<slug>/">` with the title and a one-line excerpt. If a "Coming soon" placeholder exists for this post, replace it.
6. Preview on `python3 -m http.server 8001` and screenshot the post (reuse `/screenshot` patterns). Ask Jose to review.
7. After approval, run `/deploy`. Share the live `/blog/<slug>/` URL back.

## Verify before deploy

- Em-dash check (above) prints nothing.
- Post renders, date correct, the two foot CTAs and the back-link resolve to `/consulting`.
- The Insights card is live and clickable; no "Coming soon" remains for it.
