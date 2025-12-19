src=$(wildcard *.yaml)
tex=$(src:.yaml=_problem.tex)
sol=$(src:.yaml=_solution.tex)

all: $(tex) $(sol)

%_problem.tex: %.yaml force
	pandoc -f markdown+lists_without_preceding_blankline $< --template problem_template.latex -o $@
	sed -i 's/@\(q:[A-Za-z0-9_-]*\)/\\ref{\1}/g' $@

%_solution.tex: %.yaml force
	pandoc -f markdown+lists_without_preceding_blankline $< --template solution_template.latex -o $@
	sed -i 's/@\(q:[A-Za-z0-9_-]*\)/\\ref{\1}/g' $@

force: 
