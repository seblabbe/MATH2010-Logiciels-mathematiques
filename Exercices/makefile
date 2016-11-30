FILE = exos

now:
	pdflatex $(FILE).tex

bib:
	pdflatex $(FILE).tex
	bibtex $(FILE)
	pdflatex $(FILE).tex
	pdflatex $(FILE).tex

.PHONY : clean
clean :
	rm -f *.aux *.log
	rm -f *.blg *.bbl
	rm -f *.toc
	rm -f *.tdo
	#rm -f *.pdf
	rm -f *.bcf
	rm -f *.brf
	rm -f *.out
	rm -f *.run.xml

