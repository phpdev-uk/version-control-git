PDF_FILES = output/notes.pdf output/requirements.pdf

all: $(PDF_FILES)

output/%.pdf: %.md
		filepp $< | pandoc -o $@

clean:
	rm -rf *.pdf

.PHONY: clean
