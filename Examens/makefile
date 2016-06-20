all: reponse examens

old:
	pdflatex examen_pratiqueA.tex
	pdflatex examen_pratiqueB.tex
	pdflatex examen_theorie.tex

reponse:
	ln -sf reponsetrue.tex reponse.tex
	for X in pratiqueA pratiqueB theorie; do \
	    pdflatex examen_$$X.tex ;\
	    mv examen_$$X.pdf examen_$$X-solns.pdf ;\
	done

examens:
	ln -sf reponsefalse.tex reponse.tex
	for X in pratiqueA pratiqueB theorie; do \
	    pdflatex examen_$$X.tex ;\
	    mv examen_$$X.pdf examen_$$X-blanc.pdf ;\
	done

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

