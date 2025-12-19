SRC=syllabus.yaml
HTML=$(SRC:.yaml=.html)
PDF=$(SRC:.yaml=.pdf)
TEX=$(SRC:.yaml=.tex)
INSTDIR=~/git-clones/deploy-2250/syllabus

all: $(HTML) $(TEX) $(PDF)
pdf: $(TEX) $(PDF)

.PHONY: figures

%.html: %.yaml FORCE
	pandoc --css=syllabus.css ../course_details.yaml --mathml $< -s -o $*.html

%.tex: %.yaml FORCE
	pandoc --template=template.latex defaults.yaml ../course_details.yaml $<  -s -o $*.tex

%.pdf: $(TEX) FORCE
	pdflatex $<  


FORCE:

install: $(HTML) $(PDF)
	mkdir -p $(INSTDIR)
	mkdir -p $(INSTDIR)/figures
	cp *.html $(INSTDIR)
	cp *.pdf $(INSTDIR)
	cp *.md $(INSTDIR)
	cp figures/* $(INSTDIR)/figures


clean:
	-@rm *~
	-@rm *.texe
	-@rm *.log
	-@rm *.aux
