now: exos

exos:
	pdflatex exos.tex
devoir1:
	pdflatex devoir1.tex
devoir2:
	pdflatex devoir2.tex

all: exos devoir1 devoir2

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

