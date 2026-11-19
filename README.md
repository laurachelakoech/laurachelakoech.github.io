# Portfolio template (Jekyll)

A portfolio site where all content lives in two places:

Name, bio, skills, contact, resume, site-wide SEO: `_data/site.yml`
Each project (text, images, per-project SEO): `_projects/<project-name>/index.md`

## Editing the site info

Open `_data/site.yml`.
Replace the headshot at `assets/images/headshot.svg` and drop a social-preview image at `assets/images/og-image.png` (1200x630).
To show a resume download button, put the PDF in `assets/` and set `hero.resume_file`.

## Adding a project

1. Copy the folder `_projects/example-project` and rename it (the folder name becomes the web address).
2. Put the project's images in that same folder.
3. Edit `index.md`: the content in between the '---' lines holds the title, summary, tags, cover image and SEO;
   - Everything below is the project write-up in Markdown.
   - Reference images by file name only: `![Alt text](screenshot.jpg)`.
4. A fresh blank copy with notes is in `_templates/project-template.md`.

**Reordering:** change `order:` (lower = first). **Hiding:** add `published: false`.

### Per-project SEO

By default the page title is `Project title | Your Name`, the description is the `summary`, and the share image is the `cover`.
Override with `seo_title`, `seo_description`, `seo_image` in the front matter.

## Running locally

```sh
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000. The `url` in `_data/site.yml > seo` must be set to the live address
before launch (it is used for canonical links, social previews and the sitemap).

## Deploying

The output is plain static files (`bundle exec jekyll build` -> `_site/`), so Netlify, Cloudflare Pages,
Vercel or GitHub Pages (via a GitHub Actions workflow) all work. If deploying to a sub-path, set `baseurl` in `_config.yml`.

`sitemap.xml` and `robots.txt` are generated automatically.
