# Build the CV. Requires a LaTeX engine on PATH (see README.md).
# Prefers tectonic (self-contained); falls back to pdflatex.

TEX      := cv.tex
PDF      := cv.pdf
# where the homepage links its CV (repo root); `make publish` copies there
PUBLISH  := ../cv_zzeng.pdf

.PHONY: all publish clean

all: $(PDF)

$(PDF): $(TEX)
	@if command -v tectonic >/dev/null 2>&1; then \
		echo ">> tectonic"; tectonic $(TEX); \
	elif command -v latexmk >/dev/null 2>&1; then \
		echo ">> latexmk -pdf"; latexmk -pdf -interaction=nonstopmode $(TEX); \
	elif command -v pdflatex >/dev/null 2>&1; then \
		echo ">> pdflatex x2"; pdflatex -interaction=nonstopmode $(TEX) && pdflatex -interaction=nonstopmode $(TEX); \
	else \
		echo "No LaTeX engine found. See README.md."; exit 1; \
	fi

# Copy the freshly built PDF to the filename the homepage links to.
publish: $(PDF)
	cp $(PDF) $(PUBLISH)
	@echo ">> published to $(PUBLISH)"

clean:
	rm -f *.aux *.log *.out *.fls *.fdb_latexmk *.synctex.gz
