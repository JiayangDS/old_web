# Profile Website Blueprint

**Jiayang Lu**  
Based on al-folio template · Content plan + design notes + final copy

Pages: Home · Publications · Academic · Creative · CV

---

## Contents

1. Site Structure & Navigation
2. Home Page — layout, bio copy, contact links
3. Publications Page
4. Academic Page — project cards
5. Creative Page — business/creative portfolio
6. CV Page
7. Global Design Decisions
8. Content Checklist

---

## 1. Site Structure & Navigation

```
┌──────────────────────────────────────────────────┐
│  Jiayang Lu    Home  Publications  Academic  Creative  CV  │
└──────────────────────────────────────────────────┘
  title = name (left)                    nav links (right)
```

Five pages. "Jiayang Lu" as the site title (left-aligned in header, clickable → Home). Nav links right-aligned.

| **Page**        | **Route**       | **Purpose**                        | **Status**                        |
|-----------------|-----------------|------------------------------------|-----------------------------------|
| **Home**        | /               | Bio + photo + social links         | Content ready (below)             |
| **Publications**| /publications/  | Paper list (BibTeX-driven)         | 1 paper live, 1 pending review    |
| **Academic**    | /academic/      | Research project cards             | DINO-3DRA ready, rest TBD         |
| **Creative**    | /creative/      | Business/creative portfolio        | Under construction                |
| **CV**          | /cv/            | Embedded PDF or HTML resume        | Need to prepare PDF               |

> 🎨 **DESIGN** — al-folio uses Jekyll with `_pages/` directory. Each page is a `.md` file with YAML front matter. The navbar is configured in `_config.yml` under `nav_links`.

---

## 2. Home Page

### 2.1 Layout

```
┌──────────────────────────────────────────────┐
│                                              │
│   [Photo]     Jiayang Lu                    │
│              MSc Health Data Science (UoM)  │
│              PhD Applicant | AI for Medicine │
│                                              │
│              ✉ 🔗 💻 🎓                      │
│              email linkedin github scholar   │
│                                              │
├──────────────────────────────────────────────┤
│   Bio paragraph (2–3 sentences)              │
├──────────────────────────────────────────────┤
│   Selected Publications                      │
└──────────────────────────────────────────────┘
```

> 🎨 **DESIGN** — al-folio home uses a two-column layout: photo left, name + subtitle + social icons right. Below that, the bio paragraph in full width. Remove the address block and news section from the default template.

### 2.2 Subtitle

Below your name, one line:

> MSc Health Data Science (UoM) | PhD Applicant | AI for Medical & Biological Applications

### 2.3 Bio Copy (final — proofread)

> ✅ **NOTE** — This replaces the draft bio. All typos fixed, tightened to 3 short paragraphs. Tone: professional but approachable.

I am a PhD applicant seeking funded research positions for 2026/27. I graduated with Distinction from the **MSc Health Data Science** programme at the University of Manchester, where I conducted extended research on AI for medical imaging. My recent work on **leveraging 2D Vision Foundation Models for 3D cerebral aneurysm segmentation** resulted in a MICCAI 2026 submission (under review). I am supervised by [Supervisor A] and [Supervisor B].

My technical foundation spans **computer vision, LLMs, reinforcement learning, and multi-modal learning**, with practical experience in data engineering, cloud computing, and ML systems. My research interests centre on **AI for medical and biological applications** and **multi-modal learning**.

Before MSc, I completed a BSc in Biological Science with strong wet-lab and bioinformatics skills, and co-authored a **publication on microalgal biochemistry**. My prior experience founding a creative-industry startup also gave me a strong business perspective and project management skills.

### 2.4 Social / Contact Links

Replace the al-folio default address block with icon links only:

| **Icon** | **Link to**                  | **al-folio config**      |
|----------|------------------------------|--------------------------|
| ✉️ Email  | your.email@domain.com        | `email: true`            |
| 🔗 LinkedIn | linkedin.com/in/yourname  | `linkedin_username:`     |
| 💻 GitHub   | github.com/yourname       | `github_username:`       |
| 🎓 Google Scholar | scholar.google.com/... | `scholar_userid:`    |

