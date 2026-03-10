EXTENSIONS = aux fdb_latexmk fls log out toc lof lot bbl blg synctex.gz nav snm vrb idx ilg ind dvi

# Cible par défaut
.PHONY: clean help

clean:
	@echo "Suppression des fichiers auxiliaires LaTeX..."
	@for %%e in ($(EXTENSIONS)) do @if exist *.%%e del /Q *.%%e 2>nul
	@echo "Nettoyage termine. Fichiers .tex et .pdf conserves."

# Version PowerShell (plus robuste)
clean-ps:
	@echo "Suppression des fichiers auxiliaires LaTeX (PowerShell)..."
	@powershell -Command "Get-ChildItem -Path . -Include *.aux,*.fdb_latexmk,*.fls,*.log,*.out,*.toc,*.lof,*.lot,*.bbl,*.blg,*.synctex.gz,*.nav,*.snm,*.vrb,*.idx,*.ilg,*.ind,*.dvi -Recurse | Remove-Item -Force"
	@echo "Nettoyage termine."

help:
	@echo "Commandes disponibles:"
	@echo "  make clean     - Supprime les fichiers auxiliaires (CMD)"
	@echo "  make clean-ps  - Supprime les fichiers auxiliaires (PowerShell)"
	@echo "  make help      - Affiche cette aide"
