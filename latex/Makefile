main = main
TEXFILES = $(addprefix ./, *.tex)
#BIBFILE = my.bib

#$(main).pdf: $(main).tex $(TEXFILES) $(BIBFILE) Makefile
$(main).pdf: $(main).tex $(TEXFILES) Makefile
	xelatex $(main)
	xelatex $(main)
	xelatex $(main)
	#bibtex $(main)
	#pdflatex $(main)
 
clean:
	rm *.aux *.dvi *.pdf *.log *.blg *.out *.bbl *.toc *.lof *.spl
