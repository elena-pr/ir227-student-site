# IR227 student site

Built with [Quarto](https://quarto.org). Published via GitHub Pages from the
`docs/` folder on the `main` branch.

## Weekly workflow

1. Update materials in the TA bundle as usual (`../ta_edit`).
2. From this folder, pull the new files in and refresh the week pages:

   ```
   python3 tools/sync_materials.py
   ```

   This copies `slides-NN.pdf` and the weekly worksheet `.docx` into
   `content/<session>/` and rewrites the "Seminar slides" / "Worksheet"
   section for that week on `index.qmd` (the whole site is one long page).
   It leaves everything else alone — headings, the quick-link table, any
   notes you've added, and the "Case briefing" sections.
3. Preview locally:

   ```
   quarto preview
   ```

4. Render and publish:

   ```
   quarto render
   git add -A
   git commit -m "Update week NN materials"
   git push
   ```

   GitHub Pages serves straight from `docs/`, so once it's pushed the live
   site updates within a minute or two.

## Adding the shared case briefing links

The "Case briefing (shared document)" link under each week on `index.qmd`
is a placeholder (`TODO-add-shared-doc-link-here`) until you create the
actual shared Word Online doc for that case and paste its sharing link in by
hand. `tools/sync_materials.py` never touches this section, so it's safe to
edit directly and re-run the sync script afterwards.

## First-time setup (already done for you, for reference)

- `quarto` is installed at `~/quarto/bin` (added to `PATH` in `~/.zshrc`)
  since this machine doesn't have admin rights for the Homebrew cask.
- GitHub Pages needs to be pointed at `main` / `docs` folder in the repo's
  Settings → Pages, once the repo is pushed.
