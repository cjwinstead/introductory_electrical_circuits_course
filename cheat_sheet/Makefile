SRC=cheat_sheet.tex
PDF=$(SRC:.tex=.pdf)
PNG=$(SRC:.tex=.png)
SVG=$(SRC:.tex=.svg)
DVI=$(SRC:.tex=.dvi)

all: pdf png dvi svg

png: $(PNG)
dvi: $(DVI)
svg: $(SVG)
pdf: $(PDF)

%.pdf: %.tex FORCE
	pdflatex -jobname=$* "\input{tikz_header} \begin{document} \input{$<} \end{document}"

%.dvi: %.tex
	latex -jobname=$* "\input{tikz_header} \begin{document} \input{$<} \end{document}"

%.svg: %.dvi
	dvisvgm -n -TS2,2 $<

%.png: %.pdf
	convert -density 300 $< -quality 90 -sharpen 0x1 $*.png

FORCE:

clean:
	-@rm *~
	-@rm *.texe
	-@rm *.log
	-@rm *.aux
