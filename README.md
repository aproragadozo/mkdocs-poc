# What you need to try this out locally

Have a look at [mkdocs.org](https://www.mkdocs.org/).

## Prerequisites

I am using Python Markdown, an extensible flavour of Markdown, in this project, which is why you'll need Python and all these python libraries.

### Python 3.7

### Python libraries

These are all referenced in `mkdocs.yaml`, so the builder will complain if you haven't installed them.

Most of them provide features that (CommonMark) Markdown does not have out of the box, but which are essential for serious tech writing (like file transclusion).

Install them using `pip`.

* `mkdocs` - this one makes the whole project go

* `mdx_include` - this one lets you include the content of other files (as opposed to just giving you a link to the file)

* `pymdown-extensions`- this one is used in the project to achieve the tabbed code block (`superfences` in `mkdocs.yaml`) where each tab displays a different language code snippet, letting developers select their language of choice

* `mkdocs-material`- this is the Google Material theme for MkDocs. [There are many others](https://github.com/mkdocs/mkdocs/wiki/MkDocs-Themes).

* `yafg` - Yet Another Figure Generator. This one is, in my opinion, the easiest-to-use and most accessible image caption plugin for use with Python Markdown.

* `mkdocs-macros-plugin` - this gives you the ability to define variables in `mkdocs.yaml`, and use them in the docs.

* `mkdocs-htmlproofer-plugin` - this is supposed to give you link-checking, but it seems it only checks internal links. I'll need to investigate further.

* `uuid` - universally unique identifiers. I think this is a meta-prerequisite for `mkdocs`.

* `requests`, `bs4` (beautiful soup), and `urllib3` - these are also meta-prerequisites, necessary to run some of the others.

### The [**Table cell and row span** Python Markdown extension](https://github.com/Neepawa/cell_row_span)

You will need to install this extension (and possibly some of the other Python Markdown extensions listed above, without a pip installer, if installing with pip doesn't seem to work) by building its `setup.py` file, and then copying the resulting `cell_row_span.py` file in the `PYTHON_HOME\site-packages\markdown\extensions\` folder.

---
NOTE

I've removed this extension (commented it out in `mkkdocs.yml`) for now until I find out how to install it on the Travis CI build environment.

---

## Building

`mkdocs-build` creates a `site` folder in the root, whose contents you need to deploy.

You can, if you'd like, set up a different output folder with the `site_dir` setting in the `mkdocs.yml` config file.
