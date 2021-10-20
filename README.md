# PlantUML demo

A repo to demonstrate how to generate markdown or asciidoc documents
that has PlantUML diagrams

> *PlantUML is a component that allows to quickly write both UML or non-UML diagrams* - [PlantUML.com](https://plantuml.com)

## Getting started

### Asciidoc artifacts

- Install asciidoctor

  ```bash
  $ [sudo] gem install asciidoctor asciidoctor-diagram asciidoctor-pdf \
                      asciidoctor-diagram-plantuml
  ```

- Generate pdf book

  ```bash
  $ asciidoctor-pdf PlantUML.adoc \
                    -r asciidoctor-diagram \
                    -D build
  ```
