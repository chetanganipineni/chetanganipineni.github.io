# Personal Blog Readme

For now, I'm building this blog using GitHub Pages and Jekyll. It's free and easy to use with Markdown-based posts, which I mostly write in now.

---

# Repository Structure

```
.
├── _config.yml        # Jekyll + GitHub Pages configuration
├── _posts/            # Blog posts (Markdown files)
│   └── YYYY-MM-DD-title.md
├── index.html         # Homepage with post list
├── assets/            # Optional CSS/images
└── README.md          # This file
```

### `_posts/`

All blog posts must live here and must follow these patterns:

1. filenames

```
YYYY-MM-DD-title.md
```

2. YAML front-matter

```md
---
title: "My Post Title"
date: 2025-01-15
tags: [security, programming]
---

Actual content here.
```

---

# How Jekyll + GitHub Pages Work

GitHub Pages automatically runs Jekyll every time you push to the `main` branch.

### What Jekyll does:
1. Reads `_config.yml`
2. Reads folders like `_posts/`
3. Converts Markdown to HTML
4. Applies layouts from the selected theme
5. Outputs the final static website

---

#  Build & Deployment

1. Create a new file under `_posts/`:

```
_posts/2025-01-20-my-new-article.md
```

2. Add front‑matter:

```md
---
title: "My New Article"
date: 2025-01-20
tags: [programming, security]
---

Your Markdown content.
```

3. Don't forget to set up SSH agent:

```sh
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/github
```

4. Commit and push:
```sh
git add .
git commit -m "Add new article"
git push
```

The post is live after ~10 seconds.

---

# Running Locally

To preview locally, install Jekyll:

## 1. Install Ruby + Bundler

```sh
brew install ruby
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
gem install bundler jekyll
```

## 2. Install dependencies
```sh
bundle install
```

If the repo doesn’t have a `Gemfile`, create one:

```ruby
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
```

Then run:
```sh
bundle install
```

## 3. Serve the site locally
```sh
bundle exec jekyll serve
```

Visit:
```
http://localhost:4000
```

---

# Customization

You can customize:
- CSS in `assets/style.css`
- Theme via `_config.yml`
- Layouts by overriding files in `_layouts/`

The default theme is:

```yaml
theme: minima
```