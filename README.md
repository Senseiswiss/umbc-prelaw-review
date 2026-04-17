# UMBC Pre-Law Review

Official website for the **UMBC Pre-Law Review**, a student-run undergraduate legal journal at the University of Maryland, Baltimore County.

**Live Site:** https://senseiswiss.github.io/umbc-prelaw-review/

---

## About the Journal

The UMBC Pre-Law Review publishes original legal scholarship by UMBC undergraduates on any area of law. Established in Fall 2025, the journal is currently in its inaugural volume and accepts submissions on a rolling basis.

- **Volume I, Issue 1** — Spring 2026
- **Submission email:** umbcprelawreview@umbc.edu
- **Instagram:** [@umbc.lawreview](https://www.instagram.com/umbc.lawreview)

---

## Site Structure

```
/
├── index.html          # Homepage — carousel, recent scholarship, stats, CTA
├── scholarship.html    # All published articles — search, filter, pagination
├── issues.html         # Volume/issue archive — links to filtered scholarship
├── submissions.html    # Manuscript submission form + guidelines
├── about.html          # Mission, editorial board, pillars
├── contact.html        # Contact form + social links
├── admin.html          # Editorial dashboard (password-protected)
├── data/
│   └── articles.js     # Central article registry — add articles here
├── brand_assets/
│   ├── logo.png        # Journal seal
│   ├── photos/         # Editorial board headshots
│   └── ...
└── pdfs/               # Published article PDF files
```

---

## Adding Articles

All published articles are managed through `data/articles.js`. To add a new article, append an entry to the `ARTICLES` array:

```js
const ARTICLES = [
  {
    title:    "Article Title Here",
    author:   "First Last",
    category: "Constitutional Law",   // see categories below
    abstract: "A 150–300 word summary of the article...",
    volume:   1,                      // integer
    issue:    1,                      // integer
    year:     2026,
    pages:    "1",                    // e.g. "1", "1-24"
    pdfPath:  "pdfs/filename.pdf",    // path relative to root, or null
    featured: true                    // true for one article per issue only
  }
];
```

**Available categories:**
`Constitutional Law` · `Criminal Law` · `Administrative Law` · `Civil Rights` · `Intellectual Property` · `International Law` · `Corporate Law` · `Environmental Law` · `Immigration Law` · `Family Law`

Once saved and pushed, the article automatically appears on:
- The homepage carousel (3 most recent)
- The scholarship page (with search/filter/pagination)
- The issues archive
- The editor's spotlight (if `featured: true`)

---

## Admin Dashboard

The admin panel at `/admin.html` allows editors to manage manuscript submissions received through the submission form.

- **Password:** `PLReview2025`
- **Actions:** Publish, Reject, Restore, Download PDF, Delete
- Submissions are stored in `localStorage` under the key `plr_submissions`
- Published submissions from the admin panel also appear on the scholarship page alongside `articles.js` entries

---

## Tech Stack

| Concern | Solution |
|---|---|
| Languages | HTML, CSS, JavaScript (vanilla) |
| Styling | Inline `<style>` per page, no shared stylesheet |
| CSS framework | None (custom properties + manual responsive) |
| Fonts | Google Fonts — Playfair Display, EB Garamond, Inter |
| Data | `data/articles.js` global array |
| Persistence | `localStorage` (submissions, messages, admin session) |
| Hosting | GitHub Pages |
| Build tools | None — static files served directly |

---

## Running Locally

```bash
# Python 3
python3 -m http.server 3000

# Node (if serve.mjs is present)
node serve.mjs
```

Then open `http://localhost:3000` in your browser. Do **not** open HTML files directly via `file:///` — some browser security policies will block `localStorage` and script loading.

---

## Editorial Board

| Name | Role |
|---|---|
| Duriya Khan | Editor-in-Chief |
| Qamryn Askew | Board Member |
| Sedat Sefik | Board Member |
| Evelyn Pearce | Board Member |
| Mehak Rizvi | Board Member |

---

## Deployment

The site is deployed via **GitHub Pages** from the `main` branch root.

To push updates:
```bash
git add .
git commit -m "describe your change"
git push origin main
```

GitHub Pages will reflect changes within ~60 seconds.

---

## Brand Colors

| Variable | Hex | Usage |
|---|---|---|
| `--gold` | `#F5B800` | Primary accent, CTAs |
| `--gold-dk` | `#D4A000` | Hover states, italic text |
| `--black` | `#0A0A0A` | Body text, navbar |
| `--charcoal` | `#1A1A1A` | Nav background, footer |
| `--red` | `#C8102E` | Category tags, required fields |
| `--off-white` | `#F8F5EF` | Section backgrounds |

---

*UMBC Pre-Law Review · University of Maryland, Baltimore County · Baltimore, MD 21250*
