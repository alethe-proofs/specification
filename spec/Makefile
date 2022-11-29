backport:
	latexmk -pdf -pvc -interaction=nonstopmode -shell-escape -lualatex spec

comments:
	latexmk -pdf -shell-escape doc

doc:
	latexmk -pdf -shell-escape -jobname=comments -pdflatex="pdflatex %O '\def\nocomments{}\input{%S}'" doc
	
nonstop:
	latexmk -pdf -interaction=nonstopmode -shell-escape doc
