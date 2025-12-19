PROJ=$(wildcard *.yaml)
TEX=$(PROJ:.yaml=.tex)
PDF=$(PROJ:.yaml=.pdf)
SOLN_TEX=$(PROJ:.yaml=_solution.tex)
SOLN_PDF=$(PROJ:.yaml=_solution.pdf)

.PHONY: figures problems

all: header.tex figures problems $(TEX) $(SOLN_TEX) $(PDF) $(SOLN_PDF)

header.tex: force
	pandoc ../../course_details.yaml $(PROJ) --template ../exam_template.latex -o header.tex

figures:
	make -C figures

problems:
	make -C problems

$(TEX): header.tex figures problems force
	cat header.tex > $@
	cat problems/*problem.tex >> $@
	printf "\n\\\\end{document}" >> $@

$(SOLN_TEX): header.tex figures problems force
	cat header.tex > $@
	cat problems/*solution.tex >> $@
	printf "\n\\\\end{document}" >> $@

%.pdf: %.tex force
	pdflatex $<
	pdflatex $<
	pdflatex $<


force: 
