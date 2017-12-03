# Minimal makefile for Sphinx documentation
#
GH_PAGES_SOURCES = docs/ code/
# You can set these variables from the command line.
SPHINXOPTS    =
SPHINXBUILD   = sphinx-build
SPHINXPROJ    = an_examply_pypi_project
SOURCEDIR     = source
BUILDDIR      = build

# Put it first so that "make" without argument is like "make help".
help:
	@$(SPHINXBUILD) -M help "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O)

.PHONY: help Makefile

gh-pages:
	git checkout gh-pages
	rm -rf * 
	git checkout master $(GH_PAGES_SOURCES)
	git reset HEAD
	(cd docs/ && make html)
	mv -fv docs/build/html/* ./
	rm -rf $(GH_PAGES_SOURCES)
	git add -A
	git commit -m "Generated gh-pages for `git log master -1 --pretty=short --abbrev-commit`" && git push origin gh-pages ; git checkout master

# Catch-all target: route all unknown targets to Sphinx using the new
# "make mode" option.  $(O) is meant as a shortcut for $(SPHINXOPTS).
%: Makefile
	@$(SPHINXBUILD) -M $@ "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O)
