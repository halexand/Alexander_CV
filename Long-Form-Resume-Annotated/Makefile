all: resume.pdf

clean:
	rm -rf *aux
#	pdflatex main.tex
#	sed -e "s/url\ =\ .*//g" publications.bib > tmp
#	sed -e "s/issn\ =\ .*//g" tmp > tmp2
#	sed -e "s/isbn\ =\ .*//g" tmp2 > tmp
#	mv tmp tmp2
#	sed -e 's/<i>/\\textit{/g' tmp2 > tmp
#	sed -e 's/<\/i>/}/g' tmp > tmp2
#	sed -e 's/CO2/\{CO\}\\textsubscript{2}/g' tmp2 > tmp
#	sed -e 's/<sub>12<\/sub>/\\textsubscript{12}/g' tmp > tmp2
#	TEXINPUTS="texmf:" pdflatex resume.tex
	
#	mv tmp2 publications.bib

resume.pdf: resume.tex presentations.bib publications.bib invitedpresentations.bib 
	TEXINPUTS="texmf:" pdflatex resume.tex
	bibtex resume
	bibtex pr
	bibtex ipr
	TEXINPUTS="texmf:" pdflatex resume.tex
	TEXINPUTS="texmf:" pdflatex resume.tex
	
	open resume.pdf -a /System/Applications/Preview.app/ 
