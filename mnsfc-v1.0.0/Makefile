# Makefile for MNSFC Proposal Template
# 
# You want latexmk to *always* run,
# because make does not have all the info.
# Also, include non-file targets in .PHONY
# so they are run regardless of any
# file of the given name existing.
.PHONY: main pkg doc clean distclean all FORCE_MAKE help

NAME = mnsfc
VER = v1.0.0
ZIPNAME = $(NAME)-$(VER).zip
UTREE = $(shell kpsewhich --var-value TEXMFHOME)
LOCAL = $(shell kpsewhich --var-value TEXMFLOCAL)

# make without parameter will use make main
# rule of make: target can be object file or a label
# 	prerequisites are the target dependence (file or label)
# 	if prerequisites are newer than target use command to rebuilt
# target : prerequisites
# command

# latexmk: figure out all the LaTeX-related stuff
# -use-make: relying on the Makefile for the Non-LaTeX-related stuff
main : pkg $(NAME)-main.pdf

all : main doc

pkg : $(NAME).sty

doc : $(NAME).pdf

# Generate mnsfc.ins from mnsfc.dtx (internal section)
# The internal section is executed when compiling mnsfc.dtx with latex
$(NAME).ins: $(NAME).dtx
	latex -interaction=nonstopmode $(NAME).dtx > /dev/null 2>&1 || true

# '$@' is a variable holding the name of the target, and
# '$<' is a variable holding the (first) dependency of a rule.
$(NAME).sty: $(NAME).dtx $(NAME).ins
	latex -interaction=nonstopmode $(NAME).ins

$(NAME).pdf : $(NAME).dtx FORCE_MAKE
	latexmk -xelatex $<

$(NAME)-main.pdf : $(NAME)-main.tex $(NAME).sty FORCE_MAKE
	latexmk -xelatex -use-make $<

clean :
	latexmk -c
	latexmk -c $(NAME).dtx
	latexmk -c $(NAME)-main.tex
	rm -f $(NAME).dvi $(NAME).xdv
	rm -f $(NAME)-main.{nav,snm,vrb,xdv,dat,bbl,blg}

distclean : 
	latexmk -CA
	latexmk -CA $(NAME).dtx
	latexmk -CA $(NAME)-main.tex
	rm -f $(NAME).sty $(NAME).ins $(NAME).pdf $(NAME)-main.pdf

zip : pkg doc main
	mkdir -p $(NAME)-$(VER) 
	cp -rf $(NAME).{dtx,sty,pdf} \
	  README.md $(NAME)-main.{tex,pdf} \
	  $(NAME)-refs.bib Makefile .latexmkrc $(NAME)-$(VER)
	rm -rf *.zip
	zip -r $(NAME)-$(VER).zip $(NAME)-$(VER)
	rm -rf $(NAME)-$(VER)

help:
	@echo "MNSFC Proposal Template Makefile"
	@echo ""
	@echo "Available targets:"
	@echo "  make          - Compile the main document ($(NAME)-main.pdf)"
	@echo "  make pkg      - Generate $(NAME).sty from $(NAME).dtx"
	@echo "  make doc      - Generate documentation from $(NAME).dtx"
	@echo "  make all      - Generate sty, compile main document and doc"
	@echo "  make clean    - Remove auxiliary files"
	@echo "  make distclean - Remove all generated files including PDFs"
	@echo "  make zip      - Create distribution zip file"
	@echo "  make help     - Show this help message"
	@echo ""
	@echo "Note: Uses latexmk with XeLaTeX for compilation."
