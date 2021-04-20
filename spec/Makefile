doc:
	latexmk -pdf -shell-escape doc

comments:
	latexmk -pdf -shell-escape -jobname=comments -pdflatex="pdflatex %O '\def\withcomments{}\input{%S}'" doc
