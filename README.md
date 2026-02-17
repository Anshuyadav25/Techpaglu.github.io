# Techpaglu.github.io

## GitHub Pages fix for Marrow PYQs / Q-Bank pages

If a page opens and only shows text like:

- `version https://git-lfs.github.com/spec/v1`
- `oid sha256:...`

then that file was pushed as a **Git LFS pointer**, not as the real HTML page.

### Recommended fix

1. Keep normal site files in Git.
2. Do **not** store deploy-time HTML pages in LFS (GitHub Pages cannot render LFS pointers).
3. Untrack those files and commit actual HTML content:

```bash
git lfs untrack "Pathology_Edition_8_Q-Bank.html"
git lfs untrack "Microbiology_Edition_8_Q-Bank.html"
git lfs untrack "Pharmacology_Edition_8_Q-Bank.html"
git add .gitattributes *.html
git commit -m "Store Q-Bank HTML directly for GitHub Pages"
```

### If original files are too large

Split a big HTML into smaller files (for example: by subject/unit/year) and link those from `index.html`. This avoids LFS and improves load time.
