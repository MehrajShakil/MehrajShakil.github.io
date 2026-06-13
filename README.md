# Mehraj Shakil — Personal Website

A personal site built with [Jekyll](https://jekyllrb.com/) and hosted free on **GitHub Pages**.
It includes a home/about page, portfolio, articles (blog), resume, and contact page — with light/dark mode and full mobile support.

Live at: **https://MehrajShakil.github.io**

---

## 🚀 Deploy to GitHub Pages (one time)

Because your username is `MehrajShakil`, this is a **user site**, so the repo **must** be named exactly:

```
MehrajShakil.github.io
```

1. Create a new repo on GitHub named `MehrajShakil.github.io` (Public).
2. Push this folder to it:

   ```bash
   git init
   git add .
   git commit -m "Initial website"
   git branch -M main
   git remote add origin https://github.com/MehrajShakil/MehrajShakil.github.io.git
   git push -u origin main
   ```

3. On GitHub: **Settings → Pages → Build and deployment → Source = "Deploy from a branch"**, Branch = `main` / `(root)`. Save.
4. Wait ~1 minute, then open **https://MehrajShakil.github.io** 🎉

GitHub rebuilds the site automatically every time you push.

---

## ✍️ Everyday use

### Add an article
Create a file in `_posts/` named `YYYY-MM-DD-title.md`:

```markdown
---
title: "My new post"
date: 2026-07-01
tags: [webdev]
---

Write your content in Markdown here.
```

### Add a portfolio project
Copy `_projects/sample-project.md`, rename it, and edit the front matter
(`title`, `summary`, `tech`, `live_url`, `repo_url`).

### Edit pages
- Home / about → `index.html`
- Resume → `resume.md` (drop a PDF at `assets/files/resume.pdf` for the download button)
- Contact / social links → edit the top of `_config.yml`

### Personalize
Open `_config.yml` and set your `email`, `linkedin_username`, `twitter_username`, etc.
Blank values are automatically hidden.

---

## 🖥️ Preview locally (optional)

Requires [Ruby](https://www.ruby-lang.org/) + Bundler.

```bash
gem install bundler
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000

---

## 📁 Structure

```
├── _config.yml          # Site settings (edit your info here)
├── index.html           # Home / about
├── portfolio.html       # Projects listing
├── articles.html        # Blog listing
├── resume.md            # Resume
├── contact.md           # Contact page
├── _posts/              # Your articles (Markdown)
├── _projects/           # Your portfolio items (Markdown)
├── _layouts/            # Page templates
├── _includes/           # Header, footer, head
└── assets/              # CSS, JS, images
```
