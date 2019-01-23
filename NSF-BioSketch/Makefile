all: nsf-biosketch.pdf

clean:
	rm -rf *aux
	cp ../Long-Form/publications.bib .
	sed -e "s/url\ =\ .*//g" publications.bib > tmp
	sed -e "s/issn\ =\ .*//g" tmp > tmp2
	sed -e "s/isbn\ =\ .*//g" tmp2 > tmp
	mv tmp tmp2
	sed -e 's/<i>/\\textit{/g' tmp2 > tmp
	sed -e 's/<\/i>/}/g' tmp > tmp2
	sed -e 's/CO2/\{CO\}\\textsubscript{2}/g' tmp2 > tmp
	sed -e 's/<sub>12<\/sub>/\\textsubscript{12}/g' tmp > tmp2
	TEXINPUTS="texmf:" pdflatex nsf-biosketch.tex

	mv tmp2 publications.bib

nsf-biosketch.pdf: nsf-biosketch.tex publications.bib
	TEXINPUTS="texmf:" pdflatex nsf-biosketch.tex
	bibtex Relevant
	bibtex Other
	TEXINPUTS="texmf:" pdflatex nsf-biosketch.tex
	TEXINPUTS="texmf:" pdflatex nsf-biosketch.tex

	open nsf-biosketch.pdf -a /Applications/Preview.app
