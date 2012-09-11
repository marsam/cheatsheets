
PREAMBLE = "\usepackage[landscape=TRUE,margin=1.5cm,paper=a4paper]{geometry}"

RST2LATEX 	= rst2latex.py
RST2LATEX_OPTS	= --verbose --documentoptions=10pt \
		--use-latex-docinfo --use-latex-abstract --use-latex-citations\
		--graphicx-option=pdftex --stylesheet=fancyhdr,iwona \
		--latex-preamble=$(PREAMBLE)	#--table-style=booktabs

.PHONY: all clean clean-all

all: $(shell find . -name "*.rst" | sed 's/rst/pdf/')
	
%.tex: %.rst $(FIGURAS)
	$(RST2LATEX) $< $(RST2LATEX_OPTS) $@

%.pdf: %.tex $(FIGURAS)
	pdflatex -interaction=nonstopmode $<
	pdflatex -interaction=nonstopmode $<

clean:
	-rm -rf *.aux *.log *.out *.tex

clean-all: clean
	-rm -rf *.png *.html *.pdf *.zip
