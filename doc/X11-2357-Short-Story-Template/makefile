# Document Makefile

MAC = /usr/bin/m4
SED = /usr/bin/sed
LIB = /mnt/d/db/Zotero/My-Library.yaml
PAN = /usr/bin/pandoc
RMF = /usr/bin/rm


# Targets

.PHONY: all
.PHONY: clean
.PHONY: cleanall
.PHONY: html
.PHONY: pdf
.PHONY: yaml

all:	doc.o.mkd doc.o.yaml doc.m4
	$(PAN) doc.o.mkd \
    	--read=markdown --write=html5 \
    	--citeproc --bibliography=$(LIB) \
    	--metadata=link-citations --metadata-file=doc.o.yaml \
    	--standalone --shift-heading-level-by=-1 \
    	--output=doc.html
	$(PAN) doc.o.mkd \
    	--read=markdown --write=pdf \
    	--citeproc --bibliography=$(LIB) \
    	--metadata=link-citations --metadata-file=doc.o.yaml \
    	--standalone --shift-heading-level-by=-1 \
    	--output=doc.pdf

doc.o.yaml yaml:	doc.m4 doc.yaml
	$(MAC) doc.m4 doc.yaml >doc.yaml.tmp # Build a usable YAML file.
	$(SED) -e '/(N\/A)/d' -e '/YYYY-MM-DD/d' doc.yaml.tmp >doc.o.yaml   # Remove unneeded Dublin Core Variables.

doc.o.mkd:		doc.m4 doc.mkd doc.o.yaml
	$(MAC) doc.m4 doc.mkd >doc.o.mkd

doc.html html:	doc.o.mkd doc.o.yaml doc.m4
	$(PAN) doc.o.mkd \
    	--read=markdown --write=html5 --mathjax \
    	--citeproc --bibliography=$(LIB) \
    	--metadata=link-citations --metadata-file=doc.o.yaml \
    	--standalone --shift-heading-level-by=-1 \
    	--output=doc.html

doc.pdf pdf:	doc.o.mkd doc.o.yaml doc.m4
	$(PAN) doc.o.mkd \
    	--read=markdown --write=pdf \
    	--citeproc --bibliography=$(LIB) \
    	--metadata=link-citations --metadata-file=doc.o.yaml \
    	--standalone --shift-heading-level-by=-1 \
    	--output=doc.pdf

clean:
	$(RMF) doc.o.mkd  doc.o.yaml *.tmp

cleanall:
	$(RMF) doc.o.mkd  doc.o.yaml *.tmp
	$(RMF) doc.html doc.pdf
