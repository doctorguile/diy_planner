MAIN_FILE = DYI_Main

PDFLATEX = pdflatex

MACRO_GENERATOR = ./gen_Current_Macros.py

FILES_TEX = DYI_Main.tex                \
            DYI_Year_Calendar.tex       \
            DYI_Monthly_Planner.tex     \
            DYI_Weekly_Planner.tex

# generated files
FILES_TEX_GEN = DYI_i18n.tex                   \
                DYI_Month_Tables.tex           \
                DYI_Monthly_Planner_Tables.tex \
                DYI_Weekly_Planner_Tables.tex

DEFAULT: $(FILES_TEX) $(FILES_TEX_GEN)
	$(PDFLATEX) $(MAIN_FILE)

$(FILES_TEX_GEN): $(MACRO_GENERATOR)
	$(MACRO_GENERATOR)

clean:
	rm -f $(FILES_TEX:.tex=.dvi)
	rm -f $(FILES_TEX:.tex=.aux)
	rm -f $(FILES_TEX_GEN:.tex=.aux)
	rm -f $(FILES_TEX_GEN)
	rm -f $(MAIN_FILE).log
	rm -f *~

realclean: clean
	rm -f $(MAIN_FILE).pdf

dist: clean
	cd .. ; \
	tar -czvf DIY_Organizer-dist_`date +%F`.tar.gz DIY_Organizer

realdist: realclean
	cd .. ; \
	tar -czvf DIY_Organizer-realdist_`date +%F`.tar.gz DIY_Organizer

installpkg:
	sudo apt-get update 
	sudo apt-get install -y texlive-latex-base texlive-fonts-recommended texlive-fonts-extra

#apt-get install pdftk pdfjam
#pdfnup 2018monthly.pdf --nup 2x1 --outfile 2018monthly2up.pdf
#pdftk DYI_2018.pdf cat 18-25 output 2018monthly.pdf

# links
# http://www.fountainpennetwork.com/forum/topic/312701-dot-paper-generator/
# https://michaelgoerz.net/notes/printable-paper-with-latex-and-tikz.html
# https://tex.stackexchange.com/questions/162403/creating-a-dotted-paper-pdf
# https://savorandsavvy.com/2017/02/dot-grid-paper-printable.html
# https://github.com/jrblevin/dot-grid-paper
