
RST2LATEX_OPTS 	= --verbose --documentoptions=10pt \
	--use-latex-docinfo --use-latex-abstract --use-latex-citations \
	--graphicx-option=pdftex --stylesheet=fancyhdr,iwona,fullpage

all: nmap.pdf

%.tex: %.rst $(FIGURAS)
	rst2latex.py $< $(RST2LATEX_OPTS) $@

%.pdf: %.tex $(FIGURAS)
	pdflatex -interaction=nonstopmode $<

clean:
	-rm -rf *.aux *.log *.out *.tex

clean-all: clean
	-rm -rf *.png *.html *.pdf *.zip
