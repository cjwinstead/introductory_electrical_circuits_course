SRC=$(wildcard *.tikz)
PDF=$(SRC:.tikz=.pdf)
PNG=$(SRC:.tikz=.png)
SVG=$(SRC:.tikz=.svg)
DVI=$(SRC:.tikz=.dvi)

all: pdf png dvi svg

png: $(PNG)
dvi: $(DVI)
svg: $(SVG)
pdf: $(PDF)

%.pdf: %.tikz
	pdflatex -jobname=$* "\input{tikz_header} \begin{document} \input{$<} \end{document}"

%.dvi: %.tikz
	latex -jobname=$* "\input{tikz_header} \begin{document} \input{$<} \end{document}"

%.svg: %.dvi
	dvisvgm -n -TS2,2 $<

%.png: %.pdf
	convert -density 300 $< -quality 90 -sharpen 0x1 $*.png


clean:
	-@rm *~
	-@rm *.texe
	-@rm *.log
	-@rm *.aux
