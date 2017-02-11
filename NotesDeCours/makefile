FILE = index
OUTPUT = notedecours

pdf:
	rst2pdf $(FILE)-pdf.rst $(OUTPUT).pdf
	#rst2pdf --inline-links $(FILE)-pdf.rst $(OUTPUT).pdf

rst2ipynb:
	for file in ??-*.rst; do \
		echo -n "$$file";\
		sed "s/>>> /sage\: /g" $$file > tmp.rst;\
		fname=`echo "$$file" | sed "s/\.rst//"`;\
		sage -sh -c "rst2ipynb --kernel='python2' tmp.rst -o $$fname.ipynb";\
		echo -n " -> $$fname.ipynb\n";\
	done
	rm tmp.rst
	#TODO les tables sont ignorées dans les chap 2 et 9

html:
	rst2html.py --link-stylesheet --cloak-email-addresses \
                --toc-top-backlinks --stylesheet=book.css,pygments_manni.css \
                --stylesheet-dirs=. --syntax-highlight=short $(FILE)-html.rst $(OUTPUT).html

# To use pygments correctly, see:
# http://www.futurile.net/2015/08/07/writing-highlighting-code-restructured-text/
