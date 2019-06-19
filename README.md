# mkdocs-simple-demo

Simple CI/CD-enabled repository for demonstrating aspects of mkdocs

## License

The BSD license was chosen for maximum compatibility with the [`mkdocs`](https://github.com/mkdocs/mkdocs/) project.

## Purpose

The main purpose of this repository is for demonstrating bugs or issues with `mkdocs` in a simple public environment.

## Travis CI

Info on setting up a [simple mkdocs CI/CD pipeline](https://stackoverflow.com/questions/50892018/auto-build-an-mkdocs-documentation-in-travis-ci) was found on Stack Overflow. The setup here was modeled on that info.

### Travis CI app linked to GitHub

### [.travis.yml](.travis.yml)

The `GITHUB_TOKEN` variable needs to be defined in the Travis CI GUI as an environment variable for this repository.

## Output

The rendered markdown pages are found at [Simple public demo for mkdocs](https://sbonds.github.io/mkdocs-simple-demo/)
