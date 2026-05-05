# Jiayang Lu — Profile Website Build Guide

Built on **al-folio** (Jekyll) · Deployed to **GitHub Pages**

---

## Overview of Files You Need to Edit

```
your-repo/
├── _config.yml                    ← Site settings, social links, SEO
├── _pages/
│   ├── about.md                   ← Home page (bio, photo, social)
│   ├── publications.md            ← Publications page
│   ├── academic.md                ← Academic project cards
│   ├── creative.md                ← Creative/business portfolio
│   └── cv.md                      ← CV page
├── _bibliography/
│   └── papers.bib                 ← All your papers in BibTeX
├── _projects/
│   ├── dino-3dra.md               ← DINO-3DRA project card
│   ├── msc-hds.md                 ← MSc HDS card (under construction)
│   ├── ai-journey.md              ← AI Journey card (under construction)
│   └── circusland.md              ← Circusland card (under construction)
├── assets/
│   ├── img/prof_pic.jpg           ← YOUR PROFILE PHOTO (replace this)
│   ├── img/dino3dra_thumb.png     ← DINO-3DRA thumbnail
│   └── pdf/cv.pdf                 ← YOUR CV PDF (upload this)
└── _sass/
    └── _custom.scss               ← Accent colour override
```

All ready-to-use code files are provided alongside this guide.  
Just copy them in, fill in the **[PLACEHOLDER]** values, and deploy.

---

## Step 1 — Fork & Clone the Template

```bash
# 1. Go to https://github.com/alshedivat/al-folio and click "Use this template"
# 2. Name your repo: yourusername.github.io
# 3. Clone it locally:
git clone https://github.com/YOUR_USERNAME/YOUR_USERNAME.github.io.git
cd YOUR_USERNAME.github.io
```

---

## Step 2 — Copy in the Provided Files

Replace the following files with the ones provided in this package:

| File | Action |
|------|--------|
| `_config.yml` | Replace entirely |
| `_pages/about.md` | Replace entirely |
| `_pages/publications.md` | Replace entirely |
| `_pages/academic.md` | Replace entirely |
| `_pages/creative.md` | Replace entirely |
| `_pages/cv.md` | Replace entirely |
| `_bibliography/papers.bib` | Replace entirely |
| `_projects/dino-3dra.md` | New file |
| `_projects/msc-hds.md` | New file |
| `_projects/ai-journey.md` | New file |
| `_projects/circusland.md` | New file |
| `_sass/_custom.scss` | New file (or append) |

---

## Step 3 — Fill in Your Personal Details

Search for `[PLACEHOLDER]` across all files and replace:

| Placeholder | Replace with |
|-------------|--------------|
| `[YOUR_GITHUB_USERNAME]` | e.g. `jiayanglu` |
| `[YOUR_EMAIL]` | your real email address |
| `[YOUR_LINKEDIN]` | your LinkedIn username (not full URL) |
| `[YOUR_SCHOLAR_ID]` | from your Google Scholar URL |
| `[SUPERVISOR_A]` | your actual supervisor name |
| `[SUPERVISOR_B]` | your actual supervisor name |
| `[REPO_NAME]` | your GitHub repo name |

---

## Step 4 — Add Your Assets

```
assets/img/prof_pic.jpg     ← Square photo, minimum 400×400px
assets/img/dino3dra_thumb.png ← Screenshot or figure from your paper
assets/pdf/cv.pdf           ← Your 1–2 page CV
```

For the DINO-3DRA project page assets (used on the dedicated project page):
```
assets/img/dino3dra_fig1.png   ← Architecture diagram (Fig 1)
assets/img/dino3dra_fig4.png   ← Cross-dataset visual comparison
assets/img/sample.gif          ← 3D rotation GIF
```

---

## Step 5 — Run Locally (Optional but Recommended)

```bash
# Using Docker (easiest):
docker compose pull
docker compose up
# Visit http://localhost:8080

# OR using Ruby/Bundler:
bundle install
bundle exec jekyll serve
# Visit http://localhost:4000
```

---

## Step 6 — Deploy to GitHub Pages

```bash
git add .
git commit -m "Initial site setup"
git push origin main
```

Then in GitHub:
1. Go to your repo → **Settings** → **Pages**
2. Set source to **GitHub Actions** (not branch)
3. Wait ~4 min for the Actions workflow to complete
4. Visit `https://YOUR_USERNAME.github.io`

---

## Launch Checklist

### Must-do before sharing with supervisors:
- [ ] Replace `prof_pic.jpg` with your actual photo
- [ ] Fill in all `[PLACEHOLDER]` values in `_config.yml`
- [ ] Verify bio text in `about.md` reads correctly
- [ ] Upload `cv.pdf` to `assets/pdf/`
- [ ] Test the site locally or on GitHub Pages

### Nice-to-have:
- [ ] Add DINO-3DRA thumbnail image
- [ ] Link DINO-3DRA card to the dedicated project page
- [ ] Set up Google Analytics in `_config.yml`
- [ ] Proofread all pages

### After MICCAI acceptance:
- [ ] Add DINO-3DRA BibTeX to `papers.bib` with `selected = {true}`
- [ ] Update DINO-3DRA project card status from "Under Review" to "MICCAI 2026"

---

## Key al-folio Docs

- Full docs: https://alshedivat.github.io/al-folio/
- Projects: https://github.com/alshedivat/al-folio/blob/main/CUSTOMIZE.md
- BibTeX fields: look at `_bibliography/papers.bib` examples in the template
