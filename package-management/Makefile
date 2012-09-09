
PREAMBLE = "\usepackage[landscape=TRUE,margin=1.5cm,paper=a4paper]{geometry}"

RST2LATEX 	= rst2latex.py
RST2LATEX_OPTS	= --verbose --documentoptions=10pt \
		--use-latex-docinfo --use-latex-abstract --use-latex-citations\
		--tab-width=4 --literal-block-env=verbatim \
		--graphicx-option=pdftex --stylesheet=fancyhdr,iwona \
		--latex-preamble=$(PREAMBLE)	#--table-style=booktabs

help:
	@echo "You can use \`make <target>' where <target> is one of"
	@echo "  pdf         to make a nice pdf with LaTeX"
	@echo "  all         to make all pdf files"
	@echo "  clean       to clean intermediate files"
	@echo "  clean-all   to clean ALL intermediate files"

clean:
	-rm -rf *.aux *.log *.out *.tex

clean-all: clean
	-rm -rf *.png *.html *.pdf *.zip

all: $(shell find . -name "*.rst" | sed 's/rst/pdf/')
	
%.tex: %.rst $(FIGURAS)
	$(RST2LATEX) $< $(RST2LATEX_OPTS) $@

%.pdf: %.tex $(FIGURAS)
	pdflatex $< 
	pdflatex $<

