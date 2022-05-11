
# Test site

<https://flankspeed.sharepoint-mil.us.mcas-gov.us/sites/CPF-CNAF-FRAG/Lists/jTestJSONlist/jTestJSON2.aspx>

# JSON Builder

<https://pnp.github.io/List-Formatting/tools/html-formatter-generator/>

# Architecture

## List of persons

Views:
    1. Overview, short oneline per person
    2. Detail, full card view of person

## List of projects

Views:
    1. Overview, short oneline per project
    2. Detail, full card view of project

# MkDocs

`docker pull squidfunk/mkdocs-material`
`docker run --rm -it -v ${PWD}:/docs squidfunk/mkdocs-material build`
`docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material`
`[Docs](http://localhost:8000)`
