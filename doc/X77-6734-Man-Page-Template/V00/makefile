# Three-Point Probability Distribution Annotated Bibliography Makefile

MAC = /usr/bin/m4
SED = /usr/bin/sed

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

# Clean up the intermediate files.
clean:
	rm -f doc.o.mkd  doc.o.yaml *.tmp

# Clean up the intermediate and output files.
cleanall:
	rm -f doc.o.mkd  doc.o.yaml *.tmp
	rm -f doc.html doc.man doc.pdf

