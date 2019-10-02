# What you need to try this out

Have a look at [mkdocs.org](https://www.mkdocs.org/).

## Prerequisites

### Python 3.7

### Python libraries

Install them using `pip`.

* mkdocs

* markdown-include

* pymdown-extensions

* mkdocs-material

* yafg

* mkdocs-macros-plugin

* mkdocs-htmlproofer-plugin

* uuid

* requests

* bs4

* urllib3

### The [**Table cell and row span** Python Markdown extension](https://github.com/Neepawa/cell_row_span)

Install this extension (and possibly some other Python Markdown extensions without a pip installer) by building its `setup.py` file, and then copying the resulting `cell_row_span.py` file in the `PYTHON_HOME\site-packages\markdown\extensions\` folder.

## Building

`mkdocs-build` creates a `site` folder in the root, whose contents you need to deploy.

Set up a different output folder with the `site_dir` setting in the `mkdocs.yml` config file.
