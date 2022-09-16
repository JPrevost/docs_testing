# docs_testing

## Running jekyll locally

- install `jekyll`
- from project root:
  - `jekyll serve --incremental --source ./docs`

## Generating reference docs

- install `spectaql`
- from project root:
  - `spectaql --introspection-url <https://timdex-stage.herokuapp.com/graphql> -e -t ./docs/reference docs/reference/config.yml`
