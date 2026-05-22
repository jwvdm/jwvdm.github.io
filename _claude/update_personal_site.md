# Updating the Personal Website Bibliography

## Role in the workflow

The personal website is the **source of truth** for all bibliography entries.
Update it first, then sync to the CV and AMLab site.

Full order of operations:
1. **Update personal website** (this document)
2. Sync to CV — see `update_cv_overleaf.md`
3. Sync to AMLab website — see `update_amlab_site.md`

---

## Repository

`~/Cloud/Git/jwvdm/jwvdm.github.io/` — push directly to `main` (triggers deploy).

---

## Bibliography files

| File | Rendered where | Purpose |
|---|---|---|
| `_bibliography/recent.bib` | Homepage "Recent Papers" | 2024+ papers across all categories |
| `_bibliography/selected.bib` | Homepage "Selected Papers" | Key older papers (pre-2021 plus a few exceptions) |
| `_bibliography/preprint.bib` | Publications page "Working Papers" | arXiv preprints still under review |
| `_bibliography/conference.bib` | Publications page "Conference" | Full conference paper history |
| `_bibliography/journal.bib` | Publications page "Journal" | Full journal paper history |
| `_bibliography/workshop.bib` | Publications page "Workshop" | Workshop papers |
| `_bibliography/reports.bib` | Publications page "Reports" | Older unpublished papers |
| `_bibliography/patents.bib` | (not rendered) | Patent filings |

`recent.bib` and `selected.bib` are homepage-only subsets — they do not replace the category files.

---

## Adding a new preprint

1. Fetch metadata from arXiv.
2. Add entry to **`recent.bib`** (homepage).
3. Add entry to **`preprint.bib`** (publications page).
4. Push to `main`.

## Adding an accepted paper (no prior preprint entry)

1. Fetch final metadata (venue, booktitle/journal, year).
2. Add entry to **`recent.bib`** if 2024+.
3. Add entry to the appropriate category file (**`conference.bib`**, **`journal.bib`**, etc.).
4. Push to `main`.

## Promoting a preprint to accepted

1. Update the entry in **`recent.bib`**: change type (`@article` → `@inproceedings` etc.), set `booktitle`/`journal`, update `abbr`.
2. Update the entry in **`preprint.bib`** the same way, then **remove it** from `preprint.bib`.
3. Add the updated entry to the appropriate category file (**`conference.bib`** or **`journal.bib`**).
4. Push to `main`.

---

## Custom bib fields

| Field | Purpose |
|---|---|
| `abbr` | Badge label shown on site (e.g. `ICLR`, `arXiv`) |
| `html` | Link to paper webpage or arXiv abstract |
| `pdf` | URL or local path (e.g. `/assets/pdf/filename.pdf`) |
| `code` | Link to source code (GitHub etc.) |
| `img` | Thumbnail filename for homepage template |

---

## Format conventions

- **BibTeX key**: `lastnameYEARkeyword` (e.g. `roos2026categorical`, `eijkelboom2025controlled`)
- **Author field for Jan-Willem**: `{van de Meent}, Jan-Willem` (curly braces around the particle)
- **Entry order**: newest first within each year group
- `recent.bib` should only contain 2024+ papers

---

## Checklist for each new entry

- [ ] Correct BibTeX key (`lastnameYEARkeyword`)
- [ ] `{van de Meent}` braces present in author field
- [ ] Added to `recent.bib` if 2024+
- [ ] Added to `preprint.bib` if still a preprint
- [ ] Added to (or promoted in) the correct category file
- [ ] `abbr`, `html`, `pdf`, `code` fields filled where available
- [ ] Pushed to `main`
