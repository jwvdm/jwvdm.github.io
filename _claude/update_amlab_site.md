# Syncing New Papers to the AMLab Website

## Role in the workflow

The personal website is the source of truth. After updating it, sync new entries here.

Full order of operations:
1. Update personal website — see `update_personal_site.md`
2. Sync to CV — see `update_cv_overleaf.md`
3. **Sync to AMLab website** (this document)

---

## Repository

`~/Cloud/Git/amlab-amsterdam/AMLab-Amsterdam.github.io/`

Updates must go through a pull request — **never push directly to `master`**.

### Branch workflow

```bash
git fetch origin
git checkout JanWillemUpdates
git rebase origin/master   # always sync before committing
# ... make changes ...
git push origin JanWillemUpdates
gh pr create --base master
```

---

## Bibliography files

| File | Purpose |
|---|---|
| `_bibliography/JanWillemVanDeMeent.bib` | All of Jan-Willem's publications (primary file to update) |
| `_bibliography/AMLab.bib` | Lab-wide publications — check for duplicates before adding |

Add every new paper to `JanWillemVanDeMeent.bib`. Also add to `AMLab.bib` if it is a lab paper (students or postdocs in AMLab are co-authors). Check `AMLab.bib` for an existing entry first — students sometimes add papers independently.

---

## Finding entries to add

Compare keys between the personal site and the AMLab bib:

```bash
# Keys in personal site (e.g. conference.bib)
grep -o '^@[a-zA-Z]*{[^,]*' ~/Cloud/Git/jwvdm/jwvdm.github.io/_bibliography/conference.bib | sed 's/^@[a-zA-Z]*{//'

# Keys already in AMLab bib
grep -o '^@[a-zA-Z]*{[^,]*' ~/Cloud/Git/amlab-amsterdam/AMLab-Amsterdam.github.io/_bibliography/JanWillemVanDeMeent.bib | sed 's/^@[a-zA-Z]*{//'
```

`recent.bib` on the personal site is a convenient starting point for the newest entries.

Also check by title+year for papers that may have different keys across the two sites.

---

## Format differences: personal site → AMLab

The AMLab site uses the same custom fields as the personal site. No fields need to be added or removed — **copy entries as-is**.

The only difference is that `AUTHOR+an` (used by the CV) is not needed here.

### Fields to keep

- `abbr` — used for badge display on the AMLab site (keep it)
- `html`, `pdf`, `code` — keep all
- `img` — keep if present (used by some AMLab templates)

### Author name braces

Ensure `{van de Meent}` braces are present, same as the personal site convention.

---

## Before-and-after example

**Personal site entry (`recent.bib`):**
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

**AMLab entry (copy as-is — no changes needed):**
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

---

## Checklist for each new entry

- [ ] Entry key not already in `JanWillemVanDeMeent.bib`
- [ ] Same paper not already present under a different key (check by title + year)
- [ ] Added to `JanWillemVanDeMeent.bib`
- [ ] Checked `AMLab.bib` for duplicates; added there too if it's a lab paper
- [ ] `{van de Meent}` braces present in author field
- [ ] Entry ordering consistent with surrounding entries (newest first within each year group)
- [ ] Committed to `JanWillemUpdates` branch (rebased onto `master` first)
- [ ] PR opened to `master`
