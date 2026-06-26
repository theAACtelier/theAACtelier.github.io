# Contributing to the AACtelier Website

This guide is for lab members who want to update the site — whether that means changing how it looks or adding new content.

For setting up the site locally and deploying, see [README.md](README.md).

---

## 1. Changing the Design

### Colors and fonts

All visual variables are at the top of [assets/css/style.scss](assets/css/style.scss):

```scss
$primary: #778873;          // main accent color (nav, footer, links, buttons)
$primary-dark: #5c6b59;     // hover/active state for primary
$black: #30343F;            // body text
$white-offset: #FDF6ED;     // light panel backgrounds
$page-bg: #F8F4EE;          // page background

$font-family-base: "Inter", Helvetica, Arial, sans-serif;      // body text
$font-family-heading: "Poppins", sans-serif;                   // headings
```

Change any value there and it cascades across the whole site.

### Component and page styles

Styles are organized under `_sass/` (not tracked via CDN — all local):

| Path | Controls |
|---|---|
| `_sass/components/` | Individual UI pieces: header, footer, nav, buttons, cards, etc. |
| `_sass/pages/` | Page-specific overrides: `page-home`, `page-teams`, `page-publications`, `page-service` |
| `_sass/_bootstrap-variables.scss` | Bootstrap grid breakpoints, container widths, spacing scale |

To add styles for a new page or component, create a new `.scss` file in the appropriate folder and add an `@import` line in `assets/css/style.scss`.

### Layout and structure

HTML structure lives in two places:

- **[`_layouts/`](_layouts/)** — full page templates. Each page declares which layout it uses via `layout:` in its front matter.
- **[`_includes/`](_includes/)** — reusable partials pulled into layouts: `header.html`, `footer.html`, `main-menu.html`, `team-card.html`, etc.

### Navigation links

Edit [`_data/menus.yml`](_data/menus.yml). Each entry has a `name`, `url`, and `weight` (lower = appears first):

```yaml
main:
  - name: "Research"
    url: "/research/"
    weight: 2
```

### Logo

Replace the files in `images/logo/` — keep the same filenames:

| File | Used for |
|---|---|
| `logo.png` | Desktop nav |
| `logo-mobile.png` | Mobile nav |
| `logo.svg` / `logo-mobile.svg` | SVG versions (if supported) |

Logo display size is set in [`_config.yml`](_config.yml) under the `logo:` key.

### Social links in the footer

Edit [`_data/social.json`](_data/social.json). Each entry has a `name`, `link`, and `image` (SVG icon path from `images/social/`):

```json
{
  "name": "Github",
  "link": "https://github.com/theAACtelier",
  "image": "images/social/github.svg"
}
```

---

## 2. Adding and Editing Content

### Home page

**File:** [`index.md`](index.md)

The body text (below the front matter `---` block) is the intro paragraph shown at the top of the page. Edit it directly in Markdown.

The three values cards (Agency, Accessibility, Collaboration) come from [`_data/features.json`](_data/features.json). Each entry:

```json
{
  "title": "Agency",
  "description": "The text shown under the card title.",
  "image": {
    "url": "images/features/agency.png",
    "width": 80,
    "height": 80
  }
}
```

Add, remove, or reorder entries in that file to change the cards. Images go in `images/features/`.

---

### Research page

**File:** [`research.md`](research.md) — edit the body text for the intro paragraph.

**Research project entries:** [`_research/`](_research/) — one `.md` file per project.

```markdown
---
title: "Project Name"
weight: 1
---

Description of the project in Markdown.
```

| Key | Required | Notes |
|---|---|---|
| `title` | yes | Shown as the project heading |
| `weight` | yes | Controls order — lower number appears first |
| body text | no | Shown as the project description |

---

### Publications page

**File:** [`publications.md`](publications.md) — body text for the page intro.

**Publication entries:** [`_publications/`](_publications/) — one `.md` file per paper. Filename can be anything (e.g., `author-short-title.md`).

```markdown
---
title: "Full paper title"
venue: "CHI 2026"
authors: "A Author, B Author, C Author"
date: 2026-04-15
award: false
image: false
pdf: false
video: false
code: false
---
```

| Key | Required | Notes |
|---|---|---|
| `title` | yes | Displayed as the paper heading |
| `venue` | no | Conference or journal name, shown above the title |
| `authors` | no | Author list as a plain string |
| `date` | yes | Used to sort the list (newest first) — format `YYYY-MM-DD` |
| `award` | no | Set to an award string (e.g., `"Best Paper"`) or `false` |
| `image` | no | Path to a thumbnail image, or `false` |
| `pdf` | no | URL to PDF, or `false` |
| `video` | no | URL to video, or `false` |
| `code` | no | URL to code/repo, or `false` |

---

### People page

**File:** [`team.md`](team.md) — body text for the page intro.

**Team member entries:** [`_team/`](_team/) — one `.md` file per person. Filename should match the person's name (e.g., `firstname-lastname.md`).

```markdown
---
title: "Full Name"
image: "images/team/firstname-lastname.jpg"
jobtitle: "PhD Student"
section: "lab"
interests: "AAC, Accessibility, HCI"
weight: 3
---

Short bio paragraph in Markdown.
```

| Key | Required | Notes |
|---|---|---|
| `title` | yes | Person's full name |
| `image` | no | Path to headshot; omit or set to `false` if no photo |
| `jobtitle` | no | Role shown under the name |
| `section` | yes | Controls which group the person appears under — must be `lab`, `collaborator`, or `alumni` |
| `interests` | no | Short comma-separated interest list |
| `weight` | yes | Controls order within each section — lower appears first |
| `url_custom` | no | If set, the person's name becomes a link to this URL (e.g., personal website) |
| body text | no | Bio paragraph shown on the person's individual page |

**Headshots** go in `images/team/`. Use JPEG or PNG, ideally square-cropped.

---

### Join Us page

**File:** [`join-us.md`](join-us.md) — edit the body text directly in Markdown. This is a free-form page with no associated collection.

Contact email is set in [`_data/contact.yml`](_data/contact.yml):

```yaml
email: 'aactelierlab@gmail.com'
```
