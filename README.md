# daniel-a-fisch.github.io

Personal academic website: <https://daniel-a-fisch.github.io/>

Built with [Jekyll](https://jekyllrb.com/) and served by GitHub Pages from the
`master` branch. The theme derives from
[AcademicPages](https://academicpages.github.io/), itself a fork of
[Minimal Mistakes](https://mademistakes.com/work/minimal-mistakes-jekyll-theme/)
(MIT licensed — see `LICENSE`).

## Running it locally

Needs Ruby 3.x. macOS ships 2.6, which is too old for the current
`github-pages` gem:

```bash
brew install ruby@3.3
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"   # keg-only, so this is required
ruby -v                                              # must print 3.3.x, not 2.6

bundle install
bundle exec jekyll serve --livereload --config _config.yml,_config.dev.yml
```

Then open <http://localhost:4000>.

Two things that are easy to get wrong:

- **`--config _config.yml,_config.dev.yml` is not optional.** `_config.dev.yml`
  overrides `url` to `http://localhost:4000`, which `_includes/base_path` feeds
  into every layout — including the stylesheet link. Leave it off and you get an
  unstyled page whose links all point at the production domain.
- `_config.yml` is **not** reloaded automatically. Restart the server after
  editing it.

### Without installing Ruby 3.x

Jekyll 3.9.5 does run on the system Ruby 2.6 if you pin the transitive gems that
have since dropped support for it. Useful when you cannot install anything
system-wide:

```bash
# Gems must live outside $HOME — RubyGems insists on writing ~/.gem.
export GEM_HOME="$PWD/.gems" GEM_PATH="$PWD/.gems"
export PATH="$GEM_HOME/bin:$PATH"

gem install ffi -v 1.15.5 --no-document
gem install i18n -v 1.14.8 --no-document
gem install public_suffix -v 5.1.1 --no-document
gem install jekyll -v 3.9.5 kramdown-parser-gfm --no-document
gem install jekyll-sitemap jekyll-feed jekyll-redirect-from --no-document

# Skips the Gemfile, which would otherwise pull the whole github-pages gem.
JEKYLL_NO_BUNDLER_REQUIRE=true jekyll serve \
  --config _config.yml,_config.dev.yml
```

On Apple silicon, if a gem with a native extension fails to load with an
"incompatible architecture" error, it fetched an x86_64 build — reinstall it with
`--platform arm64-darwin`.

### Checking links

The same check CI runs, against a built site:

```bash
bundle exec jekyll build --config _config.yml,_config.dev.yml
htmlproofer ./_site --disable-external --allow-hash-href \
  --ignore-empty-alt --no-enforce-https --ignore-urls "/^mailto:/"
```

`mailto:` is skipped because `author.email` is obfuscated as `d_fisch [at]
mit.edu` on purpose; html-proofer reads that as an invalid address. On
html-proofer 3.x the flag is `--url-ignore` rather than `--ignore-urls`.

## Adding content

Each kind of content is one markdown file in one directory. No other edits are
needed; the listing pages and homepage pick new files up automatically.

### A paper — `_research/`

```yaml
---
title: "Title of the paper"
collection: research
status: working-paper        # working-paper | work-in-progress | published
date: 2026-01-15             # controls ordering (newest first)
coauthors: "Jane Doe, John Roe"   # optional
excerpt: "One or two sentences of abstract."
paperurl: "/files/my-paper.pdf"   # optional; put the PDF in files/
venue: "Journal Name"             # optional; only for status: published
citation: "Fisch, D. (2026). ..." # optional
---

Body text — the full abstract, or whatever should appear on the paper's own page.
```

`status` decides which heading it appears under on `/research/`. The three
recognised values are `working-paper`, `work-in-progress`, and `published`; a
file with any other value will not be listed.

### A project — `_projects/`

```yaml
---
title: "Project title"
collection: projects
excerpt: "Short summary.<br/><img src='/files/figure.png' width='40%'>"
---
```

Used for pre-doctoral work. Listed on `/projects/` in filename order.

### A talk — `_talks/`

```yaml
---
title: "Talk title"
collection: talks
type: "Seminar"
permalink: /talks/2026-some-seminar/
venue: "Institution, Seminar Series"
date: 2026-03-01
location: "Cambridge, United Kingdom"
---
```

`/talks/` is not currently in the site navigation (see `_data/navigation.yml`) —
add it once there are a few entries.

### A teaching entry — `_teaching/`

```yaml
---
title: "Course name"
collection: teaching
type: "Undergraduate course"
permalink: /teaching/2026-spring-something/
venue: "Institution"
date: 2026-01-01
location: "City, Country"
---
```

### A new page

Create `_pages/<name>.md` with a `permalink:`, then add it to
`_data/navigation.yml` to put it in the menu:

```yaml
---
layout: archive          # or `single` for a plain page
title: "Page title"
permalink: /page-name/
author_profile: true
---
```

### Figures on the homepage

Edit `_data/home_figures.yml` — no layout changes needed.

## Layout of the repo

| Path | What it is |
| --- | --- |
| `_pages/` | Standalone pages, each with its own `permalink` |
| `_research/`, `_projects/`, `_teaching/`, `_talks/` | Content collections |
| `_data/` | Navigation, UI strings, homepage figures |
| `_layouts/` | Page templates. `home.html` is custom; the rest are upstream |
| `_includes/` | Partials. `head/custom.html` holds favicons, fonts, MathJax |
| `_sass/_custom.scss` | **All site-specific styling.** Imported last so it overrides the base theme |
| `_sass/` (rest) | Upstream theme styles — avoid editing, override in `_custom.scss` |
| `files/` | PDFs and figures linked from content |
| `images/` | Avatar and favicons |
| `assets/` | Theme CSS/JS |

## Notes

- **Analytics** is off. Google Universal Analytics was shut down in 2023, so the
  old config was dead code; wiring up GA4 would need a new include under
  `_includes/analytics-providers/`.
- **Math** is rendered by MathJax 3, configured in `_includes/head/custom.html`.
  Use `$...$` for inline and `$$...$$` for display math.
- **Google Scholar**: setting `author.googlescholar` in `_config.yml`
  automatically adds a link on `/research/` and in the sidebar.
- CI (`.github/workflows/build.yml`) builds the site and checks internal links on
  every push and pull request.
