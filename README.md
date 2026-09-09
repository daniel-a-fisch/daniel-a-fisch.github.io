# daniel-a-fisch.github.io

Personal academic website for Daniel A. Fisch, PhD student in Economics at MIT. Built with Jekyll and hosted on GitHub Pages from the `master` branch. This is a hand-written site with no upstream theme.

## Running locally

Ruby 3.3 is installed at `/opt/homebrew/opt/ruby@3.3` (keg-only, so the PATH export is required):

```bash
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000> in your browser.

**Note:** `_config.yml` is not reloaded automatically — restart `jekyll serve` after editing it.

## Adding a research item

This is the main content maintenance task. Create one file in `_research/` with the appropriate front matter, and it will appear automatically on both the homepage (recent items) and the full research page at `/research/`, sorted by date (newest first).

Example front matter:

```yaml
---
title: "Mathematical Modeling of Opinion Dynamics"
label: "Master's thesis"
venue: "University of Cambridge"
date: 2023-05-01
authors: "Daniel Fisch, John Smith"  # optional; list everyone, including yourself
summary: "A short description of the research"  # optional
link: "https://example.com/paper"  # optional
paper: "/files/paper.pdf"  # optional, relative to site root
math: true  # optional, only if the body contains LaTeX
---
```

A future `date:` is fine — `future: true` is set in `_config.yml`, so a forthcoming
paper gets its page built and sorts to the top of the list.

The `label` field is free text — use "Working paper", "Work in progress", "Master's thesis", "Bachelor's thesis", or whatever is appropriate for the item.

Because research items are pulled automatically from `_research/`, adding a working paper requires no other edits to pages or navigation — just add the file.

## Adding a page

Create a new file in `_pages/` with `layout: page` and a `permalink`, then add it to the `nav:` list in `_config.yml` if it should appear in the top navigation.

## Preserved URLs

The old site's URLs are kept alive with `jekyll-redirect-from` via `redirect_from:`
front matter, so nothing already indexed 404s: `/about/` and `/portfolio/`,
`/publications/`, `/projects/` (and each `/projects/<name>/`), `/resume`, `/talks/`
and the old per-item `/talks/…` and `/teaching/…` paths. The `talks` and `teaching`
collections no longer exist — those entries live in `_pages/cv.md` and
`_pages/teaching.md`.

## Editing research interests

Edit `_data/interests.yml`. The list appears on the homepage automatically.

## Repository layout

| Path | What it is |
| --- | --- |
| `_config.yml` | Site configuration |
| `_pages/` | Content pages (homepage, research, CV, teaching, reading list, 404) |
| `_research/` | Research items (each file is one project/paper/thesis) |
| `_layouts/` | HTML templates for page types |
| `_includes/` | Reusable HTML snippets |
| `_data/` | YAML data files (research interests) |
| `assets/` | CSS, JavaScript, and other static assets |
| `images/` | Images and photos |
| `files/` | PDFs and other downloadable files |

## Checking links

This is the same command CI runs. Requires html-proofer 5:

```bash
bundle exec jekyll build
htmlproofer ./_site --disable-external --allow-hash-href \
  --ignore-empty-alt --no-enforce-https --ignore-urls "/^mailto:/"
```

The `mailto:` ignore is necessary because `site.author.email` is deliberately obfuscated (`d_fisch [at] mit.edu`).


## Math rendering

LaTeX math is rendered with MathJax 3, opt-in per page via `math: true` in the front matter. Use `$$...$$` for display equations and `$...$` for inline math.
