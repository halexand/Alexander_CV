all: cv.pdf

clean:
	rm -rf *aux
#	pdflatex main.tex
	sed -e "s/url\ =\ .*//g" publications.bib > tmp
	sed -e "s/issn\ =\ .*//g" tmp > tmp2
	sed -e "s/isbn\ =\ .*//g" tmp2 > tmp
	mv tmp tmp2
	sed -e 's/<i>/\\textit{/g' tmp2 > tmp
	sed -e 's/<\/i>/}/g' tmp > tmp2
	sed -e 's/CO2/\{CO\}\\textsubscript{2}/g' tmp2 > tmp
	sed -e 's/<sub>12<\/sub>/\\textsubscript{12}/g' tmp > tmp2
	TEXINPUTS="texmf:" pdflatex cv.tex
	
	mv tmp2 publications.bib

cv.pdf: cv.tex publications.bib cv.bst cv.aux presentations.bib publications.bib invitedpresentations.bib 
	TEXINPUTS="texmf:" pdflatex cv.tex
	bibtex cv
	bibtex pr
	bibtex ipr
	TEXINPUTS="texmf:" pdflatex cv.tex
	TEXINPUTS="texmf:" pdflatex cv.tex
	
	open cv.pdf 
