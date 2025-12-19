SRC=$(filter-out defaults.yaml, $(wildcard *.yaml))
PDF=$(SRC:.yaml=.pdf)
TEX=$(SRC:.yaml=.tex)
INSTDIR=~/git-clones/deploy-2250/schedule

all: pdf
tex: course_schedule.tex
pdf: tex course_schedule.pdf

course_schedule.tex: course_schedule.yaml lab_schedule.yaml ../course_details.yaml defaults.yaml template.latex
	pandoc --template=template.latex defaults.yaml ../course_details.yaml course_schedule.yaml lab_schedule.yaml  -s -o $*.tex

course_schedule.pdf: course_schedule.tex 
	pdflatex $<  


FORCE:

install: $(PDF)
	mkdir -p $(INSTDIR)
	cp *.pdf $(INSTDIR)
	cp *.md $(INSTDIR)



clean:
	-@rm *~
	-@rm *.texe
	-@rm *.log
	-@rm *.aux