> 🎨 **DESIGN** — In `_config.yml`, set `display_address: false` and enable only the four icons above. al-folio renders them as a clean icon row under your name.

### 2.5 Selected Publications (on Home)

Show 1–2 featured publications on the home page. al-folio does this via the `selected: true` flag in `_bibliography/*.bib` entries.

> ✅ **NOTE** — Currently 1 paper (algae biochemistry). Add DINO-3DRA after acceptance. Set `selected: true` on both.

---

## 3. Publications Page

al-folio auto-generates this from BibTeX files in `_bibliography/`. Each entry renders as a card with title, authors, venue, year, and optional links (PDF, code, project page).

### 3.1 Current Entries

**Paper 1 — Published**

> Wu, M., Zhu, R., Lu, J., et al. (2020). Effects of different abiotic stresses on carotenoid and fatty acid metabolism in *Dunaliella salina* Y6. *Annals of Microbiology*, 70(1).

Tags: biology, microalgae, biochemistry | Links: DOI

**Paper 2 — Under Review**

> Lu, J., et al. (2026). DINO-3DRA: Leveraging 2D Foundation Model Semantics for 3D Cerebral Aneurysm Segmentation. *MICCAI 2026*. [Under review]

Tags: medical imaging, deep learning, segmentation | Links: arXiv, Code, Project Page

> ⚠️ **FIX** — Do NOT list DINO-3DRA as published until accepted. al-folio supports a `preview: true` flag or you can add it after notification. Keep BibTeX ready in `_bibliography/papers.bib`.

> 🎨 **DESIGN** — In `_bibliography/papers.bib`, set `selected: true` for both entries so they appear on the home page. Use `abbr` field for venue badges (e.g., `abbr: {MICCAI}`).

---

## 4. Academic Page

A grid of project cards. Each card links to its own detail page (built with the Academic Project Page Template). This is your research portfolio.

### 4.1 Layout

```
┌──────────────────────────────────────────────┐
│  Academic Projects                          │
│                                              │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  │
│  │  [thumb]    │  │  [thumb]    │  │  [thumb]    │  │
│  │ DINO-3DRA  │  │ MSc HDS    │  │ AI Journey │  │
│  │ MICCAI 26  │  │ UoM 2025   │  │ Self-study │  │
│  └─────────────┘  └─────────────┘  └─────────────┘  │
└──────────────────────────────────────────────┘
```

### 4.2 Project Cards

| **Project**                 | **One-liner**                              | **Tags**   | **Status**   |
|-----------------------------|--------------------------------------------|------------|--------------|
| **DINO-3DRA**               | 2D VFMs for 3D aneurysm segmentation       | MICCAI 2026 | ✅ Live      |
| **MSc Health Data Science** | Coursework highlights & capstone           | UoM 2025   | 🚧 TBD       |
| **AI Studying Journey**     | Self-directed learning path in ML/DL       | Ongoing    | 🚧 TBD       |

> ✅ **NOTE** — DINO-3DRA links to its own project page (the one we already built). Use the Academic Project Page Template hosted as a sub-page or separate GitHub Pages site.

> 🎨 **DESIGN** — al-folio supports a `_projects/` collection. Each project is a `.md` file with thumbnail, title, description, and `redirect_url`. Use a 3-column grid (al-folio default). Add a category filter if you reach 5+ projects.

> 📋 **TODO** — For "MSc HDS" and "AI Journey": show cards with a "Page under construction" badge. Use a subtle greyed-out style so visitors know content is coming. Don't leave them as dead links.

---

## 5. Creative Page

Your non-academic portfolio: business ventures, creative projects, and industry experience. This differentiates you from typical PhD applicants.

### 5.1 Layout

```
┌──────────────────────────────────────────────┐
│  Creative & Business                        │
│                                              │
│  Short intro: bridging tech + creative       │
│                                              │
│  ┌──────────────────────────────────────────┐  │
│  │  [thumb]                                 │  │
│  │  Circusland                              │  │
│  │  Innovative immersive experience studio  │  │
│  │  [Under construction badge]              │  │
│  └──────────────────────────────────────────┘  │
└──────────────────────────────────────────────┘
```

