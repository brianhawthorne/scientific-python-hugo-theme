.PHONY: help themes html serve clean
.DEFAULT_GOAL := help

help:
	@grep ": ##" Makefile | grep -v grep | tr -d '#'

themes/scientific-python-hugo-theme:
	@if [ ! -d "$<" ]; then \
	  echo "*** ERROR: missing theme" ; \
	  echo ; \
	  echo "It looks as though you are missing the themes directory."; \
	  echo "You need to add the scientific-python-hugo-theme as a submodule."; \
	  echo ; \
	  echo "Please see https://theme.scientific-python.org/user_guide/getstarted/"; \
	  echo ; \
	  exit 1; \
	fi

content/shortcodes.md:
	cp content/shortcodes.md.stub content/shortcodes.md

themes: themes/scientific-python-hugo-theme

html: ## Build site in `./public`
html: themes content/shortcodes.md
	hugo
	npx --yes pagefind --site public

serve: ## Serve site, typically on http://localhost:1313
serve: html
	@hugo --printI18nWarnings serve

clean: ## Remove built files
clean:
	rm -rf public
