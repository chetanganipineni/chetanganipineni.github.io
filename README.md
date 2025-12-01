# Personal Blog (GitHub Pages + Jekyll)

(Most of this is AI-generated)

This repository hosts a personal blog built using **GitHub Pages** and **Jekyll**. It is fully static, free to host, and supports Markdown-based posts.

This README explains:
- Repository layout
- How GitHub Pages + Jekyll work
- How posts are generated
- How builds & deployment work
- How to run and test the site locally

---

# 📁 Repository Structure

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
- All blog posts must live here.
- Filenames must follow:

```
YYYY-MM-DD-title.md
```

- Each file must include YAML front‑matter:

```md
---
title: "My Post Title"
date: 2025-01-15
tags: [security, programming]
---

Your content here.
```

---

# ⚙️ How Jekyll + GitHub Pages Work

GitHub Pages automatically runs Jekyll **every time you push** to the `main` branch.

### What Jekyll does:
1. Reads `_config.yml`
2. Reads folders like `_posts/`
3. Converts Markdown → HTML
4. Applies layouts from the selected theme (default: **minima**)
5. Outputs the final static website

### Important details:
- GitHub Pages only allows **safe** Jekyll plugins
- Build output is **not** committed to the repo
- Published site appears at:

```
https://<username>.github.io
```

---

# 🏗 Build & Deployment

Deployment is **automatic**.

### Deploy steps:
1. Commit changes
2. Push to GitHub
3. GitHub Pages rebuilds the site in ~15–30 seconds
4. New content becomes live instantly

Nothing else is required—no CI/CD scripts and no server.

---

# ▶️ Running Locally (Optional)

To preview locally (recommended), install Jekyll:

## 1. Install Ruby + Bundler
(on macOS)

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

The local server auto‑reloads when you edit files.

---

# 📝 Adding a New Blog Post

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

3. Commit and push:
```sh
git add .
git commit -m "Add new article"
git push
```

The post is live.

---

# 🏠 How the Homepage Works

`index.html` contains Liquid template code that lists all posts:

```html
{% raw %}{% for post in site.posts %}
  <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
  <p>{{ post.date | date: "%B %d, %Y" }}</p>
  <p>{{ post.excerpt }}</p>
{% endfor %}{% endraw %}
```

Jekyll automatically:
- sorts posts newest → oldest
- generates excerpts
- handles URLs

---

# 🎨 Customization

You can customize:
- CSS in `assets/style.css`
- Theme via `_config.yml`
- Layouts by overriding files in `_layouts/`

The default theme is:

```yaml
theme: minima
```

---

# 📦 Useful Commands

### Check Jekyll version
```sh
jekyll -v
```

### Clean Jekyll cache
```sh
bundle exec jekyll clean
```

### Rebuild locally
```sh
bundle exec jekyll build
```