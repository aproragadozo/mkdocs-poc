
[![Build Status](https://travis-ci.com/aproragadozo/mkdocs-poc.svg?branch=master)](https://travis-ci.com/aproragadozo/mkdocs-poc)

# What this is

This is a proof of concept for a documentation site that is automatically deployed whenever a GitHub repository is updated with Markdown content.

It currently uses [python-markdown](https://python-markdown.github.io/), [MkDocs](https://www.mkdocs.org/), [git subtrees](https://www.youtube.com/watch?v=sC1sfoCo5qY), [GitHub Pages](https://pages.github.com/), and [Travis CI](https://docs.travis-ci.com/).

Review comment support is a planned feature (probably using [GitHub Issues](https://help.github.com/en/github/managing-your-work-on-github/about-issues)).

<details><summary>Site Requirements</summary>

<ul>
<li><p>The documentation site should support multiple GitHub repositories - the site should be re-deployed if any of the dependent repositories are updated.</p>

<p>This is currently supported with git subtrees. Not ideal, because the editor needs to manually fetch updates from dependent repositories, but I haven't yet found a better solution. (Except for <a href="https://antora.org/">Antora</a>, which only supports AsciiDoc as content format.)</p></li>

<li><p>The documentation content needs to be created in Markdown.</p>

<p>The trouble with CommonMark, the quasi-standard Markdown implementation, is that it does not meet many of the requirements listed below, and is not extensible. This is why I chose python-markdown as source content format for this project. It has several built-in extensions that extend Markdown syntax with features, it is easy to extend further with supported third-party extensions, and in a pinch, perhaps I could write my own extension in Python if an unsupported feature is a must-have.</p></li>

<li><p>File transclusion (dynamically pulling the content of one file into another) needs to be supported.</p></li>

<li><p>Image captions, and dynamic links to image captions need to be supported, much like in reStructuredText.</p></li>

<li><p>Variables (e.g. for brand names, dates, or frequently recurring snippets of text or image) need to be supported.</p></li>

<li><p>A test suite needs to be supported.</p>

<p>Currently, Travis CI is only configured to deploy the automatically generated HTML files, but I am planning to run a spellchecker, a link checker, and style guide validation as part of the build.</p></li>

<li><p>Footnotes need to be supported.</p></li>

<li><p>Collapsible sections need to be supported.</p></li>

<li><p>Syntax-highlighted code blocks that dynamically reference external files (nice to have: in external repositories) need to be supported.</p></li>

<li><p>Tabbed code blocks that let the user switch between code snippets written in different programming languages need to be supported.</p></li>

<li><p>Table cells with merged rows and/or columns need to be supported.</p>

<p>I have chosen and made work the <code>cell_row_span</code> python-markdown extension locally. However, I haven't yet been able to integrate the extension with the Travis CI deployment. This feature is currently not supported, but fails relatively elegantly, that is, the tables are still displayed and styled, but cells do not span columns or rows.</p></li>

<li><p>Linking to specific anchor points and/or headings, not only to files as a whole, is supported.</p></li>

<li><p>Custom CSS styling of the output needs to be supported.</p>
</details>

# Try it for yourself

1. [Fork this repository](https://help.github.com/en/github/getting-started-with-github/fork-a-repo).

2. [Set up GitHub Pages deployment for it](https://guides.github.com/features/pages/).

3. [Sign up for a free Travis CI account](https://travis-ci.com/).

4. [Set up a Personal Access Token (PAT) for yourself on GitHub](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line).

5. [Encrypt the PAT, and replace the `secure` key with your encrypted key in the `.travis.yml` file](http://blog.code4hire.com/2016/06/adding-github-token-to-travis-ci-configuration/).

6. [Trigger a build](https://stackoverflow.com/questions/17606874/trigger-a-travis-ci-rebuild-without-pushing-a-commit), and hack away at the markdown source as you like.
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