> ✏️ **COPY** — Intro line suggestion: "Before entering data science, I co-founded a creative-industry startup. This page collects projects where technology meets creative storytelling and business."

**Circusland** — Innovative immersive experience studio. Currently the only planned entry. Show as a full-width card with a thumbnail and short description.

> 🎨 **DESIGN** — Use the same `_projects/` collection as Academic but with a different category. al-folio supports category filtering. Set `category: creative` in the project front matter. This keeps one unified grid system across both pages.

> 📋 **TODO** — Prepare a short write-up and 2–3 images for Circusland. Even a one-paragraph description + hero image makes the page feel intentional rather than empty.

---

## 6. CV Page

Two options. Pick one:

**Option A — PDF embed (simpler):**

Upload a polished PDF to `/assets/pdf/cv.pdf`. al-folio's default `cv.md` includes an iframe embed. One-click download link below it. *(Still working on writing it — will update later.)*

> 🎨 **DESIGN** — Recommendation: start with Option A (PDF embed) to launch fast. Migrate to Option B later when you have time. Most PhD committee members prefer downloading a PDF anyway.

> 📋 **TODO** — Prepare a 1–2 page CV PDF. Sections: Education, Research Experience, Publications, Technical Skills, Awards, Other Experience (Circusland).

---

## 7. Global Design Decisions

### 7.1 Theme & Colours

al-folio ships with light and dark mode. Keep both enabled. Customise the accent colour to match your DINO-3DRA project page:

```scss
// In _sass/_themes.scss
$theme-color: #0F6E56;  // same green accent
```

### 7.2 Typography

al-folio default fonts are clean and academic. No need to change unless you want consistency with the project page (which uses Georgia + DM Sans).

### 7.3 Profile Photo

Square crop, minimum 400×400px. Professional but approachable. Place in `assets/img/prof_pic.jpg`.

### 7.4 Footer

al-folio auto-generates a minimal footer with social icons and "Powered by al-folio". Keep it clean — no additional content needed.

### 7.5 SEO & Meta

Set these in `_config.yml`:

```yaml
title: Jiayang Lu
description: PhD Applicant | AI for Medical & Biological Applications
first_name: Jiayang
last_name: Lu
url: https://yourdomain.github.io
baseurl: /your-repo-name
```

> 🎨 **DESIGN** — Enable Google Analytics and Open Graph meta tags in `_config.yml` for visibility. Important if you're sharing your site with potential PhD supervisors.

---

## 8. Content Checklist

| ☐ | **Task**                                                            | **Page**     | **Priority** |
|---|---------------------------------------------------------------------|--------------|--------------|
| ☐ | Finalise bio text (use copy from Section 2.3)                       | Home         | ⭐⭐⭐         |
| ☐ | Profile photo (square, 400px+)                                      | Home         | ⭐⭐⭐         |
| ☐ | Set up social links (email, LinkedIn, GitHub, Scholar)              | Home         | ⭐⭐⭐         |
| ☐ | Add algae paper to `_bibliography/papers.bib`                       | Publications | ⭐⭐⭐         |
| ☐ | Prepare DINO-3DRA BibTeX (add after acceptance)                     | Publications | ⭐⭐          |
| ☐ | Create DINO-3DRA project card with thumbnail                        | Academic     | ⭐⭐⭐         |
| ☐ | Link DINO-3DRA card to project page                                 | Academic     | ⭐⭐⭐         |
| ☐ | Add "under construction" cards for MSc HDS + AI Journey             | Academic     | ⭐⭐          |
| ☐ | Write Circusland short description + find thumbnail                 | Creative     | ⭐            |
| ☐ | Prepare CV PDF (1–2 pages)                                          | CV           | ⭐⭐          |
| ☐ | Set `_config.yml` (title, description, social, SEO)                 | Global       | ⭐⭐⭐         |
| ☐ | Deploy to GitHub Pages                                              | Global       | ⭐⭐⭐         |
| ☐ | Ask someone to proofread all pages                                  | Global       | ⭐⭐          |

> ✅ **NOTE** — Launch priority: Home + Publications + Academic (with DINO-3DRA card) + CV. Creative page can wait. Ship the core pages first, then iterate.
