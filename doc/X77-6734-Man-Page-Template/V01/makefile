# Three-Point Probability Distribution Annotated Bibliography Makefile

MAC = /usr/bin/m4
SED = /usr/bin/sed
DOC = /usr/sbin/asciidoctor
PDF = /usr/sbin/asciidoctor-pdf

.DEFAULT_GOAL := all
MAKEFLAGS += --no-print-directory

# Targets

.PHONY: all
.PHONY: clean
.PHONY: cleanall
.PHONY: html
.PHONY: man
.PHONY: o
.PHONY: pdf


# Make all the output forms: html, man & pdf.
all:
	@-make html
	@-make man
	@-make pdf

# Create the AsciiDoc file that will feed into asciidoctor.
man.o o:	man.m4 man.adoc makefile
	@-$(MAC) man.m4 man.adoc >man.o     # Apply the variables to the AsciiDoc file.

# Make the HTML output file.
man.html html:	man.o
	@-$(DOC) --backend html5 man.o --out-file man.html

# Make the man page output file.
man.1 man:	man.o
	@-$(DOC) --backend manpage man.o --out-file man.1

# Make the PDF output file.
doc.pdf pdf:	man.o
	@-$(PDF)  man.o --out-file man.pdf

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
	@-rm -f *.8    2>/dev/null        # Remove derived man pages.

