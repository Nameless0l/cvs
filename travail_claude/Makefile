LATEXMK ?= latexmk
LATEXMK_FLAGS ?= -pdf -interaction=nonstopmode -halt-on-error

CV_TEX := $(wildcard cv_*.tex)
CV_PDF := $(CV_TEX:.tex=.pdf)

.PHONY: all cvs list clean rebuild

all: cvs

cvs: $(CV_PDF)

%.pdf: %.tex
	$(LATEXMK) $(LATEXMK_FLAGS) "$<"

list:
	@echo "CV sources:" 
	@for f in $(CV_TEX); do echo " - $$f"; done

clean:
	$(LATEXMK) -C $(CV_TEX)
	$(RM) $(CV_PDF)

rebuild: clean all

EXTENSIONS = aux fdb_latexmk fls log out toc lof lot bbl blg synctex.gz nav snm vrb idx ilg ind dvi

# Cible par défaut
.PHONY: clean help

clean-temp:
	@echo "Suppression des fichiers auxiliaires LaTeX..."
	@for %%e in ($(EXTENSIONS)) do @if exist *.%%e del /Q *.%%e 2>nul
	@echo "Nettoyage termine. Fichiers .tex et .pdf conserves."
	