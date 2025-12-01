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

---

# ✔ Summary

This repo is a fully static Jekyll blog deployed through GitHub Pages. You write posts in Markdown, push to GitHub, and the site builds automatically. Local testing is optional but helpful.

If you want enhancements like:
- tags page
- categories
- sidebar navigation
- dark mode
- a new theme (e.g., Minimal Mistakes, Chirpy)
- automatic sitemaps

Just ask!
# Personal Blog Website - Documentation

This repository hosts a simple, static blog powered by **Markdown**, **Jekyll**, and **GitHub Pages**. The site structure, build process, and deployment are intentionally minimal to keep things easy to maintain.

---

## 📁 Repository Structure
```
sitecode/
    index.html        # Homepage that loads and displays blog posts
    posts/            # Folder containing Markdown blog entries
        counting_incomplete_cubes.md
```
Nothing else is required unless you want to customize layouts or add CSS/JS.

---

## ✍️ How Pages Work (GitHub Pages + Jekyll)
GitHub Pages automatically runs **Jekyll**, which:
- Converts `.md` Markdown files into HTML
- Allows simple templating using Front Matter (`---` YAML blocks)
- Auto‑generates pages in `_site/` on build
- Publishes the final static site to the internet

When Jekyll runs:
1. It scans `posts/*.md`
2. Parses the front‑matter
3. Converts Markdown → HTML
4. Injects the content into layouts (if any)
5. Outputs final pages

You **don’t need your own layouts** unless you want custom styling. GitHub Pages already includes a default layout system.

Typical Markdown file with front matter:
```md
---
layout: default
title: Counting Incomplete Cubes
---

Your article text here…
```

---

## 📄 How the Homepage Loads Posts
Your `index.html` fetches the posts using Jekyll’s built‑in post list.

A simple example:
```html
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
```

GitHub Pages handles the generation and provides the `site.posts` variable automatically.

---

## 🚀 Build & Deployment Workflow
You don’t run builds manually.

### **Deployment steps**
1. Push to GitHub
2. GitHub Pages automatically runs Jekyll
3. The resulting site is deployed to:
   - **https://<username>.github.io** for user sites
   - **https://<username>.github.io/<repo-name>** for project sites

### ⚠️ Note
For a personal site (`username.github.io`), the repo **must be named exactly**:
```
<username>.github.io
```

---

## 🧪 Local Testing
If you want to preview your site locally:

### 1. Install Ruby & Bundler
(macOS comes with Ruby, but often old — use `brew` if needed.)
```sh
brew install ruby
```

### 2. Install Jekyll
```sh
gem install bundler jekyll
```

### 3. Run local server
In the repo root:
```sh
jekyll serve
```
This builds the site and starts a dev server at:
```
http://localhost:4000
```
Changes should hot‑reload.

---

## 📝 Writing New Blog Posts
1. Add a new Markdown file inside `/posts/`:
```
posts/my_new_post.md
```

2. Include front matter:
```md
---
layout: default
title: My New Post
---

Content goes here.
```

3. Commit + push:
```sh
git add .
git commit -m "Add new post: My New Post"
git push
```
GitHub will automatically rebuild the site.

---

## 🎨 Optional: Custom CSS or Layouts
If you want to override the default GitHub Pages look:

### Add custom CSS:
```
assets/style.css
```
Link it inside `index.html`:
```html
<link rel="stylesheet" href="/assets/style.css">
```

### Add custom layouts:
```
_layouts/default.html
```
Front matter layout references will use this.

---

## ✔️ Summary
- **Markdown-based blog** → easy to edit
- **GitHub Pages + Jekyll** → zero backend, zero cost
- **Automatic deployment** on push
- **Local preview** with Jekyll