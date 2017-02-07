FILE = index

pdf:
	rst2pdf $(FILE)-pdf.rst $(FILE).pdf
	#rst2pdf --inline-links $(FILE)-pdf.rst $(FILE).pdf

html:
	rst2html.py $(FILE).rst $(FILE).html

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

html-rougier:
	rst2html.py --link-stylesheet --cloak-email-addresses \
                --toc-top-backlinks --stylesheet=book.css,pygments_manni.css \
                --stylesheet-dirs=. $(FILE)-html.rst $(FILE).html
