OUTPUT_FILES = output/notes.pdf output/requirements.pdf output/notes.html output/requirements.html
CSS_FILE=workshop.css

all: $(OUTPUT_FILES)

output/%.pdf: %.md
	filepp $< | pandoc -o $@

output/%.html: %.md $(CSS_FILE)
	filepp $< | pandoc -s --include-in-header $(CSS_FILE) -o $@

clean:
	rm -f output/*

.PHONY: clean
