FILE = index

pdf:
	rst2pdf $(FILE).rst $(FILE).pdf
	#rst2pdf --inline-links $(FILE).rst $(FILE).pdf

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
