# theAACtelier Lab Website

Source for the [AACtelier Lab](https://theaactelier.github.io) website, built with Jekyll and deployed via GitHub Pages.

## Local Development

**Prerequisites:** Ruby and Jekyll. If this is your first time, follow the [Jekyll installation docs](https://jekyllrb.com/docs/installation/) to set up your environment.

Install dependencies:

```
bundle install
```

Start the local dev server (available at `http://localhost:4000`):

```
bundle exec jekyll serve
```

Build the site (output goes to `_site/`):

```
bundle exec jekyll build
```

## Deployment

The site deploys to GitHub Pages via the workflow in [.github/workflows/deploy.yml](.github/workflows/deploy.yml). Trigger it manually from the **Actions** tab in GitHub — it builds the site and pushes the output to the `gh-pages` branch.

The `baseurl` in [_config.yml](_config.yml) is set to `/` — keep this if the site lives at the root of the domain.

## Project Structure

### Pages

Top-level `.md` files map to the site's main sections:

| File | URL | Notes |
|---|---|---|
| `index.md` | `/` | Home page — intro text lives here |
| `research.md` | `/research/` | Research section intro text |
| `publications.md` | `/publications/` | Publications page — entries come from `_publications/` |
| `team.md` | `/people/` | People page intro text |
| `join-us.md` | `/join-us/` | Recruiting/contact page |

Navigation links and weights are controlled in [`_data/menus.yml`](_data/menus.yml).

### Collections

Content that repeats across multiple entries uses Jekyll collections:

- **`_team/`** — one `.md` file per lab member. Front matter fields: `title`, `jobtitle`, `section`, `interests`, `image`, `weight`.
- **`_publications/`** — one `.md` file per publication. Front matter fields: `title`, `venue`, `authors`, `date`, `award`, `image`, `pdf`, `video`, `code`.
- **`_research/`** — research projects shown on the Research page. Front matter fields: `title`, `weight`.

### Layouts and Includes

| Directory | Purpose |
|---|---|
| [`_layouts/`](_layouts/) | Page templates (`default`, `home`, `page`, `team`, `teams`, `publications`, `service`, `research`, `contact`) |
| [`_includes/`](_includes/) | Reusable HTML partials (header, footer, nav, social links, team card, etc.) |

### Data Files

Site-wide configuration lives in [`_data/`](_data/):

| File | Controls |
|---|---|
| `menus.yml` | Main nav and footer links |
| `features.json` | The three lab values shown on the home page (Agency, Accessibility, Collaboration) |
| `social.json` | Social media links in the footer |
| `contact.yml` | Contact email and phone (used by the contact layout) |
| `seo.yml` | SEO metadata |

### Styles

[`assets/css/style.scss`](assets/css/style.scss) is the main stylesheet entry point. Bootstrap SCSS source files are in [`_sass/bootstrap/`](_sass/bootstrap/); custom overrides go in [`_sass/`](_sass/).

### Images

| Path | Contents |
|---|---|
| `images/team/` | Headshots for lab members |
| `images/features/` | Icons for the home page values section |
| `images/logo/` | Logo variants (desktop and mobile, PNG and SVG) |

## Under Construction

The following parts of the site are actively being developed and may be incomplete or using placeholder content:

- **Home page design** (`index.md`, `_layouts/home.html`) — layout and visual design are not finalized.
- **Research page design** (`research.md`, `_layouts/research.html`) — the research projects section is being designed; `_research/` entries are stubs.
- **Publication list** (`_publications/`, `_layouts/publications.html`) — the list format and entries are in progress.
