
[![Build Status](https://travis-ci.com/aproragadozo/mkdocs-poc.svg?branch=master)](https://travis-ci.com/aproragadozo/mkdocs-poc)

# What this is

This is a proof of concept for a documentation site that is automatically deployed whenever a GitHub repository is updated with Markdown content.

It currently uses [python-markdown](https://python-markdown.github.io/), [MkDocs](https://www.mkdocs.org/), [git subtrees](https://www.youtube.com/watch?v=sC1sfoCo5qY), [GitHub Pages](https://pages.github.com/), and [Travis CI](https://docs.travis-ci.com/).

Review comment support is a planned feature (probably using [GitHub Issues](https://help.github.com/en/github/managing-your-work-on-github/about-issues)).

## Requirements

* The documentation site should support multiple GitHub repositories - the site should be re-deployed if any of the dependent repositories are updated.

    This is currently supported with git subtrees. Not ideal, because the editor needs to manually fetch updates from dependent repositories, but I haven't yet found a better solution. (Except for [Antora](https://antora.org/), which only supports AsciiDoc as content format.)

* The documentation content needs to be created in Markdown.

    The trouble with CommonMark, the quasi-standard Markdown implementation, is that it does not meet many of the requirements listed below, and is not extensible. This is why I chose python-markdown as source content format for this project. It has several built-in extensions that extend Markdown syntax with features, it is easy to extend further with supported third-party extensions, and in a pinch, perhaps I could write my own extension in Python if an unsupported feature is a must-have.

* File transclusion (dynamically pulling the content of one file into another) needs to be supported.

* Image captions, and dynamic links to image captions need to be supported, much like in reStructuredText.

* Variables (e.g. for brand names, dates, or frequently recurring snippets of text or image) need to be supported.

* A test suite needs to be supported.

    Currently, Travis CI is only configured to deploy the automatically generated HTML files, but I am planning to run a spellchecker, a link checker, and style guide validation as part of the build.

* Footnotes need to be supported.

* Collapsible sections need to be supported.

* Syntax-highlighted code blocks that dynamically reference external files (nice to have: in external repositories) need to be supported.

* Tabbed code blocks that let the user switch between code snippets written in different programming languages need to be supported.

* Table cells with merged rows and/or columns need to be supported.

    I have chosen and made work the `cell_row_span` python-markdown extension locally. However, I haven't yet been able to integrate the extension with the Travis CI deployment. This feature is currently not supported, but fails relatively elegantly, that is, the tables are still displayed and styled, but cells do not span columns or rows.

* Linking to specific anchor points and/or headings, not only to files as a whole, is supported.

* Custom CSS styling of the output needs to be supported.

    Relying on a built-in python-markdown extension that offers identifiers and class attributes for elements.

* The documentation site must accept traceable review comments.

    This is a future feature.

# What you need to try this out locally
<!--
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

-->