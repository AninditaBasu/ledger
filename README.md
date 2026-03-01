# `ledger` theme for GitHub Pages

Ledger is a documentation theme inspired by palmleafs and codex manuscripts. It is designed for clarity, readability, and zero-setup deployment on GitHub Pages, and is suitable for projects with a small set of doc files. 

It supports:

- Mermaid diagrams
- Static API pages
- Interactive API pages

---

- [Features](#features)
- [Live example](#live-example)
- [How to enable the theme](#how-to-enable-the-theme)
- [Theme configuration](#theme-configuration)
- [Specifying the left-column TOC](#specifying-the-left-column-toc)
- [Logos and favicons](#logos-and-favicons)
- [Page elements](#page-elements)
- [API pages](#api-pages)
  -  [Static API](#static-api)
  -  [Interactive API](#interactive-api)
- [License](#license)

---

## Features

- Two-column layout with left navigation panel.
- Mobile-responsive. Sidebar collapses into top navigation.
- No local setup for builds needed. Works directly with GitHub Pages through `remote_theme`.
- Mermaid support.
- OpenAPI support.

## Live example

See the theme in action, with its presets and possible customisations, at [https://aninditabasu.github.io/ledger/](https://aninditabasu.github.io/ledger/)

## How to enable the theme

1. In your own repository root, create a file named `_config.yml` with the following code snippet:

    ```
    remote_theme: AninditaBasu/ledger
    plugins:
      - jekyll-remote-theme
    ```
1. Enable GitHub Pages: In your repository settings, go to **Pages** > **Deploy from branch** > **main**.
1. Push your site files.

Your site should build itself with the `palmleaf` preset, which is the default. To use the dark theme (called `night-ink`), edit your `_config.yml` like so:

```
remote_theme: AninditaBasu/ledger
plugins:
  - jekyll-remote-theme
ledger:
  preset: night-ink
```

## Theme configuration

You can customise the `ledger` theme by specifying the following fields in your site `_config.yml` file. 

| Key      | Purpose                                              |
| ------- | ------------------------------------- |
| `title`    | Displayed as the site name in the sidebar    |
| `author`  | Used in the footer copyright line       |
| `description`   | Used in the HTML `<meta>` description tag    |
| `copyright_start`| If present, used in the site footer; default is current year |
| `github`     | Displayed in the footer      |
| `github.repository_url`  | Must be the URL of your GitHub repository      |
| `remote_theme`   | Must be set to `AninditaBasu/ledger`    |
| `plugins`     | Must include `jekyll-remote-theme`     |
| `ledger`   | Theme configuration namespace  |
| `ledger.preset`   | If used, must be `night-ink`; if unspecified, defaults to `palmleaf`  |
| `ledger.palette`   | For custom colours  |
| `ledger.palette.background`   | Background colour of the pages  |
| `ledger.palette.sidebar`   | Background colour of the sidebar on the pages |
| `ledger.palette.text-main`   | Font colour of the text of the body elements |
| `ledger.palette.text-muted`   | Font colour of secondary text such as sidebar navigation links  |
| `ledger.palette.text-heading`   | Font colour of the text of  headings |
| `ledger.palette.border-color`   | Colour of the borders in elements such as code blocks and admonitions  |
| `ledger.palette.accent`   |  Accent colour for links, highlights, and interactive elements  |

Additionally, you can set the theme of any page to be different from the site theme, by specifying an override through the page front-matter, like this:

```
---
title: Dark Archive
ledger:
  preset: night-ink
  palette:
    accent: red
---
```

Customisation work by the following order of priority: Preset < Site config < Page frontmatter.

This means that the variables in the page frontmatter have the highest priority, followed by the values you specify through your `_config.yml` file. The default (and lowest priority) is the values specified in the two presets, which are `palmleaf` and `night-ink`.

Here's an example snippet for `_config.yml`:

```
title: The title of your website
author: Your name
description: A human-friendly, SEO-friendly, RAG-friendly description.
github:
  repository_url: https://github.com/<your_github_name>/<your_repo_name>

remote_theme: AninditaBasu/ledger

plugins:
  - jekyll-remote-theme

ledger:
  preset: night-ink
  palette:
    accent: red
```

## Specifying the left-column TOC

Create a file called `navigation.yml` inside a `_data` folder in your project root (next to `_config.yml`). Then, specify the ToC in it. One level of nesting is supported.

For example:

```
- title: Home
  url: /
- title: Installing
  children:
    - title: Prerequisites
      url: /prereqs.html
    - title: Steps
      url: /install-steps.html
- title: Getting started
  url: /quick-start.html
- title: Configuring
  children:
    - title: Actions
      url: /config-action.html
    - title: Workflows
      url: /config-workflow.html
```

## Logos and favicons

You can display a custom logo in the sidebar and a favicon in the browser tab. Place your images in an `images` folder in your project root; the theme automatically detects them. You can have your logo and favicon in more than one size, for example:

| Purpose                | File name     | Recommended size    |
| ------------------ | ------------- | ---------------------- |
| Legacy browser support | `favicon.ico`     | multi-size (16 x 16, 32 x 32, 48 x 48) |
| Standard favicon  | `favicon-32.png`      | 32 x 32    |
| Android/PWA  | `favicon-192.png`     | 192 x 192    |
| Apple touch  | `apple-touch-icon.png`| 180 x 180    |

```
images/
  logo.png
  favicon.ico
  favicon-16.png
  favicon-32.png
```

Supported logo formats are `PNG`, `SVG`, `WebP`.

## Page elements

Standard Markdown elements are supported. 

Admonitions must be written like this:

```
{% include admonition.html
   type="warning"
   title="Warning"
   content="This one's a warning."
%}
```

The following values are supported for the `type` variable: `note`, `warning`, `tip`, and `caution`.

## API pages

API pages can be rendered directly from a `JSON` or `YML` file. Two kinds of rendering is available: static page and interactive page.

### Static API

Create a folder called `_data` in your project root (next to `_config.yml`). Place the API specification file in this folder. The file can be in `JSON` or `YML` format.

Then, create a Markdown file with content similar to the following code snippet:

```
---
layout: api
title: REST API
description: Simple JSON endpoints for Ledger
---

# {{ page.title }}

{{ page.description }}

{% for ep in site.data.api.endpoints %}
## <span class="method">{{ ep.method }}</span> {{ ep.path }}

{{ ep.description }}

{% endfor %}
```

In this example, the `_data` folder contains a file called `api.json`, with the following structure:

```
{
  "endpoints": [
    {
      "method": "GET",
      "path": "/entries",
      "description": "Returns all ledger entries"
    },
    {
      "method": "POST",
      "path": "/entries",
      "description": "Creates an entry"
    }
  ]
}
```

A static page is rendered, with all of the endpoints.

### Interactive API

Create a folder called `assets` in your project root (next to `_config.yml`). Place the API specification file in this folder. The file can be in `JSON` or `YML` format. Make sure that this specification file is written in the OpenAPI format. 

Then, create a Markdown file with the following content:

```
---
layout: api-swagger
title: REST API interactive
openapi: /assets/openapi_vs.json
---
```

The value of the `openapi` variable should contain the name of the API specification file. In this example, the name of the file is `openapi_vs.json`.

The rendered page is interactive, with a try-it-out option.

## License

MIT
