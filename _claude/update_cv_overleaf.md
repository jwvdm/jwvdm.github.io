# Updating the CV BibTeX files from the Personal Website

## Workflow order

1. Update the personal website bib files (source of truth).
2. Sync new/changed entries to the Overleaf CV.
3. Sync new/changed entries to the AMLab website.

This document covers step 2 (personal website → CV).
For step 3, see `update_amlab_website.md` (if it exists).

---

## File locations

| Personal website (`~/Cloud/Git/jwvdm/jwvdm.github.io/_bibliography/`) | CV (`~/Cloud/Overleaf/jwvdm-cv-long/`) |
|---|---|
| `conference.bib` | `jwvdm-pubs-conference.bib` |
| `journal.bib` | `jwvdm-pubs-journal.bib` |
| `preprint.bib` | `jwvdm-pubs-preprint.bib` |
| `workshop.bib` | `jwvdm-pubs-workshop.bib` |
| `reports.bib` | `jwvdm-pubs-report.bib` |
| `patents.bib` | `jwvdm-pubs-patent.bib` |
| `recent.bib` | (not a CV file; homepage-only subset — use as a quick-check for newest entries) |
| `selected.bib` | (not a CV file; corresponds loosely to the commented-out `jwvdm-pubs-significant.bib`) |

---

## Finding entries to add

To find entries in the website bib that are missing from the CV bib, compare by entry key:

```bash
# Extract keys from website file
grep -o '^@[a-zA-Z]*{[^,]*' ~/Cloud/Git/jwvdm/jwvdm.github.io/_bibliography/conference.bib | sed 's/^@[a-zA-Z]*{//'

# Extract keys from CV file
grep -o '^@[a-zA-Z]*{[^,]*' ~/Cloud/Overleaf/jwvdm-cv-long/jwvdm-pubs-conference.bib | sed 's/^@[a-zA-Z]*{//'
```

Also check by title+year for papers that may have different keys in the two files.

`recent.bib` is a convenient starting point: it contains the newest papers across all categories and is what's shown on the homepage.

---

## Format differences: website → CV

When copying an entry from the website bib to a CV bib file, make the following changes:

### 1. ADD `AUTHOR+an` (required — most important step)

Every CV entry must have:

```bibtex
AUTHOR+an = {N=highlight},
```

where `N` is Jan-Willem's **1-based position** in the author list. Count his position carefully. His name appears in the author list as `{van de Meent}, Jan-Willem` (or variants without braces). This field causes his name to render in bold via biblatex annotations.

Example — Jan-Willem is author 7:
```bibtex
AUTHOR+an = {7=highlight},
```

### 2. REMOVE `abbr` field

The website uses `abbr = {ICML}` for badge display. The CV does not use this field — remove it.

### 3. REMOVE `img` field

If present (local asset path for the website), remove it.

### 4. KEEP `html`, `pdf`, `code` fields

These are harmless in the CV and useful for reference.

### 5. Author name braces (optional but preferred)

The CV prefers curly braces around the `van de` particle:

- Website may have: `van de Meent, Jan-Willem`
- CV prefers: `{van de Meent}, Jan-Willem`

Most website entries already use `{van de Meent}`, but check and add braces if missing.

### 6. Preprint `journal` field

The website uses `journal = {arXiv preprint}`. The CV uses this too for newer entries. Older CV entries use `journal = {arXiv:XXXX.XXXXX [cs, stat]}`. Either is fine; keep whichever is already set, or use `journal = {arXiv preprint}` for new entries.

---

## Before-and-after example

**Website entry:**
```bibtex
@inproceedings{matisan2026purrception,
  title = {Purrception: Variational Flow Matching for Vector-Quantized Image Generation},
  author = {Mati{\c{s}}an, R{\u{a}}zvan-Andrei and Hu, Vincent Tao and Bartosh, Grigory and Ommer, Bj{\"o}rn and Snoek, Cees G. M. and Welling, Max and {van de Meent}, Jan-Willem and Derakhshani, Mohammad Mahdi and Eijkelboom, Floor},
  booktitle = {International Conference on Learning Representations},
  year = {2026},
  abbr = {ICLR},
  html = {https://openreview.net/forum?id=SA8xDYrUYB},
  pdf = {https://arxiv.org/pdf/2510.01478}
}
```

**CV entry (after editing):**
```bibtex
@inproceedings{matisan2026purrception,
  title = {Purrception: Variational Flow Matching for Vector-Quantized Image Generation},
  author = {Mati{\c{s}}an, R{\u{a}}zvan-Andrei and Hu, Vincent Tao and Bartosh, Grigory and Ommer, Bj{\"o}rn and Snoek, Cees G. M. and Welling, Max and {van de Meent}, Jan-Willem and Derakhshani, Mohammad Mahdi and Eijkelboom, Floor},
  booktitle = {International Conference on Learning Representations},
  year = {2026},
  AUTHOR+an = {7=highlight},
  html = {https://openreview.net/forum?id=SA8xDYrUYB},
  pdf = {https://arxiv.org/pdf/2510.01478}
}
```

Changes: removed `abbr = {ICLR}`, added `AUTHOR+an = {7=highlight}`.

---

## Checklist for each new entry

- [ ] Entry key not already present in the CV bib file
- [ ] Same paper not already present under a different key (check by title + year)
- [ ] `AUTHOR+an = {N=highlight}` added with correct N
- [ ] `abbr` removed
- [ ] `img` removed (if present)
- [ ] `{van de Meent}` braces present in the author field
- [ ] Entry placed in correct file (conference/journal/preprint/workshop/report/patent)
- [ ] Entry ordering consistent with surrounding entries (newest first within each year group)
