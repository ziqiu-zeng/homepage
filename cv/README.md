# CV (LaTeX source)

`cv.tex` is the single source of truth for the CV. Edit it, rebuild, publish.

## Edit

Personal details (name, role, email, links) are `\newcommand`s at the top of
`cv.tex`. Content lives under the clearly-labelled sections. To bold your own
name in a new publication, wrap it in `\me`.

> Note: the header email / Homepage / Google Scholar links were carried over
> from the old CV. The `\myscholar` URL is a placeholder — paste your real
> Google Scholar profile URL at the top of `cv.tex`.

## Build

No LaTeX engine is installed locally yet. Pick one:

- **Overleaf (zero install):** upload `cv.tex`, it compiles in the browser.
- **tectonic (single binary, recommended):**
  ```sh
  brew install tectonic
  make            # -> cv.pdf
  ```
- **Full TeX distribution:**
  ```sh
  brew install --cask mactex-no-gui   # or: brew install basictex
  make            # uses pdflatex
  ```

## Publish to the homepage

The homepage links `cv_zzeng_2026.docx.pdf` at the repo root
(`index.html:83`). After building:

```sh
make publish     # copies cv.pdf -> ../cv_zzeng_2026.docx.pdf
```

Or, to use a clean filename instead, rename the target and update the link in
`index.html` (line 83) to match.
