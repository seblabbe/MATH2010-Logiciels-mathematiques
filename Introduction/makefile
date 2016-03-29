FICHIER = talk

$(FICHIER).pdf : $(FICHIER).tex
	pdflatex $(FICHIER).tex

deux:
	pdflatex $(FICHIER).tex
	pdflatex $(FICHIER).tex
	#open $(FICHIER).pdf

bib:
	pdflatex $(FICHIER).tex
	bibtex $(FICHIER)
	pdflatex $(FICHIER).tex

en:
	ln -sf language-en.tex language.tex

fr:
	ln -sf language-fr.tex language.tex

.PHONY : clean
clean :
	rm -f $(FICHIER).aux $(FICHIER).log $(FICHIER).vrb
	rm -f $(FICHIER).toc $(FICHIER).snm $(FICHIER).nav $(FICHIER).out
	rm -f $(FICHIER).sage $(FICHIER).sout $(FICHIER).py
	rm -f $(FICHIER).bbl $(FICHIER).blg
	rm -f $(FICHIER).pdf

