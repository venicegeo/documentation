# Pelias Documentation

This repository contains the documation for Pelias as well as the markdown configuration for the Pelias documentation site.

## Table of Contents
*   [Read the Documentation](#just-the-docs)
*   [Building HTML Documentation](#building-html-documentation)
*   [Documentation Authors](#documentation-authors)

## Just the Docs

If you just want to read through the documentation start [here](docs/index.md).

## Building HTML Documentation

The delivery method for this documentation is a static HTML site.  We use
[MkDocs](http://www.mkdocs.org/) to generate the static files from the markdown
documents contained in this repo.

### Installation

#### Installing mkdocs

Mkdocs can be easily installed with Python. You'll need Python >= 2.7.2 and the
Python package manager, pip:

```
[~/workspace/pelias-docs]$ python --version
Python 2.7.2
[~/workspace/pelias-docs]$ pip --version
pip 1.5.2
```

Then install with:

```
$ pip install mkdocs
```

_For alternative installation instructions visit [www.mkdocs.org](http://www.mkdocs.org/#installation)._

#### Installing the Theme

The mkdocs configuration uses the material theme.
This theme can be easily installed with pip:
```
$ pip install mkdocs-material
```

_For alternative installation instructions see the [mkdocs-material documentation](https://squidfunk.github.io/mkdocs-material/getting-started/#installation)._

### Run the Development Server

To view the static site and see live changes when editing, run:

```
[~/workspace/pelias-docs]$ mkdocs serve
```

This will make the static site accessable on http://localhost:8000/

### Build the Documentation

You can build the documentation static site with the command:

```
[~/workspace/pelias-docs]$ mkdocs build
```

The build results will be available in the `site/` directory. This `site` dir will contain all you need in order to run the documentation site on a static file server.


An example build and deploy process could look like the following:

```
git clone https://github.com/venicegeo/pelias-documentation.git
cd pelias-documentation
mkdocs build
cd site
cf push pelias-docs -b staticfile_buildpack 
```

## Documentation Authors

All documentation that is intended to be distributed as part of the static
Pelias documentation site must be somewhere in the `docs/` directory and
should have the `.md` extension.

The behavior of `mkdocs` is controlled by the `mkdocs.yml` file in this
repo's root directory.  See [MkDocsConfiguration](http://www.mkdocs.org/user-guide/configuration/) for details.

Instructions on configuring the material theme can be found in the [MkDocsMaterial](https://squidfunk.github.io/mkdocs-material/) documentation.
For generic configuration see the [Getting Started](https://squidfunk.github.io/mkdocs-material/getting-started/#configuration) page. For more advanced customization see the [Customization](https://squidfunk.github.io/mkdocs-material/customization/) page.