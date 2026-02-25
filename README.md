# `ledger` theme

A minimal documentation theme for GitHub Pages.

---

- [Features](#features)
- [Live example](#live-example)
- [How to use](#how-to-use)
- [Configuration](#configuration)
   - [Minimal project structure](#minimal-project-structure)
   - [Navigation](#navigation)
   - [Logos and favicon](#logos-and-favicon)
   - [Page-specific overrides](#page-specific-overrides)
- [Troubleshooting](#troubleshooting)
- [License](#license)

---

## Features

- Two-column layout with left navigation panel.
- Parchment-style background with soft ink colours.
- Mobile-responsive. Sidebar collapses into top navigation.
- Zero local setup. Works directly with GitHub Pages through `remote_theme`.
- Mermaid support.

## Live example

See the theme in action, with all of its possible presets, at [https://aninditabasu.github.io/ledger/](https://aninditabasu.github.io/ledger/)

## How to use

1. In your own repository root, create a file named `_config.yml` with the following code snippet:
    ```
    remote_theme: AninditaBasu/ledger
    plugins:
      - jekyll-remote-theme
    ```
1. Enable GitHub Pages: In your repository settings, go to **Pages** > **Deploy from branch** > **main**.
1. Push your site files.

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
| `ledger.preset`   | If used, must be `dark` |

Here's an example snippet:

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
  preset: dark
```

### Minimal project structure

```
_config.yml
index.md
images/
  logo.png
  favicon.ico
```

### Navigation

Create a file called `_data/navigation.yml` in your project root (next to `_config.yml`). Then, specify the ToC in it. For example:

```
- title: Home
  url: /
- title: Getting Started
  url: /getting-started.html
- title: API
  url: /api.html
```

### Logos and favicons

You can display a custom logo in the sidebar and a favicon in the browser tab. Place your images in an `images` folder in your project root; the theme automatically detects them. You can have your logo and favicon in more than one size, for example:

| Purpose                | File name             | Recommended size                       |
| ---------------------- | --------------------- | -------------------------------------- |
| Legacy browser support | `favicon.ico`         | multi-size (16 x 16, 32 x 32, 48 x 48) |
| Standard favicon       | `favicon_32.png`      | 32 x 32                                |
| Android/PWA            | `favicon_192.png`     | 192 x 192                              |
| Apple touch            | `apple_touch_icon.png`| 180 x 180                              |

```
images/
  logo.png
  favicon.ico
  favicon-16.png
  favicon-32.png
```

Supported logo formats are `PNG`, `SVG`, `WebP`.

### Page-specific overrides

You can set the theme of any page to be different from the site theme, by specifying an override through the page front-matter, like this:

```
---
title: Dark Archive
ledger:
  preset: dark
---

```

In this example, only this page uses the `dark` preset; other pages use the site-wide preset you specified in `_config.yml`. If no site-wide preset is specified in `_config.yml`, the default (light) theme is used.


## Troubleshooting

**The theme does not load**

1. Confirm that `_config.yml` contains the following snippet:
    ```
	plugins:
  	  - jekyll-remote-theme
    ```
1. Ensure that is **GitHub Pages**, the **Source** field is set to **GitHub Actions**.
1. Push a commit after changing `_config.yml`.

**The theme is not applied**

If your site already contains `_layouts` or `assets` folders, they override the theme files. To use the `ledger` theme:

1. Remove or rename any local `_layouts/default.html` file.
1. Remove or rename any local `assets/style.css`.

## License

MIT