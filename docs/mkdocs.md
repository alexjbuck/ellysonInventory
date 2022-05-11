# Welcome to MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

If you're using Docker:

* `docker pull squidfunk/mkdocs-material`
* `docker run --rm -it -v ${PWD}:/docs squidfunk/mkdocs-material new .`
* `docker run --rm -it -v ${PWD}:/docs squidfunk/mkdocs-material build`
* `docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material`
* `[Docs](http://localhost:8000)`

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
