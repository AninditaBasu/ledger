# `ledger` theme

A documentation theme for GitHub Pages.

---

- [Features](#features)
- [Live example](#live-example)
- [How to use](#how-to-use)
- [Configuration](#configuration)
- [Navigation](#navigation)
- [Logos and favicon](#logos-and-favicon)
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

## How to use

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

## Configuration

You can customise the `ledger` theme by specifying the following fields in your site `_config.yml` file. 

| Key      | Purpose                                              |
| ------- | ------------------------------------- |
| `title`    | Displayed as the site name in the sidebar    |
| `author`  | Used in the footer copyright line       |
| `description`   | Used in the HTML `<meta>` description tag    |
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

## Navigation

Create a file called `navigation.yml` inside a `_data` folder in your project root (next to `_config.yml`). Then, specify the ToC in it. For example:

```
- title: Home
  url: /
- title: Getting Started
  url: /getting-started.html
- title: API
  url: /api.html
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

## License

MIT
