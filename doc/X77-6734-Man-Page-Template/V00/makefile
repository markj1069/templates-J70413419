# Three-Point Probability Distribution Annotated Bibliography Makefile

MAC = /usr/bin/m4
SED = /usr/bin/sed

.DEFAULT_GOAL := all
MAKEFLAGS += --no-print-directory

# Targets

.PHONY: all
.PHONY: clean
.PHONY: cleanall
.PHONY: html
.PHONY: man
.PHONY: pdf
.PHONY: yaml

# Make all the output forms: html, man & pdf.
all:	doc.o.mkd doc.o.yaml doc.m4
	pandoc doc.o.mkd \
    	--read=markdown --write=html5 \
    	--citeproc --bibliography=/mnt/d/db/Zotero/My-Library.yaml \
    	--metadata=link-citations --metadata-file=doc.o.yaml \
    	--standalone --shift-heading-level-by=-1 \
    	--output=doc.html

	pandoc doc.o.mkd \
    	--read=markdown --write=man --mathjax \
    	--citeproc --bibliography=/mnt/d/db/Zotero/My-Library.yaml \
    	--metadata=link-citations --metadata-file=doc.o.yaml \
    	--standalone --shift-heading-level-by=-1 \
    	--output=doc.man

	pandoc doc.o.mkd \
    	--read=markdown --write=pdf \
    	--citeproc --bibliography=/mnt/d/db/Zotero/My-Library.yaml \
    	--metadata=link-citations --metadata-file=doc.o.yaml \
    	--standalone --shift-heading-level-by=-1 \
    	--output=doc.pdf

# Update the intermediate YAML file.
doc.o.yaml yaml:	doc.m4 doc.yaml
	$(MAC) doc.m4 doc.yaml >doc.yaml.tmp # Build a usable YAML file.
	$(SED) -e '/(N\/A)/d' -e '/YYYY-MM-DD/d' doc.yaml.tmp >doc.o.yaml   # Remove unneeded Dublin Core Variables.

# Update the intermediate Markdown file.
doc.o.mkd:		doc.m4 doc.mkd doc.o.yaml
	$(MAC) doc.m4 doc.mkd >doc.o.mkd

# Make the HTML output file.
doc.html html:	doc.o.mkd doc.o.yaml doc.m4
	pandoc doc.o.mkd \
    	--read=markdown --write=html5 --mathjax \
    	--citeproc --bibliography=/mnt/d/db/Zotero/My-Library.yaml \
    	--metadata=link-citations --metadata-file=doc.o.yaml \
    	--standalone --shift-heading-level-by=-1 \
    	--output=doc.html

# Make the man page output file.
doc.man man:	doc.o.mkd doc.o.yaml doc.m4
	pandoc doc.o.mkd \
    	--read=markdown --write=man --mathjax \
    	--citeproc --bibliography=/mnt/d/db/Zotero/My-Library.yaml \
    	--metadata=link-citations --metadata-file=doc.o.yaml \
    	--standalone --shift-heading-level-by=-1 \
    	--output=doc.man

# Make the PDF output file.
doc.pdf pdf:	doc.o.mkd doc.o.yaml doc.m4
	pandoc doc.o.mkd \
    	--read=markdown --write=pdf \
    	--citeproc --bibliography=/mnt/d/db/Zotero/My-Library.yaml \
    	--metadata=link-citations --metadata-file=doc.o.yaml \
    	--standalone --shift-heading-level-by=-1 \
    	--output=doc.pdf

# Clean up the directory.
clean:
	@-rm -f core   2>/dev/null        # Remove code dumps.
	@-rm -f *~     2>/dev/null        # Remove backup files.
	@-rm -f *.bak  2>/dev/null        # Remove backup files.
	@-rm -f *.hold 2>/dev/null        # Remove temporary files.
	@-rm -f hold.* 2>/dev/null        # Remove temporary files.
	@-rm -f *.sed  2>/dev/null        # Remove sed commands.
	@-rm -f *.sql  2>/dev/null        # Remove sqlite3 commands.
	@-rm -f *.tar  2>/dev/null        # Remove tar archives.
	@-rm -f *.tgz  2>/dev/null        # Remove tar archives.
	@-rm -f *.tmp  2>/dev/null        # Remove temporary files.
	@-rm -f tmp.*  2>/dev/null        # Remove temporary files.
	@-rm -f *.txt  2>/dev/null        # Remove text files.

cleanall:
	@-make clean
	@-rm -f *.html 2>/dev/null        # Remove derived HTML files.
	@-rm -f doc.o.mkd 2>/dev/null     # Remove intermediate files.
	@-rm -f doc.o.yaml 2>/dev/null    # Remove intermediate files.
	@-rm -f doc.man 2>/dev/null       # Remove derived files.
	@-rm -f *.o    2>/dev/null        # Remove intermediate files.
	@-rm -f *.pdf  2>/dev/null        # Remove derived PDF files.
	@-rm -f *.1    2>/dev/null        # Remove derived man pages.
	@-rm -f *.2    2>/dev/null        # Remove derived man pages.
	@-rm -f *.3    2>/dev/null        # Remove derived man pages.
	@-rm -f *.4    2>/dev/null        # Remove derived man pages.
	@-rm -f *.5    2>/dev/null        # Remove derived man pages.
	@-rm -f *.6    2>/dev/null        # Remove derived man pages.
	@-rm -f *.7    2>/dev/null        # Remove derived man pages.
	@-rm -f *.8    2>/dev/null        # Remove derived man pages.
	@-rm -f *.9    2>/dev/null        # Remove derived man pages.

