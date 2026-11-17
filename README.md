# Zhuo Liu’s academic homepage

Hugo source for <https://joeliuz6.github.io/>. Uses **Academic Minimal**, a custom local theme in `themes/academic-minimal/`: warm white background, restrained burgundy accents, serif publication titles, and a desktop layout with section headings beside the content. Narrow screens place the portrait beside the name and stack the sections vertically. It has no JavaScript, external fonts, npm packages, or Hugo module dependencies. The stylesheet URL includes a content hash so published layout changes refresh reliably.

## Preview and build

From this `quickstart` directory:

```powershell
hugo server
```

Open <http://localhost:1313/>. Stop the server with Ctrl+C.

To generate the production site:

```powershell
hugo --minify
```

The output is `public/`, which is ignored by Git. Hugo **0.81.0** is the tested version and is pinned in GitHub Actions and Netlify. A newer Hugo version should be tested before changing the pin, since Hugo’s template APIs can change.

## Edit content

| Content | File |
| --- | --- |
| Biography | `content/_index.md` |
| Name, profile links, email, CV path, SEO description | `config.toml` |
| Publications, authors, venue, year, paper links | `data/publications.json` |
| Research interests, teaching, service | `data/academic.json` |
| Research introduction | `content/en/Research/_index.md` |
| Blog articles | `content/en/Blog/` |
| Portrait | `static/media/new.png` |
| CV | `static/files/CV_ZhuoLiu.pdf` |
| Colors, spacing, responsive layout | `themes/academic-minimal/static/css/academic.css` |

Add a publication to `data/publications.json`, keeping the newest entries first:

```json
{
  "title": "Your paper title",
  "authors": "Zhuo Liu, Coauthor Name",
  "venue": "Conference name",
  "year": "2026",
  "selected": true,
  "url": "https://example.org/paper"
}
```

`selected: true` includes the paper on the homepage. Every entry appears on the Research page, grouped automatically by year. Optional `note`, `description`, and `code` fields add an award/status label, short summary, and code link. Keep `year` a quoted string. Author order is preserved; `Zhuo Liu` is emphasized automatically.

Use ISO dates (`2024-02-13`) in article front matter. Existing `/en/research/` and `/en/blog/` routes are retained. The original fairness post’s malformed `/en/1/01/01/fairness/` address redirects to `/en/2024/02/13/fairness/`. Use lowercase URLs: Windows does not support separate output folders that differ only in capitalization.

## GitHub Pages

The workflow `.github/workflows/gh-pages.yml` builds on pushes to `master` and publishes the output to the existing `gh-pages` branch. The repository’s Pages source should remain **Deploy from a branch → gh-pages → / (root)**. The workflow also supports manual runs. No external hosting migration is needed.

Commit and push source changes to `master` to publish an update. Check the repository’s Actions page for the deployment result; the live site reflects the latest successful deployment.

## Migration notes

- Biography came from the sibling `../home_page/` draft. The research statement was replaced verbatim with the author’s updated statement on November 16, 2026. The biography now includes hardware–software co-design work with Prof. Tony Geng; the homepage affiliation label and RA experience section were removed at the author’s request.
- The current portrait is an exact copy of the supplied `../new.png`, served as `/media/new.png` on the homepage and in social sharing metadata. Earlier portraits remain in `static/media/`.
- The current CV is an exact copy of `../Zhuo_Liu_Resume.pdf`, supplied on November 16, 2026. It is served at the existing `/files/CV_ZhuoLiu.pdf` address to preserve download links. The previous CV is backed up at `../.homepage-backup/CV-before-resume-2026-11-16.pdf`.
- The publication list contains all 18 entries supplied by the author, with 5 selected for the homepage: Compiler-Guided Adaptive Proof Search, Style or Content?, Model Prior, TreeRare, and AdvEvo-MARL. AAAI papers remain in the complete Research list and are excluded from the homepage selection.
- CoRMF and AdvEvo-MARL remain in the **2025** group at the author’s explicit request. CoRMF links to the final Physica A article (volume 681, 2026); AdvEvo-MARL displays **ICML 2026** as its venue while retaining the 2025 preprint year for grouping.
- New paper links and expanded author lists were checked against ACL Anthology, arXiv, and publisher records. CoRMF’s final author order and the complete Step-Level Reward Models and Ising-Traffic titles were corrected. Citation counts and copied Scholar interface labels are omitted.
- Older publications and teaching entries are retained. Teaching dates still reflect the supplied files.
- The blog body, tags, and legacy `block` / `end` shortcodes are preserved. Its date format was corrected.
- Original content and configuration are backed up outside the repository at `../.homepage-backup/2026-11-16/`.
- The original `themes/hugo-ht/` theme and sibling `../home_page/` draft remain available.
- Browser visual QA was unavailable in the editing environment. Before publication, inspect the homepage, Research, and Writing on desktop and a narrow mobile viewport.
